# Meeting summaries

## CoRE @ IETF 109 (Virtual): Summary and Minutes

The core WG held two virtual sessions during IETF 109 held online.

---

The minutes for the two CoRE sessions are available at:

https://datatracker.ietf.org/meeting/109/session/core

https://codimd.ietf.org/notes-ietf-109-core

Thanks to the note takers Christian, Francesca, Michael and Göran!

---

The recordings of the two CoRE sessions are available at:

[Tuesday, November 17, 2020]
https://www.youtube.com/watch?v=aCiY4HS0-IY

[Friday, November 20, 2020]
https://www.youtube.com/watch?v=A70LOOSrfdg

---

Slides for the two CoRE sessions are available at:

* https://datatracker.ietf.org/meeting/109/session/core

* https://github.com/core-wg/wg-materials/tree/master/ietf109/slides

# Summary

## WG and document status

* RFC Editor Queue
    * draft-ietf-core-stateless-08

* IESG Processing:
    * draft-ietf-core-resource-directory-26: IESG Evaluation::AD Followup
        
* In Last Call
    * draft-ietf-core-dev-urn-08
    * draft-ietf-core-echo-request-tag-11

* In Post-WGLC processing:
    * draft-ietf-core-comi-10: under shepherd write-up
    * draft-ietf-core-sid-14: under shepherd write-up
    * draft-ietf-core-yang-cbor-13: under shepherd write-up
    * draft-ietf-core-yang-library-02: under shepherd write-up
    * draft-ietf-core-oscore-groupcomm-10: processed WGLC comments; one new review to process

## Resource Directory

* draft-ietf-core-resource-directory-26

Reviews from the IESG were processed and answered. Three open points will be addressed in version -27 coming in December, about DTLS replay protection, trusting links from the RD and ambiguities of Link Format. One point from Ben Kaduk requires an explicit follow-up.

## Stateless

* draft-ietf-core-stateless-08

The latest version addressed all comments left since May from IESG review. The remaining DISCUSS ballot was cleared up.

During the IETF week, the document was approved for publication as Proposed Standard and entered the RFC Queue.

## Groupcomm-bis

* draft-ietf-core-groupcomm-bis-02

The document aims at obsoleting RFC 7390 towards a Standards Track, now that there is a possible security mode for CoAP group communication. This version closes issues from earlier reviews.

Next steps include handling of multiple responses from a same server to a same request, cachability of responses and usage of ETAGs, and implementation tests.

Pending reviews: Christian and Francesca.

## Group OSCORE

* draft-ietf-core-oscore-groupcomm-10

This version addresses comments from the July WGLC and around IETF 108. The third round of interop tests occurred during the hackathon, with three different implementations, covering also the pairwise mode for message protection.

The main next step is running more tests and addressing a new review from Christian, covering among other points the need for a better distinction between anti-replay and freshness requirements. Other points to cover include optimization and generalization of the external_aad format.

## OSCORE Group Discovery

* draft-tiloca-core-oscore-discovery-07

Method to use the Resource Directory to find links for joining OSCORE groups at their Group Manager (GM). Full support for Link Format or CoRAL. 

Latest updates include an alignment with draft-ietf-ace-oscore-gm-admin as to the names of the application groups, and considerations on an application group using multiple security groups.

It was noted that the link relation between a security group and an ACE Authorization Server is a general thing that may be better handled in ACE, possibly as a dedicated document.

Next steps include adding parameters about the pairwise mode of Group OSCORE, alignment with upcoming updates to the Resource Directory document, more security considerations, and early tests among implementations.

## Multicast Notifications

* draft-tiloca-core-observe-multicast-notifications-04

Method to send observe notifications to a set of clients observing a same resource at the server, by using multicast responses. These are responses to a phantom observation request that the server creates.

Latest updates include encoding of informative response (transport-dependent and transport-specific information, flexible for non-UDP transport); improved rough counting of clients; added support for proxies.

