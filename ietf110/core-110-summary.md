# Meeting summaries

## CoRE @ IETF 110 (Virtual): Summary and Minutes

The core WG held two virtual sessions during IETF 110 held online.

---

The minutes for the two CoRE sessions are available at:

https://datatracker.ietf.org/meeting/110/session/core

https://codimd.ietf.org/notes-ietf-110-core

Thanks to the note takers Michael Richardson, Göran Selander and Rikard Höglund!

---

The recordings of the two CoRE sessions are available at:

[Monday, March 8, 2021]
TBD

[Friday, March 12, 2021]
TBD

---

Slides for the two CoRE sessions are available at:

* https://datatracker.ietf.org/meeting/110/session/core

* https://github.com/core-wg/wg-materials/tree/master/ietf110/slides

# Summary

TBD

---

# Meeting Minutes

# Monday, March 8, 2021

Number of participants: 16:10 (44); 16:50 (50); 17:30 (52)

Meeting material: https://datatracker.ietf.org/meeting/110/session/core

Etherpad: https://codimd.ietf.org/notes-ietf-110-core?both

Meetecho video stream: https://meetings.conf.meetecho.com/ietf110/?group=core&short=&item=1

Audio stream: http://mp3.conf.meetecho.com/ietf110/core/1.m3u

Minute takers: Michael Richardson, Göran Selander, Marco Tiloca (helping)

Jabber scribe: Marco Tiloca

**16:00 - 18:00 UTC**

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (10)

huzzah for new working group chairs (jaime has a new child)

* WG and document status

Two sessions, Monday + Friday, agenda trying to avoid conflict with Friday's DANISH BOF.

## Groupcomm-bis (Esko) (15)

* draft-ietf-core-groupcomm-bis-03

   - Discuss updates and open points

ED: Latest updates include also support for reverse proxies.

ED: Also added caching of responses; this requires two types of cache entries at the proxy, i.e. "aggregated" cache entries and "individual" cache entry.

ED: A validation model is also defined, between client and servers with a new Multi-ETag option, and between client and proxy with a new Group-ETag option. If you want to go through multiple proxies, then you need multiple tags.

GS: Why would I want to validate a number of reports at the proxy with Group-ETag?

ED: Say you're querying a number of device status reports, and one is large and the client doesn't want to get it sent again. The last full collection of reports at the proxy is still valid in its entirety.

CB: Is the Multi-ETag option actually repeatable?

MT: It is mimicking the ETag option.

ED: If Group OSCORE is used end-to-end, cacheability can still be achieved using the deterministic requests of draft-amsuess-core-cachable-oscore. However, this is limited end to end between client and servers, with response validation also still possible although trading flexibility against efficiency of caching at the proxy. Instead, no validation involving the proxy as active aware party is possible (i.e., the proxy can't use the Multi-ETag option as if it was client, and clients can't use the Group-ETag option with the proxy).

CA: We should treat the E-Tag options in the draft-tiloca-core-groupcomm-proxy document that would progress at its own pace, so that this new content does not hold this document.

CB: Agree.

ED: That's easy to imagine for the Group-ETag option as really related to proxies. But where should the Multi-Etag option be? It's not directly related to proxy operations.

CA: Right, but it uses the transport information structure and encoding defined in the proxy document to identify a server, so that may still be a good place.

ED: Next steps are about addressing open Github issues; moving some content to the rights places / different documents; implements aspects involving e.g. observe and blockwise.

## Group OSCORE (Marco) (15)

* draft-ietf-core-oscore-groupcomm-11

   - Discuss updates following WGLC and new open points

Marco presenting.

MT: updates in -11 address Christian's review ...

https://mailarchive.ietf.org/arch/msg/core/pXEyxhbf-s2wgGDzrDhUNPsHZZc/

... and more points agreed on during IETF 110.

