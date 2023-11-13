# IETF 118 - Agenda for Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

Please note:

Date and time: Thursday, 2023-11-09, 08:30-10:30 UTC

Meeting material: https://datatracker.ietf.org/meeting/118/session/core

Notes: https://notes.ietf.org/notes-ietf-118-core

Meetecho video stream:
https://meetings.conf.meetecho.com/ietf118/?session=31744

Meetecho for onsite participants:
https://meetings.conf.meetecho.com/onsite118/?session=31744

Audio stream: https://mp3.conf.meetecho.com/ietf118/31744.m3u

Zulip: https://zulip.ietf.org/#narrow/stream/core

Note Takers: Christian Amsüss, Esko Dijk

Chat scribe: Marco Tiloca

* * *

# Thursday, November 9, 2023

08:30-10:30 UTC

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (10)

Presented slides:
https://datatracker.ietf.org/meeting/118/materials/slides-118-core-chairs-slides-00.pdf

MT doing introductions and agenda bashing.

MT (p7): draft-ietf-core-target-attr was approved for publication.  
MT (p8-9): on current status of documents that left the WG:
draft-ietf-core-sid (in IESG evaluation) and
draft-ietf-core-oscore-edhoc (in IETF Last Call).  
MT (p10-11): documents post WG Last Call.  
MT (p12-13): other documents (updated and not in the agenda; recently
adopted; individual and recently updated; related publication of RFC
9482 developed in the ACE WG).

FP: On draft-tiloca-core-groupcomm-proxy: Understanding was that there
was consensus to be adopted, and no call for WG adoption on the mailing
list ever happened. Let's just do that.

MT (p14): Report from hackathon. CORECONF general direction confirmed by
implementation. Pubsub implementation further progressed and available.
A team already has some code for the CoAP API for RIOT.

MT (p15): Outlook of upcoming CoRE interim meetings.

## YANG Schema Item iDentifier (YANG SID) and COMI (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-sid/
* https://datatracker.ietf.org/doc/draft-ietf-core-comi/

Presented slides:
https://datatracker.ietf.org/meeting/118/materials/slides-118-core-coreconf-cri-00.pdf

CB presenting.

CB (p1): No big decisions to make, just detailed work.  
CB (p1): RFC 9254 finished and used in other WGs. Maybe we want some
more compact forms of YANG textbased items (for instance, IPv6 address
in YANG is hex text). RFC 9254 is a solid basis for that.  
CB (p1): CORE-SID is in IESG processing and has no interdependency with
YANG-CBOR except that both use "SID is 63bit unsigned". The number of
DISCUSS ballots went down by one after the Monday IESG breakfast
already.  
CB (p1): Just as there is NETconf (YANG-over-SSH) and RESTconf
(YANG-over-HTTPS) there is CoMI (YANG-over-CoAP). The feedback that we
got says that we can still further simplify this — we should take this
because we work on *Co*RE.  
CB (p1): On YANG-LIBRARY: In YANG protocols, this is replacing the
original mechanism for negotiating known components between server and
client. The standard YANG library is way too complicated, while this is
simplified. It is inappropriate to advance this while the rest is work
in progress.

CB (p2): Cleared DISCUSS because the AD agreed that his view on
consistency was in conflict with the fact that many YANG modules without
SID files are out there. IANA seems to be onboard. Pyang caught briefly
in GitHub trouble.  
CB (p2): We are working on initial allocations.

CA: At some point, could there be a venue with a tutorial introduction
for people new to the coreconf topics?  
CB: We could do it in Brisbane for IETF 119. I'm not sure of how big a
takeup it would be. Maybe it is for an interim meeting. Slideset from
Scott Mansfield who told IEEE in 2022 that "this is done, get a
megarange".

AHF (on chat): I support the idea of having some sort of tutorial for
CORECONF, I think that it could also be useful to have some slidedeck so
that the authors/chairs could redirect people to that content. I have
been following the YANG-SID just lately and could find that content very
useful  
JJ (on chat): Thank you @Alex! So you'd like SID + CORECONF tutorial,
not just SID.  
AHF (on chat): I mean, I am personally interested in the YANG-SID work,
since people at the IETF are starting to be interested in the CBOR
encoding, but I think having some simple slidedeck also pointing to the
right sections of the different drafts/RFCs could very useful for the
IETF community.

