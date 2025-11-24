# IETF 124 - Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

Date and time: Friday, 2025-11-07, 19:30–21:30 UTC

https://www.timeanddate.com/worldclock/fixedtime.html?iso=20251107T1930&p1=1440&ah=2

Meeting materials: https://datatracker.ietf.org/meeting/124/session/core

Notes: https://notes.ietf.org/notes-ietf-124-core

Recording: https://youtu.be/dXDL1o1-I1M

Zulip: https://zulip.ietf.org/#narrow/stream/core

Note takers: Christian Amsüss, Rikard Höglund

* * *

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (10)

* WG and document status since IETF 123

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-chairs-slides-00

MT doing introductions.

MT: Updates on status of drafts. RFC 9876 was published, less than 1
year since starting the effort.

## CORECONF: COMI; YANG SID PENs (Carsten Bormann) (7)

* https://datatracker.ietf.org/doc/draft-ietf-core-comi/

* https://datatracker.ietf.org/doc/draft-ietf-core-yang-sid-pen/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-coreconf-corr-clar-00

CB: The plan was to introduce the new COMI plan today, but it got
delayed.  
CB (p2): SIDs for all YANG modules should have been possible to generate
1 year ago. The tooling has now improved.  
CB: We need to be careful to not step on a document where manual
allocation (of the individual SIDs) is intended. For the actual
assignment, we need manual intervention to create ranges with suitable
margins. This is ongoing work. Let me know if you have a YANG module
which could benefit from SID files.  
CB (p3): rc:yang-data is not for CORECONF itself, but for error
messages. Can we move to sx:structure? There is bad tool support.  
CB: Implementors, let me know your feedback.  
CB (p4): Vojtech noted lack of text. In our minds, it's in RESTCONF, but
there is no reference there. How to fix that?

## Corrections and Clarifications for CoAP (Carsten Bormann) (13)

* https://datatracker.ietf.org/doc/draft-ietf-core-corr-clar/

* https://github.com/core-wg/corrclar/issues/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-coreconf-corr-clar-00

CB (p5): Ongoing work. Some concrete points:  
CB (p6): It is not spelled out whether using the CoAP Proxy-Uri option
is only a fallback or normal. There are different views (for me, it was
always a fallback). In particular, what if the CoAP client is a proxy?
It is more powerful, hence able to do conversions between using
Proxy-Scheme with Uri-\* and Proxy-Uri.  
CB: 12 years ago, I would have said that it does not matter. But the
recent Uri-Path-Abbrev option does not use the Unsafe bit. So a proxy
might be unaware. Suddenly, it does become a problem.  
CB: Next problem: Whatever we write up, it will not reach unaware
proxies.

CA: We cannot reach the proxies. I am reasonably confident (but need to
be more sure) that no proxy has ever done this operation (converting
from Proxy-Scheme + Uri-\* options on the client side to the Proxy-Uri
option on the server side). We only need to reach proxies that do this.
As far as I know, no one does this conversion today. Let's confirm that.

ED: Why would origin clients not use Uri-Path options?  
CB: An origin client is modern enough to use Uri-Path-Abbrev. Whatever
we do, the origin client will know it.  
ED: I thought you said that the client uses Uri-\* options if it cannot
use anything else. What does that client fall back from and why can't it
use those options?  
CB: It depends on the URI scheme. If it is MQTT, it is probably more
difficult to construct a URI, which ends up in using the Proxy-Uri
option. For CoAP-related schemes, it is clear. HTTP is pretty much
covered too.  
CA: You could have a proxy that allows you to post to
mailto:address@example.com but no proxy would convert to that, although
a client could.  
CB: We're talking about a client that talks to a forward proxy and wants
that proxy to send a mail. It's a cross proxy, from CoAP to X.

CB: Like Christian, I do not know anyone who has done that conversion.  
ED: Good to clarify. It looks like the origin client can either use the
single option form (Proxy-Uri) or the split form (Proxy-Scheme with
Uri-\*).

CB: It might help to create examples.

CB (p7): Next issue. This one is annoying.  
CB: An RST message is appropriate if what you have received does not
make sense for you. But the Uri-Path-Abbrev option would like to see a
4.02 error response.  
CB: What we might have liked in RFC 7252 (also to avoid surprises) is
that we only "reject" a message (hence follow-up with a RST message)
when there is no error response that can be produced. This might be a
change, a significant one for people into state machines.  
CB: But it is closer to why we have error messages. This is either a
correction or change, and which change to make this in. Any opinions?

