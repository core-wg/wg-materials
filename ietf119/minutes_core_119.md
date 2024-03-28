# IETF 119 - Agenda for Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

Date and time:

* Local time: Wednesday, 2024-03-20, 09:30-11:30
* UTC time: Tuesday, 2024-03-19, 23:30-01:30

Meeting material: https://datatracker.ietf.org/meeting/119/session/core

Notes: https://notes.ietf.org/notes-ietf-119-core

Recording: https://www.youtube.com/watch?v=r\_K8k9zLf5o

Audio stream: https://mp3.conf.meetecho.com/ietf119/32056.m3u

Zulip: https://zulip.ietf.org/#narrow/stream/core

Note takers: Christian Amsüss, Rikard Höglund

Chat monitor: Marco Tiloca

* * *

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (15)

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-chairs-slides-00.pdf

MT doing introductions.

MT: draft-ietf-core-target-attr and draft-ietf-core-sid have been
approved for publication. draft-ietf-core-oscore-edhoc is in IESG
processing and scheduled for a telechat in early April. Multiple
documents are in post WG Last Call processing, including
draft-ietf-core-oscore-groupcomm (waiting for the Shepherd write up from
Christian Amsüss), draft-ietf-core-yang-library waiting for comi
(formally also waiting for Shepherd writeup, but needed to be rehashed
as draft-ietf-core-comi progresses), and draft-ietf-core-groupcomm-bis
waiting for the resolution of old WG Last Call comments to be confirmed.

FP: I want to highlight that, for draft-ietf-core-groupcomm-bis, we have
documents in the ACE Working Group depending on it. So
draft-ietf-core-groupcomm-bis should be prioritized.

MT: A number of other documents are being worked on.

MT: The next series of CoRE interim meetings is booked. They will resume
on April 10, at 14 UTC with the same cadence as before, skipping one due
to the T2TRG interim meeting and the security hackathon at INRIA Paris.

MT: There is a discussion on using mDNS ongoing on mailing list, please
check and contribute.  
CB: IOTOPS will have a related discussion after this session, come
there.

MT: There is an upcoming Hackathon in Paris, on May 21-22, co-located
with a T2TRG WG meeting on May 21. Registrations are open.

## CORECONF Cluster (Carsten Bormann) (12)

* https://datatracker.ietf.org/doc/draft-ietf-core-sid/
* https://datatracker.ietf.org/doc/draft-ietf-core-comi/
* https://datatracker.ietf.org/doc/draft-ietf-core-yang-library/

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-coreconf-cri-href-00.pdf

CB presenting.

CB (p1): CoRECONF consists of a set of 4 documents.  
CB: draft-ietf-core-comi got comments in WG Last Call, which need time
to process. draft-ietf-core-yang-library represents a feature set of
comi implementations, so, while working on draft-ietf-core-comi, new
requirements may come in.  
CB: We have -yang-standin in the CBOR WG to optimize RFC 9254
(YANG-CBOR), which otherwise takes the YANG-JSON representation and
removes JSON complexities, but in its heart it is still a text based XML
format with IP addresses and dates as strings (which is wasteful, and
needs significant code in constrained implementations). With
-yang-standin, CBOR tags change that to binary.

CB (p2): The latest problem on implementing draft-ietf-core-sid is about
Tool support for in-flight vs. at-rest data. It's hard to work with
implementations, which is also being discussed in ANIMA. We have a clear
path now.

CB (p3): The goal is to complete the \*conf set.

CB (p4): COMI is addressing the usage of Unified Datastore, and the
RPC/Action examples have been fixed. A hallway discussion has still to
happen about "candidates".

CB (p5): Also on draft-ietf-core-comi, we received comments from its WG
Last Call. We simplified CoRECONF based on Koen's report (but they are
changes).  
CB (p6): We got input from Andy Bierman (tracked in issues), including
the need for examples and possibly allowing additional filter parameters
(the information base is small, so not filtering things may be OK but
growing, and mechanisms may need adjustment).

CB (p7): The plan is to address the remaining comments and create the
further examples. Then we will probably have another WG Last Call.

(no questions)

## Constrained Resource Identifiers (Carsten Bormann) (8)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-coreconf-cri-href-00.pdf

