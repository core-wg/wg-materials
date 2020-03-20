# CoRE WG - Summary IETF106

(Constrained RESTful Environments WG, Draft Minutes 0.1)

The core WG held two meetings at IETF 106 in Singapore, both of which are summarized in these minutes.

Videos:
: Wednesday (2019-11-20, 2 h): <https://youtu.be/YIHoiHhz2Ys?t=130>
: Friday (2019-11-22, 1.5 h): <https://youtu.be/OkYDGZz0fGY?t=222>

Slides: <https://datatracker.ietf.org/meeting/106/materials/slides-106-core-consolidated-slides>

Raw minutes:
<https://etherpad.ietf.org/p/notes-ietf-106-core>

Thanks to the note takers Niklas and Ivaylo!

## Working Group Document Status

In RFC-Editor’s Queue:

* draft-ietf-core-multipart-ct-04

In IESG processing:

* draft-ietf-core-hop-limit-07: Alexey explained that the
  "Approved-announcement to be sent::Point Raised - writeup needed"
  status is due to the open question why this cannot be mapped to
  HTTP.  Carsten proposed defining a generic HTTP header field for
  "tunneling" CoAP options, outside this document. (With that, the
  draft has since transitioned to the RFC-Editor's Queue on
  2019-11-26.)

* draft-ietf-core-resource-directory-23: In AD Evaluation, substatus
  "Revised I-D Needed".  As was further discussed in the Friday
  meeting, the main open point is the question whether the reference
  to the much less well-advanced RD-DNS-SD draft needs to be
  normative.  The outcome of the discussion was that the
  resource-directory draft should simply define the small number of
  DNS-SD service types that are needed for resource directory
  discovery, with details to be taken to the list.

* draft-ietf-core-senml-more-units-03: Status "Waiting for Writeup".
  Some need for clarification that the secondary registry SHOULD be
  implemented but the derived units still SHOULD NOT be used, and for
  the designated expert instructions.

  Concerns had been raised about opening up the second registry for
  derived units, making it harder for a SenML application to find out
  whether a unit encountered was actually of interest to it.
  Discussion in the first session resulted in the tentative proposal
  to mark secondary units with an asterisk (as in "*km/h", as opposed
  to unmarked "m/s").  Further discussion in the second session made
  clear that while this makes the use of secondary units stand out, it
  does not really improve the situation of SenML applications that
  want to quickly discard measurements for units they do not care
  about, unless they track the contents of the two registries, which
  would make the asterisks redundant.  There also was some feedback
  the asterisks would make the adoption of the SenML units registry by
  other SDOs more difficult.  The in-room consensus not to go for the
  asterisks, but to include more explanatory text about implementation
  strategies, needs to confirmed on the mailing list.  Also, it was
  brought up that proactively registering remaining SI-based units in
  table 1 now might improve the stability of that table further on;
  this should be done in an independent effort (exercising the
  registry).

* draft-ietf-core-senml-etch-05: IESG Evaluation::Revised I-D Needed.
  Latest changes are on github, a few comments still to be addressed.
  In particular, there may be a need to select for units.  Also, a
  decision needs to be made what happens if the selector in a patch
  record matches multiple records (proposal: error); need to double
  check idempotency, too.

In Post-WGLC processing:

* draft-ietf-core-stateless-03: Authors to update draft from WGLC
  input.  (Done as of 2019-12-06 in draft-ietf-core-stateless-04.)
* draft-ietf-core-echo-request-tag-08: Update made the deadline, now
  needs write-up from shepherd.

Almost at WGLC:

* draft-ietf-core-dev-urn-03: (expired), an ABNF problem needs to be
  fixed and the draft resubmitted before it can go directly into WG
  last-call.

In WG adoption call:

* draft-bormann-core-corr-clar-00: WG adoption call finished with only
  one item of feedback; in-room consensus was good before that; what
  should we do now?

* draft-jarvinen-core-fasor-02: (adoption call runs until 2019-12-03)

## CoRECONF cluster

* draft-ietf-core-yang-cbor-11, draft-ietf-core-yang-library-00,
  draft-ietf-core-comi-08, draft-ietf-core-sid-07: Now ready for WGLC,
  to be sent to CoRE as well as netconf/netmod (with the discussion to
  happen on CoRE).  (One comment on the numeric range of SIDs still to
  be taken care of.)

## Group communication cluster

* draft-ietf-core-oscore-groupcomm-06: Ongoing.  Moving to COSE-bis
  registries, discussing countersignature algorithms, details on key
  rollover.  After this round, might be ready for WGLC; previous
  reviewers please vouch for that.  Might need 7390bis (below) as a
  normative reference.