CA (in chat): Any critical option that is not pre-negotiated will want
to see that.  
ED: It seems like a good idea to correct that.  
CB: We will continue discussion in issue tracker.

MT: Would the correction be in draft-ietf-core-corr-clar?  
CB: Yes, that would be one way.  
MT: At some point, DNS over CoAP needed to refer to a clarification.
First, it referred to a Github issue in the -corr-clar repository, then
to the relevant section in the -corr-clar once added. The same
incremental approach can be taken here.

CB: So we can write it up in -corr-clar; by December should know what we
do here.

## URI-Path abbreviation in CoAP (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-uri-path-abbrev/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-uri-path-abbreviation-in-coap-00

CA (p2): The motivation is to reduce overhead when expressing well-known
paths in a CoAP request. For example, for EDHOC and cBRSKI.  
CA (p3): The solution is to use a simple CoAP option that is mutually
exclusive with the Uri-Path option. The integer value of the option
expands into the path. It is very compact.  
CA (p4): The idea has existed but was not done in the past, as it was
initially too broad. Now simplified for version -02.  
CA (p5): Are there applications? Is it justified? The best use cases are
large EDHOC onboardings (with about 20% savings) and EST/cBRSKI that
benefits from the simplification.  
CA (p6): It is implemented and ready. I think it is done.  
CA (p7): There are 4 open issues on the Github repository, but they are
most likely NO-ACTION.  
CA (p8): Dependent documents are reaching WG Last Call. Can this draft
keep the pace?

CB (as an individual): We will hate not having included the
extensibility at this point. Of course, we will not know what we should
have put in.  
CA: The document is still shaped to not rule out extensibility. We can
add an appendix suggesting how extensibility can be, but there would be
no impact on non-extended implementations.  
ED: I am in favor of keeping things simple.  
JJ (on chat): Would not the Uri-Path-Abbrev values address the
extensibility aspects?  
MG (on chat): I am also a bit surprised the extensibility was taken
away, but if it is still possible in the future, that sounds like a good
solution to me.  
ED (on chat): Yes, current extensibility is done via the IANA registry
(register new values).

CA (follow-up on chat): If it helps, I can write up a concrete extension
example in an "Remove at RFC editor time" appendix. (Maybe even keep in
it, but stripping it then ensures that the example doesn't inadvertently
get used)  
ED (follow-up on chat): that may be good to understand how it can be
extended later on.

CB: Can we finalize for the interim meeting on December 3? If we have
something more to discuss, that would be a good date. If we run out of
time today, we can do it on the mailing list.  
CA: The discussion about handling options at the proxy could be useful;
on using the RST message or not, we will not get so far.  
MT: We continue the discussion on the mailing list and can have this
topic for the interim meeting on December 3. Then we can have WG Last
Call, possibly on a revised version. Does that work?  
CA: Yes.

## CoAP Performance Measurement (Giuseppe Fioccola) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-coap-pm/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-coap-performance-measurement-option-draft-ietf-core-coap-pm-05-00

GF (p2): The motivation is to measure CoAP performance for checking that
it meets operational requirements. A lightweight solution is needed.  
GF (p3): We use the sQuare bit.  
GF (p4): We are proposing a new CoAP PM option to carry this bit.  
GF: We removed the idea of using the "spin bit". With CoAP, spin bit is
not feasible for RTT measurement because flow is not continuous. (It
would require artificial continuous flow, but it does not make sense to
complicate how CoAP works just to enable this).  
GF (p5): We have examples with collaborating and non-collaborating
proxies. The new option is Unsafe; however, non-collaborating but aware
and non-caching proxy can still forward it.  
GF (p6): A bit more testing is needed to consider retransmissions.  
GF (p7): We hope to have a demo during a hackathon or for an upcoming
interim meeting.

MG (chat): Is this mainly geared towards CoAP over UDP/DTLS, or does it
also apply to other transports (TCP, GATT, BP)?  
GF: It applies to any transport. For now, we are testing especially with
UDP because it is the most complex for these measurements but also the
most expected. We will also test with TCP, but we are more confident
that it works in that case.

## Stand-in KID and encrypted Partial IV in OSCORE (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-tiloca-core-oscore-piv-enc/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-stand-in-kid-and-encrypted-partial-iv-in-the-oscore-option-00

