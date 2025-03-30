# IETF 122 - Agenda for Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

Date and time: Tuesday, 2025-03-18, 02:30-04:30 UTC

https://www.timeanddate.com/worldclock/fixedtime.html?msg=CoRE%40IETF122&iso=20250318T0930&p1=28&ah=2

Meeting material: https://datatracker.ietf.org/meeting/122/session/core

Notes: https://notes.ietf.org/notes-ietf-122-core

Recording: https://youtu.be/0vKEC-RqxYg

Zulip: https://zulip.ietf.org/#narrow/stream/core

Note takers: Christian Amsüss, Rikard Höglund

* * *

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (15)

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-chairs-slides-01.pdf

MT doing introductions

Going over the status of WG documents and relevant documents from other
WGs.

Encouraging and thanking people for writing reviews for WG documents.
Reviewers will get a small duck for each review, as a thank you and
recognition for reviews.

FP (AD): Pleasure to work with all of you. Mike here as the incoming AD.

*applause*

## CoAP corrections, clarifications, and gaps (Carsten Bormann) (5)

* https://datatracker.ietf.org/doc/draft-ietf-core-corr-clar/
* https://github.com/core-wg/corrclar

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-corr-clar-coreconf-crihref-00.pdf

CB: Three simple and fast ones, leaving time for discussion.  
CB: This work addresses questions that were asked.  
CB: Now it is a WG document living on Github, where a lot of the
discussion is happening. It is worth having a look there.  
CB: We have been processing the issues during CoRE interim meetings (1-3
issues per interim meeting). Progress made is recorded in the document,
classifying topics as INCOMPLETE and INCORRECT.  
CB: Current focus is on issues (as in: "something is not good in
documents we have"). We also have situations where we introduced
features, but only described them for specific cases (protocol
configurations), e.g., BERT (Block-wise szx=7); from that: "wouldn't it
make sense to use the same mechanism to address gaps?"  
CB: A gap is a situation where the semantics are defined but are
unsatisfactory (e.g., BERT thinks only of stream transports but not of
datagrams, even though it could be used there). Fixes are wished/planned
to exploit orthogonality (or where little extensions were done and
commonalities can be extracted into a common base).  
CB: Question for people who looked at the document: is this (adding
"gaps" as another category) something we should do in this Internet
Draft?  
CB: For changes to be effective, a document needs to be approved.
-core-corr-clar is a working-document that cannot formally update an
RFC.  
CB (p3): Proposal: For Gaps, incubate fixes/updates here, at some point
pull them out, and make a separate document on the specific topic. Are
people comfortable with addressing the gaps in -core-corr-clar,
extending INCORRECT and INCOMPLETE? Or should we start a new document
right away before the discussion is concluded?

MT: My opinion as an individual is that the incubator approach seems
practical. Opinions or objections?  
CA (chat): I like the incubator approach (but I may not count, as I
brought in the items for that category).  
MT: You do count.  
CB: Good, then I will prepare a version -02, where the new category
"gaps" is explained, and then we can start adding such issues (e.g.,
issue #35) to the document.

## CORECONF: YANG CBOR and YANG SIDs (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/rfc9254/
* https://datatracker.ietf.org/doc/rfc9595/

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-corr-clar-coreconf-crihref-00.pdf

CB (p4): Overview of documents. The priority is getting SIDs in place.  
CB (p5): We want to generate SIDs for all YANG models from RFCs. We have
a step-by-step plan for achieving this. Later on, do the same for
Internet Drafts (hoping for cooperation from authors).  
CB (p5): A snapshot is on the website at https://tzi.org/~cabo/rfcmod/.
Numbers are not final yet (ranges are to be decided). Finally, check
ranges and register them along with SID file. This work is using the
tool PYANG which has been forked and is being further developed. Around
10 RFC models make the tool crash; we need to understand why and fix
this. Anyone interested is welcome to look at the snapshots on the
website. Let us know if you find issues with any of the SID files or if
you can help in general.  
CB: We will coordinate this in a separate list.

ED: Question on SID value allocations: they all seem to use temporary
SID values. Is that right?  
CB: Yes, we did not do range allocation as we need to look at the number
of SIDs in use first to decide on what size of range to use. Once we see
how many SIDs are there, we want at least +1/3rd of the space as slack. 

ED: It should be those that already have SIDs allocated (they should
also be considered).  
CB: Yes

## Constrained Resource Identifiers (Carsten Bormann) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-corr-clar-coreconf-crihref-00.pdf

CB (p6): Long-running effort to make URIs more useful for constrained
devices (maybe also in high-performance environments).  
CB: We did some formalizing of the data model during the work on CoAP
(when the URI path was split into CoAP options). This work generalizes
that part.  
CB: We have reached a big milestone with having the WGLC (the best
reviews come during WGLC).  
CB: Version -20 was submitted yesterday, addressing all WGLC comments.
What's the next step? Submit to the IESG or second WGLC?  
CB (p7): Overview of changes since what was under WGLC. Initial values
from old draft: let's see what the IESG and IANA say about the "Remove
in RFC" note set on a table.  
CB: The terminology still needs some updates: not all terms (e.g.,
"absent component") work for URIs and CRIs the same way. This is
something to check closer during a possible second WGLC.  
CB: Normalization is not so much a requirement as an assumption. We
realized that normalization can be destructive in certain instances,
thus we do not want to always require this.  
CB: Having normalization in constrained devices is a big stretch. There
is no requirement to check or normalize (it is expensive!). But this
creates situation where the recipient cannot rely on normalization.  
CB: We had some wiggle room around indefinite length encoding. We added
criteria for when to use and when not needing to use this.  
CB (p8): On more technical things: stand-ins are now explained. We
registered a tag for CRIs. We no longer call top-level CRI components
"absent": they are all present but they can be null or empty array etc.
As null is no longer a viable shortest version everywhere, the tail
elision now uses defaults. We clarified that scheme numbers are
preferred over scheme names. We also clarified that Proxy-Scheme and
Proxy-Scheme-Number cannot be used together in one message.  
CB: Not massive changes, but they need corresponding fixes in
implementations.

CB: Question: Do we want a second WGLC or do we submit to the IESG?  
MT: We had the second WGLC, so a further one would be the third one. Do
we wait for a version -21 regardless for the pending fixes?  
CA: If I remember correctly, version -20 addresses all the open points. 

CB: I believe so too.  
MT: I want to get feedback from the Shepherd (Thomas). If all is fine, I
think that this can move forward to the Shepherd write-up phase (without
3rd WGLC).  
CB: Please have a look if any of what I mentioned sounds suspicious to
you.

## Conditional Attributes for Constrained RESTful Environments (Jaime Jiménez on behalf of Bilhanan Silverajan) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-conditional-attributes/

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-draft-core-conditional-attributes-11-00.pdf

JJ: I am shepherding this document. I have also reviewed it. The title
has been changed to be more aligned with the content.  
JJ (p2): Bill made updates included in version -11, based on the
Shepherd review. There are three remaining issues open in the Gihub
repository. The plan is to go with what is proposed for those in the
next slides, unless more comments come in.  
JJ (p3): Issue #52 on handling complex data structures: currently, all
are scalar or boolean; multiple proposals on how to handle this.  
JJ (p4): Issue #53 on mixing the query parameters defined in this
document with arbitrary, non-registered query parameters. We have a
proposal for resolving this.  
JJ (p5): Issue #51 on explaining the concept of resource state
projection. We found no normative text on what this means. It would not
be bad if other drafts took that up.

CB: These issues are good examples of gaps about sorting documents into
one category or another. We have informational, Experimental, BCP, and
Standards Track. For this document, I remember it is Standards Track
(for other SDOs normatively referencing it). Yesterday, in another WG
meeting there was a suggestion for a "Toolbox RFC" category that
describes usable components, which one can fully exploit only in other
documents (e.g., SenML extraction, resource state projection). This is
Standards Track, but not freestanding. Other areas have solutions for
this. For example, in the security area, crypto standards are
Informational because doing differently does not make sense before using
them in specific environment. At that point, they get blessed when first
used as normative reference and added into a DOWNREF list. I am
mentioning this here because we will not take this tension out
completely, because this is a toolbox. Other specifications can use what
provided by this document and add additional information.  
JJ: Correct.

CA: On issue #52: I suggest leaving the handling of non-scalar values to
other documents. Anything that taps into "value" is just left unusable. 

CA: On issue #51: the RESTful design document (in the T2TRG Research
Group) could be a good place.  
JJ: So, for issue #52, the draft does not have to support anything other
than scalar and boolean, but nothing prevents another SDO from
supporting those.  
CA: For a particular media type.  
CB: In the interest of being a good toolbox, this document could give
this as an example.  
CA (chat): +1 on giving-that-as-an-example  
JJ: So we can hint.

MT: This document is waiting for shepherd write-up now, so JJ will have
a closer look at the issues being addressed.

## DNS over CoAP "bundle" (Martine Lenders) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-dns-over-coap/
* https://datatracker.ietf.org/doc/draft-ietf-core-coap-dtls-alpn/
* https://datatracker.ietf.org/doc/draft-lenders-core-dnr/

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-dns-over-coap-doc-bundle-00.pdf

ML: draft-ietf-core-dns-over-coap passed WGLC and reviews have been
addressed. The biggest change was clarifying that opcodes other than 0
are not supported.  
ML: draft-core-coap-dtls-alpn also had a WGLC and reviews have been
addressed.  
ML: draft-lenders-core-dnr had example scenarios added.

ML (p2=3): Minimal bundle highlighted here as a figure.

ML (p3=4): On -core-dnr, we have to handle orthogonality by better
presenting the content in two parts, coordinating with work on EDHOC
application profiles in the LAKE WG. We welcome reviews from
OSCORE/EDHOC/ACE experts.

ML (p4=5): Hackathon report: ported DoC to unbound based on libcoap. The
goal is to get code ready for merging.  
ML: digdoc is dig for DoC.

MT: On -core-dnr, then we expect an editorial revision, and syncing with
related work. On core-coap-dtls-alpn and -core-dns-over-coap, no recent
comments after WGLC changes. Anything else pending?  
ML: No.  
MT: Then their WGLC is completed. I will work on their Shepherd
write-ups in next weeks. I will give another look to both documents, but
I reviewed already during their WGLC, so I am not expecting to come with
big comments.

## A publish-subscribe architecture for the Constrained Application Protocol (CoAP) (Jaime Jiménez) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-coap-pubsub/

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-draft-ietf-core-coap-pubsub-slides-ietf-122-01.pdf

JJ presenting

JJ (p2-4): This draft has been around for a long time. There have been
many recent reviews. Those included a major point about eliding target
attributes in responses that use link-format (I will come back on that).
Going over recent updates.  
JJ (p5): Report from the hackathon: I cleaned up the code and added
examples; now I have a script that works as how-to.  
JJ (p6-7): Recap of architecture; overview of the protocol and of the
topic lifecycle.  
JJ (p8): Open points for discussion: 1) The topic property "initialize"
allows creating a topic immediately in CREATED state. 2) Deleting a
topic data resource results in reverting the topic to HALF-CREATED
state. 3) Information about any rate limiting on publications is not
conveyed to subscriber clients.  
JJ (p9): Following a GET request for discovery purposes, links in the
response payload usually convey target attributes. By making some
assumptions, some attributes can be omitted altogether, thus saving
bytes. Something to consider in other drafts? I do not think we want to
do it retroactively.  
JJ (p10): Conclusions: we got reviews and addressed comments. More
reviews are welcome. Please go for PRs on Github if you wish.

