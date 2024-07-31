# IETF 120 — Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

In-person Delegate: Laurent Toutain

Date and time: Wednesday, 2024-07-24, 16:30-18:30 UTC

https://www.timeanddate.com/worldclock/fixedtime.html?msg=CoRE@IETF120&iso=20240724T1630&ah=2

Meeting material: https://datatracker.ietf.org/meeting/120/session/core

Notes: https://notes.ietf.org/notes-ietf-120-core

Recording: https://www.youtube.com/watch?v=WyAw9m95VBQ

Zulip: https://zulip.ietf.org/#narrow/stream/core

Note takers: Christian Amsüss, Rikard Höglund

Chat monitor: Marco Tiloca

* * *

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (15)

Presented slides:
https://datatracker.ietf.org/meeting/120/materials/slides-120-core-chairs-slides-01.pdf

MT doing introductions.

Document updates:  
MT(p7): RFC9423 has been published.  
CB: "One of the most boring drafts I ever wrote. But now we have that
registry and we should use it".

MT(p8): Related documents in other Working Groups: The key exchange
protocol EDHOC was published as RFC 9528, with the companion RFC 9529
with traces.

MT(p9): -core-sid in AUTH48 and almost done with it, see the later
update from Carsten. Also -core-oscore-edhoc is approved for publication
and in EDIT.  
MT(p10): More related documents approved for publication in the ACE and
CBOR WGs.  
MT(p11): Publication requested for some related documents in the ACE and
CBOR WGs.  
FP (in chat): cbor-time-tag in AUTH48 really almost done :D

MT(p12): -core-oscore-groupcomm (Group OSCORE) under shepherd review,
new recent comments from Christian as part of the Shepherd processing
across versions -17..-21 on changes since his earlier comments; the
authors are working on it towards a new version.  
MT(p12): -core-comi completed WG Last Call, more work is required. We
expect a second WG Last Call after the new revision. -core-yang-library
has been waiting for -core-sid and -core-comi, it will proceed after
those.

MT(p13): -core-groupcomm-bis completed WG Last Call, is waiting for
follow-up comments from Carsten and his earlier WG Last Call Review, and
it has received new recent comments from Christian. The authors are
working on it. -core-conditional attributes and -core-href also
completed a WG Last Call, have been updated and are on today's agenda.  
MT(p14): Post-WGLC from other WGs: -ace-oscore-gm-admin.

MT(p15): List of other recently updated documents, some on today's
agenda.  
MT(p16): ... and again, from other WGs (in ACE, one in SCHC obsoleting
RFC 8824 on compressing CoAP headers).

CB(p17): On -corrclar. The goal is to capture things about CoAP that are
not well-captured in errata, rejections of errata items or elsewhere.
This is collecting knowledge. The document has an associated Github
repository with 29 issues. Issues are discussion topics, and can have
different resolutions (text in this document, errata reports).  
CB: We want to get rhythm in there, hence issues are processed in
interim meetings.  
CB: Notable recent discussions as examples: 1. "Match boxing"
(request-response matching). 2. Trailing slashes in URIs (it is
well-defined, but it needs much reading to understand right).  
CB: Everyone, please think about questions/issues/topics, please
contribute issues and review Github PRs and the document. Pick any issue
that resonates with you.

CB(p18): On the topic of reviews. The strength of the IETF is the review
process. Different categories of reviews: Process (part of the IETF
process), spontaneous, and cross-reviews. Github feedback is another
way.  
CB: Some people are quite productive with spontaneous reviews, including
Marco and Christian.  
CA (in chat): Half of those were Shepherd reviews and should probably be
counted as process reviews.  
CB: We need more. Reviews do not have to be full reviews, "I have looked
at section X" helps as well.  
MT: I concur, please review the documents.

MT(p19): Outlook on next CoRE interim meetings (planned dates and
times), resuming from August 28. We expect -corrclar to be a recurring
topic to work hands on about.