MT: New open point 1: Observations and GIDs. Currently forbidden to recycle GID values, to prevent bad things when using observation. Solution: the Group Manager stores also the "birth GID" of each group member, i.e. the GID that the group uses when that member joins. If, upon rekeying, the Group Manager would set as new GID the "birth GID" of any current group members, the rekeying has to exclude also those nodes, cancelling their membership. They will eventually rejoin, thus closing all ongoing observations, thus solving the problem. Then GID values can be recycled and a group can "live forever". It just requires some additional mechanics and storing of the various birth GIDs on the Group Manager.

No objections to do the change.

MT: New open point 2, also in Github issues #72, #73. Using the same identity key for two purposes, i.e. signing and Diffie-Hellman key derivation for the pairwise mode. Not really a common practice, need to be proven secure. Point raised by Ben Kaduk

https://mailarchive.ietf.org/arch/msg/core/ujj_I-LlqW9fq__quh-YqKS0fF0/

MT: There's ongoing work by Ericsson to produce a proof that what we are doing is secure, possibly with minor adaptation to the key derivation process. An alternative would be to have and provide separate signature and DH keys (which could be done in https://datatracker.ietf.org/doc/draft-ietf-ace-key-groupcomm-oscore/), but it would mean more provisioning and storage overhead. We should have more on this point in the next months.

GS: How is this draft related to the Group CoAP document draft-ietf-core-groupcomm-bis ?

MT: They refer to each each other, and have to move forward together. The original idea was to request publication for both of them together.

ED: About the mentioned proof. Are you waiting for this paper to be reviewed before advancing this?

GS: There's a pre-print in progress; mainly putting things together, possibly just a note on how proofs relate. It's probably sufficient that there is an IETF review on it; I don't think the paper needs peer review for progress here.

MT: The plan for v -12 is to address the two open points above. That should be a stable version, there are no other known issues.

## OSCORE Group Discovery (Christian) (10)

* draft-tiloca-core-oscore-discovery-08

   - Discuss updates and open points

CA: using the Resource Directory to discover links to an OSCORE group manager, hence to discover OSCORE groups and how to join them.

CA: latest updates specify also information on the pairwise mode of Group OSCORE; consider also the signature verifier as possible client; revise the examples.

CA: Marco's implementation has been tested against Christian's RD, covering all the steps defined in the draft.

https://bitbucket.org/marco-tiloca-sics/ace-java/src/master/src/test/java/se/sics/ace/interopGroupOSCORE/CoAPEndpointToResourceDirectory.java

coap://rd.coap.amsuess.com

CA: Next steps are about elaborating security considerations; aligning certain RD aspects to what added in the last version of the RD document; integrating the individually implemented steps into the actual joining node and Group Manager. Then we need reviews.

No questions.

## Multicast Notifications (Christian) (10)

* draft-tiloca-core-observe-multicast-notifications-05

   - Discuss updates and open points
   - Ready for adoption ?

CA: This enables a server to send multicast notifications to a group of clients. Possible to also use Group OSCORE. The server sends a phantom observation request to itself; observe notifications are responses to that request.