CB (p2): CoMI does not want to compete with NETconf/RESTconf; feedback
is coming in.  
CB (p3): NETCONF is stuck with XML because it is part of the protocol.
CoREconf relies on both YANG-CBOR and a managed SID space.  
CB (p4): On implementer report. We could replace separate full datastore
operations by using the main ones with SID 0. SID 0 has already been
reserved. We could chop 5 pages off the document. On RPC, general
semantics are all-or-nothing, but we may incur an expensive rollback
mechanism. (Not suitable maybe for constrained devices.) Might do in
YANG library on whether server supports it.  
CB (p5): On Andy's report and feedback. NMDA=network management
datastore architecture.  
CB (p5): Discuss instance identifier optimization. E.g., if we have 5
interfaces, we can describe which one to talk about. You complement SID
with a "key". Instance identifier then is SID + 1-or-more-keys. Does a
response need to contain all keys? Right now, it identifies top SID to
ensure that the CBOR YANG representation works. It is a simplification
that makes response data structure not quite conforming to YANG.  
CB (p5): On potential addition of depth parameter. Currently no
pagination, only block-wise, which is harder to operate from the
application layer.  
CB (p5): Summarizing, it will take about 1 week to incorporate those
comments.

AHF: Coming back to CA's comment in YANG, agree on need for tutorial /
slides with references. The YANG-SID draft was clear, but knowing what
is encoded and how (document on the data plane, is it SID encoded?) is
unclear. I am more interested in YANG push. See also the chat. I support
having something here.

## Constrained Resource Identifiers (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides:
https://datatracker.ietf.org/meeting/118/materials/slides-118-core-coreconf-cri-00.pdf

CB presenting.

CB (p6): Main report: Started out expecting support of URIs as used in
CoAP; but feedback was that URIs that are not translatable complicate
the use of CRIs. Maybe we swung too far. Now the parts unlikely to be
used for CoAP are expressed as an extension (e.g., for percent encoding
things); it simplified things just a bit and not a lot, but still good.

## Group Communication for the Constrained Application Protocol (CoAP) (Esko Dijk) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-groupcomm-bis/

Presented slides:
https://datatracker.ietf.org/meeting/118/materials/slides-118-core-group-communication-for-the-constrained-application-protocol-coap-v2-00.pdf

ED presenting.

ED (p2): Recap. This obsoletes the predecessor RFC 7390, adds things
found and updates from other documents. (Slide: s/IP multicast group
communication/& and other transports/)  
ED (p2): Now it mandates security (with Group OSCORE), and describes
when security is not an option (mentioning specific use cases).  
ED (p3): Delta since 112, mostly addressing a recent review from John
Mattsson, some points of which were also discussed at an interim
meeting.  
ED (p4): Review comments all addressed. There are no issues. There is an
old open PR with editorial points, most of which have been addressed
already. We'll double-check that all were addressed before closing it.  
ED (p5): Awaiting confirmations that the latest review was well
addressed, and that the WG Last Review (from Carsten) was also well
addressed. If all is ok, the document can move forward.

## A publish-subscribe architecture for the Constrained Application Protocol (CoAP) (Jaime Jiménez) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-coap-pubsub/

Presented slides:
https://datatracker.ietf.org/meeting/118/materials/slides-118-core-coap-pubsub-00.pdf

JJ presenting.

JJ (p2): Has been here forever. No major breakage, some implementation
updates were needed.  
JJ (p3): Architecture overview.  
JJ (p4): Architecture: Types of resources (collection resource, topic
resource with the topic configuration, topic-data resource where to
publish and subscribe).  
JJ (p5): Topic-data resource is where publications and subscriptions
happen on a topic.  
JJ (p6): People asked about the lifecycle of a topic.  
JJ (p7): Hackathon report; now also possible to do (i)PATCHing of the
topic configuration. It is usable. The implementation is easier to read
and understand than the document.  
JJ (p8-9): Ticking off to-do items. Document now more stable, it would
be good to have comprehensive reviews.  
JJ (p10): One major point is about the topic-data resources as
potentially hosted in a server different from the pub-sub broker. That
requires a state, managed between the broker and that data server. It
sounds great, it should remain possible to do that in this architecture,
but we should not overload this one and fully define it here.

