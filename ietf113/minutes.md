
# IETF 113 - Agenda for Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo@tzi.org)

Please note:

Jabber: xmpp:core@jabber.ietf.org?join

Zulip stream: <https://zulip.ietf.org/#narrow/stream/21-core>

Date and time: Friday, 25th of March 2022, 09:00 - 11:00 UTC

Notes: <https://notes.ietf.org/notes-ietf-113-core?both>

Meetecho video stream: <https://meetings.conf.meetecho.com/ietf113/?group=core&short=&item=1>

Meetecho for onsite participants:
<https://meetings.conf.meetecho.com/onsite113/?group=core&short=&item=1>

Audio stream: <https://mp3.conf.meetecho.com/ietf113/core/1.m3u>

Minute takers: Rikard Höglund, Chairs (helping)

Jabber scribe: Carsten Bormann

# Friday, March 25, 2022

09:00 - 11:00 UTC

Numbers in parentheses are minutes of time allocated.


## Intro, agenda, status (Chairs) (10)

* WG and document status

Presented slides: <https://datatracker.ietf.org/meeting/113/materials/slides-113-core-chairs-slides-01.pdf>

MT: Opening the meeting and going over practicalities of the hybrid meeting
MT: RFC 9175 and 9177 have been published, going over status of further documents


## HREF (=CRI) (Carsten Bormann) (10)

* <https://datatracker.ietf.org/doc/draft-ietf-core-href/>

    - Ready for Working Group Last Call ?

* Presented slides: <https://datatracker.ietf.org/meeting/113/materials/slides-113-core-href-cri-00.pdf>

CB: Idea is a new representation format for URIs.
CB (p2): Going over recent updates to the document. These include addition of percent-encoded text and not removing lone empty path segments.
CB: 4 ongoing implementations exist in Python, Ruby, Go and Rust. The implementations are uncovering some issues, due to this the test vectors are being expanded. The objective is to exercise CRIs in CoRAL, CURIEs and CBOR-packed.
CB: Next steps are 5 remaining issues and 1 PR on the text (+ 2 PRs on test vectors) in the Github repo. Implementation work should take around 6 more weeks. We probably need 1 more interim before a Working Group Last Call.

MT: Do you plan to submit a revision, or have some discussion?
CB: One or two revisions until we are done with the implementation testing, then discuss at an interim, then another revision.


## Conditional Attributes (Bill Silverajan) (10)

* <https://datatracker.ietf.org/doc/draft-ietf-core-conditional-attributes/>

    - Ready for Working Group Last Call ?

* Presented slides: <https://datatracker.ietf.org/meeting/113/materials/slides-113-core-conditional-attributes-for-constrained-restful-environments-draft-ietf-core-conditional-attributes-01.pdf>

BS: Will present deltas from last interim meeting. We closed a lot of the Github issues.
BS: Updates are explanation on "attribute", discussion on Conditional attribute registry, and moving towards WGLC.
BS (p3): See old and new text about Conditional attributes.
BS: Plan to submit new version which should be last before WLGC.
BS (p5): Ongoing discussion about pros and cons of having a Conditional attribute registry. Exists confusion of 'lt', "lifetime" vs. "less than". More thoughts are welcome.

ED: Reusage of 'lt' in a different context should be fine.
BS: My preference would be to have a registry for Conditional attributes.

CA: I don't have an opinion about registry structure. But there is no guarantee of no overlap just because one is used for observations and one for the resource directory (many parts of the RD are observable). So these may in fact need to be combined.
BS: So you want a common subregistry for both?
CA: Doing things across applications makes sense if a registry is used. A server could avoid combining components with overlapping meaning. A registry doesn't have to be normative ("Whenever you see attribute X it has these semantics") but can be for coordination ("Extension A is using X already, so if you want your extension B to be combinable with A you better not use X").
ED: As Christian mentioned, there is real risk of clash of these attributes. This is something to consider. Perhaps while discovering resources it can be learned if they support conditional attributes.
BS: Draft just says should support them, not must.
ED: Server could respond with error if it doesn't know the attribute. May be good for making it discoverable what a resource supports in terms of attributes.
CB: If an application uses "foo" and we register "foo", that is a problem. So a namespace for conditional attributes could be good. Not a suggestion, just something I want to bring up.
BS: The namespace approach was discouraged in the RFC.
CB: You're talking application namespace, I'm talking about a namespace for conditional attributes.
CA: A Uri-Query option is critical, in general the application should not ignore that. This comes from how things are often done with PHP.

