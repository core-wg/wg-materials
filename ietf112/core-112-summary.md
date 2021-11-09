
# IETF 112 - Agenda for Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)

Please note:

Jabber: xmpp:core@jabber.ietf.org?join
  * For the virtual microphone queue, you may want to say "help q"

Date and time: Monday, 8th of November 2021, 16:00 - 18:00 UTC

Notes: https://codimd.ietf.org/notes-ietf-112-core

Meetecho video stream: https://meetings.conf.meetecho.com/ietf112/?group=core&short=&item=1

Audio stream: http://mp3.conf.meetecho.com/ietf112/core/1.m3u

Minute takers: Christian Amsüss, Göran Selander, chairs (helping)

Jabber scribe: Marco Tiloca

# Monday, November 8, 2021

16:00 - 18:00 UTC

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (10)

* WG and document status

Presented slides: https://datatracker.ietf.org/meeting/112/materials/slides-112-core-chairs-slides-00.pdf

MT: Doing introductions, agenda bashing.

Status on published and publishable documents (p7ff). RFC 9100 published. Now 4 documents in the Editor's queue, 2 in IESG review, 3 in post-WGLC.

Outlook on milestones to be updated and next interim meetings.

CB: CA brought CoRE applications meetings, said "this week is full". But worth having an interim before 1 month's time?
MT: Might work, considering December 1st, needs syncing.
JJ: On pubsub and problem-details progress, want to have work meeting also with co-authors before an interim.
CB: OK; don't really need heft of "interim", can just be scheduled meeting.

CB: A few interim meetings ago we decided not to recharter. Now there's rumors the WG will be concluded...
MT: New to me.
JJ: Same.

MT: Interim planning made, one remaining this year on December 8, a series resumes in January alternating with CBOR (p11).

## HREF (= CRI) (Carsten Bormann) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides: https://datatracker.ietf.org/meeting/112/materials/slides-112-core-cri-draft-ietf-core-href-00

CB presenting, first 11 slides are repetition. (href is name of draft, CRI the term we started using.)

CB: Orthogonality (p3-4), implementation trouble with URIs (p5). URI data model never specified, done here (p8).

CB: Feature complete in -08 for the subset of URIs that CoAP supports; test vectors being updated and now available as a PR. By end of year, should have several interoperable implementations and finalized test vectors.
Then, reviews and WGLC.

CB: Open questions: CURIEs (which concatenate, p13)? Works with Packed CBOR for some situations but not all. No nice (!) idea how to fix it.

CB: Second question: Percent encoded text (p14), not admitted in CoAP except for the exact delimiter of the URI component in question. The W3C DIDs worked as motivation to somehow allow that in a CRI to not exclude altogether percent-encoded characters. Reasonable for CoAP.
CA (on chat): Fully supporting the "This is easier on the spec than on the implementation side" statement ...
CB: Not picking it up would mean we don't have a way to express all these cases of percent-encoded URIs. Happy we have a proposal, but not entirely convinced myself. If we want to support it, this is the simplest way.

CA: Alternative is to admit URIs where CRIs are possible. May be the easiest thing to do.
CB: Then need to support both URI and CRI.
CA: Processing out of the encoded form might be easiest by converting to a URI in the first place.
HB (on chat): +1 on the DID support effort.
HB: Hope from supporting majority of it might contain the weirdness, and then the CRI could be guidance on how you'd do it, and thus ease the wilderness out there. Effort of trying this is warranted; you fall back to URI if nothing fits, but maybe we can make that go away over time.
CB: The idea was to document what URIs are not supported. Still some weird URI is not supported even with the % handling described here.

## CoRAL (Christian Amsüss) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-coral/

Presented slides: https://datatracker.ietf.org/meeting/112/materials/slides-112-core-coral-00.pdf

CA presenting: First some repetition. Similar to CRI being constrained format for URIs, CoRAL as data model and language is constrained format for metadata.

CA: there are a number of documents as users of CoRAL, e.g. pub-sub and problem-details in CoRE, the Group Manager for Group OSCORE in ACE, plus more related to discovery. (see also links in slides)