CB: On p9, that is an important point. RFC 6690 discusses querying the
/.well-known/core resource. The wording there is not great. In the links
within the response payload, I assume that you get a subset of target
attributes.  
CB: That does not mean that this covers every CoAP query; the text is
specific to /.well-known/core . The reply to the request to a broker can
be different. The reason for the incentive to leave out the rt= target
attribute is that the original CoRE link format makes it expensive to
state. 10 years ago, we abandoned the idea of a JSON/CBOR version of
that. In the CBOR version, packed CBOR would make it light. But we do
not have that in place, so we have incentives for servers to trim the
response content. The server can decide what to leave out.

ED: I agree with CB. We are talking specifically about queries to
something else than /.well-known/core . We can use CoRE link format in
more particular ways, excluding some attributes. A good question is, why
the CBOR link format idea was abandoned?  
JJ: It can be interesting to re-visit. Packed CBOR would be useful.

CA: On why it was abandoned, I can fill in: a problematic aspect is that
the format looked similar to JSON-LD. But this exposed that a lot of the
desired conversion would require per-target-attribute conversion rules.
That was not in scope, we wanted a mechanical translation, which was not
possible. Also, that goals shifted to CoRAL, which has made progress but
not enough yet.

CB: I want to mention that the CoRAL work is supposed to be the
replacement. Of course, the original draft is there but expired, see
https://datatracker.ietf.org/doc/draft-ietf-core-links-json/ . The
transition can happen when CoRAL is finished.