## CORECONF Cluster (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-sid/
* https://datatracker.ietf.org/doc/draft-ietf-core-comi/
* https://datatracker.ietf.org/doc/draft-ietf-core-yang-library/

Presented slides:
https://datatracker.ietf.org/meeting/120/materials/slides-120-core-coreconf-cris-href-00.pdf

CB (p1): Status of relevant documents. Focus today on -core-comi.  
CB (p2): RFC 9254 is stable. Two documents are extending it, namely
-yang-standin (YANG is essentially XML and thus text; this enhances
binary data support) and -yang-metadata (support YANG metadata
annotations in YANG-CBOR).

LT: Is there something for hex-string in YANG (represented in a
hexadecimal string)? Right now, it is still a String rather than a byte
array.  
CB: Good comment. Currently, -yang-standin leverages existing tags. I do
not think that we have a tag for hex-strings (maybe tag 23 "Expected
conversion to base16 encoding"). It's probably to be adopted in the CBOR
WG.

CB (p3): -core-sid is almost out of AUTH48. We still need a Designated
Expert (we have a mailing list set up for that).

CB (p4): -core-comi is one of the 3 CONF protocols.  
CB (p5): We have focused mostly on core-sid, but we have had interesting
discussions on COMI during meetings and progress with implementations. A
question was raised about multiple RPCs/Actions in one payload, which
needs thinking.  
CB (p6): Scaling needs to be thought about. A full neighbor table might
be large to get. Currently, we can only fetch subtrees; do we need a
more selective retrieval? Depth (blunt instrument)? Projection (fetch
only some specific components of each of many containers)? Parallel
discussion in yang-scaling @netmod with some of the same issues.

CB (p7): The plan is to get the remaining comments addressed, then
probably do another WG Last Call. We plan to add examples. Probably we
may leave the scaling discussion for an extension in a separate
document.

AHF: I already asked on the mailing list: how is CBOR encoded
differently, around notifications? The context is the project in YANG on
Kafka integration. It could be useful for big data collection. There is
a reference to this draft so there is one type of notification structure
for NET/REST/CoREconf. It could be useful for YANG integration into
other environments.  
CB: The underlying problem is that, when Netconf was designed, there was
no YANG, so they did not use its capabilities. When RESTconf was done,
this was partially moved to the YANG domain.  
CB: I am in favor of a common solution, but I am not sure that we can
get there without delaying COMI further.  
TG: If you look at the NETCONF Charter, NETCONF wants to obsolete RFC
5277. We are currently discussing a YANG module replacing the
notification structure.  
CB: We should ensure that we can adopt this when it solidifies. I am not
sure if we should throw out the existing notification mechanism. Let's
discuss more about it.

## Constrained Resource Identifiers (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides:
https://datatracker.ietf.org/meeting/120/materials/slides-120-core-coreconf-cris-href-00.pdf

CB(p8): About CRIs: they are like URI, but not text based, exposing its
semantic structure. Version -16 was submitted today, with editorial
updates and an update from the IANA review.  
CB(p9): This document is almost done. How important is determinism for
CRIs? Kneejerk response: it is for full CRIs, but it is not for relative
references. We are almost there about it, but we need to find out
whether we can state that as an actual property or if it is just
aspirational. The question of equivalence is important.  
CB(p9): We should find out if we can prove properties; we should
dedicate an interim meeting to this discussion.  
CB(p10): Ongoing work: we need more test vectors, and we plan to add
more. We may add test vectors for zone identifiers. The plan is to
complete the document after the summer break.

## Conditional Attributes for Constrained RESTful Environments (Bilhanan Silverajan) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-conditional-attributes/

Presented slides:
https://datatracker.ietf.org/meeting/120/materials/slides-120-core-conditional-attributes-for-constrained-restful-environments-01.pdf

BS(p1): It completed WG Last Call, and also got an early IOTDIR review. 

BS(p2): It is currently in version -07. We received one review after
that from Marco, while the IOTDIR review was for version -06. We have
addressed almost all the received comments. I want to discuss some
points with the IOTDIR reviewer. We also got feedback from IANA.  
BS(p3): Going over updates. The intended status changed from
Informational to Standards Track some version ago.  
MG(on chat): +1 on changing this draft to Standards Track. This draft is
used in LwM2M.  
BS(p4): Introduced the concept of "projections" to ensure that there is
no interference with how Observe works.  
BS(p5): Showing message flow with example of resource state projection. 

BS(p6): Other update: how to cancel observations. Do like in RFC 7641.  
BS(p7): Updated security considerations, as to amplification, and
resource exhaustion.

BS(p8): Remaining issue are about multiple conditional attributes.
Recommended solution: If you want an OR relationship among attributes,
register several registrations independently.  
CB: If you have an OR between two registrations that overlap, of course
you get two copies of the resource. Whether that is important, I do not
know.  
BS: Yes, and if you have a combination of AND + OR, things get messy
when you want to have a single registration.  
CA: If the query language becomes too complex, further documents can be
made to define more complex query structures in the payload of FETCH
requests, if the need for an OR persists.

MT: So you will produce a version -08 addressing the remaining and new
comments.  
BS: Yes.  
MT: Hopefully version -08 will then be good to consider for the
Shepherding phase. The Shepherd is already appointed.  
BS: Sorry for the delay in revising the draft, I am back on the research
track now.

## DNS over CoAP (DoC) and related bundle (Martine Lenders) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-dns-over-coap/
* https://datatracker.ietf.org/doc/draft-lenders-core-coap-dtls-svcb/
* https://datatracker.ietf.org/doc/draft-lenders-core-dnr/

Presented slides:
https://datatracker.ietf.org/meeting/120/materials/slides-120-core-dns-service-binding-records-with-coap-00.pdf

ML(p1): This will cover DNS over CoAP (DoC) and 3 other related drafts,
including Service Binding and transport indication (then Christian will
follow up on that).   
ML(p2): The original idea was to discover DoC resolvers over DNS, DHCP,
and Route Advertisement. The problem is that only discovery of a service
using CoAP over TLS was defined. Hence the need of an ALPN identifier
for CoAP over DTLS. But then what about OSCORE and EDHOC?  
ML (p6): The "docpath" parameter is now also defined (as a list of CBOR
text strings), with text representation as Diagnostic Notation. If you
know anything about zone files and see a problem, speak up.  
ML (p7): The DTLS service binding document, i.e.,
draft-lenders-core-coap-dtls-svcb, just defines the ALPN.  
ML(p9): The DNR draft, i.e., draft-lenders-core-dnr, defines a problem
statement of service parameters for OSCORE. Everything beyond that is in
draft-ietf-core-transport-indication.  
ML(p10): Showing the current situation: the cross-referencing between
these documents was a bit messy. The normative references to a non-RFC
is now limited to just 1 reference from draft-ietf-core-dns-over-coap to
draft-lenders-core-coap-dtls-svcb.

ML(p13): This is the minimal batteries-included package that we came up
with. TLS/DTLS is in, then the rest is for the rest of year. Is DoC+DTLS
ALPN ID ready for WG Last Call?

CB: You mentioned CBOR Diagnostic Notation. Any live protocol used for
interchange?  
ML: It is used in zone files for DNS, if you need any text
representation of docpath. The problem with the zone file syntax was
whether commas in EDN might cause a problem.  
CB: I am worried about elevating CBOR Diagnostic Notation into a live
part of a protocol.  
CA: I understand that text representation of zone files is just as much
diagnostic notation as EDN is. It is internal notation for DNS server
configuration files. As I understand, it is used internally and not
necessarily portable between implementations.

CB: Operationally, these files are used in a lot of places. Even if not
officially part of the protocol. We need to be careful to not put
something into the protocol that is not meant for interchange.  
ML: About representing the CBOR sequence in some textual manner: that
could be about using a path with slashes instead of commas. However, it
might be confusing when people put text path into the record. We are not
really sending a file with CBOR Diagnostic Notation over the medium. We
want a representation, it can be called comma-separated list. So
probably it is not as critical as you think.  
CB: I hope that there is an example, then I can look at it and make up
my mind.

MT: On the procedural side, the relation and intended references between
the documents in the bundle were discussed at the interim meeting, then
they were brought up on the mailing list, and there were no objections
to the plan.  
FP (in chat): I wouldn't do WGLC on a doc that references normatively an
individual (if I understand the arrows correctly)

MT: Before having a WG Last Call on draft-ietf-core-dns-over-coap, we
need to have draft-lenders-core-coap-dtls-svcb adopted. Do you expect
more work to do on its version -00?  
ML: No, that's good. For draft-ietf-core-dns-over-coap, we need more
discussion on the diagnostic format, and there was a minor IANA review.

MT: I think that we can consider adopting
draft-lenders-core-coap-dtls-svcb sooner than later. Carsten, does it
work for you?  
CB: Of course.

Show of hands: "Who is in favor of adopting
draft-lenders-core-coap-dtls-svcb as a WG document?" (it's a 5 page
document)  
Result:

