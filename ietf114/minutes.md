# IETF 114 - Agenda for Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

Date and time: Tuesday, 26th of July 2022, 19:00 - 21:00 UTC

Notes: https://notes.ietf.org/notes-ietf-114-core

Meetecho video stream:
https://meetings.conf.meetecho.com/ietf114/?group=core&short=&item=1

Meetecho for onsite participants:
https://meetings.conf.meetecho.com/onsite114/?group=core&short=&item=1

Audio stream: https://mp3.conf.meetecho.com/ietf114/core/1.m3u

Jabber: xmpp:core@jabber.ietf.org?join

Zulip stream: https://zulip.ietf.org/#narrow/stream/21-core

Minute takers: Ivaylo Petrov, Matthias Kovatsch, Christian Amsüss

Jabber scribe: Jaime Jiménez, Marco Tiloca

# Tuesday, July 26, 2022

19:00 - 21:00 UTC

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (15)

* WG and document status

Presented slides:
https://datatracker.ietf.org/meeting/114/materials/slides-114-core-chairs-slides-00.pdf

MT doing introductions.

CB: If time allows, we can talk about jpy URI-scheme from ANIMA.  
coaps+jpy

MT going through recent documents:

Published RFCs:

* RFC 9176: CoRE Resource Directory (RD)
* RFC 9193: Sensor Measurement Lists (SenML) Fields for Indicating Data
  Value Content-Format
* RFC 9254: YANG CBOR

CB summarizing history of RD (started 2011) and YANG CBOR (started 2013)

RFC queue: core-problem-details requirements coming also from 3GPP.
Execution done in record time.

