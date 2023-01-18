# IETF 115 — Agenda for Constrained RESTful Environments (CoRE) WG

\[toc\]

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

Date and time: Monday, 7th of November 2022, 13:00 – 15:00 UTC

Meeting material: https://datatracker.ietf.org/meeting/115/session/core

Notes: https://notes.ietf.org/notes-ietf-115-core

Meetecho video stream:
https://meetings.conf.meetecho.com/ietf115/?group=core&short=core&item=1

Meetecho for onsite participants:
https://meetings.conf.meetecho.com/onsite115/?group=core&short=core&item=1

Audio stream: https://mp3.conf.meetecho.com/ietf115/core/1.m3u

Jabber: xmpp:core@jabber.ietf.org?join

Zulip stream: https://zulip.ietf.org/#narrow/stream/21-core

Minute takers: Bilhanan Silverajan, Rikard Höglund, Christian Amsüss,
Jaime Jiménez

Jabber scribe: Jaime Jiménez, Marco Tiloca

# Monday, November 7, 2022

13:00 – 15:00 UTC

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (10)

* WG and document status

Presented slides:
https://datatracker.ietf.org/meeting/115/materials/slides-115-core-chairs-slides-01.pdf

MT presenting introduction and note well. Preliminaries done and agenda
accepted.

(Marco presenting slides with document status)

MT: RFC 9290 has been published (Concise problem Details for Constrained
Application Protocol (CoAP) APIs).

CB: HTTPbis RFC7807bis just finished IETF LC based on RFC 7807; its -bis
is completing only now so not the newest version used.  
More general topic of dereferenceable identifiers and IANA is ongoing.  
By the way, this contains Hebrew text, which slowed the publication
process significantly.

MT: draft-ietf-core-sid-19 is in IESG processing. AD followup coming.
Plan to discuss during the meeting week. It can be wrapped up soon.  
MT: -core-comi, -yang-library and -oscore-groupcomm are waiting for
shepherd write-up; -conditional-attributes and -groupcomm-bis are in
WGLC; -dns-over-coap has been recently adopted; -groupcomm-proxy is
pending WG adoption call.

## HREF (Carsten Bormann) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides:
https://datatracker.ietf.org/meeting/115/materials/slides-115-core-href-cris-00.pdf

CB presenting

CB (p1): Now called CRIs ("href" is just draft name)  
CB (p2): CRIs are an attempt to be concise with URIs. We have to build a
data model for URIs, and that's complicated, especially around dark
corners -- we don't care a lot, but we need to cover them in order to
make them first class citizens. CoAP(s) are easy though. CRIs are parsed
URIs (no need for URI parser anymore). It aims to use less bytes than a
URI.

CB (p3): One contribution to this conciseness is to have integer
representations as IDs for URI schemes.