CB: We discussed this. The outcome was: a Client of pubsub should expect
topic-data resource to be on a different server, but that's part of the
protocol already. In the figure of slide 10, the line between the broker
and the separate data server is not defined, and that's a separate
protocol for a separate document. Yet, pubsub does not change. That
protocol represented by that line could even be proprietary today;
subscribers will maybe need to participate in that protocol. We can
guarantee compatibility on the subscriber side, I am not sure on the
publisher side.

DN: People think of MQTT often here. MQTT deals more with publishers and
subscribers than with topics. Is it the scope of the document?  
DN (rephrasing): If I were to use CoAP pubsub to replace a scenario
where I use MQTT, currently we may run into scalability problem. When
doing topic discovery with MQTT, the publisher will tell you out-of-band
which topic it is. Then the subscriber talks to the topic.  
CA: Disagree -- In MQTT-style deployments, a publisher that has
out-of-band knowledge could tell subscribers about the topic data
resource.

DN: On topic creation, you're not fully aware of timing. The publisher
may appear before or after the subscriber. Topics are created implicitly
there at first subscription / publication. With the creation step, is
this is till possible? From what you answered, you would do discovery
and create if you didn't find when you are subscriber, right?  
JJ: It could be optimized to follow that pattern, so first POST to the
topic-collection resource to create the topic and its topic resource,
then possible additional POST on the topic resource to indicate the
topic-data resource. But you need to have something on the topic-data
that is created upon first publication, otherwise you get 4.04 if you
try to access it before then.  
DN: To summarize, I am worried about the ease of use compared to MQTT
which you'll compete with.  
JJ: Hard question; yes. No good answer.

JJ: I was hoping to get more thorough reviews. I don't expect huge
changes to come, but it depends on the reviews. Requesting for
volunteers.

CA (note to self, for mailing list): Half-created resources can be a
thing, that's what you have when something is in /.well-known/core and
4.04s.  
JJ (note to self, for punching session with David): one-off
topic-configuration + populated topic-data could be easily added as an
example if we have a property called current representation that
initializes the topic-data. Also to DN, "MQTT has out-of-band discovery"
is like saying it does not have discovery. Also, CoAP is all about state
transfer between clients and servers, and CoAP PubSub follows that
design via a broker, it is hard to change that. Is that something we
really want to do?

## DNS over CoAP (DoC) (Martine Lenders) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-dns-over-coap/

Presented slides:
https://datatracker.ietf.org/meeting/118/materials/slides-118-core-dns-over-coap-doc-00.pdf

ML presenting.

ML (p2): Recap. Motivation: encrypt DNS exchanges, overcome the path-MTU
issue, share resources.  
ML (p3): Small changes to the document.  
ML (p4): SVCB record is under discussion. Work is needed because no ALPN
record exists for DTLS, and no SVCB for EDHOC. DoC is not right place to
define that. Shall we start a new draft?  
ML (p5): Cacheability of DNS responses is a plus coming from the use of
CoAP. If OSCORE is used, as recommended, that's possible to achieve
through draft-amsuess-core-cachable-oscore, now added as informative
reference.  
ML (p6): WGLC?  
CB: Has anyone implemented it?  
ML: I have: the client in RIOT and the server in Python.  
ML: More implementations would be helpful.  
CB: More implementers?  
(LT raising hand)

MT on p7: Discussed with CA yesterday on SVCB and ALPN. We can proceed
incrementally -- This document can have some more text that "summarizes
the current state" as in this slide, and then has an informative
reference to a new document that provides at least a problem statement
to be addressed separately and in the future. If that's good enough, OK.
Only do more if externally needed and/or requested later on during the
processing of the present document.

## Key Update for OSCORE (KUDOS) (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/

Presented slides:
https://datatracker.ietf.org/meeting/118/materials/slides-118-core-key-update-for-oscore-kudos-ietf-118-00.pdf

RH presenting remotely.