MT (p1): Updated approach, title, and author list after feedback
received at IETF 123.  
MT (p2): The motivation is to hide the real Partial IV and KID fields in
the OSCORE option (normally sent in plaintext) to mitigate privacy
issues (counteract behavioral inference and endpoint tracking). Hiding
the Partial IV is a first step, but something should be done also with
the KID (hiding it too or changing it).  
MT (p3): Like in version -00, we still encrypt the Partial IV. Now we
also replace the KID with a stand-in ephemeral value. This whole method
is optional; it is only used when both endpoints agree on using it, as a
property of the established OSCORE Security Context. If there is no
agreement, it is not used, hence preserving interoperability.  
MT (p4): Renamed new key to Obfuscation Key.  
MT (p5): Sender-side processing for encrypting the Partial IV (same as
in version -00).  
MT (p6): New: Server-side processing to obfuscate the KID.  
MT (p7): Recipient side processing. Note that it does not know if
obfuscation was used. First assumption: it was not used, then try to
retrieve a Security Context and use it usual. If there is no success,
then assume that obfuscation was used. If there is no success, inspect
the Security Contexts, use the stand-in KID to determine the candidate
Security Context and use it for decryption. If there is no success,
continue inspecting.

CA: Good update! Two questions: 1. Regarding key usage limits, would
this draft affect the counters for the key usage limits (performed
encryptions and failed decryptions)? 2. The recipient first assumes that
the message is not obfuscated and tries to decrypt it as usual... It can
produce false decryptions.

MB (in chat): Trial decryption makes me nervous. Please make sure this
gets secdir review early in the process.

MT (p8): Further details. Special cases and how they are handled (EDHOC
+ OSCORE request in RFC 9668, use of KUDOS, OSCORE-protected messages in
6TiSCH). Adaptations to use this method in Group OSCORE.

MT (p9): Next steps. We also got good feedback from Martine on
considering a sort of hybrid mode where the Partial IV is encrypted but
the KID is not obfuscated: that's better for uses cases where the same
result is achieved in a more efficient way (e.g., using aggressive
header compression that elides the KID field anyway).

CA (prep for mail):

* key limits
* why just few contexts expected? especially in device-to-central-server
  case, if device reaches out, it's 100s
* separate agreements -- just encrypting 1 makes me unsure if it'll
  really achieve its goal.

## OSCORE Key Update and ID Update (Rikard Höglund) (15)

### KUDOS

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-slides-kudos-core-ietf-124-00

RH(p6): Example flows highlight that they are not constrained to
happening on a single request-response pair.  
RH(p10): Next steps: we have implementations based on the old protocol
design predating this state machine; the intent is to update them.
Considering the timeline, we expect to import content about SCHC
compression from the draft-ietf-schc-8824-update.

### ID Update

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-id-update/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-slides-oscore-id-update-core-ietf-124-00

RH (p1): This was split out from KUDOS.  
RH (p2): Restrictions to prevent (key, nonce) reuse.  
RH (p5): Message flow examples to show flexibility.  
RH (p8): Next steps: Should we consider message counting instead of
passed time enforcing a timeout? Add more examples. Have an
implementation.

## Observe multicast notifications (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-observe-multicast-notifications/

* https://datatracker.ietf.org/doc/draft-ietf-core-multicast-notifications-proxy/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-observe-multicast-notifications-00

MT (p1): We split the work into two documents as agreed on in Madrid.
One in the main document in version -13, the other one is Informational
and covering the use of this method in setups with proxies.  
MT (p3): Addressed comments from IANA, e.g., concrete option number
suggestions.  
MT (p4-5): Going over updates. Clearer text on avoiding link-local
addresses. Simplifications due to late changes in draft-ietf-core-href. 

MT (p6): The new Informational document is now available, with suitable
references.  
MT (p6): Here also suggested a suitable option number, taking advantage
of option deltas compared to Proxy-\* options.  
MT (p7): Next steps: there are corner cases (e.g., reverse-proxy) where
transport-specific information is redundant. We can keep the redundancy
or allow the corresponding field to be absent (defining that it SHOULD
be present, but there are exceptions). Consider "max-age" for the first
notification that the server stores but does not send over multicast (I
guess it's not about the CoAP Max-Age option, but rather about a storage
lifetime at the server). Details in the new document
-core-multicast-notifications-proxy will have to be aligned with
-core-observe-multicast-notifications. Both documents will have to be
aligned with the referred documents draft-ietf-core-groupcomm-bis,
draft-ietf-core-oscore-groupcomm, and
draft-ietf-ace-key-groupcomm-oscore.