ED: I have not prepared the Shepherd write-up for this document yet. It
can be the next step.  
JJ: The plan is to address the recent comments from Christian and update
the Editor's copy. Then, I submit the result as version -19. Please do
the Shepherd write-up on that version.  
MT: Reminder: CB is acting as Chair for this draft, I recuse myself as I
am a Contributor.

CA (note to self, mail): →elision. (maybe "elisions only apply to
default link rel" to stay open for volunteered proxy links)  
CA (note to self, mail): →point out all-messages v. eventual-consistency
model.

## CoAP Transport Indication (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-transport-indication/

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-coap-transport-indication-01.pdf

CA (p2): Quick context recap. Goals: 1) Enable discovery of alternative
transports (client discovery and server advertisement). 2) Plan for how
new CoAP transports can avoid defining a new scheme coap+XXX for every
new transport.  
CA (p3): Recent updates: We have described general components to use for
an endpoint (CoAP transport, address, additional metadata). We have also
described available endpoints in those terms (proxies that are
explicitly advertised through web links; resolution services, especially
DNS). We are picking up content about advertisement through SVCB. We
plan to describe explicit configuration through the application too.  
CA (p4): The plan is that the URI authority component should provide all
the information needed to understand which CoAP transport is to be used.
IP transports can use SVCB records. The gap is that IP literals do not
provide a way to indicate those lookup results; a way to describe those
have now been added. The hard part is formalizing an information model. 