RH (p2): Recap, and pointer to the parts on the key limits that were
split out as a separate document.  
RH (p3): Key update procedure.  
RH (p3): Old-nonce field newly introduced, to be used in the reverse
flow.  
RH (p4): General changes since 117.  
RH (p5): Modes: FS and no-FS modes, and signaling for them.  
RH (p6): Y field now added, together with the "old nonce" from the
previous KUDOS message. Used in the reverse flow in its 2nd message
(CoAP request) which has to contain it anyway and now does it properly.
Previously, the old nonce was concatenated with the new one, but that
was insufficient to get the required state at the server and had
limitations.

RH (p7): Open point on enabling a more flexible message flow, as
decoupled from the currently rigid request/response flow. For example,
both KUDOS messages can be CoAP request (CA provide an example in a
scenario with the Resource Directory), or the second KUDOS messages as a
CoAP response might be paired with a CoAP request different from the one
that transported the first KUDOS message (e.g., if the response is an
Observe notification). Should we allow that?  
(no objection heard)

RH (p8): Another open point: can KUDOS messages be just regular
messages, and not necessarily be sent to /.well-known/kudos when CoAP
requests? The client can have data pending to send, and it might want to
send that data to the right resource at the server, making that request
also a KUDOS message? Implications? KUDOS requests may be in any
message. The caveat is that the server can't be sure of the freshness of
such a request (due to its protection with the temporary Security
Context CTX\_1). If the server application demands freshness and can't
assert it, the server will reply with a protected error message (also a
KUDOS message, thus completing the key update), forcing the client to
repeat its application data request to prove freshness.

CA: We have this already with Appendix B.1 of RFC 8613 -- they can get
"maybe not fresh" messages.  
ED: When combining with an application message -- is it worth the
effort? How often does a key update happen, after all? If, e.g., it
happens once every month, then maybe it is not worth optimizing /
piggybacking.  
RH: The frequency depends on the policy or other unpredictable events.
It may add some complexity. On the other hand, it may be nice to merge
into a same message, so that KUDOS is done before the application-part
of the message is forwarded to resource handler.  
ED: If it can be really separated in all cases, then it's easier and we
may go ahead. If there are corner cases, let's not.  
(CA on chat:): to ED's comment: +1 on "do it if separated easily" (I
believe it can)

RH: Counters as nonces? Proposed to allow, but limited to CAPABLE
devices, for which random nonces remained preferred. Possible to use a
similar formulation as used in the OSCORE profile of ACE (RFC 9203).  
CA (on chat): thumbs up on the counters proposal.  
GS (on chat): +1 for support for counters.

RH: Open point: splitting out to a separate WG document the procedure
for updating the OSCORE IDs. It can be run embedded in KUDOS, but also
stand-alone, and it is fundamentally independent from KUDOS. It would
shorten the document a lot.  
GS (on chat): Split out makes sense.

MT: CB, you were forming an opinion on this split?  
CB: Splitting is inexpensive. If there is a benefit, it should work. But
I am not sure who would ever have to read just one of the two.  
RH: If you use some other mechanism for key updates, one could then do
ID updates with that dedicated procedure.

GS: The comment about reading both is good. KUDOS is getting big, it is
good to try to get the number of pages down. I think we should split.
Those are two separate functions.  
RH: Yes, it reduces the complexity of the KUDOS document.

RH: Outlook. Soliciting feedback.

(some more chat on splitting)  
GS (on chat): The KUDOS document is 70 pages, which is kinda long for
replacing Appendix B.2 which is 5 pages. Of course, additional
functionality is provided, but I think it would be good to concentrate
on key update.  
RH (on chat): Sure, a benefit would be to focus the document exclusively
on key update.  
CB (on chat): If the authors think this is easy to do (and does not lead
to a ton of restatement between the drafts), let's split.  
RH (on chat): Yes, I'd say we can do the splitting without needing much
restatement.

## Constrained Application Protocol (CoAP) Performance Measurement Option (Giuseppe Fioccola) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-coap-pm/

Presented slides:
https://datatracker.ietf.org/meeting/118/materials/slides-118-core-coap-performance-measurement-option-draft-ietf-core-coap-pm-01-00.pdf

GF presenting.

