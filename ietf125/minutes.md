# IETF 125 - Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

Date and time: Friday, 2026-03-20, 06:00-08:00 UTC

https://www.timeanddate.com/worldclock/fixedtime.html?iso=20260320T06&p1=1440&ah=2

Meeting material: https://datatracker.ietf.org/meeting/125/session/core

Notes: https://notes.ietf.org/notes-ietf-125-core

Zulip: https://zulip.ietf.org/#narrow/stream/core

Recording: https://youtu.be/HYvVr3p9tbA

Note takers: Rikard Höglund, Christian Amsüss

* * *

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (10)

* WG and document status since IETF 124

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-chairs-slides-

Video: https://youtu.be/HYvVr3p9tbA?t=13

MT going over introduction, agenda, and status of documents.

## CORECONF: COMI (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-comi/

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-coreconf-corr-clar-00

Video: https://youtu.be/HYvVr3p9tbA?t=560

CB presenting

CB (p1): Preparing Errata Report related to RFC 9595. Description in
SID-file YANG model did not mention choice/case. This was held for
having pyang implementation updated (as that tool generates most SID
files).  
VV (on chat): Mr. Laurent Toutain already contributed the necessary
changes to PYANG.  
CB: I think that there is still an ongoing discussion on those changes.
We will double-check with Laurent.  
CB: Czech NIC (Vojtěch, Maria) is providing a lot of support.

CB (p2): CoMI is old enough that problem-details (RFC 9290) was not
around yet at that time, so we defined a YANG model for error messages.
No plan to change, but we can go from the YANG model based on RESTCONF
rc:yang-data \[RFC 8040\] to the now more popular sx:structure extension
\[RFC 8791\]. It would be nice to get feedback on this.

## CORECONF: YANG Metadata (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-yang-metadata/

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-coreconf-corr-clar-00

Video: https://youtu.be/HYvVr3p9tbA?t=846

CB (p3): This is now a WG document (about metadata annotations for
YANG-CBOR).  
CB (p3): Metadata annotations (RFC 7952) can be attached to data
governed by other YANG models: it allows adding, e.g., provenance or
timestamp information that was not foreseen by the original model.
Obviousy, there is no YANG-CBOR representation in RFC 7952. It turns out
this is almost trivial to add compared to JSON. So core-yang-metadata is
a simple document.  
CB (p3): A remaining question: how do you signal capability?  
CB (p4): Mechanism used: tag CPA109. It looks stable.  
CB (p5): Call for implementations. Welcoming feedback from implementers.
This should be ready for WG Last Call soon; it can be on a fast track if
implementers' feedback arrives.

## CORECONF: Stand-in Tags for YANG-CBOR (Carsten Bormann) (5)

* https://datatracker.ietf.org/doc/draft-bormann-cbor-yang-standin/

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-coreconf-corr-clar-00

Video: https://youtu.be/HYvVr3p9tbA?t=1119

CB (p6): "Smuggle" in binary data with CBOR, using stand-in tags.

VV (on chat): You most likely meant RFC 6991: Common YANG Data Types.  
CB: Yes (now RFC 9911).

CB (p6): One point is not understood yet: how to negotiate? We probably
need a "stand-in file" for control and agreement between client/server.
The plan is to nail down the model, defining the stand-in file.

CA (on chat): Just curious on metadata (keeping on chat b/c it's quite
uninformed): tagging something probably allows quite complex trees of
metadata. Is YANG CBOR metadata more expressive than the XML equivalent
(attributes usually are single layer unless they have internal
structure)?  
CB: RFC 7952 limits metadata to what can be represented in XML
attributes. No leaf lists, only scalar values.

CA: Can the use of tags cover also negotiation, similar to what is done
for the metadata?  
CB: We probably want to negotiate in terms of the YANG ecosystem. This
is very different from the stand-in thing. We need to think about it.
All is driven by CBOR tags, it may be used as a simplifying commonality.

VV (on chat): The CBOR aims not to be more expressive  
CB: Right, this is not about covering all possible functionalities that
CBOR could enable.

## Corrections and Clarifications for CoAP (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-corr-clar/

* https://github.com/core-wg/corrclar/issues/

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-coreconf-corr-clar-00

Video: https://youtu.be/HYvVr3p9tbA?t=1723