CA (p5): Question: Can we achieve the goals of this document without
registering .service.arpa? (It will not be strictly needed until the
next transport comes along)  
CA (p6): Other open questions: 1) What is the precision needed on
properties of SVCB records vs. that needed on properties of proxies?. 2)
Should SVCB considered as best practice?

CA: Please provide reviews of the document. I want to avoid flying
blind.

MT: I believe that reviews will come, considering the plans you have
mentioned and the plans for syncing this document with -core-dnr and,
through the latter, with work in other WGs.

CB: For historic context, we wrote this check to pay for
CoAP-over-TCP/-TLS; it has bounced so far. The answer is that we need to
understand the information model, what we expect from literal form or
other forms. But there is no need to define this in the same document.
It would be nice, but there is no need to.  
CA: Thanks, it is not so easy, but I will look into that.

(On chat):  
CA: CB, to clarify: you think we need an information model, not a data
model, right? (I.e., prose typing suffices as compared to formal or
serializable typing).  
CB: Yes. Sometimes a data model specification can clarify an information
model, but the reg-name based data model is going to be weird so let's
talk about an information model.

## Observe Notifications as CoAP Multicast Responses (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-observe-multicast-notifications/

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-observe-notifications-as-coap-multicast-responses-00.pdf

MT (p2): Recap on purpose: Multiple clients can be interested in
observing the same resource on the same server. With this protocol, the
server can send observe notifications over multicast, targeting all the
observer clients at once. Steps: a client indicates its wish to observe
by attempting a regular observe registration; the server rejects it and
replies with a 5.03 error response providing information about
participating in the group observation; the client gets itself ready to
receive multicast notifications; the server sends the notification(s)
over multicast. The server starts the group observation by "sending to
itself" a phantom observation request (that never hits the wire), to
which all the multicast notifications are bound, from a transport
point-of-view (by Token value) and from a security point-of-view (if
using Group OSCORE).  
MT (p3): The updates from version -09 to version -10 addressed feedback
from IANA and did editorial improvements.  
MT (p4): From now on covering the updates from version -10 to version
-11: the intended restriction on "redirects" unintentionally forbade
multicast observation requests in this setup. The new text still forbids
redirection, but now it ensures that clients can send a multicast
observation request to multiple servers.  
MT (p5): Added optional parameter 'ending' in the error informative
response (instructions from server to clients). 'ending' specifies the
time when the group observation is planned to end. If not present, the
end time is simply left unknown for the clients, but of course the
server can still terminate the group observation by the usual means.  
MT (p6): The update above was in fact triggered by the possibility for
the server to early publish the error informative response and other
group observation data via other means (e.g., through a pub-sub system).
We concluded that such published data should include the planned
termination time for the observation, which practically relies on the
defined parameter 'ending'. When doing so, the server commits to not
terminate the group observation before the time specified in 'ending'.
However, the server can stop retracting the published data before the
time specified in 'ending' has come.  
MT (p7): We have made a first description of a scenario with a
reverse-proxy and security with Group OSCORE, in the new Appendix H. We
still have to including a few more details on how this would function
and an example with exchanged messages. At a high-level, there is a need
to provide the clients with the information to contact the
reverse-proxy, and to actually trigger the client to follow-up with the
reverse-proxy to put things in motion. From then on, it becomes just
like in the scenario with the forward proxy and cacheable OSCORE
responses defined in Appendix G.  
MT (p8): Next steps: 1) Add concrete examples when using the new
parameter 'ending' and when using a reverse-proxy. 2) Align the content
with ongoing work in draft-ietf-core-transport-indication. Specifically,
revise how to determine the transport to use (which in turn determines
the client-side transport-specific information within the error
informative response), by relying on both the URI scheme and URI
authority from the server-side transport-specific information, and not
from the URI scheme alone (which is, in general, insufficient).