CB (p4): The idea is to limit the points in time when the registration
of these scheme IDs can happen to: A) Initial pre-fill done by this
document; B) when a new URI scheme is registered. A wiki exists to
collect data for the initial pre-fill (see
http://github.com/core-wg/href/wiki/uri-schemes-that-we-want-numbers-for).
The question is whether this is the way to go or not.

CB (p5): During the Hackathon an idea came up, as the URI-scheme
registry already had a column added in the past (from RFC8615). So why
don't we add another column? Generally, we avoid impinging on someone
else's space, but in this case it may be alright.  
FP (on chat): Or add a note to the IANA registry (and make sure IANA
asks the question) with a pointer to the new registry.  
CB: Why having two tables if the information can go into one?  
FP (on chat): The difference is that it would not be needed to change
the old registry, a note is less "invasive".

CB (p6): Remaining issues all have a resolution already in github and we
can use the next CoRE interim on November 23rd to finish this up.

CB (p7): Next steps are to discuss it at an interim on November 23rd.
Then submit version -12, do WGLC and profit from it.

Olle Johansson (on chat): For URI tests, check CURL blog
https://daniel.haxx.se/blog/2022/09/08/http-http-http-http-http-http-http/.

AK (on chat): It seems that the IANA registry is missing some (commonly
used?) schemes, like https://github.com/mqtt/mqtt.org/wiki/URI-Scheme
but perhaps here's a chance for more than one bird with one stone to
have such also in the URI registry.

## CoRE Conditional Attributes (Bill Silverajan) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-conditional-attributes/

Presented slides:
https://datatracker.ietf.org/meeting/115/materials/slides-115-core-conditional-attributes-for-constrained-restful-environments-00.pdf

BS presenting.

BS (p2): The current state is that the document has been in WGLC for a
while. We got a review from Marco. Issues have been opened based on this
review. 19 of them are now closed and 1 is still open.

BS (p3): Most issues were editorial. 1 was about changing a reference to
normative. Clarified draft talking about value changes and considering
state representations and changes. The still open issue requires a minor
code review.

BS (p4): We want to address the final issue. More reviews are welcome.
Should we request a review from the IoT directorate?

MT: I heard a person volunteered to review.  
IR: Would be nice to have it reviewed by the IoT directorate. Please
send a request for it, I can review the document.

## CoRE Target Attribute Registry (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-bormann-core-target-attr/

Presented slides:
https://datatracker.ietf.org/meeting/115/materials/slides-115-core-target-attribute-registry-01.pdf

CB presenting.

CB (p1): The link-format has target attributes.

CB (p2): "rt" and "if" had registries for their values in RFC 6690, but
there is no registry for the attribute names as a whole. That was in the
spirit of RFC 5988 that does not attempt to coordinate the names of
attributes.

CB (p3): RFC8288 (i.e., 5988bis) says that serializations *should*
coordinate their attributes. So let's do that.

CB (p4): The idea is to add a sub-registry for Target Attributes, within
the CoRE Parameters registry. The registration policy will be "Expert
review", and specific instructions to the expert(s) are being defined.
These are: be frugal in allocation of very short names, "specification
desired", and allowed character set.

CB (p5): (Showing all the current pre-filled values)  
CB (p5): Naturally, we put values from already published RFCs in the
pre-fill. We also have ongoing drafts, the plan for
draft-ietf-core-oscore-edhoc is to "race", and see which draft is
published first and thus can keep its registration text. As for
draft-tiloca-core-oscore-discovery, we intend to register the values
there.  
MT: As per the allowed character set in page 4, we also have to replace
underscores with dashes. Both in the registrations and in the documents
triggering those.  
CB: Yes (ABNF does not allow underscores).  
ED: I support this draft. It's good to make the available to other
standards bodies. Regarding "Expert review", it is not a quick process. 

CB: No good way for transparent sequence of messages between the expert,
IANA, the requester and other relevant parties.  
ED: The request comes in and it is difficult to see if it was granted or
not. It's something to consider to be improved.  
ED (on chat, after the meeting): This (seemingly) did not get acted upon
by the experts or IANA.
https://mailarchive.ietf.org/arch/msg/core-parameters/\_Uk\_7EMTIZF8qU0kp8tfSTNWIvU/

CA: Talking about target attributes (following RFC 8288). Should this
document state anything on the (registerable) target attributes'
semantics, precisely about whether these describe the link or the target
(in a link-independent fashion)? (If so, we can't reuse RFC 8288 as
defined in RFC 8288).  
CB: I don't think we want to change RFC 8288.  
CA: It would be about which attributes can be registered, not about
changing RFC 8288.  
CB: Then it's my mistake to put 'title' under the heading of RFC 8288
(Web linking) in the slide.  
CA: CoRAL will want to add a column for the mapping.  
CB: Let's discuss this item later on (independently of the outcome of
this draft).  
CA (on chat): About adding the column: I wouldn't hesitate to update
-target-attr in CoRAL; I might be hesitant to update RFC 3986 if I were
a CRI author.  
CA (on chat): And on the topic of "it's surprising to see non-target
target attributes": That's why I've been behind CoRAL for some time, and
cursed RFC 6690 repeatedly :-)