CB (p7): Objective of this WG document: collect corrections and
clarifications to documents around CoAP (RFC 7252 and others).  
CB: We start with issues in GitHub, form understanding, then create
pull-requests.  
CB: Full cycle executed for one instance (see later: 4.02 in relation to
draft-ietf-core-uri-path-abbrev)  
CB: 37 more issues pending; sometimes, the resolution will be "no action
required".  
CB: Upcoming processing on issue [#51][1] about the choice between using
Uri-Host + Uri-Path + ..., or using the Proxy-Uri option. Assumption:
constrained systems deal with Uri-\*, while Proxy-Uri is used only where
specifically needed. Can clients do anything, or do we expect some
discipline? The discussion became concrete when thinking of the use of
the new Uri-Path-Abbrev option; now this point is understood better.  
CB (p8): issue [#52][2] is now handled: the use of 4.02 error responses
vs. "rejecting" Non-confirmable requests, got in the way of option
negotiation. RFC 7252 has a mandate to "reject" a Non-confirmable
request, even when a 4.02 error response would have been more
appropriate. This change has a normative effect, hence it "updates RFC
7252" (now done by draft-ietf-core-uri-path-abbrev, for which this
change is actually needed).  
CB: The new text was initially in this document, and has been migrated
into an appendix of draft-ietf-core-uri-path-abbrev, leaving only a stub
in this document (please review).  
CB (p9): Another point: RFC 7252 requires piggy-backing a 4.05 (Method
Not Supported) error response to an ACK, even when piggy-backing is
impossible (i.e., when the request was Non-confirmable). PR [#55][3]
fixes this. There is an additional discussion around response
suppression (per the No-Response option, see RFC 7967) and the use of
5.01 (Not Implemented) error responses. We will continue the discussion,
and we might conclude that a fixed behavior is generally impossible for
a proxy to enact.

CB: It is good if people can occasionally look at the -corr-clar
repository and contribute with comments to the issues/PRs.
https://github.com/core-wg/corrclar/

## URI-Path abbreviation in CoAP (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-uri-path-abbrev/

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-uri-path-abbreviation-in-coap-00

Video: https://youtu.be/HYvVr3p9tbA?t=2375

CA presenting

CA (p1): This started summer last year. Especially for documents using
the /.well-known URI paths, it is good to have them shorter.

CA (p4): The fix that was mentioned as started in
draft-ietf-core-corr-clar is now here in Appendix A, enabling a proper
use of 4.02 error responses. It explicitly helps here, even though it
ends up being a niche case.

CA (p5): Another change was about the Proxy-Uri option. I am not sure if
I agree about this document helping progress issue [#51][1] in
draft-ietf-core-corr-clar. Requirements in this document have become
weaker. The niche case for mixing Proxy-Uri/-CRI with Uri-Path-Abbrev
remains possible, but it is now stated in a simpler way, also covering
hosts that are proxy-server hybrids.

CA (p6): Some further clarifications were done.

CA (p7): It is done for me. I think it is ready for WG Last Call.

CB: Implementation status?  
CA: There are two implementations. I have implemented the server side in
aiocoap, leaving the client side to the application. The other
implementation is from Jon Shallow for libcoap from October, and he also
gave feedback.  
CB: Can we run an interop test?  
CA: Yes, I can take Jon's code and run it.

CB: Can we pick up a day for an actual interop?  
CA: I am not sure that we need multiple implementers gathered together
at the same time. One can try both implementations locally. Then the
outcomes can be shown at an interim meeting.  
CB: Let's clarify the details offline. Hopefully, we can have successful
results from some form of interop tests shown at an interim meeting. I
think it is good if the tests can happen with the two people running
those and having a high-bandwidth discussion. But it is not a threshold
to pass for making an interop significant.

## CoAP Pub-Sub Architecture (Jaime Jiménez) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-coap-pubsub/

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-draft-ietf-core-coap-pubsub-19-01

Video: https://youtu.be/HYvVr3p9tbA?t=2942

JJ presenting

JJ (p1): Reviewed by Marco Tiloca and Christian Amsüss; going through
changes.  
JJ (p2-4): Recap of the architecture, topic resources, and their
life-cycle.  
JJ (p5-6): Changes in the latest version -19. We have made some redesign
around the "initialized" topic property, and multiple protocol fixes. We
refer to RFC 7252 for most appropriate response codes to use for
successful responses, without setting strict expectations here.  
JJ (p7): Updated IANA considerations; removed text string as CBOR type
for the map keys.  
JJ (p8): Addressed comments from Marco and Christian. I think this is
ready for Shepherding.

CB: Process-wise, the WG Last Call is completed and we are still
processing details, which should only take some days. The next step is
the Shepherd Write-up from Esko Dijk. When we agree on the write-up, we
can submit to the IESG.  
JJ: For any needed changes, PRs on the Github are preferred to mails.  
MT: We will first need a version -20 anyway, with the content currently
in the Editor's Copy on the Github, in turn resulting from the merged PR
[#71][4].  
CB: Correct.  
JJ: Thanks to all the reviewers.

Chat:

* CA: 🚀 on advancing pubsub
* ED: +1

## CoAP over Bundle Protocol (Carles Gomez) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-coap-bp/

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-coap-over-bp-00

Video: https://youtu.be/HYvVr3p9tbA?t=3458

CG presenting.

CG (p2): This document was adopted by the WG after IETF 123.   
CG (p3): New content added in this version is in the section about
securing CoAP over BP.  
CG (p4): We expanded considerations about using CoAP block-wise.
MAX\_PAYLOADS need to be set considering the network setup.  
CG (p5): We re-organized the section about securing CoAP over BP, and
added a note about securing responses at the same level considered for
securing the corresponding request. Marco pointed out that OSCORE and
DTLS already have their own rules concerning this.  
CG (p6): We added the request to IANA for a well-known service number
for CoAP.  
CG (p7): Additions in the security considerations: the Payload-length
option is class U for OSCORE, which means that an attacker can infer
things about the traffic. Now we mention the possible use of the Padding
option defined in draft-ietf-core-cacheable-oscore, which is of class E
for OSCORE and is thus encrypted. We plan to make it an example of a way
to achieve that, so that draft-ietf-core-cacheable-oscore can be an
informative reference.  
CG (p8): Next steps: Address Marco's review of this latest version. We
think that we are now getting close to WG Last Call.   
CG: Asking for reviews.

CB: Implementation status?  
CG: We have a section in the draft about one implementation, based on
aiocoap for the CoAP part and on the uD3TN library for the BP part. We
are working to update the implementation and make it aligned with the
latest version of the draft.  
CB: When is a good time to tell people that this is ready to be
implemented?  
CG: Even now it could be good. The document is getting stable.

CB: I can imagine that there will be updates. We may want to check the
next revision of the draft and consider if we can declare it eligible to
be taken for implementation. If not the next revision, then the one
after that. Reviews will help the assessment, so please review. Later
on, we can think of an interoperability event.

CA: Thanks for the updates about the scenarios with a proxy. Regarding
hiding the length of messages, it can make sense to also apply hop-by
hop security. You may be able to protect an entire bundle. This can be
achieved using the approach defined in
https://datatracker.ietf.org/doc/draft-ietf-core-oscore-capable-proxies/

CG: We will take a look, thanks.

## OSCORE Key Update (Rikard Höglund) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-slides-kudos-core-ietf-125-00

Video: https://youtu.be/HYvVr3p9tbA?t=4265

RH presenting

RH (p2): Recap of the key update procedure, renewing Master Secret and
Master Salt. This is also related to key usage limits (cf. CFRG work).  
RH: Advantages: not changing IDs; it works in any CoAP message; any
endpoint can start the procedure; likely completed in 1 round trip.  
RH (p3-5): Recap on extended OSCORE option, protocol states, and state
machine.  
RH (p6): Moved here the content on using SCHC header compression when
KUDOS is used, from draft-ietf-schc-8824-update. It is largely about
covering compression of the new subfields in the extended OSCORE option
that are present in KUDOS messages. Further related content: IANA
considerations and updated YANG data model.  
RH (p7-9): Added one more example of message exchange (initiated with a
request, followed by a lost response message).  
RH (p10): The current design is stable. We are working on aligning our
Java implementation to this latest version (i.e., per the current state
machine). We also have an implementation in C for Contiki-NG, which we
also plan to update at a later stage.

FG (in chat): In fact, we have an implementation based on C and
uOSCORE-uEDHOC. So we can talk for an Interop :)  
RH: That's excellent, let's sync on that and try to interop.  
CA (in chat): no feedback now, just thanks for the update, hope to
implement it later :-)  
CB: Let's try to plan some interop.

## OSCORE-capable Proxies (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-capable-proxies/

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-oscore-capable-proxies-00

Video: https://youtu.be/HYvVr3p9tbA?t=4940

MT presenting

MT (p2): Overview  
MT (p3): 1.5 years of updates since last presentation.  
MT (p4): More substantial updates since v -05 for this latest round:
Editorial, improving section on header compression with SCHC.  
MT (p5): Interactions. Covered the possible use of the Uri-Path-Abbrev
option.  
MT (p6): Explicitly required to include the Partial IV in a non-first
response to a request (multiple responses for single request). Most
cases were already covered by other documents, but not one that this
document is in fact creating.  
MT (p7): Processed Christian's review of version -04. Clarified what
"consumer" of an option means. More accurate error handling when
processing an incoming request.  
MT (p8): Two use cases were "elevated" to their self-standing
subsections in Appendix A. Reorganized, moved, and clarified text about
policies that a server can rely on to decide whether decrypting an
incoming request or not.  
MT (p9): Some points have not been addressed yet; they will be soon,
paired with a reply to the review on the mailing list. Two are largely
editorial. A third one is in this slide: can we give guidelines to a
proxy about if/when establishing an OSCORE association with the origin
server? Can SVCB Resource Records help the proxy learning about the
server?  
MT: For the proxy, it's first of all about discovering if servers
supports EDHOC and nested OSCORE. For the EDHOC support, there are means
defined in draft-ietf-lake-app-profiles. For the nested OSCORE support,
SVCB Resource Records sounds promising. Would it work also in case of
reverse DNS lookup that a proxy might need doing? Could we alternatively
rely on a new link-target attribute in the link of a new well-known
resource, for describing the abilities of the server as a whole?

CA: Discovering support for nested OSCORE may be tricky. The server
could support 2 layers, but we do not know how many layers are in there.
It is better to rely on guidance from the client, but it is unclear how
that can concretely be given.  
MT: The server can at most say "support nested", but not how many
layers.  
CA: The server can even be able to say that, but still the client cannot
tell the proxy how many layers there are in the specific message.

MT (p10): We have 2 implementations: one in Java (covering multiple
setups, tested also with CoAP Observe and EDHOC) and one in Contiki-NG
tested on constrained devices.

MT (p11): Next steps: address remaining review points from Christian;
more text on handling multiple responses to the same request (beyond
expectations of Partial IV); example of message exchange with a chain of
two proxies.

## Stand-in KID and encrypted Partial IV in OSCORE (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-tiloca-core-oscore-piv-enc/

Presented slides:
https://datatracker.ietf.org/meeting/125/materials/slides-125-core-stand-in-key-identifier-and-encrypted-partial-iv-in-the-oscore-option-00

Video: https://youtu.be/HYvVr3p9tbA?t=5721

MT presenting

MT (p2): Recap: the fields KID and Partial IV are sent in plain in the
OSCORE option, since the option is not encrypted. That enables tracking
endpoints across network paths and inferring behaviors.  
MT (p3): Contribution and features: obfuscating the two fields, which is
optional for the KID. In-band signaling of the use of this method is
explicitly avoided. It works for OSCORE and Group OSCORE, based on
lightweight operations.  
MT (p4): Updates: length of stand-in KID updated from 2 to 3 bytes, thus
reducing chances of false positives when retrieving Security Contexts.
Obfuscating the KID field is now optional (some use cases achieve the
same result more efficiently).  
MT (p5): Introducing terminology for clarity:
Ordinary/Obfuscating/Incognito Security Context.  
MT (p6): In some use cases, obfuscating the KID using this method might
defeat compression and expected performance (since obfuscation is
achieved anyway by field elision). Other, general cases should obfuscate
the KID.  
MT (p7-9): Changes to sender/recipient processing to allow KID field
obfuscation to be optional. 3 byte stand-in KID. Optimizations in terms
of error handling, allowing for the message processing to terminate as
early as possible.  
MT (p10): We have also updated the message processing for Group OSCORE,
to be aligned. Also explained that this method is not applicable (nor
relevant, really) for the Deterministic Request defined in
draft-ietf-core-cacheable-oscore.  
MT (p10): Also added further security considerations, especially related
to the possible trial decryptions.  
MT (p11): Next steps: text about external signature verifiers in Group
OSCORE; methods for peer to agree on using this method and with which
variant. We have an implementation in Java aligned with the previous
version of the document, which we plan to update..

ML (in chat): Thanks for making the KID obfuscation optional!  
MT: Thanks for the very good input. The change was simple from a
protocol design point-of-view. It was painful to enforce editorially.

## Flextime (15)

Video: https://youtu.be/HYvVr3p9tbA?t=6471

CB: AOB?  
CB: We meet again in 4 weeks at the interim meeting of April 22nd.

* * *



[1]: https://github.com/core-wg/corrclar/issues/51
[2]: https://github.com/core-wg/corrclar/issues/52
[3]: https://github.com/core-wg/corrclar/pull/55
[4]: https://github.com/core-wg/coap-pubsub/pull/71
*[MT]: Marco Tiloca


*[CB]: Carsten Bormann


*[JJ]: Jaime Jimenez


*[CA]: Christian Amsüss


*[CG]: Carles Gomez


*[RH]: Rikard Höglund


*[GS]: Göran Selander


*[JPM]: John Preuß Mattsson


*[ED]: Esko Dijk


*[ML]: Martine Lenders


*[MG]: Mikolai Gütschow


*[MB]: Mike Bishop


*[VV]: Vojtěch Vilímek


*[FG]: Francisco Gómez