* draft-tiloca-core-oscore-discovery-04: Reviewer volunteers are asked
  to provide reviews now.  Also: The usual discussion of needing a
  registry for link target attributes (which is now possible according
  to the updated RFC 8288) ensued; Klaus might have a draft soon.

* draft-tiloca-core-observe-multicast-notifications-01: New work first
  presented in Montreal; was revised with a simpler approach, which is
  could be summarized as the server redirecting a client to a
  multicast group by supplying a phantom request for that; this allows
  the server to choose a group and a token.  In-room support, but
  probably needs more work, e.g., in congestion control.  Need more
  reviewers now to make progress on this as a WG.

* draft-dijk-core-groupcomm-bis-02: intended normative successor of
  (and obsoleting) RFC 7390 (dropping the experimental RESTful
  protocol that has not been picked up), with some initial reviews
  already addressed.  In-room consensus to adopt as a WG document; to
  be confirmed on the mailing list.  Then, before WGLC, we should
  ascertain implementation support for the whole breadth of the draft.

## SenML cluster

(See also documents in IESG, above.)

* draft-ietf-core-senml-data-ct-01: updated with feedback from
  IETF105, still grappling with potential conflicts between "ct" and
  "ct_".

* draft-keranen-core-senml-base-prefix-00 (ipr #3662): need to look
  closer at use cases and find out how this is not a practical problem
  in LWM2M usage so far.  This draft could be combined with Hannes'
  draft; more analysis is needed.

## CoRE Applications

Klaus led the group through a review of results from Tuesday's side
meeting.  As a result, the following new draft was published already:

* draft-fossati-core-coap-problem-00: The draft uses custom CBOR, but
  the information could also be mapped to CoRAL.  More discussion
  needed.

With respect code point management (numeric identifiers), we might
want to learn from the CoRECONF SID approach for other code point
spaces, too.  Also, some more thinking is needed about error responses
that encode application results; some of this has been added in
RFC 8132 (FETCH/PATCH): 4.09 ("conflict", i.e., application would
reach unwanted state), 4.22 (unprocessable entity); do we want to add
more?

* draft-ietf-core-coral-01, draft-ietf-core-href-01: small update was
  needed so far.

* draft-ietf-core-coap-pubsub-09: Proposal for update was discussed in
  Montreal; feature parity with existing -09 not yet reached.
  draft-hartke-t2trg-coral-pubsub-00 explores how CoRAL might be used
  for enabling publish/subscribe-style communication over CoAP.

Various other T2TRG drafts make use of CoRAL, e.g.,
draft-hartke-t2trg-coral-reef-03 and draft-hartke-t2trg-data-hub-05,
and should be considered in this context.  It also turns out that
draft-tiloca-ace-oscore-gm-admin-01 is very similar in structure to
pubsub.

Carsten presented a proposed timeline for completing CoRAL: stable at
IETF107, implemented and validated at IETF108, WGLC mid-2020.  Klaus
agreed that a lot of validation has already happened.  Also, a
question came up whether there should be a JSON serialization of CoRAL
(there are two proposals for that now — do we need both?).

## Flextime

Francesca brought up the integration of EDHOC
(draft-selander-lake-edhoc-00) and OSCORE (RFC 8613) — can the third
EDHOC message (maybe 20 bytes) be integrated with the first OSCORE
message?  Two proposals have been made (by Mališa and Jim); this needs
discussion.  Francesca brought up a third approach, where both the
EDHOC and the OSCORE messages are included in the payload.  Christian
pointed out that this would be combining two different REST requests,
and Carsten suggested thinking about piggybacking in a more general
sense.

Carsten promised to come up with a schedule for virtual interim WG
meetings that is a bit lighter than the two-week cadence we had before
IETF106.



Core@IETF106
Constrained RESTful Environments (CoRE) WG

Chairs: carsten, jaime
Minute Takers: niklas, Ivaylo
Jabber: francesca


## TUESDAY, November 19, 2019 17:00-19:00 Butterworth
(conflicts with anima, secdispatch)
Please note: Side meeting on CoRE applications


## WEDNESDAY, November 20, 2019 1000-1200 Sophia (conflicts with raw, teep, quic)

Intro (10)
WG and document status

CB: Intro, agenda bash
Key topics today are coreconf, groupcomm and senml. 
ON Friday, Core applications will be main topic. 
RD is in AD evaluation right now and might come on Friday.

RFC-Editor’s Queue: draft-ietf-core-multipart-ct-04
In IESG processing:
draft-ietf-core-hop-limit-07: Approved-announcement to be sent::Point Raised - writeup needed
CB: I am not sure what is the status of that
Aleksey: Why this cannot be mapped to http...
CB: We have a new option... We could have a generic CoAP option for HTTP headers.
draft-ietf-core-resource-directory-23: AD Evaluation::Revised I-D Needed
(discuss under SenML cluster)
draft-ietf-core-senml-etch-05: IESG Evaluation::Revised I-D Needed
draft-ietf-core-senml-more-units-03: Waiting for Writeup
In Post-WGLC processing:
draft-ietf-core-stateless-03 authors to update
draft-ietf-core-echo-request-tag-08 made the deadline, wait for shepard to push through. 
Quick recap of related work, pointers
Fasor draft in WG adoption call


CoRECONF cluster (15)
draft-ietf-core-yang-cbor-11
draft-ietf-core-yang-library-00 (not updated)
draft-ietf-core-comi-08
draft-ietf-core-sid-07 (not updated)

Objectives:
check for any netconf/netmod/yot input that needs to be processed now
clear any remaining hurdles to WGLC (with netconf/netmod involved)
Updates: (Ivaylo) 
document core-sid are stable, no changes. SID generation tool has been merged with pyang. core-sid ready for WGLC.
Rob Wilson : should be unsigned 63bit (not 64). Ivaylo: will address
CB: there are implementations, looks good. will send out to relevant groups for WGLC (NETMOD, NETCONF).
Carsten: Poll on who cares about YANG (4 people)?
yang-cbor, a number of changes, some editorial notes and emproved examples. Should be ready for WGLC
core-yang-library: no changes (other than doc name). Ready for WGLC. 
core-comi: refer to OSCORE as potential security mechanism. Should be ready for WGLC. 


Group comm (MT, on-site)
draft-ietf-core-oscore-groupcomm-06 (10)
Discuss updates (addressed review, encoding and message processing)
ask for moving to WGLC
Marco: Ludwig provided input. Group ID must be unique. Improved encoding of external_aad. Clarifications on group rekeying. 
Ongoing: need to deide on couternsign algorithm (needs feedback). Neds to address corner case for rekeying. Define two new IANA registires (but move them to COSE-bis)
Next steps: incorporate comments from Jim, migrate IANA regs after that move to WGLC. 
No-one has reviewed this version, Carsten asks for reviews (existing reviews please review again)
Carsten: whihc normative references are needed, Marco: only what now is draft-dijk-core-groupcomm-bis that obsoletes RFC 7390. (2 people in the room and 2 in jabber)

draft-tiloca-core-oscore-discovery-04 (10)
Discuss updates (rationale, group name, target attributes)
solicit reviews
Marco: non-normative doc, covers how to join groups. Proposes to use the RD (find OSCORE group and join it). Life-cycle flow covering ace and core, diagram in slides (ace-key-groupcomm-oscore). 
Updates: clarified rationale (find links to find groups; use the RD to find the links). Introduces group-membership resource (name change). Adds "sec-gp" parameter (plain name for OSCORE group. Defines target attributes fror COSE "cs-alg". Adds examples. 
Open questions: Add optional target attribute w URI of the Authorization server. Registration of link target attributes (needs new registry, will happen in a work-in-progress core-parameters document).
Carsten: we can define such a registry) (changes on rfc8288 2.1.1.2 (?) allow for that)
Carsten (interpreting klaus): URIs and target link attr are different and used for different things. 
Marco: I will check that with Klaus.
Way forward: those who committed in 104 to provide reviews should do it (Jim, Carsten, Klaus, Bill). 


draft-tiloca-core-observe-multicast-notifications-01 (15)
Discuss updates (new simplified solution design)
ask for reviews
Marco: multiple clients observing same resource on server. Practical use case e.g., pub-sub (better performance; subscribers remain simple clients only). 
Key contribution is to describe how multicast responses can work, including management and enforcement of common token space. Assumption is that the clients have discovered the resources, server is part of right OSCORE group. 
New design after Montreal, discussed in design WS in October and at a CoRE interim. The server starts the group observation for a resource, on behalf of the group of clients. This is done through a "phantom observation request" that the server sends to itself as if sent from the multicast IP of the group. (... description of server & client side process ...). The server redirects clients to take part in the group observation via an error message providing required information and the phantom request itself. Following notifications are over multicast, and in fact matching with the phantom request. Security is about protecting the phantom request w group oscore, all multicast notifications are also protected accordingly, using the external_aad of the phantom request. In summary, the server is entrusted by the group to manage the token space. All notifications are securely bound to phantom request. Much improved performance. 
Marco: Reviewers needed.
Carsten: this is clever stuff, but how do you do congestion control? But this is a good proposal
Christian: one more feature is that the error response can be cached by pub-server. 
Marco: also much simpler than the previous approach: no new CoAP options needed, no range of token values to reserve. 
Carsten: Who is interested in reviewing (no hands, Jim plans to). Not enough to make progress.
Marco: it would be good to have someone reviewing from the pub-sub people. 

draft-dijk-core-groupcomm-bis-02 (15)
Presented by Marco on behalf of Esko
Discuss updates (addressed reviews and closed TBDs)
ask for WG adoption
Marco: obsoletes 7390 except for the experimental RESTful protocol. Intended to be standard reference for implementations (e.g., Eclipse Californium). 
Carsten: I am wondering about this obsolete except protocol. Generally experiments can last forever, but we should have a time when we say this experiment was successful or not. It seems that this experiment was not successful. It seems for me that this experiment has concluded and it was not successful. We can obsolete 7390 and simplify this.
Marco: Just removing the exceptions. OK
Updates: updates with reviewer's comments, moved over parts from 7390, closed issues. Document is reaonably complete. Clarified CoAP request/response model. Added security considerations. This draft updates 7641 (mulicast GET + observe option), add unreliable request transport and clarified .... Removed update to block-transfer (RFC 7959), this can possibly go in a separate document if there is interest.  
Next steps: handle review comments, test in CoAP implementations . propose adoption by CoRE WG.
Carsten: Who has read? (4 hands)
Carsten: it has always been an intent to revisit this, it would be good to get this going, but requires reviews. 
Francesca: as Chair of Security Dispatch (secdispatch) supports adoption
Carsten: You are talking about implementation - how far is it.
Marco: Group OSCORE already works.
Carsten: How much of the draft is there?
Jim: Full multicast implementation for OSCORE
Carsten: Does this cover all of the draft? That should be something we check before going to WGLC.
(in favour of adoption: Francesca, Jim, Christian, noone against).
Action item: Chairs to take adoption to the list.

SenML (AK, on-site)
Carsten: will look at units at later point. 
Discuss IESG processing (20):
draft-ietf-core-senml-etch-05: IESG Evaluation::Revised I-D Needed
Ari: draft in IESG review, no update this time. Good comments have been received from IESG and others. Updates w clarifications. 
Outstanding issues: Needs selector for units (today only name and time), proposal to add unit as well.
Carsten: This means you can never update the unit?
Ari: correct. You can do more elaborate w JSON patch. 
 Patch record order matters. Multi-record patch (currently selector match multiple record is error - if there is a strong case for matching many then flag: 
Carsten: are we sure that this is idempotent?
Ari: should be. But need to double check. 
Carsten: very easy to mess up this. 
Ari: no disagreement, will implement proposals.

draft-ietf-core-senml-more-units-03: Waiting for Writeup
More Units in SenML: 
Today: SenML has units registry today. Originally quite restrictive registration policy. However, with practical experience, using only unscaled SI units is unwieldy. Thus, ap proposal to add derived units (commonly used in e.g. some industries). There was a proposal to add a second registry that had derived units, that included mapping rules to primary registry. Conversion can be automatic. 
However, how to handle this when it comes to mandatory to implement. Recommendation to use primary, use secondary only if needed. But this add interop issues. 
Carsten: several facets (MAY, but SHOULD NOT unclear). 
Cullen: This (MAY or SHOULD) won't change anything in the real world. We need to hit the core problem. This is not something new we discoveded. All this has been discussed before. There is a trade-off beween interoperability (not just convenience on data generation) 
Carsten: We don't have new information, but there are SDOs that...
Cullen: This is not the time to worry about details, should look at core problem.  
Ari: Instead of writing "may, but should not" - better to write down the rational and guideance on the non-trivial aspects. This was discussed earlier today, try to accomodate for more units. How to handle the registry. Proposed expert guidance & review. Should use same style, character set as existing one. Which units to accept? Allow much more liberal (but not random proposals) to table 2. Use units base on existing scientific work or in other SDOs. Should not have two with same string, but may allow different unit identifier for different industries. May want to move some units from primary to secondary. Allow naming syntax w multiple slashes. 
Cullen: this makes for a very open registry. People also wants to use units as things w semantic meaning (not only SI units) 
Matt: (itron and oma-ipso). We ship 200 million smart meters, we will never ship joules over the air. There has to be a way for the industry to have a standard and we like the secondary unit registry. 
Cullen: Heard loud and clear, but not the first person to say this.
Ari: good agreement on that we will have more units, the problem is now how to organize it (someone needs to be the expert). (Note that ari is looking for expert reviewers with background in the field)
Ari: An open issue is if to reuse "u", or introduce a new "u2" field. Pros and cons. Having a separate field adds complexity (This needs to be further analyzed). No clear preference. 
Carsten: should probably have a another side meeting. If you add units as selector, shouldn't u2 also be one. 
Ari: yes
Cullen: should find backwards compatible way to handle this, that works well w analytics etc. Need to not break current interoperability
Ari: at least minimize damage. Current impl should expect new units already today.
Cullen: but applications not needed to understand new units, but if units change (Celsius to Fahrenheit)
Alexey: looks like this one is not ready for IESG yet.
Ari: some clarity this week. The u/u2 part might change. We might als do a preregistration of the units and figure it out later. The identfiers themselves are straighforward. This stuff is urgently needed though.  
Alexey: have you talked to Pete Resnick w one or two tables. 
Ari: not yet. 
Ari: I agree that 2 columns make more sense.
Alexsay: I am not trying to derail your emerging consesnsus.
Cullen: there is a need for a rev of the draft. The u/u2 problem should  be solved first, needed before setting the secondary registry. 
Ari: many ways to solve, this is needed in e.g., OMA where thsi is used already. 

Ready for WGLC? (10):
draft-ietf-core-senml-data-ct-01 2019-11-04
Ari: This is about content format for the vd field. 
Updates: use string for both number and string. Mandatory to understand ct field. Added examples (including content encoding). 
Complications: 
mixing b and _ fields. What will actually be used? Currently mandatory overrides, however more complicated that thought (this problem appears in other drafts as well). Input requested. 
Alexey to provide feedback on examples. 

Discuss basic approach some more; is there a problem; what else is needed (15):
draft-keranen-core-senml-base-prefix-00 (ipr) (not updated)
Ari: address problem with long names (as they need to b e unique). This draft proposes how to construct base name, using info w out-of-band information. 
IPR declaration on this draft. 
Proposed bpi names: ip address, ip+port, request based uri, public key, TLS PSDK identity, Core RD endpoint. 
Status: Hannes had a draft last IETF on same problem (address OMA problem). Some differences in approaches. Implementation experience in OMA doesn't point to much difference (wihtou indicating bpi: 
Carsten: what to do with this. 
Ari: we'll investigate, might combine w Hannes' proposal, but not sure. 

Meeting finished 1150. 

## FRIDAY, November 22, 2019 1220-1350 Hullet

Intro (5)CoRE Applications (KH, on-site)
(have side meeting first); report on side meeting (10)
(also from side meeting): problem descriptions (Thomas Fossati) (10)
Pubsub approaches: draft-ietf-core-coap-pubsub-09 (10)
Potential discussion: (draft-ietf-core-coral-01), (draft-ietf-core-href-01) (5)
extensibility discussion, numeric identifiers (KH) (10)

Discussion on RD and DNS-SD
Christian presented the 3 options on the normative reference to dns-sd: remove text (bad idea), change reference and normative text to informative, wait for completion (check on the list and with AD) of dns-sd (long delay for RD)
Cabo: ... Normative ref is a big liability and we should use it in situations where we really need it. Those docs were supposed to run simultaneously, but later on we decided not to. I believe it is important to maitain this reference. We should have a way to describe it in a way that it is not normative ref. For example we can say that there are other ways to do discovery such as ... We are not talking about service discovery, we are talking about RD discovery. It is a completely different questoin whether a discovered RD is usable. Just using language saying this is one way of doing things is the way forward.

Jim Schaad (From jabber): I think that the answer is to say there may be other in the future, one such might be ... when done

Ari: +1 what Carsten said on normative references, have a similar issue with draft in LWIG with normative dependency to RD draft that probably could have been informative too. Discovery is a highly discussed topic at the moment anyway and more relevant document are likely to come in.

Stuart Cheshire: You said this ref to rd-dnsrd is not about discovery of resource, but the directory. If you want to discover rd it is a 5 min task - add a service in dnssd. What the draft is describes is how to discover the resources that the RD has through DNSSD.
Christian: for the link to the RD that we are expressing in the draft, is just the way you can put that link in RD. We did not want to spell out again wrongly by referring to the old way DNS-SD did that.
Stuart Cheshire: it seems that discovery of RD does not need all the srv records, maybe an empty set. You might need to just register a point in IANA. If you don't specify how RD will be discovered through DNS-SD, people will be left guessing. <If I understood correctly the recommendation is to put the relevant part in this draft and not have a normative reference>

Christian: We wanted to give guidance here, hence we added this information.
Carsten: could take the mapping from RD-DNS-SD(???) draft and take it here

Christian; procedurally makes sense; not sure if covers all cases ... how do we express protocol part? Always goes to coap:// and not others? Better done with subtypes? But those not designed for protocol negotation and should use service type instead? 

Stuart: Suggestion: service such as SSH can put "_ssh" in API call and you have discovered it. 
Let's fill out the IANA form to register a string for CoAP over UDP. If in future CoAP TCP, it's different service type string since different implementations. If you have RD only for CoAP TCP and you client using UDP, they can't talk so no benefit to discover. 
Users want to discover things they can talk to. Different transports are different things, so specify one per transport in concrete terms.

Chris: that's where RD-DNS-SD is going. Looks like way forward. Bit more on the list good.

Stuart: The text in document looks like this is a normative reference. If you can define the subset to find an RD server, let's define it here. Just need to register a string and you're done with it. 

Chris: In coap the applications can rely on different protocols to have the same semantics and proxies can complexify things even more. If the client finds coap+tcp and knows a proxy, the client could still work with it. 

Stuart: What if the proxy does not know how to proxy it. For example the client finds coap+quic.

Chris: want to make sure we don't overlook this possibility

Carsten: Are we talking about _core-rd._udp and _core-rd._tcp?

Chris: don't cover all requirements for CoAP. _udp and _tcp used because generally available. For example for web sockets would need something more.

Stuart: there is some historical context about the _udp, _tcp. 
Can you list all transports currently defined?

Chris: 6: CoAP over UDP, UDP+DTLS, TCP, TCP+TLS, WebSockets, WebSockets+TLS

Stuart: Yes, 6 makes it more complicated than previous cases.
A client looking for DNS Update, needs to find the hostname of the server.
3 ways to find a server for DNS updates. For a human this is 1 thing, but we have 3 service types. The client typically looks only for the TLS. I am giving this as a datapoint to look at. For ... we don't have insecure version, so just one service type.

Carsten: problem here: we tend to use resource type. 

Carsten: Are we talking about _core-rd._udp, _core-rd-tls._udp, and _core-rd._tcp?

Chris: in DNS-SD explitly note the service type and don't try to come up with service type from resource type. Would be hard to mechanically convert them. 

Stuart: Pretend that the core dns-sd document does not exist. What do you want to write int this document so that a client can discover RD. I understand the complications, but put aside the full generality of RD-DNS-SD that tries to map all other attributes. Forget all that. Just "I have computer in network, how do I find it". Scoped that way will not take that long.

Carsten: That is useful and I think we can take the details to the list.


SenML More Units

Ari presenting.
There are two options for the 2nd registry to be referenced.

Question is how to indicate you are not using the unscaled units.
Some SenML systems push a lot of data and processing shall be done on the way. Cisco has a use case for routing based on units. This allows not to look at the field/record names, as you would need to update those otherwise. Just looking at the units allows for this.
The original design enables this but assumption to restrict to only unscaled set of units did not work out well since there's high demand for the scaled units.

Different options to cover this use case, the one that seems best:
Prefix unit ID with "*" to indicate secondary registry, could be a different symbol and it might be put at the end, but '*' seems like a safe bet. Breaks the principle of least astonisment. Multiple people voiced that it smells funny, but it seems like this is the best option.

Alexey: In the current registry there are units that are derivative. Should we change that.
Ari: if we were doing this now, yes, but breaking existing code does not seem right.

Carsten: In Germany, books have a set price. To sell them at a discount an artificial quality issue may be introduced (e.g., scribble on the cover). The asterisk looks like this. The problem remains that the people that want to use this will always see the black marker on the side. They might feel like being second class citizens, which in a way they are.
The objective was to distinguish units from table 1 from units from t2. The assumption is that units in t1 are moving very slowly, that leads to a strategy where one can look at t1 and if it's not there you look at t2. If there is a newly registered value in t1, the application will need to do something similar anyway.

Ari: Valid assumption that the first registry does not change much. But appl

Carsten: I am talking about the detection strategy. Asterisk is one way to do it, but I would have written it as lookup in t1 followed by lookup in t2 if needed.

Jaime (as reviewer): Asterisk is looking bad and this "principle of least astonishment" is a real issue (I was confused). Registry decisions should not show up in the SenML document. This is a change that will be carried down the road by anyone implementing and debugging senml.

Ari: It is not about t1, t2, but also about the semantics of those registries. Whether there is only 1 unit per measurement type. SenML was never supposed to be human readable, but it is because of JSON that it is. Asterisk can be stripped by the code, so it is going to be visible only for the developpers that might still be astonished. The question is is usecase is important enough to merit this. I am also at the fence, but after some discussions I understood where it might be needed.

Matt: Is the * needed? There will be new units coming. 
Ari: The infromation that * gives you is whether there is something you should care about or not. You will never have a new measurement type for speed in table 1.
Matt: This seems like you are using the asterisk to say "look in table 2"
Ari: * might be a way to indicate - not processing that might be something stupid.
Carsten: proposal is to create a new version of the draft that suggests the strategy of looking up the unit in table 1 and if it's not there, assume it's from table 2
Ari: Should we then proactively register units in table 1 to ensure the table is as stable as possible.
Carsten: That might be a worthwhile thing, but I would not couple it timewise as [that is a bit of work], but adding units defined in ISO/IEC 80000 proactively might make sense. 'Events per second per square meter'.

Report on the CoRE Applications Side-Meeting

* Problem Details
    * proposal by Thomas Fossati that arrived after the I-D cut-off
    * provide application-level error details for CoAP APIs
        * like RFC 7807, but for constrained environments
    * draft has now been published as draft-fossati-core-coap-problem-00
    * of course, we also checked how to do this with CoRAL :)
        * added a section to draft-ietf-core-coral-01 on meaning of a CoRAL document in an error response

* Extensibility and Code Points
    * problem details of course has a problem: how to define new error types and error attributes?
    * common theme in CoRE WG: need to allocate compact unique identifiers all the time
    * IANA registries are good for reviewed protocol extensions, but not for every possible application-specific error condition
    * we looked at Thomas's proposal for allocating IDs
        * also SIDs and the use of URIs and static-dictionary compression in CoRAL
    * probably the most difficult problem in computer science next to cache invalidation :)

