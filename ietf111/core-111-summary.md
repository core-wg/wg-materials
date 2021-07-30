# IETF 111 - Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)

# Wednesday, July 28, 2021

Meeting material: https://datatracker.ietf.org/meeting/111/session/core

Minute takers: Bill Silverajan, Christian Amsüss and Göran Selander

Jabber scribe: Marco Tiloca, Jaime Jiménez

**19:00 - 21:00 UTC**

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (10)

* WG and document status

MT: Recently published RFC 9030; 3 documents in RFC Queue; 3 in IESG processing; 4 in post-WGLC (presenting chair slides)

MT: chairs have discussed possible update to the charter. Main reasons to revise:
* For IESG when reviewing documents and for newcomers to better understand what's going on
* Better reflect what's happening in the WG.
Chairs will provide a first draft to be shared with the group.

CB: We do this when absolutely required, it's a big wheel to turn ... maybe every 10 years or so?
MT: Sure, not the first time it has happened and it's a delicate step. We'll take it carefully.

## HREF (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-core-href-00

* (p7) Resolution rules are "interesting"; it's unlikely that a regular program implements it correctly. Relative URIs are useful to make documents independent of their concrete hosting locations.
* (p8) CRI = Concise Resource Identifier. Covering what you'll find in practice.
* (p9) extending 5-tuple of URIs to 6-tuple, adding discard for relative references
* (p11) "authority anomaly" to handle URNs without anomaly, not great but a proposal
* (p12) Relax the constraints on parsed hostname (labels of fqdns or portions of addresses can go into an array), mimics how DNS servers work but can be revised if required
* (p13) We think the design is feature complete and implementations need updates to 06/publishing

TF(jabber): Use case for label splitting?
CB: Host name can also be IP address. If it's not, it's a reg-name. Having to parse the DNS name from there is a bit out of character for rest of CRI that parses everything down -- you see the components, so here you can construct DNS queries right from the components. Can't say that's a use case that absolutely requires it, more trying to make whole thing look consistent.

CA: On the topic of authority anomaly there is perhaps a better solution. I'll get back offline.
CB: Makes resolution more complicated.
CA: Resolution needs no special case, conversion does, but full discussion offline and with code.

BM(jabber): Under what circumstances does my IoT device need to care about the elements of a domain name? Isn't that the DNS's problem?

CB(jabber): That depends a lot on the document that contains the URI. This isn't all about CoAP, there may be other kinds of URI where the client needs to perform some "arithmetic" on the reg-name in the authority. s/URI/CRI/g

## Dynlink and Conditional Attributes (Bill Silverajan) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-dynlink/
* https://datatracker.ietf.org/doc/draft-ietf-core-conditional-attributes/

Presented slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-core-dynlink-and-conditional-attributes-00

Bill presenting:
* Incremental update from previous interims.
* Dynlink split into dynlink-14 and core-conditional-attributes-00, rather distinct.
* Motivated by different maturity, core-conditional-attributes almost finished.
* Text in separate repositories, issues moved accordingly.
* Mail discussion on IPR disclosure, will become correctly attributed to core-conditional-attributes
  * AS: Working on it, takes bit of time, updating as done. In general, great separation, thanks. Will provide examples.
* On dynlink, exploration due, also with CoRAL. Original dynlink draft had examples on conditional attributes; use case examples to come here.


## Transport Indication (Christian Amsüss) (15)

* https://datatracker.ietf.org/doc/draft-amsuess-core-transport-indication/

Presented slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-core-coap-protocol-indication-00