Next steps will focus on improving the examples with proxies, the negotiation for client supporting this mechanisms or not, making some content optional, and specifying a possible server acting as its own OSCORE Group Manager.

The document has its core approach stable for a while now, and there has been interest for adoption from 12 people.

People to review: Göran and Carsten (since IETF 108), Jaime, Esko and Thomas.

## Groupcomm proxy

* draft-tiloca-core-groupcomm-proxy-02

Method for proxies to work in a CoAP group communication setting, addresses the related issues from draft-ietf-core-groupcomm-bis. The proxy forwards back to the client the individual responses from the servers, for an amount of time indicated by the client. The client can distinguish the different servers originating the responses and learn their addresses. Two new CoAP options are defined. Group OSCORE is possible between client and servers; any security between client and proxy.

Latest updates include improved semantics and encoding of the two new CoAP options, and support for a chain of forward proxies.

Next steps will focus on support for HTTP-to-CoAP cross proxies, to enable HTTP clients to talk to a group of CoAP servers.

Need for reviews; promised at IETF 108 are from Christian, Carsten and Francesca.

## OSCORE with EDHOC

* draft-palombini-core-oscore-edhoc-01

Different approaches to combine an execution of EDHOC with the first OSCORE exchange following it. The different approaches can also be signaled in different ways. The third and final EDHOC message from the client is merged with the first OSCORE request protected with the derived security context. This would reduce the overall number of roundtrips.

Following feedback from IETF 108, this update reduces the candidate approaches to the one using "EDHOC in OSCORE". The goal is now to select the exact way for signaling this approach, as either a flag bit in the OSCORE option or a dedicated new CoAP option (which seems preferred). Both ways require an IANA registration.

Need for reviews; promised at IETF 108 are from Christian and Carsten.

## SenML Versions

* draft-ietf-core-senml-versions-01

This version includes only minor updates; it needs reviews before WGLC. There is a working implementation from Ari.

Alexey reviewed preview versions. Need for more reviews before WGLC.

Will review this version: Jaime and Bill.

## SenML Data CT

* draft-ietf-core-senml-data-ct-02

Need to integrate the comments following the WGLC after IETF 108. After that, plan to request publication.

The document refers to draft-bormann-core-media-content-type-format (MCTF) , which would preferably be an adopted draft before this document is sent to the IESG.

It's not clear where MCTF belongs to (out of scope for EMAILCORE, very generic for CoRE), so it will go through DISPATCH. Alexey offered as shepherd for MCTF, while Barry can possibly sponsor it as AD.

## New Block

* draft-ietf-core-new-block-02

This update addresses all major points. The WG has decided to call the approach "Q-Block". Will submit -03 soon with minor additions, then need for more reviews (also about the usage of OSCORE), then WGLC.

Will review: Christian.

## Dynlink

* draft-ietf-core-dynlink-11

Work is ongoing on new parameters and their usage, also relevant in OMA LwM2M, i.e. 'pmin', 'pmax', 'edge' and 'con'. Related issues are open on Github for comments.

It seems reasonable to allow pmin == pmax. It's still open if and how this should support the presence of proxies, that are not used in LwM2M but have to be assumed in REST as scope of CoRE.

There will be more discussion at the next series of CoRE interim meetings.

## Fasor

* draft-ietf-core-fasor-01

Presented status and planned next steps; authors see the document as stable and needing for review, also from tsvarea. After addressing review comments, WGLC would be a target. Characteristics of the approach have been emulated but there are no plans for further evaluation.

Will review: Carles Gomez

CoRE chairs will approach tsvarea chairs for more reviews.

## CoAP over GATT

* draft-amsuess-core-coap-over-gatt-01

Presented updates on the exchange of CoAP messages on GATT, a mode of Bluetooth Low Energy, targeting applications with limited APIs. The goal is to gather implementation experience and have this as Experimental "This is how a few people do it" document.

There was consensus that it is good to extend support for CoAP on more environments/platforms, and that Experimental is the right type of target at the moment. It was noted that GATT specific new COAP URI scheme might need detailed examination.