* Error Cases in CoAP API Specifications
    * API specifications feel often very repetitive
        * if the resource does not exist, then return 4.04
        * if the client is not authorized, then return 4.03
        * etc.
        * does not seem application specific
    * should suffice to make a table of error conditions and reference that everywhere
    * maybe need dedicated error response codes for application-layer errors
        * e.g.: request is fine on the CoAP level, but has an invalid payload according to application semantics
        * or maybe not

Francesca: In ACE we only specify when to send 4.01 unauthorized messages. Don't actually use all the others. For example we say:"If token does not validate, use "unauthorized" response."
Klaus: The targeted work might be more on the implementation guidance side. Need to debate meaning of 401 and 403. Confusing.

Klaus: We inherited terminology issues from HTTP: "Authorization" often actually was intended to mean "Authentication"

Francesca: (Quoting CoAP spec where this is ambiguous)

Carsten: 401 is "who are you". 403 is "I know who you are and you can't do that". Makes sense to differentiate. Good material for corrections and clarifications document.

Marco: CoRAL for error responses can be useful also in draft-tiloca-core-observe-multicast-notifications , when the server returns an error response to a client with information for redirecting to the group observation. By the way, we may also want to define a better, more specific error code than 5.03 that we are currently using for that.

Carsten: Right, you are in fact more redirecting the client, while not really in a protocol sense.