CB (p6): This is still an individual draft. Next step is for WG
adoption, then WGLC and profit from it.  
MT: I am open for adoption call soon. Any objections?  
(none heard)  
MT: We will start the WG Adoption Call this week.

## Group OSCORE (Marco Tiloca) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-groupcomm/

Presented slides:
https://datatracker.ietf.org/meeting/115/materials/slides-115-core-draft-ietf-core-oscore-groupcomm-00.pdf

MT presenting.

MT (p2): v-16 has been submitted, merging PR #98, which covers 4 things:
1) Improving response handling; 2) Downgrade MUST to SHOULD for using
the group mode to protect one-to-many requests; 3 & 4) Extended
editorials on security properties aligned in presentation style with
OSCORE, and features of the group mode inherited by the pairwise mode.

MT (p2): Early discussion with CA as document Shepherd. Appreciate
further comments from others.  
MT: PR received very careful review from Rikard.  
MT: Post cut-off open point about a possible new target attribute,
already discussed with Carsten in relation to -core-target-attr.

MT (p3): Use of group mode for one-to-many requests was a MUST, now it's
a SHOULD. A case in point as an exception is the case where a
deterministic request is sent to multiple servers at once (see
https://datatracker.ietf.org/doc/draft-amsuess-core-cachable-oscore/)

MT (p4): The handling of multiple responses from the same server needed
to be improved, as underspecified. This is due to text in
draft-ietf-core-groupcomm-bis that allows one server to respond multiple
times to a single multicast request, even if Observe is not involved.
The text in -groupcomm-bis was introduced and confirmed about 2 years
ago, and unchanged since.

MT (p5): Most things were okay already. The problem was for "multiple
non-notification responses" from the same server to the same group
request. Missing inclusion of PIV in responses following the first one
on the server side (thus causing AEAD nonce reuse). The client was not
performing ordering or replay check of responses.

MT (p6): That issue has now been fixed, using the same approach as is
taken for Observe notifications. Yet, the presentation of this approach
is separate and self-standing, since Observe is optional to support and
with its own terminology.  
MT: New concept introduced "Non-notification group exchange": "exchange"
is used to mean an "Environment" (analogous to "Observation") associated
with one group request but tracking specifically the non-notification
responses. The server now MUST include its Partial IV in a response
(except the first one where it can be omitted). The client must enforce
replay checks and ordering of non-notification responses based on such
Partial IV values.

MT (p7): Further ancillary things needed to be defined beyond actual
message processing, but the same approach as for Observe could be taken
for those too.

CA: Didn't quite get why notifications need special handling compared to
other multiple responses (cf. core-responses which unifies the concepts)

MT: It's fundamentally the same handling, but presented as
self-standing. The idea was to keep Observe as a separate service
optional to support (as has been the case in OSCORE and Group OSCORE).
Alternatively, a true unification would require bigger restructuring and
can introduce confusion in the delta between Observe in OSCORE and
Observe in Group OSCORE.  
CA: This feature is never negotiated right, so just a matter of
phrasing?  
MT: Partly yes, uses slightly different terminology again to keep
Observe as a separate optional service. The reader can ignore parts
about Observe if not interested.  
MT (post meeting): I didn't get the word "negotiation" during the
presentation. Indeed, this is not negotiated. It is just part of the
protocol and can boil down to phrasing.  
CA: They would do same implementation as for Observe handling, to handle
the "non-notification group exchange"? I need to read document, but
seems like not a good idea to me. Even if it requires more editorial
work.  
MT (post meeting): The idea was to keep two separate, logical
environments at least in the text. That's again in the interest of
keeping Observe a separate, optional service. From an implementation
point-of-view, if a client supports Observe, then almost all of the
client Observe code can be reused for this.

ED: You mentioned the server sending multiple responses. We wrote in
-groupcomm-bis that it can be a malicious server, or with a faulty
implementation or so? Do you consider a server that could send 2
responses (in a legitimate way)? For example because the resource
representation changes, and the server gives an "update", taking
advantage of the still active token.  
MT: In groupcomm-bis, we considered the first things you mentioned, plus
a server that does not support message deduplication and receives a
group request that the client retransmits with the same Token and
message ID. But then the last examples you gave applies too.  
ED: Not sure if the intent was to support a server sending multiple
responses, more like it may happen (duplicates messages). It seems that
the server should not willfully send multiple responses.  
MT: On groupcomm-bis, it was totally left to the client application to
take a final decision on what to do with multiple responses. If they are
valid for the stack, the application must have received them.  
ED: The client could also say "I am throwing away every 2nd and 3rd
response". The client may not want to process multiple responses for a
single request (for a specific Token).  
MT: The stack at the client must be ready to have this happening. Group
OSCORE must support applications that are fine with multiple responses.
Then the application takes a final decision, whatever it is.  
ED: I agree on checking for duplicates, but not sure about sending 2
non-duplicate responses on purpose as a server.  
MT (post meeting): In order to check for duplicates in the stack, the
recent additions in Group OSCORE are required.  
CA (on chat): Agree with what's being said: A client that doesn't expect
multiple responses will just consume the first only, and check whether
that's valid.  
CA (on chat): Only if the client solicits multiple responses (by sending
Observe or whatever), it can opt in to the additional processing.

MT: To Christian's comment. The processing on the server side processing
is already general. It's really about adding a Partial IV to any
responses (with a possible exception for the first one), irrespective of
the response being a notification or not.  
CA: There can be multiple ways a client solicits multiple responses (for
one request), so good to have a way of dealing with it.  
MT: Yes this also comes up in other use cases.

MT: Can we expect more input on this from you Christian, i.e., text for
the draft or a Pull Request?  
CA: I will provide some.

MT (p8): The OSCORE RFC defines the 'osc' target attribute (resource
ONLY accessible using OSCORE); of course it does not cover Group OSCORE.
So, we think of defining 'gosc', meaning a resource is accessible using
OSCORE and/or Group OSCORE. Rules in the interest of endpoints that
don't support Group OSCORE and 'gosc': If 'gosc' is specified, so must
'osc'. Endpoints not understanding 'gosc' ignore it anyway. 'gosc'
overshadows 'osc', which is ignored if 'gosc' is present.  
MT: Any objections on defining 'gosc'?  
(No comments against.)  
MT: We'll define it and register it in the new registry proposed in
-core-target-attr.

MT (p9): Summarizing changes in v -16 based on PR #98. Plan to submit v
-17 with the target attribute 'gosc' defined; need to fix the response
handling based on the follow-up discussion. Then wait for Shepherd
review and write-up.

## Profiling EDHOC for CoAP and OSCORE (Rikard Höglund) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-edhoc/

Presented slides:
https://datatracker.ietf.org/meeting/115/materials/slides-115-core-profiling-edhoc-for-coap-and-oscore-ietf-115-core-00.pdf

RH presenting.

RH (p2): Background slide providing recap of EDHOC and the optimized
request.

RH (p3): Updates since IETF 114. Version -05 submitted. IANA
considerations added, renewed the early registration of the EDHOC CoAP
Option number.

RH (p4): Moved performance considerations on using block-wise to an
Appendix. Expanded security considerations. More considerations on this
part for access control also added.

RH (p5): The target attributes that this document defines can be
registered in the new IANA registry defined in -core-target-attr.
Pre-fill the registry from Carsten's document with attributes from this
document. We may want to revise the names of these attributes to be
shorter and to start with a prefix suggesting that they are about EDHOC.

(No objections heard)

RH (p6): Proposal from David Navarro being tracked in the Github
repository to extend figure 1 by merging PR #7 (to add EDHOC
message\_4). We plan to do this and also add a note clarifying below
that figure that EDHOC message 4 is optional.  
(No objections heard)