GF (p1): This document has been recently adopted.  
GF (p2): Recap: the goal is to perform measurements of performance in
constrained environments, which can be resource intensive. IPPM
establishes methods (see RF9506). This document proposes a more
efficient method, using bits in a new CoAP option. It's mostly about
measuring Round Trip Time (RTT) and packet loss.  
GF (p3): Shown some of the methods and the related bits, known from
analogous methods used in QUIC. The S bit (Spin) measures the RTT. The Q
bit (sQuare) measures the packet loss. They can be conceptually combined
into a third bit C.  
GF (p4): The CoAP Option can convey a combined value, and it is in
itself extensible. We are working on an implementation, and aiming to
decide what can be standardized. We expect to have results that can be
shared at interim meetings.  
GF (p5): Scenarios with no-proxy, or collaborating proxies. All allow
measurements in different places (i.e., end-to-end or hop-by-hop).
Collaborating proxies interact with the CoAP option, and may modify its
value or not.  
GF (p6): The CoAP option is proxy-unsafe. No measurement is possible
across caching proxies. Non-caching proxies may treat the option as
safe-to-forward, thus still enabling measurements. Application to the
cases where DTLS and OSCORE are used.

GF (p7): Next steps, implementation, and comparison of results.  
LT: Why not encode your measurement information in the CoAP Message ID
or Token?  
GF: The option is better because it can be in each message, not sure if
can do the same otherwise.  
LT: Just a comment.  
GF: We can consider. We saw the flexibility in using the option as it
can be in each message. The employed measurement methodology needs
information for each message. The square wave enforced by the Q bit
covers all the flow.  
CB: The discussion about unsafe bit is one answer. It ensures that you
do not measure what you cannot measure.

CA: Beware that you can *not* include the option in all messages: Empty
ACKs (notes-only: and RST) can not have CoAP options.

MT: Document is not fully self-contained (some bits underdefined). The
bit C is conceptually a combination of the bits S and Q, but its
computation is defined as a function of S and D (which is not defined or
used in this document). Better to defined also the computation of C as a
function of S and Q, so that the reader does not need to check also the
document where the D bit is defined.

MT: Also it would be good to have examples, maybe in appendices, of
message exchanges in the different scenarios, showing how the bit values
change and what is measured. This can be in the same spirit of the early
examples that were built with CA during a CoRE interim meeting, when
discussing about non-cooperating proxies.

MT: is this useful and applicable in group communication? - please think
about that and add considerations to the document. (Most likely, it
won't work well - the multiple responses to a group request may disturb
the measurements, just like for the case where Observe is used. There's
no constant flow of requests all of which are paired with a single
response, which is what this method relies on)

GF: On the first point about the C bit, we will revise. On group
communication, something may work. We will look at it with the
implementation.

## Topics from the T2TRG meeting on 2023-11-03 (Christian Amsüss) (15)

Topics include the following documents:

* CoAP Protocol Indication
  * https://datatracker.ietf.org/doc/draft-ietf-core-transport-indication/

* CoRE Resource Directory Extensions
  * https://datatracker.ietf.org/doc/draft-amsuess-core-resource-directory-extensions/

* CoAP over GATT (Bluetooth Low Energy Generic Attributes)
  * https://datatracker.ietf.org/doc/draft-amsuess-core-coap-over-gatt/

Presented slides:
https://datatracker.ietf.org/meeting/118/materials/slides-118-core-t2trg-updates-and-transport-indication-02.pdf

CA presenting.

CA (p2): History of scheme names coap+foo. Some confusion present about
using the '+'. But some protocols in different drafts do not define the
transport with +.  
(p3): Examples of naming/encoding without needing +foo schemes (i.e., if
a literal in the URI authority component unambiguously identifies the
transport protocol directly).  
(p8): Proposing to move forward with the proposed naming scheme
criterion, in the interest of not using coap+foo unless otherwise
necessary. Feedback? Should we do this?

CB: Yes. We had the idea to use IPvFuture syntax for SVCB literals.   
CA: Points to slide 7 (with SVCB) as a way of doing this; I will
explore.

GS (on chat): As far as I understood, .alt is open for anyone to use so
might lead to overlap?  
CA: Yes, .alt is free for all. I don't think its an option for BLE or
SMS transports that sit on .arpa already. For a serial link that is
local anyway, it may work.