IESG Processing: core-sid  
CB: Got substantial feedback on core-sid from IESG, so while it's
officially out of WG's hands, WG should still have an eye on what's
going on (might be a second IETF LC). Please see github repository at
[https://github.com/core-wg/yang-cbor][1]

MT Presents other documents post WGLC, recently adopted and pending
adoption, and individual (new) submissions. People are encouraged to
read and comment.

## HREF (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides:
https://datatracker.ietf.org/meeting/114/materials/slides-114-core-href-cri-00.pdf

CB presenting. Mainly a report, no time to discuss much -- stuff for
interim meetings.  
CB (p2): The draft has not been updated because it is essentially done
(only finding little nits). Most work now is on test vectors and
implementations, especially checking that they work correctly with URI
implementations. Percent encoding not really compatible with CRI.  
CB (p3): How to express `foo:` in a CRI? We can only have one of the
CRIs.  
Need to decide between "0 segments" and "zero-length opaque URI" --
speaker prefers support for first (no case of zero-len opaque known).  
Could flip a coin. If you ever saw a URI of that shape, please send a
mail to the list.

BM: Are we discussing URIs or URNs? (The stuff in URNs is not opaque).  
CB: All confusing; there's WHATWG and IETF and daily terminology. All
this is about URIs; CRIs cover URIs. URIs is the overall term that
covers URNs and URLs.  
BM: So there's also CRNs?  
CB: CRI can encode all (URIs = \{URL, URN} and even IRIs).  
CB: There's a URI scheme named "urn". Half the people who say URN means
that, the other half means all URIs as on (p3) item 2.  
CB: It doesn't help to try to use these terms; you best think about URIs
with certain properties (like having an authority, having a segmented
path, etc.)

CB (p4): CURIEs. Extensively covered 6 weeks ago at an interim meeting.
Reporting from there: Nothing we need to do, but there's an opportunity
to do lexical compression (that also looks good on a whiteboard) well
here. Now it can be done based on cbor-packed, although it's relatively
complicated. At the interim meeting, it was said to do this in a
separate document (possibly CoRAL).  
(p6) This would split up which CURIEs we do support. Whatever we come up
with here doesn't have to cover the entire CURIE space.  
(p8) Plan with 4 concrete todos.

MT: When next submission expected?  
CB: Depends on bugs found in implementations, down to small number, so
weeks.

Q&A? None.

## CoRAL (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-coral/

Presented slides:
https://datatracker.ietf.org/meeting/114/materials/slides-114-core-core-coral-the-constrained-restful-application-language-coral-00.pdf

CA presenting.

CA: Having CRIs, we can now build structured documents. Similar to
RFC6690, but better support for structured data (subject, predicate,
object triples).  
CA: Literals are now simplified. Any properties expressed through CBOR
tags. Ongoing work on compact format based on cbor-packed.   
CA: There is more work to be done to have dictionaries (tables) with
terms that allow (such) shorter representations. This is not a trivial
work. Still can load terms via URI.  
CA: Security model is work in progress (not going in the direction as
ACE). Decisions on binary serialization needs more real-world examples
-- please share!  
CA: Planned mapping to problem-details; queries, patches and provenance
not likely in the first version.

Q&A:

MT: Focus on items on slides 6 and 7? Possibly working in parallel but
at a slower pace on the items from slide 8.  
CA: Yes, items on 8 are being started now, but worked on in parallel.

## Group Communication for CoAP (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-groupcomm-bis/

Presented slides:
https://datatracker.ietf.org/meeting/114/materials/slides-114-core-group-communication-for-the-constrained-application-protocol-coap-00.pdf

MT presenting.

MT: Had WGLC after Vienna. Many detailed comments received and adopted
in the latest version. Also got a PR, so far only with editorial fixes.
More are expected to come.  
MT (p3): The latest version -07 addresses all comments received so far. 

MT (p4): Group names: clarifications about naming for CoAP groups and
security groups; all examples about naming of applications groups and
group discovery moved to appendices.  
MT (p5): Added text on proxies, limited but slightly-more-possible use
of reliable transports, interworking with other protocols (revised).  
MT (p6): Clearer on "NoSec not recommended".  
MT (p7): Plan to submit version -08 once received further expected
comments from Carsten and John; Francesca recommended to request
publication together with -core-oscore-groupcomm and
-ace-key-groupcomm-oscore.

Q&A?

CA: Was there a discussion on later blocks in block-wise transfer with
groupcomm?  
MT: The switching from a first multicast request with Block2 to
follow-up individual requests over unicast has been around for a while.
Carsten recommended to add that the switch can potentially include also
moving from UDP to reliable transports.

## Observe Notifications as CoAP Multicast Responses (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-observe-multicast-notifications/

Presented slides:
https://datatracker.ietf.org/meeting/114/materials/slides-114-core-core-observe-multicast-notifications-observe-notifications-as-coap-multicast-responses-00.pdf

CA: overview of updates since -02.  
CA (p6): Open point: if using an OSCORE Deterministic Request as phantom
request, the server does not care of clients not supporting it. That is,
the server does not run in parallel a "twin" group observation not based
on the OSCORE Deterministic Request. (No objection heard).  
CA (p7-9): Todo and ongoing work: use of CRI to indicate
transport-specific information in the error informative response.  
CA (p10): Summary of next steps, including the open point above,
switching to using CRIs, and more.

Q&A:

JJ: May this affect pub-sub?  
CA: The basic pub-sub would not change. This work only provides an
additional option to realize pub-sub.

## Profiling EDHOC for CoAP and OSCORE (Rikard Höglund) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-edhoc/

Presented slides:
https://datatracker.ietf.org/meeting/114/materials/slides-114-core-profiling-edhoc-for-coap-and-oscore-00.pdf

RH presenting.

RH (p2): Summary of document contributions. Main point is that plain
EDHOC uses 2 round trips, while this optimizes it to pack message 3 in
the first OSCORE message. Also web-links to EDHOC resources.  
RH (p3): Adjusted to EDHOC changes in its v -15.  
RH (p4): Requirements relaxed, message processing simplified.  
RH (p6-7): Guidelines on when it is feasible and convenient to use
Block-wise together with the combined EDHOC+OSCORE request. Just touched
on it shortly -- please read in the draft.

CB: We have to be careful about not stuffing specs with too much
informational content. Many reasons; one is not to DoS IESG, but it's
also the reader's impression "so many pages, looks complicated". Do we
have a good way to put things like these considerations of whether it's
an improvement into a separate place (separate from relatively simple
standards track part)? Not saying this draft is where we have to do this
now, but struck me as one example of the trap of too much informational
content. Just think whether something can be exported to informational
doc so this stays crisp.

GS (on chat): +1  
CA (on chat): +1

RH: There is not much content that could be extracted; maybe use an
appendix.  
CB: Appendix hides text from some people, but it's still part of page
number / first impression. By the way, once you have an informational
document, that can be used as roadmap ("How do the normative documents
fit together?"). But sure it does make document management harder.

RH (p8): We expect one more iteration, then we might be ready for WGLC.
But it's better to synch with the LAKE WG and have the WGLC in parallel
to the one for EDHOC.  
CA: Could only make meaningful WGLC review when EDHOC from LAKE is also
in WGLC. Hence, sync timelines.

## Key Update for OSCORE (KUDOS) (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/

Presented slides:
https://datatracker.ietf.org/meeting/114/materials/slides-114-core-key-update-for-oscore-kudos-00.pdf

RH presenting.  
RH (p2-3): KUDOS inspired by Appendix B.2 of OSCORE (RFC 8613).
Recapping main features; renamed 'id\_detail' to 'nonce' in the OSCORE
option value.  
RH (p4-5): two modes of operations: normally with Forward Secrecy or
alternatively without Forward Secrecy, if devices can't store in
persistent memory and need a stateless key update. This was an appendix
and was moved to the document body. The signaling relies on a bit in the
OSCORE option value, is integrity protected and allows for an "agreed
downgrade" to no Forward Secrecy.  
RH (p6-7): the two peers can negotiate whether preserving their ongoing
observations beyond the key update. Both peers have to agree so that it
happens. A peer not interested in updating keys per se can still run
KUDOS leveraging this feature, thus efficiently cancelling all the
observations. This was an appendix and was moved to the document body.
The signaling relies on a bit in the OSCORE option value and is
integrity protected.  
RH (p8): also possible for the two peers to update their OSCORE IDs,
using a new CoAP option. This can happen stand-alone or embedded in the
KUDOS key update. This was an appendix and was moved to the document
body.  
RH (p10): Revised the OSCORE option value to specify both the size of
'nonce' and signaling bits for the features discussed before.

RH (p10-11): Revised the body of the updateCtx() function, also aligned
with latest changes in EDHOC. The different input are wrapped into CBOR
byte strings to protect against attacks when different values are
concatenated to the same sum.  
RH (p11): Still considering two possible methods within updateCtx():
MEDHOD 2 for when EDHOC was used and based on EDHOC-KeyUpdate(); the
simpler MEDHOD 2 based on HKDF-Expand() otherwise. We're thinking to
introduce an "agreed fallback" to METHOD 2, e.g., when the EDHOC session
has become invalid.

Q&A:

CA: If fallback to Method 2 is OK if any party says so, why having
METHOD 1 at all?  
RH: We'd like to use EDHOC-KeyUpdate if possible.  
CA: But which security and key update properties does it lose?  
RH: Good question. Can't answer that right now.  
MT: Let's take that offline in the interest of time.

GS: In the spirit of CB's comment on size of drafts, could some parts of
this be split out, e.g., the part on changing OSCORE IDs?  
RH: It could; that can also be run stand-alone independent of KUDOS. The
split would be feasible.  
GS: How about key limits and KUDOS protocol?  
RH: Same, that could also be split. It grew like this because of earlier
discussions and feedback. Related by causality, but if desire is to have
more, smaller drafts, it could be split.

## DNS over CoAP (Martine Lenders) (10)

* https://datatracker.ietf.org/doc/draft-lenders-dns-over-coap/
  
  Ready for Working Group adoption ?

Presented slides:
https://datatracker.ietf.org/meeting/114/materials/slides-114-core-dns-over-coap-doc-00.pdf

ML presenting.

(page numbers as printed on the pages and labelled in the PDF)  
ML (p1): DNS push discussion is more recent than current draft version. 

ML (p2): Motivation is to protect DNS queries from IoT devices.  
ML (p3): Overview of proposal and how this is more efficient than
competing solutions.  
ML (p4): Restatements of CoAP behavior reduced in various places. Also
added algorithm based on CoAP Max-Age to drive caching.  
ML (p5): Changes done as addressing early TBDs. Still to pick-up an ID
for the Content-Format.  
ML (p6-7): DNS push primer. Problem: requires DNS-over-TLS. Solution:
use CoAP Observe as signal to use SUBSCRIBE instead of QUERY at DoC
Server. Then PUSH is turned into an observe notification.  
ML (p8-9): Example of the above.

Q&A

MT: Draft received pretty well also on last IETF, with people interested
to review. Obvious next step is WG Adoption Call. Any comments or
objections? (Head none)  
MT: We'll start a WG Adoption Call on the mailing list.

CB (on chat): +1

## Constrained Application Protocol (CoAP) Performance Measurement Option (Giuseppe Fioccola) (10)

* https://datatracker.ietf.org/doc/draft-fz-core-coap-pm/

Presented slides:
https://datatracker.ietf.org/meeting/114/materials/slides-114-core-coap-performance-measurement-option-draft-fz-core-coap-pm-02-00.pdf

GF presenting.

GF (p2): Coming from operational requirements; reading IDs / sequence
numbers is resource intensive.  
GF (p3): Overview of changes following comments received at interim
meeting.  
GF (p4): Spin bit vs sQuare bit.  
GF (p5): New CoAP Option to carry performance measurement (PM)
information.  
GF (p6-7): Use cases. Mostly for end-to-end measurements, but split
measurements are also possible. Considered also collaborating and
non-collaborating proxies, network function or probes (e.g., looking
deep into application). Considered possible use of OSCORE.  
GF (p8): Next steps: evaluate WG adoption.

MT: Hard to navigate the various combinations of the different variants.
Best to revise the draft with a very systematic presentation of those,
highlighting what they achieve and what limitations they have. Also
examples with message exchanges can further help, perhaps as appendices.

GF: Yes, there are many. Maybe provide references for better
understanding.  
MT: I will provide a review.

CB: What is the target status (Informational, Standards Track,
Experimental)?  
GF: For now, Standards Track because it is asking for a new CoAP Option.
But I don't know what the procedure is.  
CB: For getting a CoAP option, you just register one. We have space for
Expert Review CoAP options. Not saying this is what we should do, but
this is the gamut of possible outcomes. Experimental is also a
possibility.

CB (on chat): Obvious questions that we won't have time to discuss: How
well does a spin bit work with NSTART=1?  
CA (on chat): Or phrased differently: Which mechanism do you use to
arrive at NSTART>1?  
CB (on chat): What are the interoperability requirements (essentially
the echoing?) vs. the "how do I best use this"?

CB: Building on the discussion in the chat, how much of this is
interoperability requirement? How much is information on how to use
this? Let's chat on the mailing list.

CB (on chat): Is this something that should be discussed in CoRE and/or
IPPM?  
JJ (on chat): Good point, does IPPM handle application layer too?  
CB (on chat): Sounds like an opportunity for Chair-to-Chair chats.  
JJ (on chat): IPPM charter: "The IP Performance Measurement (IPPM)
Working Group develops and maintains standard metrics that can be
applied to the quality, performance, and reliability of Internet data
delivery services and applications running over transport layer
protocols (e.g. TCP, UDP) over IP."  
JJ (on chat): It seems they cover applications. We have to check this.

## CoAP over GATT (Bluetooth Low Energy Generic Attributes) (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-amsuess-core-coap-over-gatt/

Presented slides:
https://datatracker.ietf.org/meeting/114/materials/slides-114-core-core-coap-over-gatt-coap-over-gatt-00.pdf

CA presenting.

CA (p2): Initial proposal in 2020 (as an Experimental document), then
getting traction in 2021 (typo on slide). There is more work done in the
related draft-ietf-core-transport-indication. Now seen some interest
from the industry.  
CA (p3): There are more considerations of going directly over GATT
instead of some of the alternatives (e.g., supported by the Chrome
browser). Some of the issues of the other alternatives is that there
needs to be a routed network between the two endpoints.  
CA (p4): Fixing limitations: multiplexing, role reversal. Reconsidering
req-res on single Characteristic, framing like on CoAP-over-WS,
composite reads/writes  
CA (p5): Addressing: A new schema + MAC address would be simple, but
MACs are not always available. The device might not directly need the
MAC address due to use of proxies or when registering in services like
Resource Directory (RD).  
CA (p6): MAC-addressing might not be the preferred one. RD-like gateway
might generate a typical CoAP URI.  
CA (p7): Roadmap: Capabilities built on GATT might need BLE experts. It
might be more appropriate to go for a Standards Track.

CA (on chat): Link to the Chrome demo:
https://chrysn.gitlab.io/verdigris/

CB: Might take some extra time now. How to work in an environment that
does not have the typical assumptions? This is a good example.

CB (on chat): We need to devote an interim to this!  
JJ (on chat): +1  
MT (on chat): Yes

## Flextime (10) (No time)

### Come back to core-groupcomm-proxy status

CB: JJ and I will look at it.   
Expect to hear from the Chairs soon.

### coaps+jpy from Anima meeting

CB: Using tunneling protocol. Knee-jerk reaction on transport change was
to add + in URI scheme. Is that what we want? Without this new URI
scheme, resource type registration is a bit icky because it's on
non-existing resource.

### Fall 2022 interim meeting schedule

MT: Interim meetings will probably resume on August 31. Will be
confirmed on the list and with the CBOR Chairs.

Σ 120

* * *



[1]: https://github.com/core-wg/yang-cbor
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


*[BM]: Brendan Moran