Update on CoRAL

* Update on draft-ietf-core-coral-01
    * Added section on meaning of a CoRAL document
        * in error responses and
        * in non-2.05 success responses

* Update on draft-ietf-core-href-01
    * No changes

* Open GitHub issues
    * 16 CoRAL <https://github.com/core-wg/coral/labels/coral>
    * 7 HREF <https://github.com/core-wg/coral/labels/href>

Update on CoRAL-based Applications

                       ___
               Topic  /   \
          Collection  \___/
                          \
                           \___________________________
                            \          \               \
                             \ ......   \ ......        \ ......
                            : \___  :  : \___  :       : \___  :
                     Topic  : /   \ :  : /   \ :       : /   \ :
             Configuration  : \___/ :  : \___/ :       : \___/ :
                            :  _|_  :  :  _|_  :  ...  :  _|_  :
                     Topic  : /   \ :  : /   \ :       : /   \ :
                      Data  : \___/ :  : \___/ :       : \___/ :
                            :.......:  :.......:       :.......:

             Figure 3: Resources of a Publish-Subscribe Broker


                     HALF                       FULLY
                   CREATED                     CREATED
                     ___                         ___     Publish/
      ----------->  |   |  ------------------>  |   |  ------------.
         Create     |___|        Publish        |___|  <-----------'
                          \                   /          Subscribe
                     | ^   \       ___       /   | ^
               Read/ | |    '-->  |   |  <--'    | | Read/
              Update | |  Delete  |___|  Delete  | | Update
                     '-'                         '-'
                                 DELETED

                      Figure 4: Lifecycle of a Topic