CA: (p4,p5) In CoRAL, advantages compared to RDC, link format and CBOR, although it can be used with them. Similar information to what is in link format is expressed in CBOR. Semantic information instead of ad-hoc attributes. Reuse of terminology, no need to define from scratch (eg. pubsub terminology mixed with vendor extension in one document). Compact representation of predicates. CoRAL can be mapped to RDF, RFC 6690. Literals inherited from CBOR.

CA: Status of work (p6). Advanced status for information model, interaction model and dictionary setup, for which CBOR Packed is used with variations under discussion. Initial setup done using query of content format, but not clear how else to set up dictonary. Text serialization removed. Easier to use CBOR diagnostic notation using serialization with EDN.

CA: Next steps: coordinate with users, get examples to try binary serialization against, get input what needs to be in an initial version.

AK (on chat): Good stuff, thanks!

## Group Communication for CoAP (Esko Dijk) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-groupcomm-bis/
    Ready for WGLC ?

Presented slides: https://datatracker.ietf.org/meeting/112/materials/slides-112-core-group-communication-for-coap-00

ED presenting.

ED: Repetition. Successor of RFC 7390. Updates RFC 7252, 7641, adds security.
ED: Update in -05: Removal of Multi-ETag, using ETag. Single section collecting all that is updated/obsoleted w.r.t. other RFCs. Naming of application group can be done in different ways.
See issue [#28](https://github.com/core-wg/groupcomm-bis/issues/28), could have different places in URI (p4).
Clarified in current version, but still needs WG confirmation.

ED: More updates (p5). Different kinds of group discovery. See issue [#29](https://github.com/core-wg/groupcomm-bis/issues/29)

ED: Unsecured groupcomm now NOT RECOMMENDED (normative), with stronger discouragement on using it.
CB: On NOT RECOMMENDED: Does this mean we deprecate multicast for discovery? ED: Was mentioned as one case where it is still needed.
MT: Correct; "NOT RECOMMENDED", if you use it you better have good reasons and done a good analysis, discovery is one case.
CB: Discovery needs to be made more precise, eg "If you use it that way, ensure response is not much larger than request"; need to position ourselves w/rt that usage, it was quite popular when this WG began.
MT: Following John's review we are now discussing more details of amplification attacks and how this can be limited.
CB: ok.

ED: ... and editorial and terminology enhancements.

ED back to #29: Non-RD discovery, both of groups and group members.
JJ: Clarification, I'm missing examples, could you please add? Like as request-response exchange.
ED: They are now as actual text, yes would have them more explicit.

ED: Next steps: More reviews. Can we close the issues? More reviews or the entire document? Two committments from IETF 111. CA already reviewed.

FP: Will not have time to look at it until after WGLC.
CA (chat): can have another look.

## Group OSCORE (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-groupcomm/
    Ready for 2nd WGLC ?

Presented slides: https://datatracker.ietf.org/meeting/112/materials/slides-112-core-group-oscore-00.pdf

MT presenting.

MT: Updates (p2f). Previous version was a major update, less updates now. Main update: MTI now following EDHOC. Non-constrained endpoints must support both signature algorithms EdDSA and ECDSA as well as both key agreement curves X25519 and P-256. Constrained endpoints should support at least one signature algorithm and one or the other key agreement curve. It seems reasonable for time being while hardware support is limited.

MT: Updated implementation for Californium. Ready for 2nd WGLC. In parallel, test vectors. In separate informational draft? No urgent to decide, just raising the point for now.
GS: How does this align with groupcomm-bis? Will they have separate WGLCs?
MT: Content-wise they are aligned and both mature. Easier if separate WGLCs; IESG should get them in one go as also easier.
FP: Yes, I'll move them on together when they reach me.

JJ: Can start second WGLC on the mailing list this week. How long would test vectors take (estimation)?
MT: Full set will take a while, preliminary can be there by end of year. I see them as supplementary material and not part of this document; let's see later how to best release them.
JJ: Could we get estimation of who read the latest major update?
JJ: Who read one of the latest 3 versions?
Chat: Christian Amsüss, Rikard Höglund.
JJ: For 2nd WGLC we'd need more eyes.
ED (chat): pending.
John Mattsson: +1
Esko Dijk +1
Rikard Höglund +1
Thomas Fossati +1

## Key Update for OSCORE = KUDOS (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-hoeglund-core-oscore-key-limits/
    Ready for WG adoption ?

Presented slides: https://datatracker.ietf.org/meeting/112/materials/slides-112-core-key-update-for-oscore-kudos-00.pdf

RH presenting.

RH: Recap (p2). Document in two parts: i) studies limits in key usage and defines thresholds; and ii) defining new method to rekey ("KUDOS") inspired by OSCORE B.2 achieving Perfect Forward Secrecy and additional benefits.