CB: On Max-Age, also see Leisure in RFC 7252.

## CoAP over Bundle Protocol (Carles Gomez) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-coap-bp/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-coap-over-bp-00

CG (p2): Document overview.  
CG (p3-4): Updates in the latest version, also based on Marco's review. 

CG (p5-6): Aggregation of multiple CoAP messages into a single bundle
and group communication.  
CG (p7-8): Proxies MAY aggregate, there is a new motivation. There can
be intermittent connectivity. Note that proxies must ensure recomputing
CoAP option deltas when starting/interrupting aggregation.  
CG (p9): BPSec is still useful even when using OSCORE end-to-end.  
CG (p10): BP freshness and CoAP Echo option; the BP freshness cannot
verify CoAP message freshness.

CG (p11): Information leaks from the Payload-Length option.  
MT: Check the CoAP Padding option from draft-ietf-core-cacheable-oscore,
it might help.  
CG: I got the same suggestion from Martine.

## CoAP over GATT (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-amsuess-core-coap-over-gatt/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-coap-over-gatt-00

CA (p1): We can also transport CoAP over GATT.  
CA (p2-3): A device may have radio connectivity, but no APIs for
communication. GATT is what we have. It is not ideal, but it is the
reality.  
CA (p4): This document extends CoAP, with the same motivation as in CoAP
over WebSockets.  
CA (p5): Capabilities.  
CA (p6): Different CoAP header, due to different lower layer.  
CA (p7): There are two implementations. I have addressed certain
concerns raised by RiotOS people.  
CA (p8): Any interest from the Working Group?

MT: This was presented multiple times, I remember interest.  
MT: How many have read the latest version? Or any version?  
MT: Some have. Carsten offered to review.

Show of hands: Ready for adoption? 7 yes, 2 no-opinion.

MT: Start adoption call on the list?  
CB: Or we can solicit some reviews before the adoption call. Any
interest in reviewing?  
CG: Yes.   
MG (on chat): I'd like to have a look at the updates, yes :)

MT: So we count on three reviews (Carsten, Carles, Mikolai), then we can
have an Adoption Call.

## Non-traditional responses (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-bormann-core-responses/

Presented slides:
https://datatracker.ietf.org/meeting/124/materials/slides-124-core-coap-non-traditional-response-forms-00

CA (p2): Definition of non-traditional response. This is not a new
concept (see, e.g., Observe notifications).  
CA (p2-p7): This is thinking about a generalization of Observe and other
situations like multiple responses to a group request. Using a common
term for these kinds of responses simplifies understanding for
implementers.  
CA (p8): There is also an orthogonality issue. The generalization helps
apply OSCORE rules that were originally defined and relevant only for
notifications also to the general concept of non-traditional responses. 

CA (p9): Things to keep in mind.  
CA (p10): Potential (draft) users. Some were potential users, multiple
are still potential users.  
CA (p11): Define useful CoAP options related to the concept.  
CA (p12): Next steps.

MT (as individual): I reviewed an old version and I find this useful.
It's good to have this kind of guideline around a general concept that
somehow spontaneously emerged in . Can avoid future pitfalls.

MT: How many have read it? Solicit more response before adoption call?  
CB: If I were chair on this, would propose as for previous doc: ask for
two reviews, then ask for adoption.

MT: I can make one review.  
CA: I will like to ask Göran.

## Flextime (5)

# AOB

TE: Following-up on previous discussions in CoRE, I have just sent a
mail about wildcards in the IANA registry "Resource Type (rt=) Link
Target Attribute Values". This is related to the work in
draft-ietf-anima-brski-discovery. Please check it. See
https://mailarchive.ietf.org/arch/msg/core/WjqLrxLEYKzARyoRinPRHGSFOH4/

CA: On another topic: CoAP over QUIC people, please get in touch;
multiple seem to be active.

Σ 120

*[MT]: Marco Tiloca


*[CB]: Carsten Bormann


*[CA]: Christian Amsüss


*[ED]: Esko Dijk


*[RH]: Rikard Höglund


*[GF]: Giuseppe Fioccola


*[CG]: Carles Gomez


*[ML]: Martine Lenders


*[JJ]: Jaime Jimenez


*[MG]: Mikolai Gütschow


*[TE]: Toerless Eckert


*[MB]: Mike Bishop


