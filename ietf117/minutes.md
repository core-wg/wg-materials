# IETF 117 - Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

Please note:

Date and time: Tuesday, 2023-07-25, 16:30-18:30 UTC

Meeting material: https://datatracker.ietf.org/meeting/117/session/core

Notes: https://notes.ietf.org/notes-ietf-117-core

Meetecho video stream:
https://meetings.conf.meetecho.com/ietf117/?session=30622

Meetecho for onsite participants:
https://meetings.conf.meetecho.com/onsite117/?session=30622

Audio stream: https://mp3.conf.meetecho.com/ietf117/30622.m3u

Zulip: https://zulip.ietf.org/#narrow/stream/21-core

* * *

# Tuesday, July 25, 2023

16:30-18:30 UTC

Minute takers: Christian Amsüss, Rikard Höglund, Jaime Jiménez (helping)

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (15)

MT doing introductions.  
MT (p7+):

* -core-target-attr is in IETF Last Call.
* -core-oscore-groupcomm-19 in post-WGLC processing (shepherd review
  addressed); now waiting for the Shepherd write-up
* -core-oscore-edhoc waiting for Shepherd Review
* -core-sid (moved back to WG anticipating a new WG Last Call),
  -core-comi (expected new WG Last Call) and -core-yang-library (waiting
  for Shepherd Write-Up for a long while, but will go through a revision
  and new WG Last Call once -core-sid and -core-comi have progressed)
* -core-groupcomm-bis waiting for some expected editorial comments and
  confirmation of addressed WG Last Call review
* -core-conditional-attributes-06 completed WG Last Call; some more
  changes expected based on received comments. The next revision will be
  Standards Track, as previously confirmed.
  
  CB: There was also activity from the IESG looking at related IPR
  issues: this document is the result of a split out from -core-dynlink,
  and the IPR stuck with one side (the new document), but in the Data
  Tracker it's on the other side (the old document -core-dynlink). We
  are waiting for more guidelines on this.  
   MT: Thanks for checking

* core-href-13 completed WG last call; waiting for chair go-ahead. TF
  and MT provided input, CA will still send comments.
  
  MT: Can you confirm you'll give comments Christian?  
   CA: Yes

* Other documents:
  * key-limits-01: not in the agenda, new version was submitted
  * core-coap-pm-00: recently adopted, new revision expected soon
  * core-groupcom-proxy-08: pending WG adoption since its version -06
    (keep-alive followed since)

* Recently updated individual submissions:
  * cacheable-oscore-07
  * coap-over-gatt-04
  * core-corr-clar-01

MT (p13): Informal side meeting will take place on Friday 09:30 (San
Francisco time) in Golden Gate 4 + Meetecho. Main topics are
non-traditional responses, corr-clar, and locally significant URIs.

MT (p14): Interim meetings will resume on 2023-08-30 in the same cadence
as the last years, alternating with CBOR. We will book them soon.

## YANG Schema Item iDentifier (YANG SID) and COMI (Carsten Bormann) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-sid/
* https://datatracker.ietf.org/doc/draft-ietf-core-comi/

Presented slides:
https://datatracker.ietf.org/meeting/117/materials/slides-117-core-href-coreconf-00.pdf

CB (p3): Set of documents; one RFC, -core-sid came back to the WG from
the IESG. The remaining task is to extract identifiers from YANG
document based on enhanced understanding of YANG.  
CB (p4): -core-sid: We'll have to make sure that all the data node
identifiers that the document contains are listed. LT is around and has
experience with PYANG; I hoped we could do that together, but it didn't
happen during the Hackathon. Éric Vyncke (assigned AD) predicted that
Francesca probably will be back before this gets done. LT, I hope you
can help me this week.  
LT: thumbs-up.  
CB: -core-comi: Received YANG fixes. Most focus will be on YANG issues
(because we could address the constrained-related ones). The document
was missing an RPC example -- YANG has RPC (object independent) and
action (linked to object, like method) -- An RPC example has now been
added (initially, we thought it needs identifiers, eventually it turned
out to be redundant).  
CB: RESTconf does send these redundant identifiers (nested in the RPC
action), COMI now says "don't send them", so COMI work can proceed
without the identifiers.  
CB: We got an unexpected IANA early review, noting that registering a
module through IANA means not only registering a URN but also,
separately, a module name.  
CB: Next step for -core-sid, add further lines regarding the identifiers
and then ready for WG Last Call.