RH: Explaining setting of cfrg-aead-limits.

RH: Updates: Explicit size limit (presented the 'l' limit value also not in cipher blocks but actual bytes). Setting 'q', 'v' and 'l' values and calculating probabilities, using limit guidelines set in cfrg draft.
RH: So, should we increase the 'l' value to consider?
CA: Can we increase l to 2^11 to ensure we can fit in a 1024 byte payload plus headers?
CB: Is that in bytes or cipher blocks?
RH: Cipher blocks
CA: Then scratch that.

RH: AES_128_CCM_8 needs special treatment, because that's reaching the limits.
RH: Is it ideal to aim for 2^-50 (quoting from the cfrg draft)? Still an open point.

RH: KUDOS (p6f). No change in KID Context, compatible with EDHOC. Extends OSCORE option with ID-Detail option.
RH: Simplifications applied thus reducing overhead on the wire(p7).

RH: Observations stopped after rekeying; price for possibly keeping is jumping forward with larger PIV and sequence numbers (or even more complex alternatives).
CB: If observations going away, rekeying event is visible on application layer. Is that what we should be doing?
RH: It's open. 
CB: How bad is stepping the PIV?
RH: We'll have to define some more. Pairs have to agree on what to do. Should be stated in text. Other possible solutions?
CA (chat): "visible on application" ... depends where application starts. REST-engine-level would just reestablish.
CA on chat: BTW, I think the observe business can be much easier: as long as it wants the observation alive, just skip over that sequence numbers when generating new requests. (non-mic, just for Rikard and further discussion)

GS: If you need to update keys for other reasons, is your proposal that that shouldn't be visible either? Should it be controlled, or it just happens without notice?
CB: Application should have way to ask security component to rekey, but what's in here now means that this involves the application.
CA: The application might ask a fresh notification, and the stack would poll or observe and just re-establish observations if they go away for good reasons.
RH: Material for further discussion.

RH: 6TiSCH case added (p9); keeps pledge identifier in place at KID Context.

RH: General updates (p10). Next steps (p11). Document foundation and key update are stable. Ready to adopt as WG document?

JJ: Adoption time scale ... who read?
Chat: Göran Selander, Christian Amsüss, John Mattsson
JJ: Asking WG adoption show-of-hands. 9 raised, 1 not-raised, out of 28 total participants; to be confirmed on mailing list.