CB presenting.

CB (p8): We have defined an exchange format for parsed URIs, based on
CoAP's parsing and increasing the coverage. What is left to do is adding
more test vectors, making the registered URI scheme non-negative to be
conveniently used in CoAP options (because those can directly use only
unsigned integers), and clarify objective for determinism (applicable to
CRIs, but not to CRI references)

CB (p9): Overview of new content from version -14, including sections
that mirror Sections 6.4 and 6.5 from RFC 7252. We have also defined new
CoAP options Proxy-Cri and Proxy-Scheme-Number, analogous to Proxy-Uri
and Proxy-Scheme.  
CB (p10): Clarified conflict between Proxy-Uri and Proxy-Cri.  
CB (p11): Proxy-Scheme-Number will convey a URI scheme as an unsigned
integer.  
CA (in chat): The uint encoding also makes the Proxy-Scheme option very
short (0 bytes of data).

CB (p12): Plan: Get test in place, address the TODOs, complete the
Internet Draft in May.

(no questions)

## DNS over CoAP (DoC) and CoRE DNR (Martine Lenders) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-dns-over-coap/
* https://datatracker.ietf.org/doc/draft-lenders-core-dnr/

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-dns-over-coap-doc-discovery-of-network-designated-core-resolvers-01.pdf

ML presenting.

ML (p1): DNS over CoAP has been around for a few years, while the
discovery document is new.

ML (p2): The idea is to protect DNS requests against eavesdropping. Use
of CoAP, allow encryption with DTLS or OSCORE, and block-wise if needed.

ML (p3): Minimal document changes (referencing DNR).  
ML (p4): Deliverables from 118 have been fulfilled.  
ML (p5): Implementations available are Python/aiocoap (server side) and
RIOT/gCoAP (client side). Do we need to have more?  
(no response)  
CB: (commenting on slide with a guess:) "unbound" is the server side.  
ML: I am not sure which sides of unbound (which actually provides both)
the student will implement.

ML (p6): On the resolver discovery, so far there is what is listed on
the slides.  
ML (p7-9): We can have different message types depending on the specific
protocol used. There is also possible fields overlapping; service
parameters are present in all three.

ML (p10): What is missing? Keys/values for service parameters. We
registered ALPN for CoAP over DTLS ("co"). Beyond that, we have
described coaptransfer.  
ML: We need a way to identify a transfer protocol other than TLS and
DTLS. For OSCORE and the use of EDHOC in ACE to establish an OSCORE
association, we have also defined keys in the draft.  
ML: Thinking of the latter ACE case, we wondered how the authenticator
domain name is relevant in the CoRE context. Feedback from OSCORE and
EDHOC experts is welcome.

ML (p11): Is draft-ietf-dns-over-coap ready for WG Last Call?  
MT: From my point of view, it can be considered for WG Last Call. Jaime
and Carsten, what do you think?  
CB: Do we want to put this into one bucket with DNR? Maybe it is not so
useful without that?  
ML: We can use it without discovering DNS over CoAP, for example through
manual configuration.  
CA: I agree. Discovery options for CoAP over DTLS were fixed. Those can
be used. The work for DNR is about integrating it with EDHOC and OSCORE.
It may take the rest of this year, but other parts are ready. So the
easy parts work, and DNS over CoAP can be worked without specifying DNR
with EDHOC.  
CB: What if we move the DTLS case into draft-ietf-core-dns-over-coap?
Then we have something that is "battery included".  
ML: The problem is that CoAP over DTLS discovery is not just something
for DNS over CoAP. One may want to discover service binding for CoAP
over DTLS. So I am not sure this draft is the right place to define
that.  
ML: I would rather divide out that part, so that CoAP-over-DTLS
discovery is a separate draft.  
CB: Looks good to me, we can still accelerate the DTLS side. Then WG
Last Call sounds good at this point.  
CA: Partially relevant as if it is moved, it will be moved to a WG
document, and thus need a WG adoption to progress.

FP: It would be good for the Chairs, when doing WG Last Call, to also
request early reviews. Please consider requesting them at the same time.