* yes: 13
* no: 0
* no opinion: 4

MT: The Chairs will issue a WG Adoption call on
draft-lenders-core-coap-dtls-svcb.

ML (on chat): @Carsten Bormann wrt to an example of CBOR diagnostic
notation of the docpath, sadly there is none. Should we add one (and
maybe also for the other conversions described there) to the draft?  
CB (on chat): We can start with an example on the mailing list  
ML (on chat): Ok, will do ASAP.  
CB (on chat): But ultimately, I think we should have examples for every
feature in the spec

## CoAP Transport Indication (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-transport-indication/

Presented slides:
https://datatracker.ietf.org/meeting/120/materials/slides-120-core-coap-transport-indication-01.pdf

CA(p1): Martine joined as an author.  
CA(p3): Two main changes have been done. The quick one: there was an
open question about the relation between a resource and its proxy, and
whether that should be the Host-relationship or instead build on the
Same-origin concept. I got no feedback, so I picked the easier one.

CA(p4): SVCB parameters is a larger topic. Nothing changes the fact that
we are treating transports as proxies.

CA(p6): We have a URI with its scheme and a message to be sent to an
address (with header and option parameters). We get from a URI to the
CoAP message using name-resolution (which often means performing a
lookup). This requires that the scheme encodes all that we need to know
in order to pick the right transport (if many are available).