CB: Amazing technical work, I like seeing this developed. Editorial
question: the Internet Draft is currently 99 pages. It's great to have
examples, but I am wondering if we can make these specifications more
accessible, e.g., by separating the specification from the examples.
This is what happened with the EDHOC protocol (RFC 9528) and its traces
(RFC 9529). I am just encouraging some thinking.  
MT: Yes, a lot are appendixes, providing examples of message exchanges
and pseudocode. An easy way out is to split that content out into a
separate document.

MK: CB complemented some of my thoughts. Can this complexity be adopted
on larger scale? Any feedback from implementors? It feels you like to
put every corner case into the starting specification, which makes
rolling it out a high entry barrier. Do you need all the proxy chains to
get this working? For field bus level networks? Hearing how big the
document is and its appendices, can this be narrowed down, focused on
use cases? There is need for this, but not for its complexity. Reduce
the scope, make it more robust, make it simple to implement. Then extend
from there.  
CA: A lot of the work on proxies is not about specifying what to do, but
more about showing that what we specify works transparently. We added
those parts in the documents to convince ourselves that we are not
breaking the REST architecture. We can take that content out into an
informative document. So yes, it can be slimmed down.  
MT: For now we wanted all on the table, also as a sanity check. The
appendices are not specifying new content as protocol components and
functionalities.  
MK: Ensuring that things work well also through a proxy is important, I
agree. But it feels a bit overwhelming. I would appreciate any
simplifications.  
MT: Thanks for the feedback.

ED: Thinking about the proxy case: if that is what makes things
complicated, then splitting it out could be good.  
CB (chat): It is great that we have thought through all this! But it
does not have to be in the same document.

CA (note to self): →ending to become CDDL ~time. maybe max-age in stored
first response?  
<!-- CA (note to self for transport-information): →point out that some
cases an require unique result (such as this). (done) -->

## Key Update for OSCORE (KUDOS) (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-slides-kudos-core-ietf-122-00.pdf

RH (p2): Recap of the protocol. A major redesign took place.  
RH (p3): KUDOS decoupled from server/client roles.