FP (in chat): https://datatracker.ietf.org/dir/  
ML (on chat): There was already an early review from DNSDIR.  
CB (on chat): Martine: Is it worth to ask for an update of that?  
ML (on chat): Sure!

MT: We will soon start a 2-week WG Last Call on
draft-ietf-dns-over-coap.

## CoAP Protocol Indication (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-transport-indication/

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-coap-transport-indication-00.pdf

CA presenting.

CA (p1): Unified naming. Martine Lenders joined as co-author.  
CA (p2): The goal is to enable the discovery of alternative transports
for CoAP.

CA (p3): coap:// and coap+tcp:// diverged.  
CA (p4): Guidance for when defining new transports has been added. If
the transport is IP based, refer to Appendix E; if using IP literals,
refer to Appendix F. Security guidance has been simplified.

CA (p6): What is the scope of "has-proxy"? The current text focuses on
relying on link relations. Clean from a theoretical point of view, but,
considering that HTTP focuses on the origin, that may be the simpler
way. So, switching makes sense to me.

CA (p7): How is self-description supposed to be handled? Either
explicitly by using canonical names, or relying on the client to
re-interpret the document after having partially parsed it.

CB: I think that we need to make this work. So we do care. But maybe
optimizing for something else.  
CA: This question is not relevant for something else. If we say that,
for RFC 6690, we prefer one version, then it needs some reasoning to
re-canonicalize what it actually means.  
CA: Any preference on which version to use?  
CB: I will need to look at some examples.

CA (p8): The last open question is what to do with appendixes. Do we
need to motivate why we need this, considering that we have coap+tcp?
Shall we keep "historical" information?

CA (p9): It would be helpful to have reviews. A number of open questions
exist, like the fate of the appendices, and "only through link relation"
vs. "always when origin matches".

CB: What are the opportunities for interoperability tests?  
CA: I am working on an implementation with aiocoap, but it would be
preferable to test with a library where certain processes are automated.

CB: What venue or event can we attach interoperability tests to? The
next Hackathon?  
CA: I am not sure, it depends on the participants. Using the RIOT summit
in September is also an option.

MT: I think that historical information in the appendices are useful for
giving context to the reader.

## Proxy Operations for CoAP Group Communication (Esko Dijk) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-groupcomm-proxy/

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-proxy-operations-for-coap-group-communication-draft-ietf-core-groupcomm-proxy-00.pdf

ED presenting.

ED (p1): Recently adopted in the Working Group.

ED (p2): The scope is to define proxy operations for CoAP group
communication. It considers forward-proxies, reverse-proxies, chains of
proxies, and HTTP-to-CoAP cross-proxying. Clients need to be configured
to do it, proxies need to know the protocol. There has to be
authentication of the client at the proxy, to avoid anyone sending group
requests through the proxy.  
ED (p3): The timeout for forwarding responses back to the client always
has to be specified by the client in the Multicast-Timeout option;
addressing information pertaining to the response sender is included as
an option in the response (renamed now to Reply-To).  
CA (chat only): Reply-To sounds weird, assuming that "reply" and
"response" are synonymous (Reply-From?)  
CB (chat only): yes.  
MT (on chat): Yes, "Reply-From" is nice and also avoids possible
confusion with "Response-For" in
https://datatracker.ietf.org/doc/html/draft-bormann-core-responses-02#section-4

ED (p3): Security options.