CA(p7): Discovery from DNS or DHCP/RA can provide service-binding data.
This includes a number of pieces of information. All this data can be
used to create a CoAP request.  
DNS over CoAP is the first document that needs this for CoAP. We spell
out the conversion from SVCB record to the CoAP message to build.
Transport indication now provides a generalization of this process.  
There is another way of using this: it could do like HTTP for discovery:
1) Perform SVCB lookup when we have a name; 2) Receive service-binding
bundle data; 3) Compose the CoAP message.

CA(p8): Above is something the applications can opt-in to. It is a
useful mechanism to describe.  
Data relevant for setup of a security context can also be received, and
goes into the creation of the CoAP message without being able to be put
into the CoAP URI.

CA(p10): Question: Is the opt-in approach too cautious? How do we phrase
the binding request? As a dedicated resource record or a more generic
one? Do we want to have both \_coaps and \_coap SVCB?

CA(p11): Please review. Please look at the section on SVCB param
literals. Who wants to do interoperability testing and of what?

MT: I can review. A question about using the has-unique-proxy as target
attribute, and build on it to omit the Uri-Host option for efficiency.
Does this introduce a relevant deviation from the algorithm in RFC 7252
for building CoAP Options from a URI? If so, is it warranting an update
of RFC 7252?  
CA: It does not constitute changes as you are going through a proxy. The
URI is the same, but because it goes through a proxy it may change the
CoAP options. It does not change the eventual URI. If you take the CoAP
message and go in reverse, then you better be aware that proxying is
involved. That conversion would only happen on the server which has
advertised that they are all the same.