RH (p7): The fundamental procedure of the optimized request and the
whole draft are stable; the document is aligned with the latest EDHOC v
-17. Proposal at this stage is to start Working Group Last Call.

## Key Update for OSCORE - KUDOS (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/

Presented slides:
https://datatracker.ietf.org/meeting/115/materials/slides-115-core-key-update-for-oscore-kudos-ietf-115-core-00.pdf

RH presenting.

RH (p2): Recap. The draft contains 3 main parts: OSCORE Key Update
procedure (KUDOS); AEAD limit considerations; and OSCORE
Sender/Recipient ID update procedure.

RH (p3): Recapping how the KUDOS rekeying procedure works. Exchange of
nonces, built new Master Secret and Salt from that. Then new OSCORE
Security Context and OSCORE keys from that. The ID Context remains
unchanged.

RH (p4): Details of OSCORE flag bits have changed. Bit 15 indicates
KUDOS message, while now bit 0 instead of bit 1 is used for signaling a
second flag byte.  
RH: Related to IANA considerations: defined meaning and registration of
flag bit 0; changed status of bit 1 from Reserved to Unassigned; defined
meaning and registration of flag bits 8, 16, ... 48.  
RH: Plan to request soon for the registration of the flag bits 8, 16,
... 48, as extension bits.