* Update on draft-hartke-t2trg-coral-pubsub-00
    * How to configure topics at a PubSub Broker using CoRAL
    * Proposal discussed in Montreal
        * Separate configuration of topics from publish/subscribe
    * Want to rewrite draft-ietf-core-coap-pubsub based on Proposal
        * Didn't make it in time
    * Published draft-hartke-t2trg-coral-pubsub-00
        * Authors need to iterate on this to reach feature parity with draft-ietf-core-coap-pubsub-09

Cabo: we want to ship this thing. Need to make sure we have all in place to do that.


* Update on draft-hartke-t2trg-coral-reef-03
    * How .well-known/core and Resource Directory looked like with CoRAL
    * Updated to match the same documentation style as draft-hartke-t2trg-coral-pubsub-00

* Update on draft-hartke-t2trg-data-hub-05
    * How to store files on a server using CoRAL
    * Updated to match the same documentation style as draft-hartke-t2trg-coral-pubsub-00

                       ___
                Data  /   \
          Collection  \___/
                          \
                           \____________________
                            \___    \___        \___
                            /   \   /   \  ...  /   \  Data Items
                            \___/   \___/       \___/

                     Figure 1: Resources of a Data Hub


* Update on draft-tiloca-ace-oscore-gm-admin-01 (to be published)
    * How to configure OSCORE groups at a Group Manager
    * Updated to explore how to do this with CoRAL
    * Updated to match the same documentation style as draft-hartke-t2trg-coral-pubsub-00
    * Identical to Pub/Sub Broker!
        * except: different configuration properties and status properties
        * and, of course, no creation of a topic that can be published or subscribed to