## Observe Notifications as CoAP Multicast Responses (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-observe-multicast-notifications/

Presented slides:
https://datatracker.ietf.org/meeting/120/materials/slides-120-core-observe-notifications-as-coap-multicast-responses-00.pdf

MT presenting.

MT(p2): Recap of draft contents. The specified protocol allows a server
to start at itself a group observation. If multiple clients come in to
observe that same resource, the server gives them instructions on how to
listen to Observe notifications sent over multicast to all the clients
at once, when the resource representation changes. The server starts a
group observation by sending to itself a cosmetic "phantom request".  
MT(p3-5): Updates in the latest versions. Several clarifications and
detailed additions to the protocol behavior. Major points:
considerations and fixes on the rough counting of alive clients in
different setups; fixes in the semantics of the new CoAP options; ways
for the server to handle early publication of the phantom request
starting a group observation, or to self-manage an OSCORE group
(Appendix C), or to using OSCORE-protected deterministic requests as
phantom requests (Appendix D).  
MT(p5): In Appendix C, we also introduced a parameter about the residual
lifetime for the self-managed OSCORE group (parameter 'exi'). In
Appendix D, we clarified that there can be no "twin" group observations
to aid clients that do not support deterministic requests if one is used
as phantom request. We also made improvement updates to the
rough-counting solution.  
MT(p6): Major update: revised the tp\_info in the instructions that the
server provides to the clients. Now it uses CRIs from
draft-ietf-core-href to express transport-specific information.  
MT(p7): Showing comparison of old and new approach for tp\_info.  
MT(p8): Concrete example for CoAP over UDP. One CRI provides addressing
information of the server, practically the source address of the
multicast notifications. A second CRI provides addressing information of
the clients, practically the destination multicast address of the
multicast notifications. A CBOR byte string is also provided, conveying
the value of the CoAP token used for the all multicast notifications of
the same group observation.  
MT(p9): We also extended security considerations about rough-counting of
clients. On the message exchange examples: all were revised, both
esthetically (e.g., use of AASVG and improved notation) and in order to
use CRIs in tp\_info. Also updated IANA considerations: new target
attribute "gp-obs" and revised registry related to the tp\_info field.  
MT(p10): Outlook and plans for next steps. Mostly: discussion and
example when using a reverse-proxy; advanced case with multiple servers
as observation targets; revocation of early published phantom request;
SCHC compression of the two new CoAP options.

CB: Question (all, think about it): Do you care about deterministic
CRIs?  
MT: Good question, also relevant for the related point on HREF in
itself. We will think about it.

## OSCORE-capable Proxies (Rikard Höglund) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-capable-proxies/

Presented slides:
https://datatracker.ietf.org/meeting/120/materials/slides-120-core-slides-oscore-capable-proxies-core-ietf-120-00.pdf

RH(p2): This document updates OSCORE to be used with proxies *and*
origin servers. It is also about admitting nested OSCORE, and encrypting
as many options as possible whenever possible.  
RH(p3): Overview of updates; explicit order of protections for outgoing
requests.  
RH(p4): Christian reported a bug in the process of escalating the
protection of CoAP options from their original Class U/I to Class E,
when that is about the Uri-Host or Uri-Port Option. The bug is fixed
now: those two options are never escalated to Class E, with one safe
exception related to forward-proxies.  
RH(p5): More concrete rules are now defined for the escalation process,
which also got simplified by merging previously different cases.  
RH(p6): Figure showing the updated escalation algorithm. There is also a
diagram of this in Appendix B of the draft.  
RH(p7): We clarified the process for SCHC compression/decompression when
a message is protected by multiple OSCORE layers. We added two new
examples of message exchanges as diagrams, considering a reverse-proxy. 