MT: What is the timeline for the next version?
BS: As soon as the queue is open I will submit. We could come and present updates in 1 month.

(some more chat-ter: DN: "prefix is more bytes"; CB: "yes"; CA: "fetch content format might be better than query parameters, but not practical on short term")


## Group Communication for CoAP (Esko Dijk) (10)

* <https://datatracker.ietf.org/doc/draft-ietf-core-groupcomm-bis/>

    - Ready for Working Group Last Call ?

* Presented slides: <https://datatracker.ietf.org/meeting/113/materials/slides-113-core-group-communication-for-coap-06-00.pdf>

ED: Going over updates to the document. Examples were added for encoding application group names, discovery of CoAP groups & application groups, and message exchanges for group communication. 2 of these were related to issues on Github. Usage of Uri-Host option for encoding application group names was removed. All open issues are closed.
ED (p3): Going over application group name encoding example in detail.
ED (p4): Going over group discovery example in detail. Given a CoAP group the associated application groups and servers including resources in it can be discovered.
ED (p5-6): Explaining example of group message exchange. Included is one server responding from different port than the request arrived on. Also showing examples where the block options are used.

ED: We are ready for Working Group Last Call (for version -06)
CB: Why did you remove the Uri-Host option for encoding application group names?
ED: Idea was to not include the group name in the Group URI, but add it after.
CA: Naming the group according to the Uri-Host is still fine.
ED: But that means a single option would be both CoAP group and application group

CB: Seems we are ready for a WGLC, sounds like the next step.


## Group OSCORE (Marco Tiloca) (10)

* <https://datatracker.ietf.org/doc/draft-ietf-core-oscore-groupcomm/>

    - Ready for Shepherd Write-Up ?

* Presented slides: <https://datatracker.ietf.org/meeting/113/materials/slides-113-core-group-oscore-secure-group-communication-for-coap-00.pdf>

MT: Document underwent a 2nd WGLC, based on this we submitted a version -14. Based on 2 reviews from Esko Dijk and Rikard Höglund. We worked on going through the reviews, processing the comments in them.
MT (p3): Summary of updates based on Esko's review; most delicate points were discussed at an interim meeting. Some of these points were distinguishing between "authentication credentials" and "public key", making it optional for the Group Manager to recycle Group IDs (further confirmed on the mailing list), some restructuring of the document and better classification of normative/informative references.

MT: We believe that v-14 addresses the 2 reviews from the 2nd WGLC. No further open points or issues exist as far as we know. Shepherd write-up can be next step, Christian Amsüss accepted to be Shepherd.

CB: What are the pending normative references?
MT: Groupcomm-bis (mutual normative reference) and the COSE documents (-cose-countersign, -cose-rfc8152bis-algs, -cose-rfc8152bis-struct).



## Key Update for OSCORE (Rikard Höglund) (15)

* <https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/>

   - Discuss updates, including new proposed protocol features

* Presented slides: <https://datatracker.ietf.org/meeting/113/materials/slides-113-core-key-update-for-oscore-kudos-00.pdf>

RH presenting.

RH: recapping, draft in two parts: first, limits of AEAD ciphers; then actual key update procedure, signaled with a flag in the OSCORE option so that shares of a nonce are exchanged to use for deriving new keying material.

RH: One main update is the alternative mode without Forward Secrecy (FS). Needed as stateless method for devices that cannot keep state. This no-FS mode is signaled with a new dedicated bit in the OSCORE option. This mode should not be used by a device initiating the protocol and capable to store in persistent memory (i.e., to keep state). The no-FS mode relies on the same "bootstrap" Master Secret/Salt at every run. FS is sacrificed but all other properties of KUDOS remain. An "agreed downgrading" is possible, where the initiator can do FS but the responder cannot.
GS: Thanks, this is good and useful, should be moved to the document body. Also, it doesn't look overly complex.
CB: Good work. How often can you use the bootstrap Master Secret/Salt?
RH: No analysis on that yet, to be thought through. We assume the device itself cannot change it, a technician might.
GS: This shouldn't be a problem. If there's good entropy for the bootstrap material, what matters is having good entropy for the exchanged nonce shares used for key update.

