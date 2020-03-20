CoRE WG - Summary IETF102
=========================

* Video Recordings: [Session 1](https://www.youtube.com/watch?v=2i9VAOJq8LU),
[Session 2](https://www.youtube.com/watch?v=M0XfeVynCAY)

* [Slides](https://datatracker.ietf.org/meeting/102/materials/slides-102-core-consolidated-slides/)

* [Raw minutes](https://etherpad.tools.ietf.org/p/notes-ietf-102-core?useMonospaceFont=true)


# CoRE @ IETF102 WG summary

* draft-ietf-core-links-json-10 and draft-ietf-core-cocoa-03 are in
  IESG processing and are awaiting new versions from the authors.
  Side meetings at this meeting have made progress addressing some of
  the open issues from AD and IESG input.

* draft-ietf-core-object-security-13 is in IESG processing and is
  waiting for a review from Eric Rescorla, with a view to Eric
  clearing the remaining DISCUSS held on the document.  Technical
  Changes resulting from IESG and directorate inputs were discussed.
  Responsible AD Alexey triggered a second IETF last call to cover
  those changes.

* draft-ietf-core-oscore-groupcomm-02 is nearing WG last call. The
  plan is to progress this independently from the related ACE
  documents as the membership and group key management can be done by
  other means (e.g., using a simple REST API).  Before the WGLC
  another interop should be held (implementation draft then to be
  published based on outcome of the processing of basic OSCORE).

* draft-ietf-core-echo-request-tag-02 requires a few more reviews; no
  formal dependency but it would be good to finish this approximately
  on the same timeline as OSCORE.

* draft-ietf-core-resource-directory-14 was discussed, with some focus
  of the semantics of the incoming (registration) and outgoing
  (lookup) links.  With several implementations becoming available An
  interop would be next; September/early October time frame is
  envisioned.  Next step then could be WGLC.

* draft-ietf-core-rd-dns-sd-02 was discussed (and later presented in
  DNSSD WG as well).  Much of the discussion centered about how the
  rt= target attribute can be turned into a service type on the DNSSD
  side.  (Later in the DNSSD meeting, the question came up whether
  that is the right pairing in the first place.)  All DNSSD service types
  must be registered (15 ldh characters max); CoRE resource types can
  be registered (63 characters max) or can be URIs.  Further work on
  this is needed, as is on the pairing of ins= and DNSSD instance
  identifiers.

* The CoRECONF cluster (new old name for yang-cbor
  draft-ietf-core-yang-cbor-06, comi draft-ietf-core-comi-03, and sid
  draft-ietf-core-sid-04) has recently received reviews fro the netmod
  community; a few more from the CoRE side and maybe another interop
  would be good before WGLC of this cluster, envisioned to close
  before IETF103.  draft-veillette-core-yang-library has a little more
  time.  As a major technical change it was agreed to always start a
  yang-cbor tree with a SID delta base of 0.  This has slight
  performance disadvantages, but makes handling the payloads much
  less error-prone.

  The CoRE WG is not the place to develop YANG modules that match this
  functionality.  A group will initiate the steps toward a new WG,
  tentatively called Yang Of Things (yot).

* draft-ietf-core-dev-urn-02 was presented, with a focus on the small
  changes needed for alignment with OMA LWM2M.  There was some support
  for this alignment in the room.  Jari Arkko will coordinate with OMA
  and report back.

(end of Monday meeting)


* draft-ietf-core-senml-16 is in AUTH48 as of 2018-07-19, RFC-to-be
  8428.

* A quick heads up from Roman Danyliw pointed to the 2nd WGLC of DOTS
  signaling draft-ietf-dots-signal-channel-21, which uses CoAP.
  Interested reviewers were found.

* draft-keranen-core-senml-fetch-01 found a few reviewers.  Interest
  to be confirmed on the mailing list, in the case of success followed
  by a call for WG adaption.

* A procedural point about IANA registering of SenML fields was
  discussed.  If a registrant is not interested in EXI, no attempt
  should be made to register a new XML/EXI schema name.  Authors to
  check with IANA whether the schema could be stored with the
  registration.  As the first exercise of the registry went less than
  perfectly, AUTH48 to be used to add a couple of clarifying sentences.

* For stateless forward proxies, there was good interest to explore
  the option of introducing an extended token.  The plan is to realize
  (WGLC) or dismiss (revert to separate option, now also called
  Extended Token) before Bangkok.

* draft-ietf-core-too-many-reqs-02 has passed WGLC.  Authors will fix
  typos and then publication will be requested (instead of a second
  WGLC we will use the IETF last call for any emerging WG comments).

* draft-ietf-core-multipart-ct-01 is ready for WGLC.  As thw WG tends
  to think this will be successful, early registration of the
  Content-Format codepoint will now be pursued (following the
  procedure for this).

* draft-bormann-core-proactive-ct-00 received good support.  Next step
  is WG adoption call on mailing list.

The second meeting ran over time significantly.  The remaining items
on the agenda, CoRE interfaces, dynlink, pubsub, and protocol
negotiation, as well as presentation and discussion of
draft-jarvinen-core-fasor-00, will move to interim meetings.

* CoRE will hold regular virtual interims starting from Aug 15.  The
  regular date envisioned is every second Wednesday (with some gaps)
  at 0800 California time.


# Raw minutes

~~~

---------------------
 ╔═╗┌─┐╦═╗╔═╗  ╦ ╦╔═╗
 ║  │ │╠╦╝║╣   ║║║║ ╦
 ╚═╝└─┘╩╚═╚═╝  ╚╩╝╚═╝
---------------------

Core@IETF102

Constrained RESTful Environments WG
Chairs (core-chairs@ietf.org):
Jaime Jiménez
Carsten Bormann

Minute Takers:  Ludwig Seitz, Ana Minaburo, Christer Holmberg, Ari Keränen, Francesca
Thank you!

Slides
https://datatracker.ietf.org/meeting/102/materials/slides-102-core-consolidated-slides-03.pdf
Meetecho
http://www.meetecho.com/ietf102/core

# MONDAY, July 16, 2018
**1550–1750  Duluth**

## Intro (10)

  * WG and document status
  * In RFC editor queue: draft-ietf-core-senml-16
  * Quick recap of related work, pointers
CB: Patents needs to be known, new version of Note Well

CB: DNSSD Thu 9.30-12.00 Duluth, OCF/T2TRG coordination call Wed 11..12 (ask chairs)

### In IESG processing:

* Document status only (IESG Processing):
  * draft-ietf-core-links-json-10      2018-02-26    Waiting for AD Go-Ahead::Revised I-D Needed
CB: Did refocussing after extensive feedback in IESG, still ongoing

* Document status, pointer to new work
  * draft-ietf-core-cocoa-03      2018-02-21    AD Evaluation
CB: Great TSV AD feedback, need to process. Carles has produced already a PR. 
CB: Core WG does not expect to have a single Congestion Control
Christer Holmberg: Provided a review for the document.
Carles: The updates with his feedback are already in a PR, we should have captured your feedback there.

  * Related work:
  draft-jarvinen-core-fasor-00    new  2018-07-02  ➔ Thu
CB: To be discussed on Thu if time


## OSCORE cluster (40)
  * draft-ietf-core-object-security-13      2018-06-27    IESG Evaluation::AD Followup

Göran Presenting. 
Now in version 13
Main changes: Clarifications based on IESG reviews, Appendix D: overview of Security properties
Add protection for some options, 
Additional clarifications and simplifications. Comments are linked to the IESG review
Wiki contains explanations about how reviews were addressed
Previously Observe was entirely an outer option but no it's an inner option which enables endpoints to verifies each others intent
Separated out Observe and Blockwise processing to simplify description. 
NoResponse option now essentially inner  
New subsection on URI-Host/Port processing
Updates on HTTP processing based on Martin Thomson's comments
New parameter called ID context, to transport context information to retrive the security context
Updated deployment examples and test vectors

Next steps:
    Updates based on new review comments
    Continue IESG evaluation
    Interop-testing new version

CB: Who has read this version of this draft? (Answer: 2)
Alexey: Lots of good changes, sections moved around -> not easy to diff . To do IETF Last Call this week, will happen while Ekr is reviewing the last version of the draft. Will try to start this week.

  * draft-ietf-core-oscore-groupcomm-02    new  2018-06-28    Active
Marco presenting
Major revision based on discussions at IETF101
Updates from -01
Revised terminology
Group Id stored in new parameter Context Id
Format of external_aad aligned with OSCORE
Security considerations section has 2 new subsections: first is on uniqueness of key and second on collision of group identifiers
Appendix C Example of Group Id format, discourage collisions
Appendix D.2 provisioning/retrieval public keys

Implementations: Java version based on CF planned
OSRAM in C
Contiki OS PoC
need to be aligned with latest versions

Related Activity:
    joining an oscore group using the ACE framework
    renaming for consistency

CB: We are finishing other docs now dealing with groups, eg RD has a way to handle groups. Does this fit together in any way?
Peter vdS: Some work should be done given the work in the RD
JimS: Do not believe there is overlap. Who is managing groups in RD? The party doing the management in RD and here should be the same, however that is being defined in ACE. 
CB: Who wants to do the job Peter suggested?
PvdS: Will contribute, also Michael Koster and Jim Schaad.


CB: most likely 3 docs that work together to do this would be in a cluster. What is the relative speed for finishing this?
Jim: Not expecting the docs in ACE to go anywhere before next summer, how much does this doc rely on those docs?
Marco: Think we can progress independently
CB: Using this without ACE requires some other form of management of keys
Jim: if willing to do static config, no (dynamic rekeying necessary?)
CB: Who has read a recent version? (5 hands). Who would be reviewing: Peter, Jim, Bill, Michael. 
GS: Volunteers please have a look first to OSCoRE. 
CB: Do the authors believe this is ready for WGLC? 
GS: Interop test would be nice. 
CB: Is the current draft the implementation draft?
FP: We could wait for the update on OSCORE before the interop. Process reviews for v13 and IETFLC


* draft-ietf-core-echo-request-tag-02    new  2018-06-29    Active
GS: Would be good to have more reviews on that, related to security
CB: Who has read a recent version? (answer: 6)

GS: (on EDHOC) We updated it, key-exchange protocol for OSCORE, have formal verification on last version,
reduction of message sizes 1/2 for RPK and 1/3 for PSK compared to DTLS
CB: One more review cycle to be done. 


## Resource directory cluster (40)
  * draft-ietf-core-resource-directory-14    new  2018-07-02    Active
Peter vdS presenting 
Gives the improvements to the URI section
explain how to get from reference to target URI

Link semantics from host to RD to the resolution of the absolute target 
Registration Base URI
RFC6690 and RFC8288 anchors and URIs
Other improvements (renaming, clarifications)
TODO react to reviews, some ambiguous text left, time for WGLC

Jim: Don't think WGLC is good before interop.
CB: Did start interop testing.
CB: Who has an RD implementation? (4-5 hands) Acklio, Matthias, Jim, CB
CB: Set something up during September for interop, convenient?

  * draft-ietf-core-rd-dns-sd-02    new  2018-07-02    Active
Kerry Lynn presenting

Hoping for co-authors from DNSSD
KL: How many people have read the draft (two hands).

Why? We should be able to interop between RD and DNS services
Granularity of DNS is larger so that can be used to drill in to find out exact services needed

Who knows how DNS works? (most hands raised). Short overview of DNS-based service discovery
New Link Target Attributes
exp is currently defined as a binary
ins is globally unique across devices of this type
may need to generate service types from the rt

Link-format 2 DNS-SD mapping
Example mapping

Please follow up proposals you make on the list, we will spend more cycles on this now

Dave Thaler: That string (_oic) must be IANA registered
Stuart Cheshire: DNS-SD designed for constrained, CoRE as well but allows much more verbose content
DT: The discussion is on the _oic field. if _oic must be iana registered what is the process to deriving the rest. 
CB: General comment: Seeing situations with different IANA regs that need to be synced. May be how we can handel this here as well ... How should the hierarchy be used? Needs thinking. If people have ideas, please comment on the mailing list
KL: <Notetaker: too fast, didn't capture>
SC: Quick comment on the hierarchy. When we did DNS-SD we settled on a very limited hierarchy with types and subtypes but not deep nested hierarchies. Hierarchy is useful when software access it at different points. Hard to find an app that would use a collection of devices when they have nothing in common (notetaker: i.e.  printer and toaster.)
KL: May have additional problem: CoAP used to be about UDP, now we need to express everything else, may need to expand the # of labels in service part to express more complete bindings
CB: Second SCs comments on restricting hierarchies
Matthias Kovatsch: Issue with (discussed on ML) ins attribute, originally used to distinguish resource with similar rt. With redefinition we lost that capability, need to rethink framework to solve this problem, good that definition is clear now, but need the lost functionality
KL: Scope of the end point 
KL: People using things before they are defined, need to go back and define them
MK: Need has been there all along, need to go back and fill gap
CB: Not much feedback on ML because messy to clean up
KL: Mapping from free-form environment now vs specific constraints in DNS-SD, should we become more specific?
MK: It is also fine to define it as it is. Implementations will have to change as they are not interoperable.
SC: Question, didn't understand example (MKs). How is this different form other instance names
MK: Need to know to whom the device belongs (a hierarchical)
SC: How is this done today?
MK: Hierarchies
SC: Written down?
MK: Was in early versions of interface draft, also used in web linking, need to write it down (again) to make it clear
SC: Need way to diff instances in RD
DT: OCF doesn't use it but RFC 6690 allows arbitrary values in rt values, is there a way to map them? RFC6690
KL: Did not consider
KL: Not many rt registered in IANA as of today. Only OIC.
Michael K: I wouldn't assume that no registration means no existance.
DT and CB: By definition there is no need to register them, there are two options there. 


## CoRECONF  cluster (15)
Carsten gives exposition:
SNMP => Netconf + YANG
HTTP + html + json = RESTCONF
CoAP + cbor + sid + yang = CoRECONF

Document called COMI and bundle called COMI -> confusing
Now called CoRECONF to reduce confusion

Alexander Pelov presenting
  * draft-ietf-core-yang-cbor-06      2018-02-08    Active  
    (discuss observations from active use, NMDA)
  * draft-ietf-core-comi-03      2018-06-04    Active
  * draft-ietf-core-sid-04      2018-06-04    Active
  * draft-veillette-core-yang-library-02      2018-01-24  

The status of the different drafts that are almost ready for WGLC after the inputs of today
Next slide: Different protocol stacks
What we have today: example SID registry, implementations, 3 hackathons
Hackathon 102: 
    supposed to be achieved: Open source python examples, implementation and documentation
    what was achieved: base examples, COMI client implementation started

CISCO has Yang DK that allows to generate examples in C, Python and Go.

YANG-CBOR + SID was reviewed
comment related to delta-encoding
Include the encoding in the payload to reduce ambiguities
Proposed change to help debugging but adds overhead

CB: There was no ambiguitty in the existing proposal but we missed a requirement, the one to rip the payload out of the context and do somehting usefull with it. It is important to fullfill it. On the specific example, you would compress the dates there. Thinks that's a valid comment
Dave Robin: on other protocols there is a similar situation. We used tagging, adding an attribute called "self" which was the URI of the context. On the wire is redundant, it is only used when handing the informaiton to someone else. 
Henk B.: Think this is similar, do /p for payload. Do <too fast didn't get that> and problem goes away.
CB: No exactly same problem
AP: We need to discuss to see how to get this requirement
CB: Hard to make sure the transformation always happens. Need to figure out details. Other results: # of media types goes down, the differ on how we use context, less if we use less context
AP: This is for COMI type, the YANG and CBOR is different. Please give feedback on the mailing list.
Laurent Toutain: on constrained network use the restricted format and extend it through the cbor-template
AP: Conclusion Yang-CBOR + SID ready, same for COMI, next steps: Hackathon, BOF for Yang of Things
CB: WGLC during September, after interop is done.
HB: Notion of Netconf notiff(?) drafts modular wrt transports, need to align with Netconf
CB: Would write this draft with content "look there". Wouldn't want to destabilize the well-ripened (sic!) documents. The YANG library need to be included in this cluster
Is nimda damaging your document? (question to Michel Veillette)
MV: Next step WG adoption
HB: <didn't capture>
AP: This could be the place for Yang of Things (YoT) for communities to meet
CB: Want to talk about YoT?
AP: Had side meeting several IETF ago. If there is CoREConf there will be modules usable for IoT. There was a lot of interest at the time.
CB: On Thu a CoAP customer will present how CoAP is used for DDOS detection (DOT WG).

Concise YANG Telemetry  (draft-birkholz-yang-core-telemetry, )

Henk B: Short intro on Concise YANG telemetry
2 drafts: subscribe notifications and yang push 


## SenML cluster (15)
  * draft-ietf-core-dev-urn-02    new  2018-07-02    Active
    * (discuss in proximity to RD endpoint naming issue)


draft-ietf- core-dev-urn-02
Jari Arkko presenting

Version -02
aligning:
with OMA LwM2M
   3 levels of "private" device ids

Questions:
    Do we agree to align with OMA?
    OMA uses OUIs we use PENs, which should we use?
    Does this affect use of org/os/ops?

Jaime Jimenez: OMA perspective: Ok with PEN, unification OK. Most common URN usage is IMEI (rather than dev:urn).
JA: Could this be discussed in OMA?
JJ: Since in IETF there are quite a few OMA members we could discuss this.
Kerry Lynn: When you use "private" you are not talking about privacy?
JA: There are cases where that makes sense, want to enable ???
Ari Keranen: In SENML we recommend URN as solution dev:urn. Concerned about adding person sign (?) would make this only semi-compatible
AK: Good agenda point for OMA coord.
Padhu S: Several evolving URN formats. Generalized here with one format would be useful. 
CB: What is next step?
JA: Need to coordinate with OMA, will try and report back

Σ 120

# THURSDAY, July 19, 2018
**1810–1910  Van Horne**

## Intro (5)

  * draft-ietf-core-senml-16      2018-05-18    RFC Ed Queue
SenML in AUTH48!  RFC8428!

* F-INTEROP 
F-interop https://go.f-interop.eu/

## DOTS (updated agenda)
* draft-ietf-dots-signal-channel-21

Using CoAP for DDOS mitigation signaling.
Standardize the messages/communication from a system under attack to ask for mitigation help.
Asking for help: CoAP protocol doc in 2nd WGLC. Would like to have expert reviews.

Please review within the next 2 weeks: DOTS Signal Channel document
Dave T, Bill S, Jaime J, interested to have a look at this. 

## (Any spillover) (0)


## FETCH and PATCH for SenML
  * draft-keranen-core-senml-fetch-01    new  2018-07-02

Ari presents changes since -00
Add/Append/Replace/Delete with (i)PATCH: Delete is new. Concluded there is no need for op-codes. Adding time needs two operations.
3 T.B.D.s
Ari asks for WG adoption.

4 read a version
Reviews to be done by Michael Koster, Bill, Carsten
Some hands for doing this.
No hands against doing this.

Confirm on the mailing list for interest, and then (possibly) adoption call

## IANA registry maintenance for SenML

XML Schema needs to be changed and renmed when adding a new entry.
Bad for EXI, which needs the Schema for (de)serialization.

proposal: clarify that you don't have to register schema, but if someone needs it, they can register all those needed

Jim Schaad: Would like to see that you don't have to add several field in order to register the schema. 
Alexey: do you really want to publish EXI in the current doc (AUTH48)?
Ari Keranen: Let's publish this, this does not need to update the document. It has to do more with the registry.
Carsten: maybe this is more about creating awareness.
AK: Latest request for LwM2M "vlo" shoud be fine. No need to change rfc. 
(LWM2M thing should be fine) All the schema could be somewhere like a wiki, but don't need to be in RFC.
Alexey: will you need new mediatype for EXI schema?
Carsten: no
Alexey: not totally confident about EXI nor changes. Would you have a draft describing this?
CB: It's all in the SenML draft already
AK: yes everythig we are discussing is already in the doc, maybe just clarifying.


## Related work in other WGs (15)

### Stateless Forward Proxies
  * draft-ietf-6tisch-minimal-security-06 (discuss stateless)

Problem statement: Normally proxy fw the request. and while it waits for the response, it has to keep state in 6tisch, proxy is very constrained
Idea: forward the state to the origin server and receive it back with the response. 
Question: what is the best way to do this?
This could go into the token, which was defined with this behavior, but unfortunately limited to 8 bytes.
Using a token option introduces a second token, which is ugly.
Could use reserved values for the token length for option length encoding. This would work for 6TiSCH, but would break generic deployed CoAP implementations.
(like for options)
It would need all intermedaries to understand this mechanism.
Should do the right thing way too late or do a thing that is not quite right. Would need to write a draft that updates RFC7252 and 8323.

Dave Thaler: decent idea. Not clear of caveat slide (9).  Are you assuming the client (and intermediaries acting as clients) are allowed to do stateful and stateless?
Carsten: implementation would keep in practice one state. Tries to do stateless thing once but keeps the state to handle errors.
Dave: rest may be worth doing, this I am more scheptical. Intermediary as client. Others may come in. Need to wrap in anyway. Queue length of 1 has problem with intermediaries.
Carsten: doing this without support is not catastrophic
Dave: would rather keep simple. If client asks for stateless one and who path doesn't support, you get error/failure.
Carsten: problem is you would not have way to tell; what do you do with proxy 1
Dave: that's where you lost me.
Carsten: fw proxy knows nothing about where the message comes from
Dave: slide is under-specified; have to deal with path changes in middle of things. 
Carsten: Fw proxy, so every proxy is aware of the next hop
Dave: can change but you just know when they changed

Dave Robin: what is the short red line on the client (sl 9)?
Carsten: token goes to ultimate server, proxy 3 can keep state
Dave R: there is no alternative, I don't like this. Extra token works in all places?
Carsten: no you are in the same situation, beause the proxy does not support the option
Dave: tokens are not safe to forward but are forwarded?
Carsten: safe to forward *when you dont know what it means*. Safe to forward bit to indicate if elective for proxy to understand.
Dave R: seems layering is the safer version even if it takes more space. Involved in very similar discussion earlier.
Carsten: proposal (sl ?) <- we know this is the right way to do it, but ... (missed it)

Carsten: Klaus proposes: write this up. (in particular explain slide 9) 
Needs to be done by BKK.
Dave R: not being able to not recover at all is bad. You have one or two slots for state. If can't do stateless because next doesn't. You start dropping stuff. In few minutes could work. But in this refuse to keep any state and will not get the message.
Carsten: yes with the amendment you keep one state, you know it will work.
Dave T: is there a case for client to need a token larger than 8?
Carsten: the client might be in the same situation.
Dave: sounds like answer is: when CoAP client is acting as intermediary.
Carsten: which most devices do
Matthias: What about NSTART=1? To send multiple request (NSTART>1), the client needs CoCoA or similar. In this case we do not talk about highly constrained devices that must be stateless. Conversely, with NSTART=1, we should be able to expect the client to store the state for this one open request.
Carsten: good question; but think we have this covered. Sympathy in the room that it is worth for authors to write this up. Has to be done quickly. Who would be willing and able to review? August time frame: - Peter vdS, Jim, Dave R. 

## Housekeeping cluster (12)

### Too Many Requests response code for CoAP

  * draft-ietf-core-too-many-reqs-02    new  2018-07-02    Active

Presenting the changes since IETF101 (see slides)

Carsten: we should not delay this unnecessarily. Can we do WGLC?
Ari: we did, ended today
Carsten: do we need another one?
Ari: very similar version. One update to fix the typo but after that we are ready to go forward.

Peter van der Stok: the related is not very clear to me.
Ari: it would be up to the application to have that knowledge. you would not have to use this similar method at all, only for the application it would make sense. in the current spec we cannot define what is "similar enough"
Peter: ok

Carsten: fix the typo, then chairs ship to IESG. (there is still the IETF LC) Anybody have a problem with that?
No rejection from the room

### Multipart

  * draft-ietf-core-multipart-ct-01    new  2018-07-02    Active

Replaces a number of proposals including Maybe.
Needed for EST over CoAP.

Time for WGLC? Objections?

Peter vd Stok: very much in favor for WGLC. Would like to do a request for early registration for content formats
Carsten: there is a procedure and we just follow it

Alexey: just follow procedure?
Jim: are you going to ask something 0-255? then you don't need early registration, just ask AD. Over 255 needs early reg.

Assumption: WG think this doc will happen.

### Proactive

  * draft-bormann-core-proactive-ct-00    new  2018-07-02

Should start registering all sensible available media types.
With less than 2000 media types and 64k code points, we can "waste" some.

Alexey: what problem trying to address?
Carsten: the threshold. Person needs to exercise a process they don't understand.

Ari: it makes sense 
Matthias: didnt have the time to read the draft, but followed the discussion and repeatedly had the problem of missing Content-Format numbers.

Jaime: anybody have a particular problem with adopting this?
No objections
Jaime: we will do mailing list poll


Carsten: missed many presentations. Will start virtual interims.


# End of meeting (out of time)


## Active (14):

  * draft-ietf-core-coap-pubsub-05    new  2018-07-02    Active
  * draft-ietf-core-dynlink-06    new  2018-07-02    Active
  * draft-ietf-core-interfaces-12      2018-06-26    Active
  * draft-silverajan-core-coap-alternative-transports-11      2018-03-05
  * draft-silverajan-core-coap-protocol-negotiation-09    new  2018-07-02  
    (what is needed to be ready for WG adoption?)


## New work: Congestion control, continued (14)

  * draft-jarvinen-core-fasor-00    new  2018-07-02

Σ 60

# No Agenda time in IETF 102

## Not discussed this time:
  * draft-birkholz-core-coid  -00    new  2018-07-02
  * draft-dorfner-core-simplemetadata  -00      2018-04-16
  * draft-urien-core-blockchain-transaction-protocol  -00      2018-03-02
  * draft-urien-core-identity-module-coap  -04      2018-06-25
  * draft-urien-core-racs  -11      2018-06-12

## Last IETF:
  * draft-wang-core-opcua-transmission  -03      2018-03-03
  * draft-mattsson-core-coap-actuators  -05      2018-03-20
  * draft-bormann-core-ace-aif  -05      2018-01-18
  * draft-amsuess-core-rd-replication  -01      2018-03-02

## Replaced by other drafts:
  * draft-hartke-core-pending  -02      2018-02-26

~~~