RH(p8): Proposed update to RFC 8768 on explicitly defining the Hop-Limit
Option as Class U for OSCORE. This avoids inefficiencies and other
issues in the case where the origin client adds the option, which would
default to Class E and thus be protected end-to-end between the origin
client and the origin server. Instead, with the option defined to
originally be of Class U, the escalation algorithm in this document will
ensure to encrypt Hop-Limit for a proxy, but not end-to-end between the
origin client and the origin server, thus avoiding the reported issues
and inefficiencies.

CA (chat): +1 on making Hop-Limit Class U.

CB: Does Hop-Limit as Class U disclose more than we want to disclose?
Take it to mailing list.  
RH: If the client chooses to include Hop-Limit, it wants proxies to see
the option. We should mention any privacy concerns.  
CB: Nested pairs of proxies may want to protect this.  
RH: The option will be protected if it is for a proxy that uses OSCORE. 

MT: At any rate, a Class U Option definition has to come together with a
dedicated security/privacy considerations section. So we have to provide
that sort of discussion anyway.

## OSCORE Key Update (KUDOS) and ID Update (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/
* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-id-update/

Presented slides:
https://datatracker.ietf.org/meeting/120/materials/slides-120-core-slides-kudos-core-ietf-120-00.pdf

RH(p2): Recap, and pointers to split-off parts as now separate documents
(ID update and key usage limits).  
RH(p3): KUDOS procedure for OSCORE key update, and extended OSCORE
option.  
RH(p4): Updates in -08. The message flow is flexible: no strong tie
between request and response is needed. We introduced the abortion of
simultaneous execution (if both finished, the state of both peers may
become bad).  
RH(p5): More updates: Interaction with OSCORE notifications, on setting
"uninitialized" the Notification Number upon establishing the new
Security Context (aligned with the intent of RFC 8613). Content was
moved around for readability. We added a request for IANA about adding a
reference to this document in the OSCORE Option entry of the CoAP Option
Numbers registry.  
RH(p6): We added more security considerations, with a reference to a
paper from John Preuß Mattsson comparing key update protocols. For peers
that are CoAP servers only and have reached their crypto limits for
message decryption: we describe the situation they might get into, still
avoiding to open for exceptions when keys might still be used beyond
their limits.  
CB (on chat): +1 reference

RH(p7): Then there is also the companion document on the protocol for
updating OSCORE Recipient IDs. Showing a recap of how it works and its
properties. This protocol can be run embedded in KUDOS or stand-alone.  
RH(p8): Updates on that document: it is now also allowing the legitimate
offer of zero-length OSCORE Recipient IDs; it defines what failure
means, and what it means when either this procedure or KUDOS fails, when
they are run combined. We also added a note on the maximum length of
Recipient IDs that can be offered (based on the used AEAD algorithm),
and error handling about it.

RH(p9): Outlook on next steps. For draft-ietf-core-oscore-key-update,
the main thing is processing a recent review from Christian. We have a
Java implementation of KUDOS in forward message flow, building on
Eclipse Californium. We also have an ongoing implementation for the
Contiki operating system for constrained devices.

CB: On tie-breaking for two simultaneously started KUDOS executions:
Usually, when you tie-break, you try to ensure that both sides arrive at
the same way forward. If both abort, they will both retry and experience
the same thing again. Maybe the tie-break should actually ensure that
both parties get to the same result?  
RH: We wanted a simple solution. It is fine if both peers abort. It is
unlikely that the collision happens again.  
CA: I gave a proposal in my review that solves this and that allows a
simultaneously started update to complete.

## CoAP over BP and in space (Carles Gomez) (10)

* https://datatracker.ietf.org/doc/draft-gomez-core-coap-bp
* https://datatracker.ietf.org/doc/draft-gomez-core-coap-space

Presented slides:
https://datatracker.ietf.org/meeting/120/materials/slides-120-core-coap-in-space-and-coap-over-bp-00.pdf

CG(p2): On CoAP in space: the scope now is not only deep space, but it
is by characterization including LEO sparse constellations that require
store-and-forward (related to 3GPP work). Overview of updates.  
CG(p3): Updates to group communication and Group OSCORE interactions.
Considerations on the choice of the Replay Window size.