MT: The criterion is very clear. On not using coap+foo when the
transport is anyway understandable, a slide gave a "not recommended"
statement, while another one said "must not". Is there a clear direction
on the normative language to use? In other words, if the transport is
understandable by other means, is it still legitimate to use coap+foo?  
CA: No clear answer yet - a document defining a new CoAP transport will
be Standards Track, so it needs to convince the IETF community about
using a new scheme. Guidance can be given then by the current documents.

CA: (p6) here we use the + syntax already, getting rid of the + here is
not worth the trouble. We didn't anticipate this discussion back then.

AP (not in queue): for future protocols, don't we need the + syntax?  
CA: We don't need to define coap+quic if we want to do CoAP over QUIC.  
AP: Perhaps old clients can support both old and new formats?  
AP: How to keep the coexistence working?  
CA: The existing schemes keep doing what they do with the +. For new
ones, use the new criterion on how the transport can be determined.

CA (on chat): More precisely, we can claim the implication for the coap
scheme, or even more precisely, for the URI interconversion steps.  
CA (on chat): I think that it can get away with lose coordination even
(no document that finally says any e164 address in CoAP is sent as SMS),
the same way we handle the names being DNS: It's fine if another system
uses anything else, and the global consistency is more a matter of
awareness. (Not ideal but maybe OK).

## Applying Generate Random Extensions And Sustain Extensibility (GREASE) to EDHOC Extensibility (Christian Amsüss) (5)

* https://datatracker.ietf.org/doc/draft-amsuess-core-edhoc-grease/

Presented slides:
https://datatracker.ietf.org/meeting/118/materials/slides-118-core-grease-for-edhoc-00.pdf

CA presenting.

CA: The LAKE WG has rechartered and can now take extension work.  
CA: This document was presented in LAKE on Monday, proposing a GREASE
mechanism for the EDHOC key establishment protocol, see
draft-ietf-lake-edhoc.  
CA (p4): No-op "options" are introduced to EDHOC, based on well-known
EDHOC authentication methods and cipher suites intended only for this
purpose. This ensures that middle boxes and EDHOC peers are capable to
process / react upon EDHOC messages as intended, and will allow to
promptly detect deviation and prevent ossification.  
CA: There seems to have been interest in the LAKE WG, and this will
likely progress there.

## Flextime (10)

ED: What about CoRE Link format work encoded as CBOR?  
CA: We are waiting on completing the work on CRI (see
draft-ietf-core-href) and packed-CBOR (see draft-ietf-cbor-packed), that
we should use to keep the content small. The work on CoRAL (see
draft-ietf-core-coral) should continue when those are done.

Σ 120

* * *

*[MT]: Marco Tiloca


*[JJ]: Jaime Jiménez


*[FP]: Francesca Palombini


*[JPM]: John Preuß Mattsson


*[CB]: Carsten Bormann


*[CA]: Christian Amsüss


*[KH]: Klaus Hartke


*[RH]: Rikard Höglund


*[TF]: Thomas Fossati


*[MG]: Matthew Gillmore


*[DN]: David Navarro


*[GS]: Göran Selander


*[BS]: Bilhanan Silverajan


*[AS]: Alan Soloway


*[MCR]: Michael Richardson


*[AK]: Ari Keränen


*[MJK]: Michael Koster


*[NW]: Niklas Widell


*[ED]: Esko Dijk


*[HB]: Henk Birkholz


*[ST]: Sean Turner (here)


*[ML]: Martine Lenders


*[MW]: Matthias Wählisch


*[KZ]: Koen Zandberg


*[GF]: Giuseppe Fioccola


*[MN]: Massimo Nilo


*[LT]: Laurent Toutain


*[AB]: Andy Bierman


*[JT]: Jernej Tuljak


*[RML]: Rafael Marin-Lopez


*[AF]: Alex Fernandez


*[MK]: Matthias Kovatsch


*[RW]: Rob Wilton


*[IP]: Ivaylo Petrov


*[BSc]: Ben Schwartz


*[AP]: Alexander Pelov


*[AHF]: Alex Huang Feng