RH (p5): Simplified method for the actual updating of the OSCORE
Security Context. This was discussed at a CoRE interim, and simplified
to not use EDHOC-KeyUpdate, but rather only one and simple method.
Hence, also no need to support EDHOC or be aware of its use. And no need
for "fallback" or negotiation if EDHOC-KeyUpdate is unavailable (e.g.,
since the EDHOC session is invalid).

RH (p6): Building on the above, the UpdateCtx function is also
generalized, and not locked to HKDF as key derivation function. It can
now support other possible future KDFs defined for OSCORE.

RH (p7): Defined ways that you can use EDHOC to signal support for
KUDOS. Defined EAD items for peers to signal each other for KUDOS
support and in which modes. The peers can indicate no KUDOS support,
only no-FS mode, or full (FS and no-FS) KUDOS support.  
GS: Is it worth implementing this signaling in EDHOC? Is it necessary in
order to then use KUDOS?  
RH: Even if you didn't have this signaling you could do a trial/error
approach to see if KUDOS works at all with the other peer. Or
trial-and-error for the FS mode first, and then for the no-FS mode if
need be. It is not something that KUDOS relies on. It is an extra
feature to gain pre-knowledge during an EDHOC execution, in case it is
happening anyway.  
GS: There is a tradeoff between adding nice features and adding
complexities  
RH: Agreed. Even if you support EDHOC, this signaling is not mandatory
to use.

RH (p8): Further updates from IETF 114. One is on avoid reusing the same
pair (AEAD nonce, key) in the client-initiated KUDOS. Clarify CAPABLE
and non-CAPABLE device support for KUDOS. (A CAPABLE device can store
information to disk, while a non-CAPABLE device cannot). A CAPABLE
device must support the FS mode and SHOULD support the no-FS mode. A
non-capable device MUST support the no-FS mode.

RH (p9): Related to the first point of the previous slide, there is an
open point for understanding Partial IV in responses. In the
client-initiated version of KUDOS, in Response 1 the server must include
its Partial IV, otherwise there is (AEAD nonce, key) reuse.
Fundamentally this is because of switching contexts between unprotected
requests and responses protection.  
CA: Good thing to do to send Partial IV again.  
RH: Agree, including the Partial IV is an easy fix.  
RH: For now, this is an ad-hoc fix for the client-initiated version of
KUDOS. However, we plan to make the fix more general, and applicable to
any case where a response is protected with an OSCORE Security Context
different than the one used to protected the request.  
(No objections heard)  
CA (chat-only): To detail why I don't think that this is just "an ad-hoc
fix": I keep saying that you MUST ONLY EVER send a response on the
piggy-back nonce if you just removed that number from that replay window
for the key you're responding with. (Admittedly, that last detail I'm
only adding since reading this...).