![](https://notes.ietf.org/uploads/upload_c6b6abe45cce2805b1436535d3243cc7.png)

## Cacheable OSCORE (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-amsuess-core-cachable-oscore/

Presented slides: https://datatracker.ietf.org/meeting/112/materials/slides-112-core-cacheable-oscore-00.pdf

CA presenting. 

CA: Basic mechanics is coming in place. On one hand, what does this do in terms of request-response binding, when requests do not have source authentication? On the other hand, what do we need for cacheability of OSCORE-protected responses? It's actually two topics, now split in v -03.

CA: A cache match does not happen in normal OSCORE since keys are shared only with one client. In group OSCORE, there is a shared key which can allow matches for multiple clients, that here can all act as the Deterministic Client producing Deterministic Requests that produce a cache hit.

CA: Alternatives for how a response can be made usable and bound to a request, even without trusting the client and without source authentication of the requests (p6). This can be: the response embedding the full request as a class I/E option; the response embedding the hash of the request as a class I/E option (as this document does), but the hash can be elided as the client is able to rebuild it; the request embedded in the OSCORE external_aad.

CA: Cacheable OSCORE now split in two parts that can be seen as self-standing topics: 1. binding of response to a request w/o source authentication (also w/o freshness). 2. deterministic requests as particular requests without source authentication to re-enable cache-entries and requiring to rebuild the req-resp binding as above, avoiding reuse and limited request privacy.

CA: is the split good and good to have here? I think so.
GS: No strong opinion on this point; I am happy that cacheability is possible, and would prioritize to make that feature easy to use where it is most useful.

## OSCORE-capable Proxies (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-tiloca-core-oscore-capable-proxies/

Presented slides: https://datatracker.ietf.org/meeting/112/materials/slides-112-core-oscore-capable-proxies-00.pdf

MT presenting.

MT recap(p2). OSCORE used between Client and Proxy, plus possibly also between Client and Server end-to-end. Use cases: Group comm proxy needing to identify a client before forwarding to a group of servers over multicast;  CoAP observe using multicast notifications and Group OSCORE end-to-end; OSCORE used between LwM2M Client and an external application server, as well as between LwM2M client and server.

MT: Updating OSCORE to define also intermediaries as possible OSCORE endpoints, plus enabling double-or-more OSCORE (nested OSCORE). Updating OSCORE but also applicable to group OSCORE.

MT: Processed feedback to v -00, simplified message processing (algorithm now the same for all endpoints in the chain), added use cases. Chain of proxies (hiding position of the client in the network) a la onion OSCORE in there but would need much more work.

MT: Main deviation from OSCORE RFC: Endpoint shouldn't panic any more when finding OSCORE option after decryption. Also, some options defined as class U can be encrypted, e.g., the OSCORE option and proxy-related options.

MT: Things are interesting when processing an incoming request (p7). Just 3 cases. Decrypting and strip an OSCORE layer until either forwarding to the next hop or delivering to own application. Error handling also included in the draft. Protection of response is just applying the OSCORE layers stripped out when unprotecting the request but in reverse order.

MT: Next steps are examples, cacheability (likely just following core-cachable-oscore), elaborate on "onion OSCORE", use of (an adaptation of) RFC 8824 to help minimize overhead during nested OSCORE through CoAP header compression.

ED (on chat): Name should involve Matryoshka ;-)
GS, CB (on chat): +1
ED: Would just need a good acronym built from that.
CB (on chat): Nested OSCORE Matrushka = NOM, nested NOMNOM
CA (on chat): +1

## Performance Measurement Option (Giuseppe Fioccola) (10)

* https://datatracker.ietf.org/doc/draft-fz-core-coap-pm/

Presented slides: https://datatracker.ietf.org/meeting/112/materials/slides-112-core-constrained-application-protocol-performance-measurement-option-draft-fz-core-coap-pm-00-00

GF presenting.

GF: New work on CoAP performance measurements. (p2) With non-confirmable messages there is no easy way to do measurements of Round Trip Time and packet loss.
GF: Looked for simplified mechanism.
GF: EFM mechanisms just adopted in IPPM (spin bit, square bit). 
GF: Proposed new option for performanced measurement, spin and square.

GF: Benefits (p5). No need for IDs/sequence numbers to measure RTT.
CA (on chat): +1 on not going into detail; need to understand use case first

GF: on-path observer (probe or gateway or proxy) to adjust protocol parameters.

CB (on chat): Could you hide the bits in the MID? This will be a ... echoed

CA: Which exact devices are involved here and interested in using this? I think you may want to use this just hop-by-hop, and then discussion is way easier and can go to parts like the MIDs Carsten mentioned.
GF: Several ways. Can be applicable to session. Proxy can be client in terms of this document. Based on comments, would add usage scenarios to next revision (with and without proxy).

## Flextime (10)

None had. The previous and last presentation ended on top of the hour.

Σ 120


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