Christian presenting:
* Quick run of existing coap schemes. When coap+tcp came along the situation about the scheme changed. No perfect scheme. 
* No established terminology where to put information about CoAP transport 
* URI aliasing is an issue that still lingers today. Application needs to make a choice about advertising two URIs (coaps:, coaps+tcp:) or one as the canonical one.
* We have an easy way to use resource metadata and also very cheap costs for proxying
* A proposal thus is to treat alternative transports as proxies ([!!](https://en.wikipedia.org/wiki/Chess_annotation_symbols#!!_(Brilliant_move))). Server advertises a link to its coap+tcp version with a relation pointing to the proxy. Client may ignore or open a connection, indicating with the coap proxy option that it wants to use that uri.
* Includes scheme for avoiding static overhead due to announcing proxy
* Problematic on the DTLS side on how DTLS behaves with proxies. Author would like input from DTLS domain experts.

CB: The scheme is one variable, the IP address is another
CA: It works for both, everything identifying the connection is part of the proxy information. 
CB: That is the beauty of the proposal.
CA: Does not add traffic analysis weakness, since the original information about traffic came from the same source.
BS: Similar problems as protocol negotiation. 1st are we doing proxying or protocol indication? With proxy mechanism, same transport can be represented with different URI. Might have similar indication with coaps. 2nd, we need to understand if we have priority mechanisms that server can indicate to client.
CA: on 1st question, this is not about a new scheme for a new transport but rather to get a new transport for an existing scheme. Canonical URI (coap, coaps) will be default for most clients (proxy relation can be ignored). On 2nd, most likely client will just pick one, if not possible then server will not advertise it. Security is the tricky one, because it behaves differently between OSCORE or DTLS. 

## CoAP Attacks (John Mattsson) (10)

* https://datatracker.ietf.org/doc/draft-mattsson-core-coap-attacks/

Presented slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-core-coap-attacks-00

John Preuß Matsson presenting.
* core-attacks was initially intended as informational. We think CoRE needs to discuss amplification attacks.
* Amplification attacks got a lot of recent media attention. Amplification factor is a key metric. CoAP has a factor between 27-34. 
* Map indicating open servers -- they don't fulfill the CoAP requirements, but then again these are very soft.
* CoAP Observe increases the amplification factor as it will increase the number of responses. CoAP multicast provides another factor.
* Propose harder language and requirements to update RFC7252 and RFC7641 (MUST) as well as draft-ietf-core-groupcomm-bis.
* QUIC has strict amplification limit (3 times)
* While existing implementations cannot be fixed CoRE needs to make sure it does not get worse.
* Do you agree? Where should updated recommendations be published?

CB: Too late to be included in Echo-Request-Tag.
CB: QUIC is not a good role model as they can inflate the requests. We have to avoid overloading existing documents. Needs to be a best Current Practice (BCP). 
JM: Another question is if we can publish existing documents (conditional observe). Before BCP, we can make updates regarding amplification attacks in groupcomm-bis, conditional-attributes, etc.

CB: If we don't have specific advice we should not say anything else. 
JM: Agrees with recommendation guideline.
MT: Items 1 and 4 are already addressable in coap-attacks
CB: That is the opposite I recommend. If we smear this problem over all RFCs it will create overhead and slow work. BCP is a better option.
JM: I like the BCP option. 
GS: Why is it a problem to have the BCP and to bring it up on various drafts?
CB: Bringing it up is fine, but the solution had better be in one referable RFC/BCP

JJ: Are there well-known solutions to UDP-based DDOS amplification attacks anyways?
JM: Don't think so.

## Group Communication for CoAP (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-groupcomm-bis/

Presented slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-core-core-groupcomm-bis-00

Marco presents
* Main updates about the caching model; both the freshness and validation model
* Caching model at proxy moved to the groupcomm-proxy document
* (p5) Updates following review by John, including a starting point discussing risk for amplification attacks

CB: Even if NoSec is NOT RECOMMENDED, we will not be able to deprecate
CB: We can at this point rely on multicast not working over the Internet. But we can't deprecate NoSec, as needed before security can be established. (cf. SDES discussion in dispatch: Not being deprecated for lack of alternatives, can just guide people towards DTLS whenever applicable.)

* Question to WG about terminology for backward/forward security vs. backward/forward secrecy
* JPM: Just be careful to explain what you mean. Even security experts use terminology differently.
* CA(jabber): +1 on explicitly stating goals for forward/backward.


## Group OSCORE (Marco Tiloca) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-groupcomm/

Presented slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-core-core-oscore-groupcomm-00

Marco presents
* Update based on review from Christian (p3). For each node, the GM remembers the GID used in the group when a node joined the group (that node's "Birth Gid"). This allows the GM to securely re-assign a same GID to the OSCORE group.
* From Ben (p4): question about security of using the same public identity key for both key exchange and signature. Now precise proof, making use of included Sender/Recipient public key in the key derivation of pairwise keys.
* Alternative formats to represent public keys (p6): CWT, UCCS, X.509, C509
* Further content in the security context (p7) and external AAD (p8); Group manager public key added to prevent against group cloning attack.
* Group privacy in group mode is obtained by additionally separately encrypting the signature (p9), using a streamcipher construction (XOR with keystream)
* In group mode, admit encryption-only algorithms. Complemented by strict rekeying policy for nodes leaving the group.

GS: Plans for intreop testing? Which version should people test?
MT: RH updating, CA interested; after summer.


## Combining EDHOC with OSCORE (Rikard Höglund) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-edhoc/

Presented slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-core-combining-edhoc-and-oscore-00

RH presenting.
* Combined OSCORE and EDHOC signaled with the new CoAP EDHOC option, requesting number 21.
* Rationale for changed number: Still has flags set, and delta <= 12 to OSCORE option (which is sufficient for 1byte option b/c OSCORE option will be present when this is)
* Adaptations depending on changes in EDHOC. Mapping between EDHOC Connection identifiers and OSCORE Sender/Recipient IDs split between this document and the EDHOC document in LAKE.
* The document scope can be broadened to be about "profiling the use of EDHOC for CoAP and OSCORE". Besides the combined request and converting from OSCORE IDs to EDHOC IDs (which is needed in this document), it can be about using Christian's separate proposal on URI compression, and  covering web linking (rt=edhoc, target attributes aligned with the EDHOC applicability statement ...).

GS: Thanks for producing content. In which draft it ends up is not critical, defined by charter.
MV: According to its charter, LAKE needs to produce a specification for key establishment of OSCORE. Optimizations and additional technical solutions can be in this draft. Thanks.
MT: Resource type had better be defined in LAKE draft, when a media-type is also defined.
MV: Let's bring it up in the LAKE WG.

CB: What is "Christian's separate proposal"
CA (in Jabber): That was about expressing Uri-Path: .well-known/core in a single option
CB: send pointer in chat
CA: single one-byte; no draft yet but will called common-option-compression, was presented in the 2021-05-12 core interim.
Slides at: https://datatracker.ietf.org/meeting/interim-2021-core-05/materials/slides-interim-2021-core-05-sessa-core-option-for-well-known-resources-00

## Key Update for OSCORE (Rikard Höglund) (10)

* https://datatracker.ietf.org/doc/draft-hoeglund-core-oscore-key-limits/

Presented slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-core-key-update-for-oscore-00

Rikard presenting
* Revised key usage limits (following input from John); how to handle them; new efficient key update procedure for OSCORE
* (p5) CCM_8 is the most problematic; used to look at "good enough" values.
* (p6) New key update method. Improvements over the method in Appendix B2 of OSCORE.
CA (jabber): mhm, gotta read that update method (didn't get that far), the properties list sounds delicious
GS (jabber): Looks good!
JM (jabber): I agree. looks good.

GS: This does both client and server initiated rekeying?
RH: Yes, both can take initiative, example shows client-initiated.
GH: How to handle the Appendix B2 method? Deprecate it?
RH: Have list of possible rekeying list, including ACE profile. Would make sense to deprecate existing Appendix B2.
GH: You still have to derive one intermediary security context ... can we avoid even that? (Still better than Appendix B2 that derives two intermediary contexts).
CA: Can probably do this in some situations but not all; may not be worth the additional code paths.

## OSCORE-capable Proxies (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-tiloca-core-oscore-capable-proxies/

Slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-core-oscore-capable-proxies-00

Skipped for time reasons, will bring to an interim meeting.

## Flextime (10)

## AOB

MT: Biweekly interim meetings will resume on September 15. See you there.

---

*[MT]: Marco Tiloca
*[JJ]: Jaime Jiménez
*[GS]: Göran Selander
*[JM]: John Mattsson
*[FP]: Francesca Palombini
*[CG]: Cenk Gündogan
*[CB]: Carsten Bormann
*[CA]: Christian Amsüss
*[KH]: Klaus Hartke
*[BS]: Bill Silverajan
*[NW]: Niklas Widell
*[IP]: Ivaylo Petrov
*[MR]: Michael Richardson
*[BL]: Barry Leiba
*[AK]: Ari Keränen
*[JS]: Jon Shallow
*[MB]: Mohamed Boucadair
*[AS]: Alan Soloway
*[BL]: Barry Leiba
*[MG]: Matthew Gillmore
*[ED]: Esko Dijk
*[HB]: Henk Birkholz
*[MG]: Matthew Gillmore
*[DN]: David Navarro
*[CG]: Carles Gomez
*[MK]: Markku Kojo
*[HT]: Hannes Tschofenig
*[BK]: Benjamin Kaduk
*[AM]: Alexey Melnikov
*[RH]: Rikard Höglund
*[BM]: Brendan Moran
*[MV]: Mališa Vučinić