RH (p10): Question to bring out is whether the document structure should
be split out into separate WG documents? Benefit of doing this split is
to have the document focused on KUDOS only, instead of on 3 separate
topics. For now we suggest splitting out the part about the AEAD limits,
and perhaps later on also the part about Sender/Recipient ID update once
it's completed.

RH (p11): Main next steps: Work on open points. General considerations
on when to include Partial IV in responses. Consider feedback from Rafa
Marin-Lopez on soft vs. hard limits. Work on the section about updating
OSCORE Sender/Recipient IDs.

MT: Is the conclusion of the splitting following the idea of slide 10 as
is?  
CB: Yes.  
GS: Good proposal to split out the part on the AEAD limits.  
CB: Experience with a student group: They looked into a draft and RFC
page sizes, and decided to implement the smallest one. So let's try not
to create documents that appear more complex than they need to be.  
MT: So we'll split out the part on AEAD limits as a separate WG
document; a possible split of the part on OSCORE IDs update will be
considered later on.

## DNS over CoAP (Martine Lenders) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-dns-over-coap/

Presented slides:
https://datatracker.ietf.org/meeting/115/materials/slides-115-core-dns-over-coap-doc-dns-messages-in-cbor-01.pdf

ML presenting.

ML (p3): Motive: We want to perform encryption of DNS messages.

ML (p4): DNS over CoAP (DoC) would give such encryption possibility, and
also block-wise support. Take advantage of the CoAP retransmission
mechanism.

ML (p5): Got feedback from DNSOP. (Slide covering feedback and
responses)

ML (p6): Next steps. For DoC: Address feedback, pick ID for
application/dns-message Content-Format. For DNS in constrained networks
guidance: see https://datatracker.ietf.org/doc/draft-lenders-dns-cns/ .
Is there value in this guidance?

CA: I recommend for the server to place a lookup resource at `/`.  
ML: I agree.  
BSch: It is possible to bootstrap a DNS over CoAP connection without
explicitly defining a path.   
CB: If we can emulate DoH, that's fine. It is important to be reminded
that constrained discovery often will be on the RD and we can indicate
the path in that case.  
CB: One possible outcome is that servers using RD discovery they'd use
any path; for those with a more limited discovery they're stuck with the
empty path.  
ED: We could reserve a .well-known resource for this. I've seen that in
other WGs that you can then skip discovery (and the discovery takes a
round-trip). It's not that many bytes. I'm not sure that we can assume
that after getting an IP and port you can always assume it's at `/`.
(Maybe we can, see in the ANIMA WG; you discover an IP and port there). 

ML: We also have the content format in there, but maybe that's not a
good idea. In our evaluation, we used `/dns` but that's 4 bytes.  
ED: At least consider .well-known. A server can easily support multiple
ones.

(JJ: wondering why a content format is a bad idea?)  
(CA: because it starts multiplexing based on something that's already
used for multiplexing extensions; like, if a future format is just
"CoRAL" or "JSON", whom will it go to?)

## DNS messages in CBOR (Martine Lenders) (10)

* https://datatracker.ietf.org/doc/draft-lenders-dns-cbor/

Presented slides:
https://datatracker.ietf.org/meeting/115/materials/slides-115-core-dns-over-coap-doc-dns-messages-in-cbor-01.pdf

ML presenting (p9 of combined slide set).

ML: The drawback of DNS in constrained networks is that packet size
exceeds the PDU size, leading to fragmentation. We can reduce packet
size by using CBOR encoding and omitting redundant fields in DNS queries
and responses.

(Showing defined structure for DNS queries, DNS resource records, DNS
response in CDDL.)  
ML: The basic example shows a compression rate of 400% for query. A more
complex example gives 305.9% for ANY query, but around 100% for the
response.

ML: Our proposal is to do Name and Address compression using Packed
CBOR. This improves the compression rate. Using global compression
contexts may improve things further. Is it worth it?

ML: Why not using SCHC? It assumes exchange of rules and thus an
established connection, which is usually not present for a DNS
Client->DNS Server.