## Rekeying for OSCORE and AEAD limits

* https://mailarchive.ietf.org/arch/msg/core/bbzZCt6ZZn4ysR7yLujPNscBF3g/

Depending on the used encryption algorithm, a safe limit exists in terms of performed encryptions or failed decryptions using the same key. Once passed the limit, the key should not be used any longer. This affects also OSCORE, especially when using CCM_8, and should be considered also for Group OSCORE.

Some preliminary assessment was presented, and more work is required to have a better model and better values to take as threshold. It has to be taken into account that CCM_8 is used today.

The immediate next step is a new draft where the problem is better documented and analyzed. Building on that, it will be possible to better understand if OSCORE needs a new lightweight, symmetric-key rekeying mechanism.

There will be more discussion at the next series of CoRE interim meetings.

---

# Meeting Minutes

# TUESDAY, November 17, 2020

Number of participants: @05:05 UTC 41, @06:15 UTC 47, @06:45 UTC 46

Meeting material: https://datatracker.ietf.org/meeting/109/session/core

Etherpad: https://codimd.ietf.org/notes-ietf-109-core

Meetecho video stream: https://meetings.conf.meetecho.com/ietf109/?group=core&short=&item=1

Audio stream: http://mp3.conf.meetecho.com/ietf109/core/1.m3u

Minute takers: Christian, Francesca, Marco (helping)

Jabber scribe: Marco and Jaime

**05:00 - 07:00 UTC**

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (10)

Jaime doing introductions, IPR policies, note-well, agenda etc.

* WG and document status

* IESG Processing:
    * draft-ietf-core-resource-directory-26: IESG Evaluation::AD Followup
    * draft-ietf-core-stateless-07: IESG Evaluation::AD Followup
        
* In Post-WGLC processing:
    * draft-ietf-core-dev-urn-08: AD Evaluation::AD Followup
    * draft-ietf-core-echo-request-tag-11: AD Evaluation::AD Followup 
    * draft-ietf-core-comi-10: under shepherd write-up
    * draft-ietf-core-sid-14: under shepherd write-up
    * draft-ietf-core-yang-cbor-13: under shepherd write-up
    * draft-ietf-core-yang-library-02: under shepherd write-up
    * draft-ietf-core-oscore-groupcomm-10: processed WGLC comments

## Resource Directory (Christian) (10)

* draft-ietf-core-resource-directory-26

   - Processed IESG review; remaining open points

Presenting update following IESG review - highlights.

Open points:
* DTLS replay protection should be considered -> #291 in github
* How much can you trust links from the RD? -> would like more discussion outside of RD doc
* Ambiguity on reading link format usage from RFC 6690, especially related to the 'Anchor' parameter; usage on the wire to be relaxed.
* -27 will come in December addressing three remaining points.

BL: Remember to followup on a point from Ben Kaduk.

GS: Can you elaborate more on verifying what the client really intended to do?

CA: (goes through slide)

GS: What to do about it?

CA: For the application to differentiate between what is a hint and what is a statement that is necessary to come from a trusted source.

FP: On the possibilities to explore, are they alternatives?

CA: Yes, they may be possible to combine, not part of the RD document itself. They can land on the work on CoRAL.

MG: Could you rely on link layer security?

CA: Link Layer security won't get you to origin server so it won't get any better security on the statement.

## Stateless (Michael Richardson) (10)

* draft-ietf-core-stateless-07

   - Discuss updates and open points

Stuck on review comments since May; several marked as WONTFIX.

Automatic Key Management issues: Precise key doesn't matter, as long as it's resisting a fast attacker. Replay window size needs to be considered carefully. Attacker can still replay seen tokens.

-08 just uploaded, DISCUSS just cleared. One more cycle may or may not be necessary.

BL: Let me know when you think it's ready to go, I'll give a final check.

MR: I think -08 is ready to go. Could have one word here or there, but minor editorial and nothing DISCUSS worthy.

BL: Will send out.

JJ: Klaus's positive comments this morning from issue tracker?

MR: Have not seen them yet. Will check.