ED (p4): Changes in latest version. Terminology enhanced ("individual
request" defined explicitly). Clarified that UDP over IP multicast is
default transport, alternatives are possible out of scope. Now it also
considers the usage of the newly introduced options Proxy-Cri and
Proxy-Scheme-Number from draft-ietf-core-href.

ED (p5): More updates. Considered two points of feedback from CA about
reverse-proxies. The Multicast-Timeout option must always be used in the
client's request. Also, do not use the Uri-Path option to provide the
proxy with information on host/port; there are Uri-Host and Uri-Port for
doing so.

ED (p6): Renamed the Response-Forwarding option to Reply-To. Still
considering better names. Clarified the exact meaning of this option.  
ED (p7): Now using CRIs to encode this option. Details in the content
and use of option value depend on the specific setup considered
(forward-proxy, or reverse-proxy hiding only the group or also the
individual servers in the group).  
ED (p8): (Skipping some.)  
ED (p9): Specific setups with reverse-proxies.

CB (in chat): You may want to use sf for HTTP (also base64url, but with
some decoration) -
https://datatracker.ietf.org/doc/draft-ietf-httpbis-sfbis/  
CA (on chat): That sounds like good general guidance for HTTP encoding
of CoAP options unless there is an obvious better way in an existing
HTTP header.  
CB (on chat): Indeed.

ED (p10): List of TODO items, including the cancellation ongoing
response forwarding.

MT: Some suggestion on better names for the Reply-To option are in the
chat, including Reply-From.

(no more questions/comments)

## OSCORE-capable Proxies (Rikard Höglund) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-capable-proxies/

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-slides-oscore-capable-proxies-ietf-119-core-wg-00.pdf

RH presenting.

RH (p2): This enables OSCORE-protected communication between proxies, or
between client/server and a proxy. It defines rules to encrypt CoAP
options whenever possible, so escalating class U/I options to be treated
as if they were class E, whenever it is possible. It also allows for
nested OSCORE protection "OSCORE-in-OSCORE", by applying multiple OSCORE
protection layers to the same CoAP message.  
RH (p3): Included feedback from Christian Amsüss and Göran Selander.  
RH (p4): Now more explicitly updating RFC 8613 on the possible
escalation of option encryption. Revised and simplified the criteria
governing such an escalation. Good although unexpected side-effect is
the protection also of Uri-Host and Uri-Port, between origin client and
server in case there are no proxies in between.  
RH (p5): Flowchart of the encryption escalation (set of rules for when
to treat an OSCORE class I or U option as class E). There is also a
corresponding diagram figure in an Appendix.  
RH (p6): Based on an input from Christian, we added that a server has to
check that it is fine to proceed with the decryption of an incoming
request, e.g., taking into account local rules or access control and the
source addressed of the alleged sender. Terminology was adjusted to
match with the common use of "authorization", so we talk of such a
decryption as an "acceptable" operation instead. We have also updated
the list of "proxy-related options", including more in consideration of
reverse-proxies.  
RH (p7): Also based on input from Christian, we have aligned the
behavior of a forward-proxy with RFC 7252 for requests actually
targeting the proxy in itself, which has to directly consume the request
in that case. In order to avoid infinite loops when stripping OSCORE
layers, we added a requirement on setting a cap on the number of OSCORE
layers to use.  
RH (p8): Summary of next steps.

CB: Implementation status?  
RH: We do not have an implementation yet, but we have plans to implement
it. It will be in some time. A possible starting point is our
implementation of OSCORE for the Eclipse Californium library.

## OSCORE Key Update (KUDOS) and ID Update (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/
* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-id-update/

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-slides-key-update-for-oscore-kudos-core-ietf-119-00.pdf

RH presenting.

RH (p2): Now this document specifies only KUDOS. We have split out the
content on key limits in March, and now also the content on the OSCORE
ID update.

RH (p3): Overview of the KUDOS produced.  
RH (p4): Summary of updates to be detailed in coming slides.  
RH (p5): We have allowed the use of non-random nonces and described
under which conditions they can be used. It is fine to use counter
values as nonces for CAPABLE devices that can store in persistent
memory. This has privacy implications that are also discussed.  
RH (p6): Highlighted and discussed that the KUDOS execution flows are in
fact independent of the request-response flow. It is allowed to have
more flexible message flows, like two requests as KUDOS message #1 and #2, or KUDOS message #2 as a response to a request different from that
used as KUDOS message #1 (e.g., when Observe is used).  
RH (p7): There is no need to necessarily target a special KUDOS
resource. It is also possible to send a request as a normal application
message as KUDOS message #1, targeting a normal application resource at
the server. If the server application requires freshness of such
requests, the server will reply with a protected 4.01 response, thus
triggering the client to possibly resend the same request application
request, yet having completed KUDOS.  
RH (p8): We have split-out the content on OSCORE ID update, now as a
separate document. The ID update can be run stand-alone or combined with
KUDOS. Rules on the ID reuse/recycling are also specified. We added
examples. One reason for doing ID update: privacy preservation, e.g.,
decoupling past identities after switching to a different network.  
RH (p9): On draft-ietf-core-oscore-key-limits, it is inspired by the
draft-irtf-cfrg-aead-limits. We are waiting for an update to that
document and other feedback before moving this forward.  
RH: We have ongoing implementations in Java and in C.

GS: There has been a new paper this year on symmetric ratchets and
keychains, mentioning many protocols including KUDOS, for which it made
recommendations. Have you processed it into the draft?  
RH: We are aware of it, it's one of those items that we want to take
into account.

MT: Links to the papers:   
https://eprint.iacr.org/2023/913  
https://eprint.iacr.org/2024/220 (which GS mentioned)

## CoAP: Non-traditional response forms (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-bormann-core-responses/

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-coap-non-traditional-response-forms-00.pdf

CA presenting.

CA (p2): Non-traditional responses are explicitly or implicitly used,
and are defined in multiple documents. To make document authors' lives
easier, this document intends to assist them by defining related, common
terms and concepts.

CA (p3): Version -02 defines behavior for usage of these concepts with
OSCORE. We added a list of steps/guidelines to follow, for a secure and
correct handling of these kinds of responses. I want to ask anyone with
experience with OSCORE to review this list, to make sure that nothing is
missing.

CA (p4): Interoperability tests will be more about interoperating other
documents that use non-traditional responses, not this exact document.  
CA: Do we want this as WG document?

MT: About interoperating, the next best target can be
draft-ietf-core-groupcomm-proxy. We have running code for it already,
also using Group OSCORE. Specifically on using OSCORE or Group OSCORE,
that document does not add anything special.  
CA: I refer to a scenario with multicast proxies, not to the use of
Group OSCORE.

MT (as an individual): I believe that having this document is good for
setting a common ground. As we could see, other documents came up with
these concepts on their own, but it is good to make things homogeneous
and in a single place to look at. I plan to review this document.  
GS (on chat): +1 Marco

## CoRE Resource Directory Extensions (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-amsuess-core-resource-directory-extensions/

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-core-resource-directory-extensions-00.pdf

CA presenting.

CA (p2): This document contains extensions to the CoRE Resource
Directory (RD) (RFC 9176): reverse-proxy registration, infinite
lifetime, exploring pub-sub like functionality, using the RD in the
context of the ACE framework (RFC 9200) and EDHOC (RFC 9528) (focus for
today).

CA (p3): When using the RD with EDHOC, the flow can be: a minimal CoAP
Resource Server (RS) sends a request to the RD to trigger the simple
registration procedure. This can be unauthenticated. Then, the RD drives
the use of EDHOC. How should registration parameters be protected? Some
scenarios have no registration parameters.

CA (p4): Using ACE is more complex. CoAP and OSCORE are flexible for
role reversal. EDHOC can be used in both directions (forward or reverse
message flow). ACE is stricter in its roles (ACE RS and ACE Client).
Thinking about role-reversal for ACE has uncovered some gaps. There is
ongoing related work in draft-ietf-ace-workflow-and-params and in
draft-ietf-ace-edhoc-oscore-profile.

CA (p5): Next steps are about driving the ACE enhancements, and then
re-evaluate if ACE and EDHOC are suitable for use with the RD and very
constrained endpoints.

JJ: Procedural question on Experimental drafts. Do they become RFCs and
they are updated? Are they treated differently?  
CB: Different labels are possible and we have to decide what we want.
Processing is fundamentally the same. They receive a different level of
attention from the IESG. In the WG, we just need to decide the label
appropriate to what we want the document to be.

MT (as an individual): Based on early thoughts/discussions regarding the
relation with ACE/LAKE, the direction looks promising. I hope to help
out with some text in this part of the document.

## CoAP over BP and in space (Carles Gomez) (5)

* https://datatracker.ietf.org/doc/draft-gomez-core-coap-bp
* https://datatracker.ietf.org/doc/draft-gomez-core-coap-space

Presented slides:
https://datatracker.ietf.org/meeting/119/materials/slides-119-core-coap-in-space-and-coap-over-bp-00.pdf

CG presenting.

CA (on chat): Looking forward to seeing CoAP-over-BP.

CG (p1): We start with CoAP in space.  
CG (p2): Introduction. Deep space communication means long delays and
intermittent communication. The IP stack was considered unsuitable for
this, but this is being re-evaluated. We claim that CoAP is suitable for
such communication. The intended document status is Informational, as
giving guidance for using CoAP in deep space.

CG (p3): We propose the use of CoAP over UDP (for a number of reasons).
A number of CoAP parameters need to be modified as to their recommended
value (timeouts, NSTART, etc.), considering the very long expected
latencies.  
CG: Do we need congestion control? CoAP enables resource observation
(RFC 7641), which can be suitable in deep space, allowing efficient
retrieval of resources that changed in their representation. For
block-wise, we propose using RFC 9177. Security-wise, OSCORE is
interesting as it can avoid initial handshakes (if relying on pre-shared
keying material and parameters).

CG: By the way, tomorrow there is a deep-space side meeting.

CG (p5): Now we cover CoAP over Bundle Protocol (BP). The CoRE and DTN
WGs are relevant for this topic. On this document: how can CoAP be
carried over BP?   
CG (p6): We provide an architecture and an abstract layer. We define a
messaging model (the same as for CoAP over UDP). Pure ACKs can be
replaced with BP status reports.  
CG: Is it a good idea to increase the size of the Message ID field in
the CoAP header (see Appendix B)? BP has its own fragmentation and
re-assembly mechanism. CoAP block-wise can be used under some scenarios.

CG: We also define a new URI Scheme coap+bp.

CG (p7): Appendix A gives reference values for interplanetary
communications (RTT between some solar system bodies). These must be
floor values for some CoAP parameters.

CG: By the way, this document is also in the Friday session of DTN,
where we will have more time.

CB (as an individual): When you say coap+bp, we do not have IP addresses
there, but bundle endpoint IDs. Maybe the same consideration applies
that, if a certain host structure implies BP, then we do not need it in
the scheme.  
(CA, chat): See also mail thread.  
CG: I am not sure if BP identifiers are unique. Perhaps that is the
case, I need to check. If that is the case, then +bp can be removed.  
CB: I still need to think about a way to encode endpoint IDs. Percent
encoding does not work so well.

JJ: On CoAP-over-space, space has popped up in routing (yesterday,
routing for LEO constellation). Tony Li (Juniper) presented the [Routing
Architecture for Satellite Networks][1] draft, which was adopted; so we
can expect more of this in the IETF.  
CG: I have not read it, but I am aware of it.  
JJ: One concrete problem is that it is currently worked in an IETF
vacuum, with no feedback from satellite vendors. I see a satellite
company here in the authors' list. Do you have deployment experience or
plan for deployment?  
CG: Not yet, it could be in the roadmap to create a deployment. We can
have experiments not in space. Possible things that can come.  
JJ: There is work on Non-Terrestrial Networks (NTN) ongoing. An NB-IoT
flavor is done by satellite and telco vendors.  
CG: NTN is in scope.

MT: Regarding the new URI scheme, I suggest checking Section 6 of
draft-ietf-core-transport-indication. It recommends (non normatively, at
the moment) to avoid new URI schemes for new transport for CoAP, and
instead to use subdomains of .arpa, allowing for specifying what you
need anyway in the URI authority component.  
CG: Thanks, we will check it out. That can be incorporated.

CA: Regarding NSTART, what properties do we get from the IP network?
Congestion notifications? If so, that can help find a suitable NSTART.  
CG: I am not sure about congestion indications in BP. There are flags
for requesting status reports from end nodes or intermediate nodes.  
CG: BP was different in the past. Version 7 is more similar to UDP.
There is no clear way for congestion indication.  
CG: On NSTART, 1 leads to stop-and-wait. The correct setting is an open
question. The need for congestion control in space is discussed in the
past with differing opinions. It can be discussed more tomorrow.

CA (on chat): Thanks, that's interesting work!  
CB (on chat): +1

## Flextime (5)

Σ 120

* * *



[1]: https://datatracker.ietf.org/doc/draft-li-arch-sat/
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


*[IvP]: Ivaylo Petrov


*[BSc]: Ben Schwartz


*[AP]: Alexander Pelov


*[AHF]: Alex Huang Feng


*[CG]: Carles Gomez