ML: Next steps are to define more details on using Packed CBOR, e.g.,
the construction of the packing table and global compression contexts.

(JJ: Wondering if they use similar compression in DoH and why yes/no?)  
(CA: When you're in HTTP you don't care so much about saving 50 bytes)  
(JJ: per request! it is a big saving, no? does it put extra burden on
the DNS processing maybe?)  
(CA: Not sure it's really a big saving. It's a packet either way, and
going into a HTTP request with headers, so it's diminishing. But on CoAP
and 6LoWPAN it's the difference between one or two packets.)  
(JJ: IDK, it sounds like it could also be beneficial in DoH but I get
the point.)

BSch: There have been many attempts to re-phrasing DNS; DNSOP was
generally not friendly with these proposals. Go there first. Biggest
concern generally: About ossification -- if a new format cannot express
later messages losslessly, it's ossifying (creating devices that appear
to do DNS but actually do a subset). Generally, I don't see value. DNS
messages are almost always tiny fraction of the total bandwidth; saving
50% off DNS messages is not measurable in aggregate.  
ML: I tend to disagree as it is not such little traffic.

ED: Normal DNS format has packing integrated; you can use it or not, but
it's all the same format, so it might be easier to handle. So it's
nothing that needs to be negotiated. The sender can decide to compress
or not, the receiver can restore.  
ML: The idea is that the client might not support packed CBOR. So it's
negotiated.  
ED: On laptop, running simulated DNS-SD nodes. Be aware of that use
case.  
BSch (on chat): If clients signal which formats they support, the extra
bytes for that signal will eat into the savings from the compression.

CB: ad Ben: If you look at the percentage of DNS traffic, the total gain
is limited. But as in ML's first slides, environments with limited PDU
sizes have cost for using larger packets beyond a few bytes. The problem
is that you're using DNS in recovery from network failure, which is when
everyone else does it, and the network is impaired. If then the
adaptation layer starts fragmenting, performance drops. This creates the
boundary of ~80 bytes.  
ML: What you can see also in the slide is that larger packets also
create more overhead due to the 6lowpan headers and we tried to avoid
this.

BSch: If you try to stay within these limits, a more appealing path is
to not provide a general-purpose representation, but instead to define a
very simple service ("name to IP").  
ML: We also need to support DNS-SD, not just IP addresses but also other
records.   
BSch: even then, look into API specifically for that use case.  
CA (on chat): +1 on BSch's "not replace general purpose DNS but special
case"

MW: Why arguing against the compression of DNS messages?  
BSch: I think that there is a cost and adding new things with small
benefits is a bad path forward. Specifically in this case, there are
alternative representations of DNS messages, for example in JSON.
Standardizing that is different as it hampers evolvability. Much space
can be saved when information is discarded, but discarding DNS
information is a sticky area.  
CB: We have already the Resource Discovery service, so we don't need a
new one.  
ED: What I work with is a Thread mesh (6lo based). Not too constrained
(still 2.4GHz, large band usage, no duty cycle limits; others are more
constrained). We use normal DNS and DNS-SD for registration and
querying. It already has some compression, and it's not much traffic in
total. Don't know if systems so constrained they use a single frame
would use DNS-SD at all. Maybe then there is no requirement to do all of
DNS.

## AOB

MT: Interim meetings are scheduled. The interim on November 23rd can
focus on core-href, -core-target-attr and any further discussion on DNS
CBOR. The interim on December 7th can focus on -core-sid. After that, we
resume on January 18th.

Clapping.

FP: Went through CoRE errata. 10 reported, see
https://www.rfc-editor.org/errata\_search.php?rec\_status=2&wg\_acronym=core&presentation=table.
Looking for agreement in the WG that they are treated correctly. I will
send a mail shortly.  
Mail available at:
https://mailarchive.ietf.org/arch/msg/core/0VM6waLVW1v3B9ghF0EmUBeZZ3E/

## Flextime (10)

Σ 120

* * *

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


*[BSch]: Ben Schwartz


*[IR]: Ines Robles