JJ: Any last comments?

## Groupcomm-bis (Esko) (10)

* draft-ietf-core-groupcomm-bis-02

   - Discuss updates

Obsoleting RFC 7390 towards a standards track, now that there is a possible security mode.

-02 updates:
* Server may respond from different UDP port
* Response suppression based on code class
* Group definition (CoAP, application, security), added best practice
* FETCH, also with Observe and block-wise

Next steps:
* Handling multiple responses from same server in the application
* Cachability of responses, validity of caches
* Pending reviews (Christian, Francesca)
* Implementation tests for more exotic features

CB: Wouldn't be nice if we could send etags for all responses in cache?

ED: We are thinking about it

CA: We had a discussion at the hackathon about that. It would work. Only, the client wouldn't know if servers have collisions with each others' ETAGs.

CB: You would have to include server identifications together with the etags, which is why it becomes big and ugly.

CA: The client might send a request in a very small block size.

ED: Short message back, or first small block.

## Group OSCORE (Marco) (15)

* draft-ietf-core-oscore-groupcomm-10

   - Discuss updates following WGLC

Updates in -10: addressing WGLC and later comments.

Interop during hackathon with 3 implementations, including pairwise mode.

Algorithm and key parameters updated.

5.03 can be returned by the server as "I Don't Have A Recipient Context Right Now, come back soon".

Non-Recycling policies in GM: "Never ever reassign sender ID", based on latest review to be relaxed, see later. Group ID to never ever be re-assigned to the same group.

Single SSN space shared for both group mode and pairwise mode; SSN reset to 0 when a new context is established. Helps in understanding change of key material. Own SSN needed to use for the server, when answering a request across key changes (i.e. response protected with a context different than the one used to protect the request).

request_kid_context added to external_aad to allow observations across key changes, while still ensuring a notification cryptographically matches with only one observation request.

Observations: Client and server store original Group ID of the observation across rekeyings, if intended to survive key changes. The client additionally stores the invariant group identifier ("group name" in ACE documents).

From latest review:
* distinction between replay and freshness requirements, and related "synchronization" terminology.

* Appendix E to be updated from the surrounding discussions, E.1 and E.2 already follow from a correct implementation and can be removed.

* Loss of recipient context can happen due to server memory limitations.
    * Following an overflow of recipient contexts, new ones start with an invalid replay window. If the server cares about replays, it has to run an Echo exchange (getting also freshness) or be rekeyed. (To be clarified in next version)

* Relaxing non-recycling: "never ever" -> KIDs grow in size irreversibly. Relax to limit non-reusage only under a same GID -- can we?
    * GS: How do you make sure you actually only recycle when you've changed GID?
    * MT: It's under control of the GM, all managed there.
    * GS: So it's assigned from GM, OK.
    * ED: Group ID value, will that ever change?
    * MT: GID changes when key material changes, which happens when the GM decides that.
    * ED: Sounds safe to me.

* Converging on single external_aad format for both encryption and signing? Before adding 'request_kid_context', the encryption version mirrored the structure in OSCORE, now it's not the case anymore. So now we're deviating from OSCORE anyway, then maybe use single format for both?
    * GS: Sounds reasonable, but need to look at details.

* algorithms field: There's redundancy between parameters from algorithm and of keys. Trivial for implementation, but should we do this?
    * CA: Align with COSE.

* par_countersign: Can we generalize this for possible future algorithms to be admitted into COSE, which may have any number of capabilities. Currently, that'd still be what we have already hardcoded in the document.
    * ED: backward compatible or changes?
    * MT: Yes, just more flexible for possible future algorithms.
    * ED: So the definition is then future-ready. Sounds good.

## OSCORE Group Discovery (Christian) (10)

* draft-tiloca-core-oscore-discovery-07

   - Discuss updates and open points

CA presenting recap, updates from -07
* registration GM->RD and discovery of OSCORE groups node->RD
* names of application groups specified when creating the sec group, that makes the GM aware of them when registering the security groups in the RD
* multiple sec groups can be retrieved from a same app group, guidelines are given, more details are in draft-ietf-core-groupcomm-bis