Jaime: is this common pattern?
Klaus: already two applications here and know of one more application that has this pattern. Seems common.

##

Carsten: need probably one more IETF round to finalize stable CoRAL. Then validate, implement, review. Could aim for WGLC in mid 2020. Should we be faster? Need more time? Love to get some input.

Jim (in chat): href draft needs to happen in parallel (yes!)

Klaus: ton of validation of CoRAL has happened. Applied to large use case internally. Concepts are now rock-solid. Will not change those. May tweak things baed on issues.

Jim: want to solve JSON coral in same schedule?

Klaus: interesting question
Carsten: not enough data to answer the question, but could try to
Klaus: have two serializations now. Just need to choose. But both are ugly.


Flextime (40)

Francesca: for OSCORE EDHOC want feedback from implementors. Have talked with some alredy; now looking for more feedback. 
For EDHOC we have 3 message exchange. The third message can be combined with the first OSCORE request. All of it will be transported in CoAP.
Have identified 3 possible solutions. Several opinions. Malisha from 6tish would prefer to transport EDHOC message in OSCORE protected CoAP request. Would mean having EDHOC message 3 in payload with cipher text. Signal it to the server. Signaling could be done in 2 ways: Klaus supported using OSCORE option value. Server would have to parse that in order to know there's also message there. 
OSCORE message inside EDHOC message, what EDHOC message is a CoAP message with EDHOC inside. <lost track>
People can listen to this.
Ari: can you send a flowchart with this; bit hard to follow
Francesca: We can scetch this, yes.
* New option - edhoc - empty...

Would like to hear opinions on this. On one side constrained implementations and CoAP integrated with OSCORE and on the other side more general having libraries where switching libraries can be hard.

Chris: on semantic level two different messages. ...

Francesca: yes; trying to do in a way with least implementation pain.

Klaus: at some point we decided to use CoAP just simple message forwarding. No good option here. Only bad and really bad.

Francesca: this is just optimization. Still have the default option with more messages (that is not ugly). But important for 6tisch to have smallest amount of round trips.

Klaus: need multiple datagrams? 

Francesca: EDHOC message 20-something bytes. Don't think so.

Klaus: can we do IPv6 over OSCORE next year? :)

Carsten: maybe worth thinking about piggybacking in more general sense.


Carsten: will come up with lighter interim schedule than every two weeks
