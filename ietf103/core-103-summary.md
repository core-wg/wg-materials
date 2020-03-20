CoRE WG — Summary IETF103
=========================

(Constrained RESTful Environments WG, Draft Minutes 0.1)

The **core** WG held two meetings at IETF 103 in Bangkok, both of
which are summarized in these minutes.

* Video Recordings: [Session 1](https://www.youtube.com/watch?v=fXr6EpE88uc),
[Session 2](https://www.youtube.com/watch?v=e1LynPQvYgw)

* [Slides](https://datatracker.ietf.org/meeting/103/materials/slides-103-core-consolidated-slides/)

* Raw minutes at
 [Etherpad](https://etherpad.tools.ietf.org/p/notes-ietf-103-core?useMonospaceFont=true)
  are incomplete (etherpad problem).  We have Etherpad minutes for
  Thursday only.  See also end of these minutes for offline minutes on
  Monday.

## MONDAY, November 5, 2018: 1350–1550

### Published

* draft-ietf-core-senml is now published as RFC8428.

### In IESG processing

* draft-ietf-core-links-json may be pulled back in favor of
  developing CORAL (draft-hartke-t2trg-coral) as the preferred
  hypermedia solution.  Next step is WG adoption of the CORAL
  document; decide then.

* draft-ietf-core-cocoa has been pulled back from the IESG.  In
  London, misunderstandings of the algorithm defined by the document
  surfaced, and it now has become clear that even the author didn't
  quite have the same views.  This puts the copious empirical results
  in some question, and these will need to be reexamined before
  resubmitting the document.  At the same time, there is a proposal
  for a second advanced congestion control scheme (FASOR, see below).

* draft-ietf-core-object-security (OSCORE): Many reviews from the
  IESG followed by a trickle of comments from one DISCUSS holder,
  which triggered a sequence of updates towards current –15.
  Additional comments were received just last Sunday.  This DISCUSS
  has not yet been cleared.  Carsten pointed out that it is hard to
  shepherd this document as we are getting the feedback only in small
  bits.  Padhu pointed out that for OMA, this document is needed done
  as soon as possible  as it is part of OMA LWM2M 1.1.

* The changes in draft-ietf-core-too-many-reqs resulting from IESG
  processing were briefly presented by Ari Keränen.
  (The document has since been approved by the IESG.)

### Completed WGLC

* The status of draft-ietf-core-multipart-ct was briefly
  presented by Carsten Bormann.  After comments, the agreement is now
  to remove the "null" alternative, further simplifying the document.
  In the discussion, the question came up whether reintroducing this
  would necessitate a new media type; AD Alexey Melnikov pointed out that
  backwards compatibility is required.

### Candidates for Adoption

* draft-hartke-core-stateless: This actually passed WG adoption,
  waiting for resubmission as a WG draft.

* draft-bormann-core-corr-clar is a proposal to maintain a
  running document with corrections and clarifications to the WG RFCs,
  similar to the role the drafts leading up to RFC 4815 played in ROHC.
  This is intended to run for a few years and may never be published —
  the content could then move into updates of the RFCs.
  If adopted, it might need to define a process for assigning status
  to entries.

### OSCORE, continued

Based on the OSCORE document currently in IESG processing, documents
discussing group communication and discovery are available.

* Marco Tiloca presented draft-ietf-core-oscore-groupcomm.
  This is moving forward smoothly, with first implementations planned.
  Marco said that an interop event in summer 2019 would be possible,
  with something already testable over the Internet earlier than that.

* Marco also presented draft-tiloca-core-oscore-discovery, which
  was started from input at IETF 102:  OSCORE Group Manager registers
  itself with the RD, together with the links to its own join
  resources to join its OSCORE groups.  A joining node performs a
  resource lookup at the RD to retrieve the links to the join
  resources at the Group Manager, together with related information.
  Using observe can be convenient for getting updates and handle
  devices deployed before the Group Manager or before group creation.
  Jim asked how the use of groups in the RD relate to the plan to
  remove groups from RD; Marco clarified that his approach does not
  need the (old) RD groups and he has an update in mind that uses
  normal registrations.
  Carsten Bormann states that this is a good work and he would like to see
  comments and feedback.

* draft-ietf-core-echo-request-tag has been reviewed by Jim Schaad
  and is believed to be ready for WGLC.

* draft-mattsson-core-coap-actuators might be a candidate for
  inclusion in either draft-ietf-lwig-coap or
  draft-bormann-core-corr-clar.

### Resource directory

* Christian presented draft-ietf-core-resource-directory from remote.
  The special concept of groups will be removed, as it does not seem
  current designs need all the functionality; what is needed can be
  mapped to registrations with group addresses.
  Instead of trying to redefine RFC 6690, the specification will now
  simply define what subset of RFC 6690 can be safely used.
  To be validated on the mailing list.

* Peter presented draft-ietf-core-rd-dns-sd.  The mapping between
  resource discovery and service discovery has been clarified.
  Dave Thaler commented that the mapping is actually easy on one
  direction but not in the other one (resource type names are more
  complex).  Peter mentioned that an alternative may be to define a
  new parameter, so there is no need for a mapping.

### CORECONF

* Peter gave a quick update on the policy behind draft-ietf-core-sid.
  To send data described in a YANG spec over constrained networks, the
  YANG names are reduced to shorter SIDs, then encoded in CBOR.
  SIDs can be registered and allocated in an RFC but then they cannot change.
  The proposal is to ask IANA to provide an extension to the YANG
  parameter registry, with an additional SID module sub-registry.

### Pulled forward from Thursday

* Jari Arkko presented the updates to draft-ietf-core-dev-urn.
  There were no major changes, except that %-encoding was disallowed again.
  Remaining questions focused on the best way to align with existing
  usage in LWM2M.


* Abhijan Bhattacharyya presented
  draft-bhattacharyya-core-a-realist. a video streaming system
  using CoAP.  CoAP turned out to be useful to manage video quality in
  the presence of impairments.  The way CoAP is being used here merits
  some further discussion in the WG.



## THURSDAY, November 8, 2018: 1120—1220

The meeting continued on Thursday; where the above drafts were taken
up again, the discussion is already documented above.

### Active drafts

* draft-ietf-core-hop-limit: Carsten relayed that this is being
  discussed for being ready for working-group last call.

* draft-ietf-core-senml-etch was presented by Ari Keränen.  The
  main question remaining is if we should use the same media types as
  SenML proper or different ones; and, if the latter, whether we
  needed the full complement of XML, EXI, JSON and CBOR.
  Padhu noted that CBOR is the way to go forward; Zach responded that
  it is probably worth keeping both JSON and CBOR.
  While there was some support for re-using the old media types, it is
  not clear that the patch documents actually are valid SenML.
  This also meshed with the other open question, the specific way to delete
  a record with PATCH.  This should probably be compared with CORECONF
  and a common view should result.

* The presentations of draft-ietf-core-interfaces and
  draft-ietf-core-dynlink were uneventful.  For the latter, an
  implementation of conditional observe was now added, which provided
  some new insights.

* draft-ietf-core-coap-pubsub: An update is needed (relatively
  urgent).  There was good feedback so far.  An interim mini-plugfest
  is next; Carsten proposed to figure out plugfest logistics
  online and asked Michael to update the document for that.

### Deferred from IETF102

* Ilpo Jarvinen presented draft-jarvinen-core-fasor, a new
  advanced congestion control algorithm for CoAP based on state
  transitions between a fast, a fast-slow, and a slow state.
  Carsten
  explained how the WG will need to handle the IPR declaration
  (https://datatracker.ietf.org/ipr/3227/).

### Other new work

* Carsten briefly pointed to draft-birkholz-core-coid, which
  enables the use of CWT technologies to encode assertions
  traditionally handled using X.509 certificates.


# Raw minutes

## Monday

Thanks, Marco Tiloca!

Intro, Agenda, Status

WG and document status

draft-ietf-core-senml published as RFC8428


draft-ietf-core-links-json:

- Work in progress to address IESG feedback, be more genera from RFC6690 limitations, consider CORAL as more likely ultimate target
- CORAL is optimized for small devices
- Jim, Ari, Mathias. Jaime and Christian would reiew the document if CORAL is actually taken as direction (to be decided)
- Next step is WG adoption of the CORAL document
- Zach: this seems a bit indirect
- Carsten: Then it might need some discussion first


In IESG processing

draft-ietf-core-cocoa:

- Good feedback from the AESG, need to address towards a version -04
- A new work about congestion control has been proposed, namely draft-jarvinen-core-fasor


draft-ietf-core-object-security:

- Many reviews from the IESG followed by updated towards current -15
- One remaining DISCUSS to address


draft-ietf-core-too-many-reqs-05:

- Ari presents
- version -06 is work in progress
- Clarifications about re-usage of Max-Age an IANA registration
- Clarifications about service behavior, as per answers to clients
- Clarifications about client behavior, as per Max-Age interpretation
- Extended text on security aspects
- Open point on Proxy policies to avoid a client starving other clients
- Alexey: when can (an update) be ready? --> Soon, likely tomorrow, there seems not to be particular issues still open
- Dave Thaler: ???
- Carsten: Point out why this is a little more complicated than we like, due to the server not keeping states for clients
- ? : How is this working in practice right now? --> Not much, but based on implementations it seems to work better than just 5.03 saying to clients that something is going wrong

------------------

Completed WGLC

draft-ietf-core-multipart-ct-02:

- Carsten presents
- Gone through comments from Klaus, suggesting to possibly remove some parts/examples
- Jim: how would the application handle the usage of a null value for the representation of an absent optional part
- Alexey: the current proposal is deviating from mine, better to keep it simple, not clear that it is needed
- Carsten: do we need a new media type?
- Alexey: depends on the type of content you want to have; you need to ensure backward compatibility anyway
- ? (Nokia): does it apply a single time or multiple times?

------------------

draft-hartke-core-stateless-02:

- This passed WG adoption, waiting for resubmission as draft-ietf
- The chosen way to go is considered the best one for the targeted ecosystem
- 5 people read this version of the document


draft-bormann-core-corr-clar-00:

- Do same as done in RFC 4815, so describe corrections
- Intended to run for a few years
- If adopted, it might need to define a process for assigning state to entries
- 2 people have read the draft, need more readers
- Alexey: as an alternative, consider to publish an update rather than this, but it's fine if it's just an internal document for the WG

------------------

OSCORE, continued

draft-ietf-core-oscore-groupcomm-03:

- Marco presents
- Editorial and technical updates
- Not seen any big issues stopping from implementing, only clarifications/considerations are expected
- RISE will start an implementation in Californium
- OSRAM Innovation will start an implementation in C for the Dotdot framework
- Carsten: what's the plan, also timewise?
- Marco: we can aim for an interop in summer 2019, hopefully something already testable earlier than that


draft-tiloca-core-oscore-discovery-00:

- Marco presents
- Started from an input at IETF 102
- An OSCORE Group Managers registers itself with the RD, together with the links to its own join resources to join its OSCORE groups
- A joining node performs a resource lookup at the RD to retrieve the links to the join resources at the Group Manager, together with related information
- Using observe can be convenient for getting updates and handle devices deployed before the Group Manager or before group creation
- Jim: you use resource lookup, I wonder how this relates to taking away groups from the RD
- Marco: in this current version, we don't need the RD (old) groups, we have an update in mind depending on what happens with them in the RD
- ? (Nokia): any actual use of Group OSCORE in this work?
- Marco: no, what happens later on in the group is out of scope of this document
- Mathias: RD is supposed to be modular and extendable, so not necessarily needed to be limited to a resource lookup
- Marco: ok, although the resource lookup is (right now) everything we really need
- Carsten: and also not needed to introduce or use an extension if not required
- Nobody has read the draft
- Carsten: this is a good work, I would like to see comments and feedback


draft-ietf-core-echo-request-tag-03:

- We can go for WGLC, this document looks ready
- Jim and Francesca can provide reviews and comments


draft-mattsson-core-coap-actuators-06:

- Need to improve the common understanding on this document

------------------

Resource directory

- Christian presents remotely
- Update to security policies, pug test successful (groups not tested), editorial
- Redefined interpretation of links from RFC 6690
- About groups, better to consider a group as almost an endpoint, with no members registered but resources. Then one can look up for group resources, i.e. exported by a group application
- Zach: we used to have groups collecting membership due to feedback from the industry through Peter. Now this new model for group seems a ligher way to solve the same problem.
- Mathias: is more than the subset in RFC6690 something that is really wanted?
- Peter: the lighting commnunity has no objection to the new group model
- Carsten: we should raise these questions in the list, and then go for WGLC

------------------

RD-DNS-SD

- Peter presents
- Clarified mapping between resource discovery and service discovery
- Dave Thaler: mapping is actually easy on one direction but not on the other one (arbitrary mapping of resource types)
- Peter: an alternative is to define a new parameter, so there is no mapping

------------------

Protocol negotiation

- Peter presents
- Content of YANG specs sent over constrained networks
- YANG names reduced to shorter SIDs, then encoded in CBOR
- SIDs can be registered and allocated in an RFC but then they cannot change
- Ask IANA to provide an extension to YANG parameter registry, with an additional SID module sub-registry
- ?: this is all well aligned

------------------

draft-ietf-core-dev-urn-03:

- Arkko presents
- No major changes, disallowed &-encoding
- This is formally defining parts of LwM2M, tell now if there's any problem with some deployments
- Ready for WGLC?

------------------

draft-bhattacharyya-core-a-realist-00:

- Abhijan presents
- Use case: steaming of real-life person view over the Internet
- Goal: single RESTful protocol good for high QoS for both small sensor data and real-time stream
- Use CoAP and its options to this end

## Thursday

### Intro (4)

- CB: Introducing session.

### other security (10)

* draft-ietf-core-object-security-15 ➔ 
Waiting for DISCUSS to be cleared

    - GS: Delays at the AD level, feedback received only last Sunday.
    - CB: From the chairs pov it is hard to shepherd this document as we are getting the feedback only in small bits.
    - Padhu: from OMA's pov we would need this document done asap as it is part of OMA LWM2M 1.1

* draft-ietf-core-echo-request-tag-03 ➔ WGLC
    - GS: We got comments from Jim and we believe it is ready.
    - CB: Who has read a version? 5
    - CB: To go to WGLC now.

* draft-mattsson-core-coap-actuators-06 \[~5] ➔ To be integrated into lwig-coap or corr-clar
    - \[Objective: a) Report remaining issues; b) Ask for adoption]
    - GS: Should we continue, drop?
    - CB: this document could be integrated on lwig-coap or corr-clar.
    - GS: OK

## Active (21)
* draft-ietf-core-hop-limit-00 ➔
    - CB: Submitted and discussing if ready for WGLC

* draft-ietf-core-senml-etch-00 \[~10 min] ➔
    - \[Objective: new media types OK? Method for delete? Ready for WGLC?]
    - Ari presenting
    - AK: Question is if we should use the same media type or different ones.
    - AP: In favour of the same mt.
    - Padhu: CBOR is the way to go forward.
    - Zach: Worth keeping both JSON and CBOR.
* On deleting with PATCH:
    - Alexey: Fine with choices.
    - AK and AP: Need to look into COMI is doing this.
    - AK: Pending from OMA pov.
    - CB: Implementation?
    - AK: Interop in OMA.
    - CB: Can be done in 2 hours.
    - AK: Request to the floor.
    - CB: Send to list.

* draft-ietf-core-interfaces-13 ➔
    - Incorporate feedback received.

* draft-ietf-core-dynlink-07 ➔
    - Implementation of conditional observe. New learnings from the OCF code.

* draft-ietf-core-coap-pubsub-05 ➔ Update needed (relatively urgent).
    - Good feedback. Interim mini-plugfest.
    - Jim Schaad: new version of the draft is needed. -05
    - MK: ??
    - ...
    - CB: Figure out plugfest logistics online. Michael if you could update the document...

## Deferred from IETF102: (20)

* draft-core-cocoa ➔ Back to WG
    - CB: new finding on congestion control, missunderstanding btw authors and empirical simulators.

* draft-jarvinen-core-fasor-01 ipr ➔
    - Jarvinen presenting. FASOR (Fast-Slow RTO), not vulnerable to congestion collapse.
    - Note: exponential backoff works but do not retain the backed off RTO.
    - Has IPR https://datatracker.ietf.org/ipr/3227/

## Other new work (5)

* draft-birkholz-core-coid-00