CA: recently added a new encoding for informative error responses to the clients; a new encoding for expressing addressing information in the informative responses; optimization for a server self-managing its OSCORE group and for having the phantom request as a deterministic request (https://datatracker.ietf.org/doc/draft-amsuess-core-cachable-oscore/).

CA: Next steps include considering also reverse proxies and deterministic requests used together with proxies.

ED: Intention with appendices, examples or normative?

CA: Implementation guidance, no need for normative additions. Appendix C specifies a simple way to manage a group.

GS: What is the state of the content, are all components in place?

CA: Yes.

CB: Is this work the WG wants to take on?

+13 on adopting, no objections.

Reviews? Esko, Göran would review.

Planned implementations? Christian, Marco (the authors)

CB: Would be good to have non-author implementor to ensure it's implementable if you haven't invented it.

CB: Energy is there, outside implementors are no prerequisite. Sounds like in-room consensus.

## Groupcomm proxy (Esko) (10)

* draft-tiloca-core-groupcomm-proxy-03

   - Discuss updates and open points

Esko presenting.

ED: Signaling protocols with two new CoAP options, to enable proxies in group communication.

ED: The encoding of server's addressing information conveyed in one of the options is also aligned with the format from https://datatracker.ietf.org/doc/draft-tiloca-core-observe-multicast-notifications/

ED: Now added also support for reverse proxies (with two examples).

ED: For when OSCORE is used between client and proxy, together with Group OSCORE between client and servers, we have simplified the high-level characterization of options to be protected as class E between client and proxy.

GS: Can it be solved with two separate OSCORE connections?

MT: Group OSCORE between client and servers is one thing. Then the proxy needs to verify authenticity of client, before forwarding at all. That requires a separate secure association between client and proxy, which leads to OSCORE in OSCORE.

ED: And OSCORE in OSCORE is actually forbidden. This would require proper definition, analysis and update of RFC 8613. Better to move out from this appendix and rather to a separate document?

GS: Supporting separate document.

CA: Supporting separate document.

JM: As to why this is forbidden now, we were worried about collisions of identifiers. Nothing that can't be addressed.

CA: Pretty sure it won't come to that because transport information differs.

GS: It's also interesting to consider a chain of proxies, i.e. whether this results in more than two OSCORE layers applied to a message, or in just two layers with the outer one replaced at each hop.

ED: Next steps are about addressing the points raised today and covering the case where client and cross-proxy talk HTTP. Earlier promised reviews: Christian and Carsten.

## Cacheable OSCORE (Christian) (10)

* draft-amsuess-core-cachable-oscore-01

   - Discuss updates and open points

CA: Enabling caching of OSCORE-protected responses; all group members can act as a deterministic client with a well-known Sender ID and Sender Key. The exact encryption key is derived for each different request. The key derivation process is similar to the one in the pairwise mode of Group OSCORE; will have to consider the feedback from Göran about it. Overall, you safely trade some security properties with enabling cacheability. This also improves the way things work in https://datatracker.ietf.org/doc/draft-tiloca-core-observe-multicast-notifications/

CA: During the hackathon, Marco and I interoped and came to decrypt each others' deterministic requests. Finding from the hackathon improved some design aspects, already in the editor's copy.

CA: Next steps would be about more interop, process the feedback and then go for a proper review with security in mind.

ED: For deterministic request it is not possible to determine the order, but for the server responses?

CA: Yes, but you cannot determine that the response is later than the request (by design, since the intent is to reuse cached responses)

## OSCORE with EDHOC (Rikard) (10)

* draft-palombini-core-oscore-edhoc-02

   - Discuss updates and open points
   - Ready for adoption ?

RH: Combined last EDHOC message to establish an OSCORE context together with the first request protected with that OSCORE context.

RH: Based on feedback also from implementors, converged to a single approach based on a new EDHOC option (zero-length). Proposed option number 13 to keep the overall option size 1 byte; number 21 would also work fine.

CA (on jabber): if option number 21 also works, pick 21. Another future protocol might make a better use of 13.

RH: Further optimization, i.e. only part of the EDHOC message goes on the wire, while the rest can be reconstructed by the server, saving at least 2-4 bytes.

RH: Keep in synch with the main EDHOC document; something specific of CoAP and OSCORE may better fit in this document.

ED: Recap, what's the purpose of EDHOC?

RH: Establishing keys for OSCORE in a secure way. This optimization just reduces the round trips around the last EDHOC message.

JM and CA (in jabber): +1 on (calling for) adoption.

Adoption call: +9, one "not raise hand" (ED explaining: not against, but not sure either), no opposition. In-room consensus, to be taken to the list.

## AEAD limits in OSCORE (Rikard/John) (10 + 10)

* draft-hoeglund-core-oscore-key-limits-00

   - Present new work
   
RH: This considers the AEAD cipher limits defined in https://datatracker.ietf.org/doc/draft-irtf-cfrg-aead-limits/ , and defines additional actions for OSCORE (so updating RFC 8613). Need to count key usages and renew the OSCORE context of the two peers when a limit is passed. One limit 'q' is about performed encryptions with a key, while 'v' is about failed decryptions using a key. Plan to cover more algorithms than CCM_8 and give optimizations for constrained devices and implementation guidelines.
   
* https://mailarchive.ietf.org/arch/msg/core/h5JHgX5wTBkJtrKl_ezswiCdUBI/

   - Broader discussion on the topic

JM: What the draft has described is important to happen in OSCORE. Renewing the security context might also be useful to do for other reasons like for counteracting key compromise, especially if the rekeying provides perfect forward secrecy.

JM: The original procedure used to compute the limit considers arbitrary assumptions that yield the actual limits now considered in the draft. It's also unfair to some particular algorithms. It would be good to have an overall revision of that procedure. OSCORE in particular may possibly consider a same value 2^20 for the two limits and a smaller block size of 2^8 rather than 2^10.

MT: So the possible revision of the procedure is not something for the presented draft.

JM: No, it belongs somewhere else. The presented draft can still end up with recommending the right limits to use, with some short explanations.

***Meeting closed at 18:07 UTC***

---

# Friday, March 12, 2021

Number of participants: 12:10 ( 32 ); 12:50 ( 36 ); 13:30 ( 30 )

Meeting material: https://datatracker.ietf.org/meeting/110/session/core

Etherpad: https://codimd.ietf.org/notes-ietf-110-core?both

Meetecho video stream: https://meetings.conf.meetecho.com/ietf110/?group=core&short=&item=2

Audio stream: http://mp3.conf.meetecho.com/ietf110/core/2.m3u

Minute takers: Rikard Höglund, Marco Tiloca (helping)

Jabber scribe: Marco Tiloca

**12:00 - 14:00 UTC**

Numbers in parentheses are minutes of time allocated.

## Intro, agenda (Chairs) (5)

MT: Carsten standing in as chair for Jaime

## CORECONF Comi (Carsten) (15) <1205>

* draft-ietf-core-comi-11

   - New open points from the shepherd review

CB: 4 CORECONF documents, of which 2 in last call, i.e. core-sid and core-yang-cbor, while 2 waiting for shepherd review (from Carsten), i.e. Comi and Yang-library.

CB: For Core-sid Ban Kaduk commented that this document wants to create a new global naming system. That is the intention and we want views from security community on this.

CB: For Comi issues came up. One in netmod about incompatibility between uint8 and int8. Do we need to rely on this? Is it really needed to encode uint8 and int8 in two different ways? Other open points: string may not be URL-safe, the definition of "CBOR key", and key vs. CBORencode(key).

CB: Further issues are text about block-wise transfers (can be changed to mention briefly only). Also further details on instructions for pagination of /.well-known/core. How can this be done? When can the SHOULD be violated (why is it not a MUST, what are the conditions)? This is a general problem in YANG. We may want to wait for YANG to solve this.

CB: Some NITS. Current text is not clear about leading zeros in base64 encoding of SID numbers. SID 0 should be "A" and not the empty string.

CB: Plan is to have a new version of Comi with these things addressed. We need one more round, for instance to be careful not to create the backwards incompatibility between uint8 and int8.

MT (from chat): Christian and Ivaylo agree on the /.well-known/core point.

IP: We could consider changing the encoding. Should not be an issue for implementations. I am interested in other implementations that are deployed where this would be an issue.

CB: Do we have to do another WG last call if we change the table (of data encoding)?

MT: Leaning for a not needed, we'll see, it would be the third WG Last Call if one thinks of the CORECONF cluster as a whole.

## SenML Versions (Carsten) (10) <1220>

* draft-ietf-core-senml-versions-02

   - Check status before WGLC

CB: draft-ietf-core-senml-versions-02 submitted addressing comments from Jaime (for instance approach to bitmapping a number). Ari added to his SenML validator the bit for additional units. This is ready to go for me.

MT: Discussed in November meeting we wanted comments, got from Jaime now. Next is starting WG last call. We will start that.

## SenML Data CT  (Carsten) (10) <1230>

* draft-ietf-core-senml-data-ct-03

   - Comments following WGLC and next steps

CB: draft-ietf-core-senml-data-ct-03 updated with editorial clarifications and decompression bomb security consideration. Document has normative reference to draft-bormann-core-media-content-type-format, seems that document will take a while, based on the Monday discussion in DISPATCH. Proposal is to remove that normative reference, and include in this document the minimal set of things needed from the one above.

MT: I think this is a good thing to do. Does Francesca have input?

FP: Seems most straightforward, I want more discussion in DISPATCH. We should try if we can figure out things, otherwise remove it as normative.

AK: Can we do it in parallell?

CB: Yes.

MT: So next step is making a PR on the senml-data-ct document to gain time and be ready to take the new direction (*action on Carsten).

## New Block (Med/Jon) (15) <1240>

* draft-ietf-core-new-block-07

   - Discuss updates following WGLC; ready to move on?

JS: Christian Amsüss provided comments. Updates to latest version: CSM Option was removed. Emphasized disadvantage of mixing NON/CON in same request/response. Clarity over different MAX_PAYLOADS. Naming is Q-Block1 and Q-Block2. Emphasis on non-confirmable support. Require use of confirmable when testing Q-Block. Clarified mixing Q-Blockx and Blockx with OSCORE. Also clarified use of the M bit in requests.

JS: Request-Tag was removed, congestion control was defined with new variables, examples were updated, security considerations updated to include OSCORE and updated references to CBOR RFCs.

JS: Implementation is based on libcoap, PR has been submitted. Has been tested in DOTS environment and behaving as expected. We believe all issues have been considered and handled. We request publication of the document.

CA: I am largely happy with the changes. It fits the scope it sets out. Not enthusiastic about some mechanisms, but should work fine for what it wants to do. Thank you for addressing my comments.

MT: The last updates better clarifies the intended scope. Agree it can be seminal material for a blockwise bis document. Next step is shepherding (Marco can take it). Will start a final review next week (not expecting big comments), then start the write-up.

## Dynlink (Bill) (15) <1255>

* draft-ietf-core-dynlink-13

   - Discuss status and next steps

BS: Current version is at 13, continuing incorporating feedback. Dynlink was also discussed during a Core interim meeting.

BS: Separated Conditional Attributes into Conditional Notification Attributes and Conditional Control Attributes. Separate table for each now. Edge attribute and confirmable notificatiom attribute was added in last version. The "edge" attribute indicates wanting notifications on falling or rising edge of boolean resource state. The "con" attribute indicates if a notification should be confirmable or either NON/CON.

BS: Currently we have "band" and "con" defined as parameters with boolean type value. Do we need to harmonize so that "band" and "con" have an actual value (in key, value format)?

MK: I would be fine if we made it explicit requiring key, value pair. But there may be reasons not to do that.

CB: I checked RFC7252, it says the argument is often in key, value pair. So query parameters without "=" sign is fine. For parameters without "=" sign you have presence and absence. So you can either express a parameter or that you have nothing to say. Seems it fits with the "con" attribute (not setting means no preference, setting means preference).

AS: Presence indicates desired behaviour. We did not want to spend extra bytes ("=" + 1 character) since it did not add value. I assume "band" is same logic (as "con").

BS: We have 3 boolean attributes, the last being "edge", where it is significant if it's 0 or 1. 

MK: I think for "band" you always have a preference. You will get notifications based on how it is set. It is very much like "edge". "con", in my implementation experience, it is useful to specify. It can work better to avoid the extra messages (using NON). I have seen value in being able to set it as false.

AS: In LWM2M we created a resource covering the default meaning you don't need to send if using default. Default is NON, certain cases make it CON.

MK: This is for LWM2M, not clear if "can" in our spec can be just presence/absence. Not being able to set false may limit some uses.

AK (on Jabber): LwM2M use of parameters:
http://www.openmobilealliance.org/release/LightweightM2M/V1_2-20201110-A/HTML-Version/OMA-TS-LightweightM2M_Core-V1_2-20201110-A.html#Table-512-2-lessNOTIFICATIONgreater-class-Attributes

AS: I agree, if you have no default state you want each independent observation to be able to set full characteristics, due to not having a default. As Carsten says, there are 3 states, 0, 1 or absent.

MK: I was thinking 2 states. If you don't include "band" that is now considered as equal to false. For "con" we have historically said the system can choose.

CA: Doing "con" as more of a hint seems like the correct thing, also considering proxies. Making this a hard rule seems excessive. I would phrase this as a recommendation.
Would it make sense to distinguish which attributes are useable for which methods (eg. edge makes sense for POST but not for PUT and observation).

BS: For instance how will pmax/pmin combine with "edge"? We need more work to understand this.

AK (on Jabber): We need at least 0/1 since LWM2M uses that.
Alan supports that.

BS: Changes done and planned. pmin == pmax is now allowed (implementation considerations covers this more). Considering impact from proxies, should include more examples, in section 3.3 Michael contributed code for server processing of Conditional Attributes.

CB: Recent discussion on second part of draft?

BS: Not much recently.

MK: Dynamic link concept can be used independent of link attribute. We may want to split things further.

BS: So when we split it the link part gets link name, and other part gets other name. So we need to update other documents considering this.

MK: Parameters close to being RFC, needs more work on link part.

CA: I agree it makes sense to split this. (As much as I regret losing the chance to let the document's drive push the bindings part that I care about.)

BS: Looks like group is in favor of splitting it.

CB: So we agree to keep dynlink document with the link material, and split out the other part.

MT: What about considerations for proxies? Like usage of with pmax. I think this can be coverd in a future interim meeting.

BS: Yes, it boils down to plans of interactions (end-to-end or hop-by-hop.) We were looking at hop-by-hop approach, but if we need to look at it considering proxies sitting in the middle we have to consider its impact.

## RD extensions and protocol negotiations (Christian) (15) <1310>

* draft-amsuess-core-resource-directory-extensions-05

* draft-amsuess-core-transport-indication-00

   - Discuss status and current directions, plus new document
  
CA: RD extensions are about what you can do with the RD without changing the spec. Most important here is reverse proxy extension. Can ask resource directory to provide you with a proxying service (publically reachable name), thus becoming a reverse proxy for you. It is being used in practic a lot, most of LWM2M uses a similar mechanism. The reverse proxy has been used in the hackathon for simplified testing.

CB (on Jabber): Can the RD partner with a proxy?

CA: In part, since the RD has to contact an endpoint on the Internet to establish the addresses in the first place and open up the firewall state. The RD could use a separate proxy but the endpoint would need to open up the endpoint to that proxy. Doing it in the RD seems a practical thing.

CA: We end up with a property that is better to avoid in the general web. It can be avoided if devices use RD only as proxy. Similar problem in protocol negotiation case, coap+tcp:// and coap:// both collapse onto same resource.

CA: Proxy discovery started in transport-indication-00. A server announces using link-relations that it has a proxy at a location. Everything hosted on this host is reachable via a specific proxy. No URI aliasing in the application (only on the wire when has-unique-proxy is set).

CB: I wonder if the /res line is in addition to a resource?

CA: That is just another resource advertised on the server. You discover this (resource and proxy information).

CB: It could also say anchor="/res".

CA: Yes but then it would only apply to this resource. Employing this indirection allows one statement for everything hosted on that server.

CA: Next steps are to gather feedback, tuning relationships, and update the RD extensions to show how it can be used. Reverse proxy in RD may not go away, some applications may not care about URI aliasing. But in other cases we do care. Do I want reverse or forward proxy can be distinguished.

MT: The idea would be to build on transport indication document in the RD extensions?

CA: Yes. Last point is that in the -00 it outlines security considerations (some can be taken from the HTTP working group.)

MK (on Jabber): NAT => URIT.
MK: Meant jokingly. We are building a URI translating gateway rather than a NAT translating gateway.

## A Data-centric Deployment Option for CoAP (Cenk) (10) <1325>

* draft-gundogan-core-icncoap-00

   - Present new work

CG: Can draw parallells between ICN and CoAP deployments. Shared this with ICN community earlier. ICN allows not specifying a server endpoint, focused on content delivery. Two prominent architectures are NDN and CCNx. Features are name-based stateful forwarding, content caching, object security.

CG: Object security provides end-to-end protection (this also applies to cached content). Parallells to CoAP between NDN and CCNx. Request-response paradigm. All hops on the path creates state, state is consumed when response traverses back. Can prevent traffic amplification (DDOS). Caching is hop-wise.

CG: One benefit is retransmission can originate from any intermediate entity in the path, which reduces link traversals. Content object security has been deployed.

CG: There is paper from 2020 about bulding a CoAP deployment similar to an ICN deployment using only standard CoAP features. For the standard deployment retransmissions are end-to end. In the data-centric each hop is also a cache (provides hop-wise caching and retransmissions). Forwarding decisions based on names. Between proxies we used link-local IPv6 which helped saving bytes due to 6LoWPAN compression.

CG: Most ICN systems support multiparty communication (mostly using request aggregation and response fan-out, or request fan-out and response deduplication.) We are working on providing more results focusing on the multi-party communication.

CG: The take-away is we were able to show this kind of deployment reduces latency and improves resilience. Location indedepent of content mobility, efficient multi-party communication and gave new perspectives on CoAP deployment. Future work is dynamic proxy discovery.

CB: What about interest routing? How would it work in a network mostly looking like a CoAP network?

CG: Slide 8 shows a CoAP deployment. Forwarding is on proxy-level (it knows for each GET for a URI where to forward the message.) For now we have hardcoded parameters, future work is dynamic parameters.

CB: How could the RD aid this process?

CG: For discovery we thought about using the RD.

CA: It's more about local discovery of links than using the RD. I can see the RD serving as announcement point for routes. If for a particular host there is a particular good next-hop proxy this can be discovered from the RD.

CG: It's an unconventional way of deploying CoAP using proxy all the way. Is this still a good home for this kind of work?

MT: I think it's worth exploring. It's not out of scope.

CB: Adding OSCORE can be interesting.

CG: We did add OSCORE, and used the cacheable OSCORE draft https://datatracker.ietf.org/doc/draft-amsuess-core-cachable-oscore/. It worked quite good. Saw improvement of success rates in lossy network.

MT: May be easy to build a relation with the multi-party case. There are building blocks for this too as work in progress in CoRE.
  
AK (on Jabber): Can also be brought to the attention of T2TRG.

CB: Can we come up with experiment that broadens the base?

CG: This deployment works well with safe or idempotent requests. The same request giving the same content. Firmware updates is a good potential use case.

CB: We have a whole working group for this, i.e. SUIT. They are looking mostly at security. But many of them do firmware updates. Can be good basis for further experiment. Not using OSCORE there but their SUIT approach. Can be interesting to propose getting the update from the closest location, rather than always from a certain update server.

CG: More comments are welcome on the mailing list.

## Flextime (25) <1335>

MT: Will resume interim meetings from April 28, on Wednesdays. 6 meetings planned before IETF 111.

CB: Can you give an overview or guess of what the interims will be about?

MT: No agenda yet. I can imagine Dynlink, cachable OSCORE and groupcomm-bis, as a tentative list.

CB: Can be good to have an agenda for the first interim. We can discuss this on the mailing list.



Σ 120

---

*[MT]: Marco Tiloca
*[JJ]: Jaime Jiménez
*[GS]: Göran Selander
*[JM]: John Mattsson
*[FP]: Francesca Palombini
*[CG]: Cenk Gündogan
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
*[MG]: Matthew Gillmore
*[DN]: David Navarro
*[CG]: Carles Gomez
*[MK]: Markku Kojo
*[HT]: Hannes Tschofenig
*[BK]: Benjamin Kaduk
*[AM]: Alexey Melnikov
*[RH]: Rikard Höglund