RH: Another update is more details on possibility to preserve observations following a key update. A peer can use a new bit in the OSCORE option to signal explicit interest in having observations preserved. The "long jumping" approach discussed in the past is used to update the Sender Sequence Number after key update thus preventing a possible AEAD nonce reuse.
GS: Not sure we should do this at all, might be overengineering, I'll get back to this after checking the details.

RH: One more update is the possibility for the two peers to update their OSCORE Sender/Recipient IDs. This can happen as a stand-alone procedure or embedded in a KUDOS execution.
RH: It relies on a new CoAP option "Recipient ID" of class E for OSCORE. Showing example of message workflow (stand-alone procedure).
GS: No seeing a problem, can't think of a compelling use case either. Not to use unless a safe security context is available.
RH: Right, for instance not right after reboot, we have considerations on it.

RH: Also working on details on how all the signaling above can work, meaning where to exactly put those bits in the OSCORE option. Need for a better place than the flag bytes, also to integrity-protect those bits. They can be in the 'x' byte of the OSCORE option, that now indicates only the size of the nonce share conveyed in the 'id_detail' field. That byte 'x' can also be input to key derivation, thus being integrity protected.


## Transport Indication (Christian Amsüss) (15)

* <https://datatracker.ietf.org/doc/draft-amsuess-core-transport-indication/>

   - Ready for Working Group adoption ?

* Presented slides: <https://datatracker.ietf.org/meeting/113/materials/slides-113-core-coap-protocol-indication-01.pdf>

CA presents. Use case: device with different transports that share resources.

CA: Server MAY indicate for instance coap+tcp, but does not have to. Aliasing is discouraged in URIs, what about multiple cache entries?
CA: Proposal is to not unify these utilizing proxy-scheme option. Suggestion for advertising this is using web-links. This informs the client about availability of other transports. Goal is to have no URI aliasing, must be opt-in by the server.

ED: Do you always get the proxy-related info? Or do you have to ask for something specific to get them?
CA: Not strongly defined now, might warrant a few more words. Can make sense to narrow it down. I'll take that as an input to an updated version. 

CA: Security considerations are that this is just like any other proxy. It works well with OSCORE, and TLS-based connections (proxy is on the same device). 

CA: Further goals are to reduce need for duplicate cache entries, and allow thirds parties to announce that they provide alternative transports.
CA: Optimization possible, arguably aliasing but more like "compression".

CA: To summarize, it can probably be this simple, no URI aliasing for the applications.

CA: Should this be done? Should it be in this Working Group?
CB: Chair-hat off, my answers are yes and yes.
ED: This sounds useful to me.
MT: Chair-hat off, yes and yes from me too.
AK (in chat): we need a solution to this and the presented solution looks good


Question to the room: "Who thinks the draft is ready for Working Group adoption? Raise hand if agree."
Result: 10 agree; 0 disagree (with about 27 in the room)

MT: We'll start a call for adoption on the mailing list; given the support in the room, it will be about confirming. Further feedback is of course welcome.


## Non-traditional Responses (Christian Amsüss) (15)

* <https://datatracker.ietf.org/doc/draft-bormann-core-responses/>

   - Go through existing and envisioned cases; refine document scope

* Presented slides: <https://datatracker.ietf.org/meeting/113/materials/slides-113-core-coap-non-traditional-response-forms-00.pdf>

CA (p2): Going over history of related things.
CA (p4): Definition of "non-traditional response" and "non-matching response".
CA: This document provides terminology useful for other specifications. For instance groupcomm-proxy and multicast-notifications. It can also be useful for implementers, in addition it defines options such as Response-For which can be useful for generic applications.

CB: We need to understand how security models are impacted.
CA: Yes

CA: Is the working group interested in work on non-traditional responses? For taxonomy or concrete options? Does it conflict with existing concepts? Any other feedback?
ED: From implementer perspective, you think this would improve implementation quality?
CA: Yes, now the stack needs to be aware of the full semantic of all non-traditional response options. With this they can simply have a list with the respective rules.
MT: Chair-hat off, I've read the draft and plan to give out a review. Can't see any conflicts, good to have a document like this as single reference point about taxonomy and concepts. Since these concepts are already used in other documents anyway, this would prevent development of dialects around those terms/concepts and thus would avoid confusion.
GS (in chat): +1 to Marco's comment