RH (p4): Highlighting high-level rationale of the new design: more
flexible and simpler. Request/response, client/server, first/second
message do not matter anymore. Defined concept of CTX\_BOOTSTRAP for the
no-FS mode for non-capable devices.

RH (p5): Explaining the two KUDOS message types: divergent or
convergent. The message type is indicated by one bit in the OSCORE
option. At a high level, the message type indicates if one or both
nonces have been exchanged between the two peers. There are three OSCORE
Security Contexts involved: CTX\_OLD (starting context to eventually
abandon), CTX\_NEW (new context to establish), and CTX\_TEMP (temporary,
intermediate context).

RH (p6): CTX\_OLD is bound to the pair (X byte, Nonce) included in the
OSCORE option of a KUDOS message and offered by a peer. To deal with the
decoupling from the concept of first/second message, the two exchanged
nonces are now lexicographically ordered within the key derivation
function used, so that the order of their sending/reception does not
matter.

RH (p7): Explaining the three possible KUDOS states: IDLE, BUSY, and
PENDING. Defining start and end of a KUDOS execution in relation with
the states. Defined meaning of the three states, reflecting the progress
on the nonce exchange and the achieved key confirmation.

RH (p8): Presenting the KUDOS state machine with the three states and
the state change conditions.

RH (p9-10): Example of message exchange in a typical case, with
highlighted changes of state. This completes in 1 round trip.

RH (p11): Short update on related drafts (-core-oscore-id-update and
-core-oscore-key-limits). Check them out, new versions are available.  
RH (p12): Simplifications are under consideration in the state machine.

CB (on chat): Beautiful simplification.

## CoAP in space and over Bundle Protocol (BP) (Carles Gomez) (10)

* https://datatracker.ietf.org/doc/draft-gomez-core-coap-space/
* https://datatracker.ietf.org/doc/draft-gomez-core-coap-bp/

Presented slides:
https://datatracker.ietf.org/meeting/122/materials/slides-122-core-coap-over-bp-and-in-space-00.pdf

CG: Presenting v-03 of -core-coap-bp.

CG: Showing updated ToC.  
CG (p4): Updated the Payload Length option. Enabled message aggregation.
Enabled recovery of single message from aggregate message.  
CG (p5): Overviewing concept of proxies and their use.  
CG (p6): Showing scenarios using a proxy, including cross-proxies.
Relevant for uses cases with a relay, e.g., Earth-to-Mars and
orbiter-to-Mars surface.  
CG (p7): BPSec can protect all CoAP fields, however it cannot work over
proxies. So we recommend using OSCORE.  
CG (p8): Are there reasons to use BPsec and OSCORE? If not, what are
those?  
CG (p9): Added a section to make the IANA registration request for the
Payload Length option.  
CG (p10): Details on setting the bundle lifetime depending on message
properties. Mentioned conditional attributes in the section about CoAP
Observe.

CG (p12): Now covering -core-coap-space: we may need store-and-forward.
This considers running on an IP-based stack.   
CG (p13): Updated ToC. Added a section on proxies and on message
aggregation.  
CG (p14): Describing proxies, which are relevant to this use case.  
CG (p15-17): Showing scenarios with or without proxy, including a
cross-proxy.  
CG (p18): Explaining message aggregation using the Payload Length
option. Message aggregation is about concatenating messages and
including the Payload Length option.

CA: I like message aggregation. If it works out like that technically,
then aggregation with the Payload Length option might be an instant
candidate for -core-corr-clar.  
CG: Yes, this may work outside this Internet Draft.  
CB (on chat): +1 (Even though I'm still not sure why this isn't part of
the header...)  
CB: I mentioned previously that, for CoAP over TCP, we changed the CoAP
header. Putting a Payload Length option is not so different, but it
requires parsing all the options in the individual messages in order to
parse the aggregate message.  
CA (chat only): That was also my knee-jerk reaction; that is what I
meant with "not sure on technical implementation".

MT: This document is also in the agenda for the TIPTOP WG, right?   
CG: Yes.

## AOB

MT: Thanks, enjoy the rest of the week!

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


*[ZL]: Zhuoyao Lin