next steps: more updates and reviews needed

ED: is this an optional thing (link of application to sec group)?
CA: someone needs to provide that information to the client. That someone needs to get all information from the GM. In principle this does not need to be done by the GM but it seems like the logical choice.

JJ: doesn't seem to be only tailored to OSCORE. 
CA: The retrieval of the link to the Authorization Server in slide 5 can be used more generically. Hope it gets picked up in ACE.
JJ: Do we need to coordinate with ACE?
MT: Several meetings ago it was mentioned as a possibility, with no hurry.

GS: What do you want to be picked up by ACE?
CA: The link relation between security group (link to join it) and the Authorization Server (link to get the token to join the group).

CB: Most important is to have the right security considerations. Clients that rely on this info retrieved in this way have to go through the right steps to validate it.

CA: In the current way ACE works: the client contacts resource server, gets back an unprotected response with that same link to the AS (just not in link format) and acts back on that.

FP: About ACE, I would say this would be a different document for ACE.

GS: There is time in the ACE agenda tomorrow, so why not present it there?

CA: Yes, will talk to the ACE chairs.

CB: As to an Authorization Server relationship with the client - how do you validate the server in the first place? Right now a client has to know all this information or it has to have a secret relationship with a Group Manager which has this validated information.

CB: The ace-actors document has been on hold, maybe resurrect and complete this now. Trust anchors are great, but whether trust anchors provide the right information, that requires more info.

CA: sounds like I have to spend more time with Ace.

CB: Maybe this is what we need IoT-OPS for. ACE stuck in OAuth path [?], need more comprehensive view of authorization flows. Onboarding discussion is a good source of information here; had that in T2TRG, and if IoT-OPS takes off, that may be good focal point.

JJ: any meeting for IOTOPS?

HB: No. Timing issue.

ED: advertising iotops mailing list from Jabber

## Multicast Notifications (Christian) (15)

* draft-tiloca-core-observe-multicast-notifications-04

   - Discuss updates and open points

Presenting what, why, how and updates.
- encoding of informative response (transport-dependent and transport-specific information, flexible for non-UDP tranport);
- improved rough counting of clients, building on feedback from Carsten
- given support for proxies, need some more fix also in the examples

Open points:
* Proxy examples need more work
* negotiation for client supporting this or not
* last notification in the informative response to become optional?
* add an appendix about how a server could be its own GM

JJ: I have it on the todo list to do a review of this one. Urgency?

CA: No. Important to make sure we converge on the understanding of the basic principles, which have not changed for a while now.

ED: intention the server becomes the GM for its own group? Advantage?

CA: Yes. that group would only be used between that server and that client. No larger audience than the audience of the server itself. This might be kind of a shortcut option.

FP: Adoption?

JJ: I understand Christian wants one more round.

CA: Not necessarily, if we have rough consensus on the basic approach. Work is needed on the details.

FP: For information, I am also authoring, I think it should move forward.

MT: Speaking as author, I agree with my co-authors.

JJ: Counting on Meetecho for interest in adoption:
- 12 say "Raise your hand"
- 1 says "Do not raise your hand"

Potential reviewers are Göran, Jaime and Carsten.
Other volunteers: Esko, Thomas

## Groupcomm proxy (Esko) (15)

* draft-tiloca-core-groupcomm-proxy-02

   - Discuss updates and open points

This specifies how proxying can be done towards groups: the client sends unicast, the proxy translates that to multicast, then forwards back responses.

Client indicates capability to handle responses, and its listening timeout, using a Multicast-Signaling option. Proxy includes Response-Forwarding option, so the client can distinguish the individual responses and the servers originating them.

Group OSCORE possible between client servers; any security between client and proxy.

-02 updates: clarifications on support for notifications, updated security considerations,  semantics and usage of the new CoAP options, chaining of proxies.