CG(p4-5): On CoAP-over-BP, we added a section on encapsulating bundle
and defined the bundle lifetime. We also defined what the Destination
EID should be. We added tentative text about aggregating multiple CoAP
messages into one bundle. We got recent feedback from Carsten about this
last point, and we will take it into account for future update.  
CG(p6): We consider now a URI scheme following
draft-ietf-core-transport-indication. Example: dtn://JupiterSensor ->
coap://JupiterSensor.dtn.arpa/.well-known-core   
CG: Expected change for next iteration: the IPN-based URI order will be
flipped (per a comment from Carsten) to keep the hierarchical order.

CG(p7): On securing CoAP over BP: we use DTLS (not recommended), or
OSCORE, or BPSec. Should we use both OSCORE and BPSec at the same time?
We welcome input.

CG(p8): We want to increase the CoAP MessageID field from 16 to 24 bits.
Cons are: Memory/wire overhead. Pros are: More Message IDs.  
CB (on chat): RFC 8323 does not have the Message ID field.

CA: In the Deep-Space IP meeting, I have heard a discussion on
high-bandwidth links. What if CoAP proxies are present on links
supporting QUIC? Tokens can be limited to regions.  
CA: More generally, picking up a topic from Deep Space IP: do we intend
to do CoAP all-the-way-through? Links there sounded like if proxying at
high-bandwidth links may be useful. QUIC was heard of a lot.  
CG: Different types of links are used. Some are low-bitrate, some are
high-bitrate. Still, what you mention applies.

BS: Comments, mostly for CoAP-in-space, not so much for CoAP-on-BP:

1.  For the use of Observe, look at
    draft-ietf-core-conditional-attributes (especially epmin, epmax) and
    to draft-ietf-core-coap-pubsub.
2.  There has been a lot of work on CoAP with LEO. Running DTLS is not
    really recommended, but that is not BP specific, it is for all
    high-latency transports. We can share experiences.  
    CG: Thanks.

--  
CA (prepared but ran out of time, to be followed up on list): Not sure
max-age needs specialization: IIRC it has an exception that "it was just
requested and we just needed retransmissions" is explicitly fresh, no
matter how long the retransmit time.

CA (prep) on groupcomm: Do you expect long-latency-and-then-fanout?
(otherwise, groupcomm-proxy has a tunable time parameter)

## Flextime (10)

Σ 120

* * *

*[AB]: Andy Bierman


*[AF]: Alex Fernandez


*[AHF]: Alex Huang Feng


*[AK]: Ari Keränen


*[AP]: Alexander Pelov


*[AS]: Alan Soloway


*[BS]: Bilhanan Silverajan


*[BSc]: Ben Schwartz


*[CA]: Christian Amsüss


*[CB]: Carsten Bormann


*[CG]: Carles Gomez


*[DN]: David Navarro


*[ED]: Esko Dijk


*[FP]: Francesca Palombini


*[GF]: Giuseppe Fioccola


*[GS]: Göran Selander


*[HB]: Henk Birkholz


*[IvP]: Ivaylo Petrov


*[JJ]: Jaime Jiménez


*[JPM]: John Preuß Mattsson


*[JT]: Jernej Tuljak


*[KH]: Klaus Hartke


*[KZ]: Koen Zandberg


*[LT]: Laurent Toutain


*[MCR]: Michael Richardson


*[MG]: Matthew Gillmore


*[MJK]: Michael Koster


*[MK]: Matthias Kovatsch


*[ML]: Martine Lenders


*[MN]: Massimo Nilo


*[MT]: Marco Tiloca


*[MW]: Matthias Wählisch


*[NW]: Niklas Widell


*[RH]: Rikard Höglund


*[RML]: Rafael Marin-Lopez


*[RW]: Rob Wilton


*[ST]: Sean Turner (here)


*[TF]: Thomas Fossati


*[TG]: Thomas Graf