CB: Could we have a hands-raise for the first question?

Question to the room: "Is the working group interested in work on non-traditional responses?"
Result: 10 yes; 0 no (with about 26 in the room)

MT (in chat): Interested to review.
GS (in chat): I can review.
ED (in chat): Can also review at some point.

DN (in chat): I'm kind of discovering these Respond-To-* options. They look like a vector for DoS attacks. Should the document address it?
CB: Yes! That is security considerations.

 
## DNS over CoAP (Martine Lenders) (15)

* <https://datatracker.ietf.org/doc/draft-lenders-dns-over-coap/>

   - Discuss updates and received feedback

* Presented slides: <https://datatracker.ietf.org/meeting/113/materials/slides-113-core-dns-queries-over-coap-doc-00.pdf>

ML: Motivation is to protect against eavesdropping for DNS request from IoT devices. Possible solutions are DNS over HTTPS and DNS over TLS, DNS over QUIC, and DNS over DTLS. First 2 use TCP, last one has a path MTU problem. Due to this, we want DNS over CoAP (encryption with DTLS or OSCORE). Block-wise messages overcome path MTU problem.
ML: The DNS query is put in a CoAP request, sent to a DoC Server which then does DNS request to DNS server.
ML: Some updates are: Get and POST were removed, note added on ETag and response codes, clarify why DoQ conflicts with constrained IoT scenarios, clarified content-format.
ML: Evaluation was performed, experimental setup shown in slide 6. Results are related to when fragmentation happens. Conclusion is that fragmentation has bigger impact. 
ML: Realistic query format and response sizes lead to fragmentation. We want compression (and new content format) to avoid this. Have ideas on what can be omitted in the messages (see page 9). Two options proposed are: CBOR-arrays, or "remote getaddrbyname()". This can be a separate draft.

CB: What is percentage of space taken by the actual labels (DNS names)?
ML: Most of the time it is a small part, I have backup slide on this to possibly show at end.

ML: Other open question is caching vs. max-age vs. TTL. Showing message flow examples in slides.
ML: (p12) Option 2 has less cache invalidation; workload is on the more powerful server.
ML: Need to account for Observe, and HTTP/2 Server Push?
ML: Issue raised by Klaus Hartke, how abstract should the draft be? Specify a REST API and leave protocol detail to implementers?

LT: Do you look only into A/AAAA records or also others?
ML: At the moment focusing on that because it was most requested in the data set. Apart for mDNS, it was the only ones we saw.

ED: One interesting technology is the DNS push approach. That seems suitable to apply. RFC 8765.
ED: Also used on embedded devices. They query for DNS-SD services and get updated responses over time. Device can be notified of new services through DNS push. Could probably be done well with CoAP observe.
ML: We were wondering if there is use case for Observe; from what I hear it's just normal observe. We can still describe it for DNS push, will depend on direction taken.

MT: So I see 4 topics to proceed with. A thread on the mailing list can be started for each of thos, and of course we can follow up during interim meetings.

CB: Please send chat message if interested in reviewing.
Interested to review: Thomas Fossati, Carsten Bormann, Laurent Toutain

## Flextime(10)

MT: We resume with biweekly interim meetings on April 27th.

---

*[MT]: Marco Tiloca
*[JJ]: Jaime Jiménez
*[FP]: Francesca Palombini
*[CB]: Carsten Bormann
*[CA]: Christian Amsüss
*[KH]: Klaus Hartke
*[RH]: Rikard Höglund
*[TF]: Thomas Fossati
*[DN]: David Navarro
*[GS]: Göran Selander
*[BS]: Bilhanan Silverajan
*[AS]: Alan Soloway
*[MCR]: Michael Richardson
*[AK]: Ari Keränen
*[MJK]: Michael Koster
*[JM]: John Mattsson
*[NW]: Niklas Widell
*[ED]: Esko Dijk
*[EB]: Henk Birkholz
*[ST]: Sean Turner
*[ML]: Martine Lenders
*[MW]: Matthias Wählisch
*[GF]: Giuseppe Fioccola
*[LT]: Laurent Toutain