C->P option: Multicast-Signaling indicating response-forwarding time interval to the proxy. New: can be 0 (send request, don't forward responses), which should be paired with the No-Response option. Issues? (none raised)

P->C option: Response-Forwarding indicating network address. Helps client contact the server either through proxy or directly. This now has the servers' addressing information as address+port, rather than a URI which would have been more flexible for DNS resolution. OK anyway? (no objections).

Proxy chaining: Next hop configured except on last proxy in the chain. If there's a long chain a proxies, a proxy may not determine a feasible timeout value to pass on that would work. In that case, return 5.05 to the previous hop, including the minimum timout acceptable time value in a Multicast-Signaling option.

OSCORE between client and proxy can coexist with group OSCORE between client and servers. In the client-proxy leg, this means protecting some options as class E, rather than as class U as usual. We list some of those options. Can we have a future-proof general rule to identify these Class-U-to-E options? Shown a proposal; good enough? anything simpler?

CA: it should be ok to apply that simply to all options that the proxy needs to understand and process.

Next steps: enable HTTP-to-CaAP cross proxying; this would enable HTTP clients to talk to a group of CoAP servers.

We need reviews, some promised at IETF 108 from Christian, Carsten and Francesca.

## OSCORE with EDHOC (Francesca) (10)

* draft-palombini-core-oscore-edhoc-01

   - Discuss updates and open points

Postponed to the Friday session.

## Flextime (15)

Σ 120

---

# FRIDAY, November 20, 2020

Number of participants: @09:07 UTC 55, @10:16 UTC 58, @10:49 UTC 55

Meeting material: https://datatracker.ietf.org/meeting/109/session/core

Etherpad: https://codimd.ietf.org/notes-ietf-109-core

Meetecho video stream: https://meetings.conf.meetecho.com/ietf109/?group=core&short=&item=2

Audio stream: http://mp3.conf.meetecho.com/ietf109/core/2.m3u

Minute takers: Michael Richardson, Göran Selander and Marco (helping)

Jabber scribe: Marco

**09:00 - 11:00 UTC**

Numbers in parentheses are minutes of time allocated.

## Intro, agenda (5)

Some documents have move forward yesterday.

- stateless was approved by IESG, and entered the RFC-EDITOR Queue.
- dev-urn entered LAST CALL
- echo-request-tag entered LAST CALL

## OSCORE with EDHOC (Francesca) (10)

* draft-palombini-core-oscore-edhoc-01

JM: Should probably not use the last remaining flag bit of the first flag byte. Better to save that for other stuff that are sent in every message.
-> Agreed, do not use last flag bit.
-> prefer to register a new CoAP option. 
[Minute taker Göran's comment: I think the conclusion above is wrong. John's comment was that to not use the last flag bit of the first flag byte, but a flag bit in the second flag byte.]

CB: will the new option really be one byte?

FP: the option will be empty.
CA: yes, if the delta is less then 13 from the previous CoAP option.

FP: both alternatives require an IANA registration, either for a flag bit in the OSCORE option, or for a new CoAP option.

CB: Let's grab the option number.

GS: Stefan Hristozov planned to implement, we should check with him about status and his preference.
    
Discussion about how to get a CoAP option number through IANA, it can be an early registration through the WG chairs; to be taken to the list.

CA (on Jabber): CoAP option numbers in that range are "IETF Review or IESG Approval", which is what Early Allocation works for

JM (on Jabber): Having it in a new EDHOC option makes it clearer that this includes EDHOC, without digging into the OSCORE option.

FP: There seems to be a preference for specifying an EDHOC option.
   
## SenML Versions (Carsten) (5)

* draft-ietf-core-senml-versions-01

CB: Minor edits in the latest -01; waiting for reviews (promised from Bill and Jaime), before moving to WGLC. Are there any implementations?

AK: I have implemented it, seems to be working.

MG: If you are not using version, what is your solution?

MR: the actual problem is using NUMBERS (monotonically incrementing integers), not versions per se, this sets bits

AM (on Jabber): every bit is a feature (used if set)

AM: I did review earlier versions, looks sensible

BS: I commit again to review in the next days.

JM (on Jabber): Version numbers vs. bitfield remind me of discussion of negotiating cipher suites vs. negotiating individual algorithms in IPsec/TLS. Benefits/disadvantages with both. For many applications the best solution might be a combination of the two approches. 

## SenML Data CT  (Carsten) (10)

* draft-ietf-core-senml-data-ct-02

CB: Since IETF 108, WGLC happened, then comments followed. Plan to integrate the comments, then ship to the IESG.

MG: Question about the use case that the draft addresses.

CB: Indicate a content format when binary data are sent in SenML, using a new CT field.

MG: Ok.
   
AM: Does the referenced draft (draft-bormann-core-media-content-type-format) need to be DISPATCHed? If I remember correctly, the referenced draft doesn't belong to EMAILCORE or CORE

BL: It's certainly not in scope for EMAILCORE.

AM: And it's very generic for CoRE.

BL: So, yes, take it to DISPATCH.

AM: I volunteer to shepherd it.
   
CB: Can we submit this to the IESG with the reference dangling? It happens often.

BL: No particular opinion on it. If a normative reference is not ready, the RFC Editor holds on anyway. We're good as long as a referred document is available for people that reviews.

CB: It would be good if the referenced draft was adopted before IESG submission of this data-ct document

AM (in Jabber): Barry could potentially AD-sponsor the referenced draft.

## New Block (Jon) (15)

* draft-ietf-core-new-block-02

JS: Naming of block, poll resulted in "Q-Block", but may not work globally

MR, CA, IM: preference for "Tough Block"

MB, JJ, MG: preference for "Q-Block"

Tie between "Q-Block" and "Tough Block". Authors prefer "Q-Block", so WG decided on that.

Discussion on whether we can tolerate the ack timeout?

JJ: More reviewers?

Christian Amsüss volunteers

JS: Will soon submit -03 (minor change), then we would target WGLC.

MR: What security is required? Can it be used with OSCORE?

CA (in Jabber): Will be covered in my review

MR (in Jabber): OSCORE does not validate the originating IPaddress, I think.

JM (in Jabber): TLS, DTLS and ESP does not validate IP address either, you need AH for that.
   
MR (in Jabber): If I see (offpath possibly) a valid OSCORE + Q-Block request, I can change the IP address and send it again.

## Dynlink (Bill) (10)

* draft-ietf-core-dynlink-11

BS: The epmin and epmax parameters are included in the editor's copy.
   
Open issues on allowing pmin == pmax
   - Impact on current wording in the draft; related suggestions for OMA.

AM (in Jabber): it is reasonable to allow this

   Latest OMA specification: http://www.openmobilealliance.org/release/LightweightM2M/V1_2-20201110-A/

Another open issue is about the new "edge" attribute

CA: How does this work with a proxy?

Another open issue is about the new "con" attribute, about sending notifications on confirmable transports. What does confirmable mean exactly?

   - DN: If CoAP over UDP, use CON messages.
   - CA: This works for origin servers, but it does not work for proxies. Assume you set up an observation. If CON attribute is set, the proxy needs to decide on how to send the notification on. You can request the server to do this, but you can't expect it to work along the whole end-to-end chain of nodes.
   - JJ: This applies also to other attributes. This is the time for the WG to discuss this.
   - HT: In LwM2M there are no proxies.
   - CA: If you want this to work with REST, then you have to assume the existence of proxies. This is the scope of CoRE. 
   - JJ: Need to set up an interim meeting to discuss this.

BS: Please comment on the Github issues.

There will be discussions also at coming interims, focus on end-to-end and hop-by-hop.

## Fasor (Markku) (10)

* draft-ietf-core-fasor-01

MK: Status and next steps, need reviews and feedback also from the transport area, WGLC would be a target after integrating those comments.

CG: Important work. Do you have a plan for further evaluation of this mechanism?

MK: Currently no plans. We have emulated characteristics. More tests are welcome.

JJ: Reviewers? Needed to progress the draft. We'll check with the chairs of the transport area for possible reviewers there.

CG: I can review within ~2 months

## CoAP over GATT (Christian) (15)

* draft-amsuess-core-coap-over-gatt-01

CA: Discuss updates. Is this a good work to do?

JM (in Jabber): Making sure that CoAP can be used in more environments/platforms is a good thing. BLE is popular. Experimental seems correct.

CB: +1

AM: Experimental sounds good at the moment.

JJ: (in Jabber): back on the scheme discussion: coaps+tcp:// coaps+bluetooth:// , etc.

MG: Why is this not done in 6lo?

CB: 6lo is IP over foo. This is not IP.

MR: How is bluetooth authenticated?

CA: Opportunistic authentication in Bluetooth. Rely on higher layer end-to-end security.

MG: If it is not IP, why in the IETF?

MR/CB: Because CoAP is in the IETF.

CB: Comparable to https://tools.ietf.org/html/draft-bormann-t2trg-slipmux-03

AM (from Jabber): GATT specific new COAP URI scheme might need detailed examination. This was rather contentious in the past.

CB: Good stuff

## Rekeying for OSCORE and AEAD limits (John) (20)

* https://mailarchive.ietf.org/arch/msg/core/bbzZCt6ZZn4ysR7yLujPNscBF3g/

JM: Discuss the issue; maximum encryptions or maximum failed decryptions (modeled as 'q' and 'v') before needing to rekey; rekeying in OSCORE or with EDHOC

JM: We may need something lightweight with the right properties; something similar will be needed in Group OSCORE too

JM: Plan to have a new draft discussing the problem according to the two parameters q and v, and what more is needed.

BK (on Jabber): I don't think we had a huge amount of justification for the 2**(-60) and 2**(-57) bounds in TLS, FWIW

BK: I think "might not close the connection and might send an error message saying please rekey" is not strictly keeping with the theory behind these limits. Perhaps if you only send it once and then close the connection it is close enough
   
CB (on Jabber): The main reason why we never switched away from CCM is that it is much less brittle, or in today's parlance, it is moderately misuse-resistant. Since more misuse-resistant modes are coming up, there might be a time to reconsider.

JM (on Jabber): I think sending an error message without verifying the ciphertext would not give the attacker any more information.

Verifying without using the plaintext would give the attacker some additional information. In GCM the attacker would get quite a lot of information regarding the authentication key but it would not matter. In CCM the attacker gets very little information as shown in the multi-forgery paper by mcgrew et al.

GS: We need to go also through what is used today (CCM_8) and find ways to handle it.

CB (on Jabber): Sure

MR (on Jabber): Yes, we need to talk about EDHOC+DTLS/OSCORE/CCM_8-rekey as a group.

MG: Any group in mind that can provide feedback?

GS: For instance industry groups that use CCM_8, which is MTI for CoAP

This is material for future interim meetings.

Σ 120

---

*[MT]: Marco Tiloca
*[JJ]: Jaime Jiménez
*[GS]: Göran Selander
*[JM]: John Mattsson
*[FP]: Francesca Palombini
*[CB]: Carsten Bormann
*[CA]: Christian Amsüss
*[KH]: Klaus Hartke
*[BS]: Bill Silverajan
*[NW]: Niklas Widell
*[IP]: Ivaylo Petrov
*[MR]: Michael Richardson
*[BL]: Barry Leiba
*[AK]: Ari Keränen
*[JS]: Jon Shallow
*[MB]: Mohamed Boucadair
*[AS]: Alan Soloway
*[BL]: Barry Leiba
*[MG]: Matthew Gillmore
*[ED]: Esko Dijk
*[HB]: Henk Birkholz
*[MG]: Matthew Gilmore
*[MB]: Mohamed Boucadair
*[DN]: David Navarro
*[CG]: Carles Gomez
*[MK]: Markku Kojo
*[HT]: Hannes Tschofenig
*[BK]: Benjamin Kaduk
*[AM]: Alexey Melnikov