No questions.

## Constrained Resource Identifiers (Carsten Bormann) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides:
https://datatracker.ietf.org/meeting/117/materials/slides-117-core-href-coreconf-00.pdf

CB (p1): Reminder: "href" is the old document name from before "CRI"
name was decided on.  
CB (p1): It builds on CoAP, where we send URI in parsed form (raw
information). This is for sending parsed URIs in applications.  
CB: We tried extracting a data model of URIs, which is an interesting
undertaking. As with URIs, we have CRIs like URIs and CRI references
like URI references.  
CB: Numerical identifiers for URI-schemas are now under control. We
decided to add numbers for all of them (full coverage). WG Last Call
finished yesterday.  
CB (p2): Processing review from MT. Marco had comments on CRI vs. CRI
references, editorial nits, and empty path representation in CRIs.  
CB (p2): Empty path is the focus now. The draft has some text on how a
CRI reference in transfer form gets ingested, but no such section for
CRIs. CRIs benefit from leaving out parts of defined structure when
null. Shall we stick with natural representation, or translate this into
null? So far, the discussion has shown preferences for null, but this
needs to be settled.

LT: Interesting issue, we have the same one with SCHC -- signing a rule
needs to differentiate between empty array or null.  
CB: Okay, can you point us to the document, please?  
LT: No document yet.  
CB: No document, but?  
LT: Sometimes the tables are empty, we'll align on your choice.  
CA: No strong opinion, a normalized CoAP URI would have slash at the end
regardless (CoAP doesn't make that difference), in CRIs that are
normalized, the elision wouldn't happen on a normalized URI.  
MT: Preference for NULL in the interest of elision of trailing null.  
CB: Christian is not against but says there are limited benefits. We can
still save the byte by sending the URIs in non-normalized form. I'll
take this as a definite "maybe"; being in the shave-bytes camp, I'll
implement this by (not) sending null, and will look at how to process
that editorially.

CB: The plan is to submit version -14 after Marco's review comments have
been addressed. Late review comments will be taken into account too.

## DNS over CoAP (DoC) (Martine Lenders) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-dns-over-coap/

Presented slides:
https://datatracker.ietf.org/meeting/117/materials/slides-117-core-dns-over-coap-doc-01.pdf

ML presenting.

ML (p2): We want encrypted name resolution for the IoT, using DNS over
CoAP, sharing system resources with CoAP, and benefiting from its
fragmentation mechanism and other ones.  
ML (p3): An evaluation has been done and will be published soon. Most
interesting is that using OSCORE a lot of memory can be saved,
especially in the ROM. This will be published in ACM CoNEXT (preprint on
Arxiv).  
ML (p4): Related to DNS CBOR: This provides content format for the
application/dns-message (and dns-cbor provides a CBOR based format, see
presentation in CBOR yesterday). application/dns-message is a fallback
for when the application doesn't know the CBOR format, or the CBOR
format is larger.  
ML (p5): Since IETF 116, recommendations for root path "/" have been
added, the TTL rewriting has been explained (caching advantage), and an
implementation status section has been added.

* Clarified there is no DoC-DoH proxying (can still be combined, but at
  DNS level)
* Updated requested content-format number
* Added recommendation to NOT use unencrypted communication  
  ML (p6): Discussion ongoing around SVCB records. See Github issue
  [#22][1] for one point regarding this.  
  ML (p7): Waiting to conclude SVCB discussion. And taking any other
  feedback.

BSc: Thanks for processing the feedback carefully. Noticed discussion of
application/dns-cbor -- never heard of it before; I'm surprised, because
it was not on DNSOP. There has been history of alternative
representations, which should happen in DNSOP, especially when the
representations subset the format.  
ML: As shown in the slide, this is not meant to replace the wire-format,
but to be a concise alternative. The wire-format can still be used.  
BSc: That will be very interesting on DNSOP. Bring it there, get
feedback early.  
ML: I made an implementation during the Hackathon and realized that the
draft omits a lot of works. We will keep DNSOP in the loop.

BSc: As for the SVCB interaction, I'm happy to help provide more
assistance (but I lack context of normal CoAP use)  
ML: Ok

CB: From a getting-it-done point-of-view, it's a good thing to first do
DNS-in-CBOR in the CBOR WG (first find out what we get -- avoid
additional programming by using CBOR and -cbor-packed). We need to
complete that, then go into DNSOP.  
BSc: This isn't DNSOP or CBOR ... but especially concerning compactness,
DNS isn't usually the big wedge in the pie chart. Shaving bytes is not
likely to save >1% of total bytes.  
ML: DNS is involved a lot during the bootstrapping, so for low-power
networks, with long latencies, true it's a small part of the pie chart
but it is significant for the communication part. Especially when there
is much sleep time for devices.  
BSc: If there is an example system deployment or a measurement of an
overall system, DNSOP would love to see that.  
ML: It's not a big part of the pie chart, but can have significant
impact  
BSc: Are you saying due to the synchronization effect?  
ML: Consider a sleeping node on a LoRA network that needs to bootstrap
every time it wakes up. This needs a long wait for performing name
resolution if it exceeds the frame size.  
BSc: So it's about wake time?  
CB: Latency  
BSc: So fragmentation introduces significant effects?  
CB: The CoRE WG has worked a lot to be able to run our systems without
DNS. But it's still meaningful to enable applications that use DNS. So
this is an obvious thing to do. Constrained systems have very different
requirements than large DNS-servers that may be discussed in DNSOP.  
BSc: That's an interesting set of use cases, it would be great to bridge
that gap and help the DNS community understand the category of use
cases.

CB: Regarding the recommendation about using an empty path, is this
recommendation done in a BCP190 compatible way? Good to verify this.  
ML: It's just a recommendation.   
CB: What is the strength of this recommendation?  
ML: In DoH it has ossified.  
BSc: About 80% of deployed servers have chosen a path mentioned in an
example from the RFC. A temptation exists to start pinning that path,
but we have avoided that so far.  
ML: We could remove it again  
CA: We'll have another look at the wording. The approach can be having
value as examples as we did in the CoRE Resource Directory (just there
*is* a reason to use a particular path), and mention that using these
values can be a good idea.  
CB: We can put one example that uses a different path. We should have
language making it clear that it's the server's decision.

## Attacks on the Constrained Application Protocol (CoAP)

(Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-attacks-on-coap/

Presented slides:
https://datatracker.ietf.org/meeting/117/materials/slides-117-core-attacks-on-coap-01.pdf

CA (p2): Going over document history. Used to have -core-coap-actuators
and -core-request-tag.  
(p3) Was decided to split into 2 documents: Attacks and solutions. The
solutions became 9175.  
(p4) Even when CoAP is used with state-of-the-art security methods, and
assuming non-broken encryption, various pitfalls still exist.   
(p5-6) "Request Fragment Rearrangement"-attack. Still relevant and needs
to be solved. Going over details of the attack. In a specific scenario,
even when the currently mandates behavior is followed, this attack is
still possible.  
(p7) One solution is to mandate the use of the Request-Tag option in
even more situations. This can be a short document updating RFC 9175
(and maybe also RFC 9177).  
(p8) The impact on OSCORE is negligible, but for DTLS basically every
request would need a Request-Tag.  
(p9) Another solution is allowing servers to declare Request-Tag for
client use. This would update RFC 9175.  
(p10) A third option is to add constraints or tighten restrictions on
the use of ETag. This can be a short document updating RFC 7252 and RFC
7959 (and maybe also RFC 9175)  
(p11) The plan is to take the current examples and turn them into
minimal examples covering the problem area. Then the proposed solution
can be checked against the examples. No need to rush this through
without a solution, so we need to settle this before proceeding.

CB: We're transitioning away from GET towards FETCH that has a request
payload. CBOR can be used to frame the data, but it will probably be
smaller than the URI parameters would have been.  
CA: If block-wise had been done differently things would have been
easier. Eventually that would be shorter than the workarounds we're
adding.  
CB: Can we fix this in block-wise?  
CA: Maybe, we can change the behavior of the Block1 and Block2 option.
But it's a breaking change on Options already around and in-use.

CB: Assume that we make an elective option that the client uses as a new
alternative to Block2. One byte. The server can ACK in one byte. Would
this be breaking change?  
CA: No, but would be using up one of the remaining cheap option numbers.

CB: We may want to try to decide a fix, in addition to the work-around,
and see what solution is best.  
CA: We have never done extensive interops on RFC 7959. It's not clear
how much we would actually break. I got it wrong, and nobody spotted the
mistake doing RFC 9175, so maybe we wouldn't even break too much  
CB: The problem is that RFC 7959 was before we did FETCH. The kind of
applications changed.  
CA: Combining Block1 and Block2 back then were SOAP style requests were
used. They ended up being treated as 2nd class.

MT: The possible short new document for the first solution would
certainly update RFC 9175, but why also RFC 9177?  
CA: It's a maybe. Need to check the precise statements. If it is
sufficient for RFC 9177 to simply inherit what is in an updated version
of RFC 9175, then it would not need any update for itself.

## Key Update for OSCORE (KUDOS) (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/

Presented slides:
https://datatracker.ietf.org/meeting/117/materials/slides-117-core-draft-ietf-core-oscore-key-update-05-00.pdf

RH presenting.

RH(p2): Original parts, of which (2) has been moved out. (1) is loosely
inspired by OSCORE B.2. (2) is based on CFRG results. (3) allows peers
to get new IDs.

RH (p3): KUDOS procedure overview. Nonces are exchanged.  
RH (p4): Updates since IETF 116.  
RH (p5): More updates: SCHC affects necessity of rekeying (smaller
partial IV space requires more frequent rekeying); more detailed
explanation of ID update.

RH (p6): The Recipient-ID option could be used for other purposes, so
not limiting length in the actual option definition. The practical limit
for the use case considered in this document is OSCORE dependent anyway.

RH (p7): Split out the OSCORE ID update procedure? Benefit is that this
document would be focused on key update with KUDOS. The possibility of
this split was raised in the past, and it was agreed to postpone the
decision to then we had all the intended content written, which is the
case now.

CA: The ID updates, when done consecutively, need to keep the list of
past IDs -- until KUDOS is done. So there is some link, and in practice,
ID update will depend on KUDOS.  
RH: That link exists. But there are other ways to update the keys other
than KUDOS, like EDHOC would also give fresh master secrets for later ID
updates.

MT: more opinions on the split?  
GS: The split makes sense. The ID update is a confined functionality.
You need to keep track of identifiers in either case. That doesn't mean
that the two things can't be split.  
RH: If we do split, we'll mention that you need to keep the list of past
IDs until you do an action that does something like KUDOS.  
MT: Opinions from co-Chairs?  
CB: Haven't made up my mind. It is important to find homes, but
splitting is usually something I like to do when the people are
different. So, not sure (it doesn't hurt either). Again, not made up my
mind.  
JJ: Didn't follow this draft, no recommendations at the moment; I'm
taking action to do that.

RH (p8): x-byte in the OSCORE option. It's a place to indicate the size
of the KUDOS nonce, and flags indicating how KUDOS is run. In the
interesting of extensibility, we thought of creating a new IANA registry
where to register the assignment of bits from the x-byte, and from
possible future adjacent bytes resulting from extending the x-byte.
Opinions?

CA: I'm currently in charge of the OSCORE option bits registry: Not much
benefit in extending here as well. Leave the currently unused bits 0 and
1 as reserved, and if it turns out that we need those precisely, then a
later document can just update this one.  
CB: Are they must-be-zero or ignored?  
RH: Will check.

RH (p9): If a KUDOS message is a request, should it target a specific
KUDOS resource or any resource?  
GS: See my mail to the list also on this point. It depends on the
direction (forward or reverse flow).  
CA (on chat): Will follow up on the list about that, it would exceed the
time available here.

RH (p10): The two peers can agree to preserve observations after
completing a KUDOS execution. In that case, we have to say explicitly
what the client does with the notification number of its ongoing
observations with the server. It's wrong to reset it to 0 (that would
result in a wrong replay detection for the notification sent with
Partial IV = 0, as a false positive). It's better to set the
notification number to "uninitialized", just like when the observation
started. Thoughts/comments?  
(no comments or objections)

RH (p11): Next step is mostly processing open issues and feedback.

## OSCORE-capable Proxies (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-tiloca-core-oscore-capable-proxies/

Presented slides:
https://datatracker.ietf.org/meeting/117/materials/slides-117-core-draft-tiloca-core-oscore-capable-proxies-07-00.pdf

RH presenting

RH (p2-3): What and Why.  
RH (p4): Use cases.  
RH (p5): Stable mechanism, no need for extra signaling. Enables
authorization enforcement at the proxy before an incoming request can be
forwarded.  
RH (p6): Can go through this twice (e.g., as a server behind a reverse
proxy)

RH (p7): Recent updates.  
RH (p8): More updates. Point out that EDHOC can be run through secured
proxy connections.

RH (p9-11): More updates.  
RH (p12): Summary. Stable, and encrypting as much as possible. WG
Adoption?

MG: Chairing the Omaspecworks IPSO Working Group of the Open Mobile
Alliance. You mentioned a use case in Section 2.4 about LwM2M, with a
proxy towards external end devices.  
RH (p4): Got this as feedback from there, I am not LwM2M expert.  
MT: Input came from David Navarro. When using the LwM2M Gateway in a
setup based on CoAP, then the LwM2M Gateway is essentially acting as a
CoAP reverse-proxy between a LwM2M Server in the LwM2M domain and
external end devices hosting resources to access.  
RH: Thanks, we will try to make it more understandable.

CB (chair hat off): I think that this is necessary work that fills a
gap. In favor of adopting.  
CB (via chat, on p6): We tend to model different layers separately;
adding the nesting ("recursion") to the model of one layer can be
confusing.

GS: On the LwM2M scenario, there was a requirements phase in the device
management services enablement group, where an application server talks
to the LwM2M management server talking to a LwM2M client. The question
was, how do we enable E2E security application-server-to-client. As far
as I recall, that created that use case.  
MT (post meeting): The setup mentioned by GS is actually a different
LwM2M use case (the first one we thought about), which is discussed in
Section 2.3 of the draft.  
RH: We can also revisit with David Navarro.  
MG: The whole point is end-to-end security with OSCORE. When the LwM2M
gateway is a reverse proxy, what does that mean?  
MT: In that setup, you may want to use OSCORE with the LwM2M Gateway
within the LwM2M domain, as well as OSCORE end-to-end between the LwM2M
domain and the external end devices (through the LwM2M Gateway acting as
proxy). This is something that becomes possible with this solution.  
RH: We will come back on this.

CA (on chat): Supporting adoption.

MT: It's on CB and JJ to think of follow-up.  
CB: To get sense of the room for adoption call, who has read this
document?  
(4 showing in chat)  
CB: Objections to WGA?  
(none)  
CB: Polling for WGA: 6 raise-hand, 0 not-raise.  
(to be verified on the mailing list.)

## CoAP over GATT (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-amsuess-core-coap-over-gatt/

Presented slides:
https://datatracker.ietf.org/meeting/117/materials/slides-117-core-coap-over-gatt-01

(There are some audio problems from CA to meetecho.)

CA (p2): One issue to address was discovery.   
CA (p3): The main update is separating characteristics for inbound and
outbound traffic. The semantics of the service data field in
advertisement field has been defined.  
CA (p4): Why use .arpa? We already have 2 natural identifiers: BLE MACs
and self-described names. Using a DNS-style authority component could be
ruled out.  
CA (p5): Further exploration  
CA (p6): Possible WG adoption was raised previously. I'd like to bring
that up in a future meeting. I will continue on the URI-schema question
(main open point).

CB: This point is the reason why I put it on the agenda for the Friday's
side meeting. We also have other options available.  
CA: If we go for the custom-route (which seems best), we can take that
all the way and fully customize.

MG: Is this not a layer violation? Using a MAC address as part of a URN
or URL?  
CA: That has been defined and is in use as far as I know. As far as URLs
it makes sense in some situations. I would treat it as using an
IP-address as part of a URL.  
CA: CoAP-over-GATT is not IP-based, but intended for devices that cannot
do proper IP-communication, and rather use BLE. Similarly to CoAP over
WebSocket, there the constraint comes from the environment (web
browser). Only MAC-addresses are usable in this context.  
CA: When using BLE: I recommend using IP over BLE. But this can require
having a full IP-stack in the browser (JavaScript), or having a
different transport for CoAP.

CB (in chat): We can pick up this subject (locally valid URIs) on Friday
as well. (During the side-meeting).

## Flextime (0)

MT: Reminder: A side-meeting is planned for Friday. Check the Chair
slides and side-meeting wiki for details.

Σ 120

* * *



[1]: https://github.com/core-wg/draft-dns-over-coap/issues/22
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


