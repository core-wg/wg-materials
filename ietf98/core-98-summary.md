CoRE WG - Summary IETF98 {#toc_0}
========================

Slides: <https://www.ietf.org/proceedings/98/slides/slides-98-core-consolidated-slide-set-02.pdf>

Raw minutes: <http://etherpad.tools.ietf.org:9000/p/notes-ietf-98-core>

Summary below, followed by detailed minutes.

Tuesday 2017-03-28 {#toc_1}
==================

## WG status

-   RFC8075 (Guidelines for Mapping Implementations: HTTP to CoAP)
    published.

-   draft-ietf-core-etch: To become RFC8132, in AUTH48 as of time
    of meeting.

-   draft-ietf-lpwan-coap-static-context-hc (LPWAN work item) was
    briefly presented, the authors are looking for feedback about
    whether the compression works.

-   Multiple Interops are being planned. Virtual format to occur about
    monthly until Prague.

    -   OSCOAP interop event already took place during February and
        during Hackathon this week.
    -   Interest for the organization of other interops as well was expressed:
        -   Organization of interop event for CoAP-TCP/-TLS/-Websockets?
        -   Organization of interop event for Links-JSON?
        -   Organization of interop event for Etch?
        -   Organization of interop event for SenML?

## Post-WGLC drafts

-   draft-ietf-core-coap-tcp-tls–07: undergone 3 versions since the
    first WGLC and submitted to IESG, –08 soon to resolve a few
    editorial issues.  Still some nits to be worked out on the CSM
    messages. There is interest to make an interop, need to work out
    the details before IETF99.

-   draft-ietf-core-links-json-07 2nd WGLC finished. (Since has been
    sent to IESG.)

## Maybe WGLC (15)

-   draft-ietf-core-cocoa-01 document ready for WGLC, we will take it
    to the mailing list. Suggestion is to contact other groups like
    TCPM WG and IRTF ICCRG in the WGLC for comments.  (Running code in
    Californium/Java, Erbium/C, an Android port of libcoap/C.)

-   draft-ietf-core-resource-directory-10.

    - The discovery of RD itself seems to be problematic in some
      scenarios as there are maybe too many ways for a CoAP server to
      find RD instances to register to.  A smaller set is desired.
    - To move the document and track the remaining issues the chairs
      have asked Christian Amsüss to act as document editor of the RD
      document.
    - There was a proposed split of the RD document to have the DNS-SD
      part in a separate document, to be operated on in the same
      timelines.  Although there was high consensus on the importance
      of having normative text on DNS-SD there was some opposition to
      the split.  Discussion to be taken to the mailing list.  (A lot
      of hallway discussion happened during the week, too, now with a
      rough consensus between the authors of the various parts to go
      for the split.)

## COMI

-   draft-ietf-core-yang-cbor-10: there was in room consensus on the
    document being ready for WGLC. Will be taken to the list for
    confirmation.

-   draft-veillette-core-yang-library: there was not enough people in the
    room who have read the doc to have consensus on WG adoption.

-   draft-ietf-core-comi: A discussion on PATCH formats led to a rough
    consensus to go for the simple array of ID-value pairs for now.
    Further PATCH formats can be added.  (Notification is noted as an
    interesting next item of work.)
    (See also Friday.)

## Object Security (Tuesday and Friday)

-   draft-ietf-core-object-security-02: Per packet overhead and memory
    usage reduction in –02.  Two interops have been held (see above)
    where 2 implementations have been tested. Blockwise transfer still
    under discussion (rolling MAC already covered?).  The addition of
    a request-tag option to OSCoAP was received positively
    (draft-amsuess-core-request-tag) but in need of more work.  A bit
    of concern by one of the coauthors about the size of the document.
    Work based on interops will continue.  Target is to have WGLC
    before Prague.


Friday 2017-03-31 {#toc_2}
=================

-   draft-vanderstok-core-coap-est was presented. It specifies
    Enrollment over Secure Transport (EST) over CoAP in ACE
    WG. Discussion: The use of 2.06 as response code would create
    another code for retry (5.03 is the current code).

-   draft-becker-core-coap-sms-gprs-06: New interest from original
    authors, additions to the team.  Interested in the room to
    complete this now.  Key remaining problem is how to identify an
    SMS that carries CoAP.

-   draft-ietf-core-sid–02 had a discussion with IANA on the range
    allocations for this document. Some more work needed to figure out
    the remaining details for working with IANA.  More examples,
    reflections on the discussions held with the NETMOD group to reach
    wider adoption to be added to document. Documentation of the
    automatic SID registration as well as a reference to RFC5226
    should also be added.

-   draft-mattsson-core-security-overhead provided good empirical data
    on the overhead between TLS/DTLS/OSCOAP.  OSCOAP overhead
    significantly lower than (D)TLS even with various types of
    compression.  This document is still changing; it may live best as
    a wiki on the WG github organization; Carsten to set up.

-   draft-ietf-core-object-security-02 (added to Tuesday above)

-   draft-tiloca-core-multicast-oscoap: informally discussed in IETF95
    the draft defines the use of OSCoAP for Group
    Communication. Looking for reviewers.

-   draft-hartke-core-e2e-security-reqs useful informative document.
    Need more volunteers to review the draft (Dave Thaler, Merike).

-   draft-ietf-core-senml: small update over the last
    version. Discussion on adding specific information on RSSI ended
    up with a decission on not adding anything extra. The use of +exi
    suffixes needs discussion. AD ok with sponsoring this document.

-   draft-ietf-core-coap-pubsub looking for reviewers. Brokerless case
    could use an extended OSCoAP Profile for pubsub. Some new issues
    with QoS and missed publications, edits on the URI template and
    mandatory operations for the broker.

-   stateless-proxy option: Work was presented that happened in the
    context of draft-ietf-6tisch-minimal-security.  The proposed
    stateless-proxy option allows a proxy to hand off state to a
    server, allowing it to operate statelessly (important for security
    in the unsecured join process).  Discussion about having multiple
    proxies in a row, does the option have to be repeatable?  Some
    interest in continuing this work.


# Detailed minutes

Thank you to the note takers!

~~~ text/plain
CoRE WG Meeting

IETF 98 - Chicago
TUESDAY, March 28, 2017
1300–1430 Afternoon Session I: Zurich C
Chairs: Carsten Bormann, Jaime Jimenez
Jabber: Francesca

Note takers: Jaime, Ludwig, Matthias, Alex, Ari
Links:
    https://github.com/core-wg/
    https://datatracker.ietf.org/wg/core/documents/
    https://www.ietf.org/proceedings/98/slides/slides-98-core-consolidated-slide-set-00.pdf to -02.pdf

Intro (10)
Agenda bashing, WG status

Carsten presents agenda

Carsten: Milestones == Swiss cheese

Mention RFC 8075, draft-ietf-core-etch

HTTP mapping - RFC 8075
ETCH 8132 TO BE: Fetch/Patch in AUTH48.

* Static Context Header Compression** for CoAP, Laurent Toutain

CoAP compression draft-ietf-lpwan-coap-static-context-hc

Works for LPWAN because of its star topology and limited number of network flows.
Take particular attention to compressing assymetrical trafic (CoAP is assymetrical).

Comments welcome whether this works. Meeting tomorrow 1pm to discuss

Carsten: good for CoAP to enter millibit networks. But need to make sure CoAP is not destroyed.

# Time for interops

OSCOAP has had two virtual interops, other nearly finished drafts should follow lead.
Francesca will say something during the OSCOAP slot on this.

Carsten: who interested to participate in interops?

OSCOAP: 4 people
CoAP-TCP/TLS: jim, hannes, carsten, olaf  (plus OMA).
Links-JSON: 2
ETCH: 2
SenML: 3

Carsten: Virtual interops once a month. End of each month, next physical one in Prague. Could ETSI support?
Carsten: Who thinks that is a good idea?  (5 people)

Post-WGLC (15)
(brief update) draft-ietf-core-coap-tcp-tls –07 2017–03–06
(Note: closed issues https://github.com/core-wg/coap-tcp-tls/issues?q=is%3Aissue+is%3Aclosed+milestone%3Acoap-tcp-tls-06 )
(Note: Interop to be organized in the future)

Resolved problem with securing CoAP: some solution is mandatory to implement (not specified which)

Status: submitted to IESG for publication.

AD Alexey completed (secret) review.

Alexey: nits only. Question on CSM messages. Hand-waving on version numbers. (Note: version negotiation issue is https://github.com/core-wg/coap-tcp-tls/issues/20 )
Carsten: often don't solve the problem that needs to be solved. Putting in version negotation now sounds wrong. Hooks for extensions mechanisms to do that if later needed.
Alexey: Probably can find text for this if WG wants it. CSM message not going to change in the future. New options don't require format to change. If change, just need new mapping.
Carsten: needed in the doc?
Alexey: don't feel strongly for now. No need to block the doc at this moment.
Brian: captured in the issue
Dave: OCF depends on this draft. Not yet in certifiable way. OCF wants this done sooner than later. For interop event, what application layer on top of this?
Carsten: What would be in the test cases?
Dave: OCF uses different discovery than CoAP; can't just take OCF implementation and expect to interop.
Hannes: Agree with Dave, what exactly are the test cases? Should be possible to do interop anyways. For example with OMA LwM2M and OCF since the protocol stack is the sam e.
Carsten: About a month to make the test description and prepare the interop. CoAP TCP also testing the GitHub process. Worked well. RD draft next victim to go for this.


(results of 2nd WGLC) draft-ietf-core-links-json –07 2017–03–13
Carsten: Cut down grand claims in the doc. No technical changes. Finished 2nd WGLC. Soon to be sent to IESG.

Maybe WGLC (15)
(new appendix, WGLC now?) draft-ietf-core-cocoa –01 2017–03–13

Carles presenting CoCoA.
Document mostly stable, new appendix B, update of weak estimator discussion.
Question to WG: should appendix B be included in published document?

Matthias: was published in papers so citing them should be enough.
Carles: something shorter than in paper?
Matthias: something short is fine too

Running code: Cf, Er, libcoap4Android+Cocoa
Authors think ready for WGLC (minus appendix A, which is to be extracted in a separate document)

Carsten: who has read the doc? (two hands)
Carsten: interesting to involve other groups such as TCPM and Internet measurement research group.
Jaime: will take WGLC question to the mailing list and will contact the other groups.

(call for review) draft-ietf-core-resource-directory –10 2017–03–13
(Note: https://github.com/core-wg/resource-directory )
(Note: proposed splitted repo https://github.com/core-wg/rd-dns-sd )

Carsten: stable, in use (partially).  Question from Seoul: Splitting off DNS-SD into separate doc

Carsten (as individual): propose to continue with split. (chair hat back on) Cluster of docs that will be worked together.
Kerry Lynn: Against split, discovery mechanism was not part of the charter. Peter Vanderstok and me discussed for two years on this part. We anticipated that RD would be a way to centralize this information, DNS-SD was done to proceed on the WG.
DSN mapping is straightforward. Just specifies semantic mapping to have 1:1 way to do this. Current charter does require us to come up with way to export these to DNS-SD. Would like to see these published together. The consensus from Seoul was not discussed on the list.
Carsten: agree with last point

Akbar: Don't think it should be split. Going to be more confusing.
Stuart C: Thanks to Kerry for the work done. Puzzled when CoRE community said that while there is service discovery infra, decided to do a new one. Semantic mapping established by Kerry is valuable. Apple is now getting involved in home automation. At Thread group meeting had discussions on SD. Folks didn't know DNS could do all that. Wondering why using CoRE links etc. Would love folks to join DNDSD session. Will start with overview of various methods available. Hopefully seeing that architecture presented will make clearer. Splitting the two docs a part may create problems.
Hannes: ARM not using DNS-SD. Don't understand why all working on the SD? Is it used and deployed? We use RD and want that published ASAP.
Stuart: 6Lo has potential to be general networking technology. But needs to have generic service discovery. If want CoAP devices to work with the infra, need way to map these.
Carsten: The proposal is NOT to remove DNS-SD but to split the document.
Dave: OCF depends on this too. Don't reference normatively yet because draft, but would like to. Another technical issue (discusedin T2TRG),  how do you discover RD. Doc have 6-7 different ways. Discovery has been already solved for DSN-SD. Is there ways to improve discoverability? If you use DSN-SD, you don't have to.
James Woodyatt: Echo Dave and Stuart. Interested in how to discover RD. Open problem that causes grief.
Hannes: Question to Dave: Dependency on OCF, what part?
Dave: informative dependency now. Limitations using just multicast, e.g., with multiple subnets. Implementation uses non DSN-SD part. CoAP unicast to RD. Don't use CoRE link format but OCF links. Trying to get OCF to converge to IETF tech. Two different formats in RD; but should be able to answer with the right format. Trying to push for non-OCF specific RD.
Hannes: Didn't run into that problem: We have industrial setting, not connecting into random nodes that happen to be on the network.
Jaime: question is not about DNS-SD or not, but about the split. Why not split?
Kerry: split include 2 sections; section 9, attributes that are necessary. Those attributes need to remain in RD. Otherwise node can't even expose that it wants informtion to be there. (missed second). If no instance attributes to separate different sensor types, not sure how to discriminate between RDs. Information vital for exporting to any directory. Many devices have DNS-SD already. Seems one reason behind the split is that some SDO have different approach.
Jaime: agree, should have been on the list. Alternative to have in the appendix. Appendix usually for examples etc. Suprised that not OK with split but OK with appendix. We will take it on the mailing list either way.
Alexey: doesn't matter if in Appendix. Can have normative.
Michael Koster: 3 part that can be separated out: Finding RD with DNS-SD makes sense (missed 2nd).
MIchael Koster comments on RD
1. finding RD using DNS-SD is a great idea and will be happy to add it to the section on finding an RD
2. ins and exp are general functionality which should be included in RD
3. The mapping part and examples showing DNS-SD equivalents might be better as a standalone draft with its own introduction and use case explanation.
Carsten: one thing wanted to achieve with split was to have more DNS-SD folks here; seemed to work. Will make decision on the split on the list.
Carsten: noone against the split noone against Christian as Editor.


comi (20)
Discuss results from Monday’s 15:20 to 16:50 semi-formal COMI meeting
Objective: Which of these can we WGLC now? Where are we with installing a SID process with IANA and other actors needed? [SID] Check status of IANA processes (register SIDs, lookup SIDs).
draft-ietf-core-yang-cbor –04 2017–02–07
draft-ietf-core-comi –00 2017–01–26
draft-ietf-core-sid –00 2016–10–26

Michele V Presenting YANG-CBOR.

Is it ready for WGLC?

Carsten: who has read recent version? (7 hands)
Who thinks ready for LC: few hands (4?)
Who thinks not? 0 hands

Take descision to list, but inroom consensus on readiness.

Alex Pelov: sent some slides that we can use if needed
Carsten: seems enough interest from YANG people that they will look at this in WGLC. Feedback: this may be good enough for big boxes as well. Don't want this to cause feature creep, but interesting to hear that there's interesting to make this happen for big boxes too.

* draft-veillette-core-yang-library

No changes in functionality, just constrained version. Question: ready for adoption?

Carsten: who has read the doc (1+0.5)
Carsten: concern with the doc that is this the right WG to understand thigs? Who speaks YANG (5 hands). Who would be interested to read the doc? (about same set). Don't have enough people in the room who have read the doc to have consensus.
Alexander Pelov: At meeting yesterday there were 17 of people interested in this. Before YANG people didn't speak SID and vice versa. We should work in a very efficient way as the documents are in a good state so that the we can use them for IoT but then routing comunity can adapt them. If we delay the decision, it will (the sense was that it will not be a good thing to do).
Carsten: next step on the mailing list is asking for reviews

* draft-ietf-core-comi (Peter van der Stok)

Which PATCH format to use? More general but slightly more verbose or CoMI specific but more compact?
Alexander Pelov: Clarification? should we wait for something that is not finished and less efficient or use what we already have?
Michele: Why say more efficient?
Peter: especially for delete
Michele: All CoMi based on two methods; this would be departure from that. Reduces code reuse. Current version doesn't support delta-encoding so large payloads. Parsing needs to be schema aware. No deletion of leaf nodes(?). We have great solution already.
Matthias: Do we have to nail this fully down? Could support future versions when available.
Carsten (no hat): What Matthias said. Also, co-author of merge-patch doc. But doing something less powerful here could be better way. With using arrays we get symmetry with PATCH and individual PUTs and GETs. For implementations easier to do both. Implementations with GET and PUT but no PATCH could be issue.
Peter: will go forward with the existing less efficient approach

Notification payload: Array with several notifications, what about single? Need one-item array?

Michelle: plan to put YANG module dedicated to generic information notification. Time of event etc. That would be handled as YANG module within the protocol.

object security (30)

Report of the Interop (Summary)
Updates on the bigger changes on v –02
Confirm results of inner-blockwise discussion, cf. http-encryption
Objective: ➔ more interops + WGLC before or right after Prague.
draft-ietf-core-object-security –02 2017–03–13

Carsten: lots of references to OSCOAP work. Number of docs with normative references, and informative too.
(Note: https://datatracker.ietf.org/doc/draft-ietf-core-object-security/referencedby/ )
(Note: https://github.com/core-wg/oscoap)
Francesca presented OSCOAP.

Draft status: https://github.com/core-wg/oscoap
Check issue tracker! Few issues that require more CoRE feedback.

Two interops:

    1. Feb  2 implementations, good feedback
    2. Mar. at hackaton

Blockwise issue: no difference in multiple concurrent requests. Christian (via Meetecho) will present.

Göran relaying Christian: based on request-tag, analog to e-tag. Attacker can delay a block. Replay would not be detected.

Carsten (no hat): This would be detected by DTLS
Göran: not within the replay window
Carsten (still no hat): True. Good to make explicit this is about Block1. So far the best solution I've seen on this.
Göran: Document on Request Tag https://tools.ietf.org/id/draft-amsuess-core-request-tag-00.txt

Francesca: Next steps: More (coap expert reviews) welcome, more interops, then WGLC
Carsten: who has read the request-tag (3 persons); was submitted yesterday. Good for base COAP implementors to read this. Seems like good way to solve the problem.
To be taken on the mailing list.

Carsten: WGLC target is in Prague. 20 issues open, sure that no more will open then?
Göran: blockwise issue is example how we find corner cases in CoAP when building security there. Would be perfect if CoAP Blockwise, Observe etc authors look at this to make sure we've made the right assesment
Dave T: OCF was looking into this. Could have hallway / bar BoF discussion on this. OCF is reviewing this.

(session adjourned; will continue on Friday)

What does the WG want to do with (the subjects of) these documents:
draft-hartke-core-e2e-security-reqs –02 2017–01–06
draft-mattsson-core-security-overhead –00 2017–03–13
draft-tiloca-core-multicast-oscoap –01 2017–03–13


----

Day 2:

Note takers: Ludwig, Ari, Matthias

Spillover agenda: Peter, Michel, Francesca

Thomas Fossati: Is SMS on agenda? Need to leave
Carsten: yes, PvdS first though


CoAP-EST: draft-vanderstok-core-coap-est
Pending response code -- Peter v. d. S.
See presentation: https://www.ietf.org/proceedings/98/slides/slides-98-core-consolidated-slide-set-02.pdf

Peter: Is this useful for the WG?
Ari: Looks interesting; could be useful for pub/sub broker
Dave Robin: Looks useful, can you go into detail about redirection?
Peter: in response there's location that is attached to the server side. If more flexilibity needed, needs to be added. Location at different site not supported, not full URI
Dave: Why redirect to other resource on same device?
Peter: Good for maintainance (for example /tmp1, /tmp2, etc)
Dave: Was intrigued by sending the client somewhere else; same server seems less useful
Carsten (no hat): We have 503 in CoAP, this would be other way to indicate need for retry. Does every CoAP client need to understand this? Need to discuss a bit more.


--

(jumping to slide 136 for SMS GPRS doc)

Transports
draft-becker-core-coap-sms-gprs-06


Carsten: Original author changed jobs... was picked up by LWM2M. Need to get new editor team.
Thomas: want to help with this. Getting to contact with current set of authors. This is important. Usage in LWM2M Need both dtls and object security.


Carsten: There are new editors. Now self-contained. You want to finish this? Who would like to finish this?
ThomasF: Yes-> Jaime, Kerry, Alexander. Issue would be if we need to register code in ETSI if needed.
Carsten: sufficient amount of people who want to finish this.
Carsten: Key problem is how to identify an SMS that carries CoAP

--
draft-silverajan-core-coap-protocol-negotiation
Carsten: Not going to discuss here. Will do in Prague. Becoming interesting since we have multiple transports now.

--

Back to page 82

COMI report, Alex Pelov
Discuss results from Monday’s 15:20 to 16:50 semi-formal COMI meeting

Was a lot of interest in the room.
Most are converging on CBOR for binary.
Recommendation from NETMOD: SIDs MUST be 64 bit

presenting update of draft-ietf-core-sid based on input from Monday meeting.

Slide 88:
First 2 points stable
Latter 2 points need adjustments

Mega-ranges!
Rules for IANA allocation

Juan-Carlos: Experimental is temporary registration?
Alex: will be temporary; for development use. Not policed by IANA.
Carsten: should never leave the lab
Alex: can be conflicts etc.
Dave Thaler: RFC for this IANA allocation explains this; best cite it  (Jabber: RFC 5226 is the RFC that defines the various IANA terms ("Specification Required", "IETF Review", etc.) and it references the following for Experimental: [EXPERIMENTATION] Narten, T., "Assigning Experimental and Testing Numbers Considered Useful", BCP 82, RFC 3692, January 2004.)

Questions to WG: Ok to introduce mega range, readjust sizes?
Need more examples in appendix
Meet at IETF99 with NETMOD

Carsten (w. hat): Question came up in the meeting; Shouldn't that be done in NETMOD. NETMOD folks protested; NETMOD know how to do network devices but not constrained devices.
Alex: We agree on many of the main principles
Carsten: SID document should reflect these discussions.
Alexey: Have you talked to IANA about the suballocation?
Alex: yes, talked several times during the week. Have gone through iterations with the text. And will send the doc to them ahead of time.
Jaime: Automatic SID registration documented somewhere?
Alex: not in draft yet; many caveats. If try to solve here, would slow down the draft. For the second million can integrate this automatic allocation to policy. Want to have way for machines to automatically register IDs. Problems with space exchaustion that need to be solved. Need rate limitation. Can be used for the first few blocks; if doesn't work, go back to drawing board.

--

John Mattsson  Message Size overhead of CoAP security protocols
draft-mattsson-core-security-overhead

presents different TLS/DTLS/OSCOAP overhead numbers (partially dependent on seq. numbers)
OSCOAP overhead significantly lower than (D)TLS with compression.

Carsten (w. hat): what's way forward with this?
John: what WG wants?
Carsten: seem useful; maybe OSCOAP appendix

Mohit: Useful for LWIG?
John: Can present at IETF 99 in LWIG
Dave Thaler: WG wiki?
Carsten: Set up a wiki! Use github might be good way to maintain this. Could be WG landing page (like HTTPbis).
John: can maintain the numbers when you put them somewhere

--

Francesca draft-ietf-core-object-security

presented on Tuesday, went fast due to time running out.

page 6: Describe the changes. Reduced the packet overhead.
COSE objet compression, no sequence number in responses, sender id is sent in requests.. all in slides.

Blockwise issues and Request-Tag outstanding issues
Carsten: yesterday BarBof on FUD (Firmware Update). Briefly touched on the question of rolling MAC. Need to be able to check blocks before you have the whole message
Francesca: needs to be addressed in OSCOAP. Either put in a different draft and OSCOAP will have a normative reference to it, or keep it there.
Matthias: yes, for Block2 need e-tag. No equivalent. Could happen indendent of OSCOAP so need in general.
Francesca: doing this in OSCOAP would take longer so separate draft good idea
Carsten (no hat): thing that came up; need to have certain amount of entropy to surive reboots etc. Might want to carry entropy in repeat option proposed by actuator draft. Could reduce overhead by carrying both entropy pieces in same option.
Francesca: suggesting two extensions/tools in one document?
Carsten: separate or new doc but close together makes sense
Ludwig: Speeking as co-author. Concerned that the OSCOAP document is growing. Wouldn't that be good to have a separate document. We need to avoid growing it in a monster document if we want people to read it.
Francesca: only 40 pages now. John's numbers to OSCOAP doc? Makes sense to keep separate
Christian Amsuss: about entropy: requtest type; no need for additional entropy. Req tag only valid from one endpoint to server. Can have zero byte or absent.
Jim S: 0 reasons to put this in the OSCOAP document. This is a blockwise issue. There is not even any reason to put it as a normative reference. This is a blockwise problem. You only need to do blockwise - no need to specify anything more.
Agree with Christian, don't know why we need entropy here?
Carsten (no hat): blockwise and observe are two separate documents extending CoAP but any extension to CoAP should support them.
Francesca: planning to mandate use of this and repeat option. Discussion more on where should that text be.
Matthias: etag ids representation, should think about that when disucssing request-tag
Christian: thinks that work for etag don't work similarly for request tag. E-tag need to be determined by server. Caching and uniqueness don't work for request type.
Matthias: Just wanted to make sure we think it through.
Carsten: work that needs to be done here. Should think what docs result from this. Don't seem really hard. Should be possible to finish with other OSCOAP work. Request tag should be made good enough to provide the needed functionality.

--

Secure group comm 4 CoAP

https://datatracker.ietf.org/doc/html/draft-tiloca-core-multicast-oscoap
Was discussed informally at IETF 95
Draft explains how to use OSCOAP for group comm.

Updated to fit OSCOAP -02

Carsten: observation from ACE: Pub-sub proposal seems to be interrelated with group comm.

Looking for more comments and reviews on this.

--

Requirements for CoAP e2e sec.
https://datatracker.ietf.org/doc/html/draft-hartke-core-e2e-security-reqs

Came up at T2TRG meeting in Amsterdam

Authors think draft is stable. Some comments from Jim to be included.

Carsten: wonder if term "requirement" is right here. Seems very much security considerations. "What you need to get e2e security". Seems way more useful than a requirements doc. Wonder what is good way to further develop this doc? Merge with general security consideration in the RG? Who has read the doc? (6 people into security +1 from jabber)

Francesca: feel that this is useful. Cleared many things we needed to develop solution. If CoRE wants to move forward with this..

Merike Kaeo: Looking into related doc in 6ops. Wouldn't fit into sec considerations in any other documents.

Dave Thaler: have skimmed the draft but volunteer to review the doc
Carsten: more volunteers? (Merike)

--

SenML  Ari
https://datatracker.ietf.org/doc/html/draft-ietf-core-senml

Ari: Quick update from the last version. Clipboard support for Mac/Win. Fragment id support, schemaId for the EXI representation.
Request to add more units (e.g. power level)
Do we need somethign for RSSI (vendor/device specific)?

Kerry: How would it be used without knowing the vendor?
Ari: Exactly... would need out-of-band info anyway
Carsten: Cullen doesn't want to add anything specific to RSSI could be done later.

Issue from prev. meeting: must-understand extensions
Discussion on character to indicate extension -which one to choose? _, *, ... ? which one to choose?
Alexey: just pick one
Ari: "_" suggested, hear no strong objection, will go on with this
Ari: Document is overdue, want to get done.
Christian A: CoRE Interfaces might not work with SenML naming. See e-mail thread "name vs URI"
https://mailarchive.ietf.org/arch/msg/core/c4Z5h5JK6ROoX5Kgum4bCT534hE
Ari: Need to change something in the base spec? Wouldn't like to change semantics of the names.
Ari: Problem with +exi -- does not exist
Alexey: There is a draft to add +exi suffix. Sub-registration has to be done first.
Carsten: Will not be in time for SenML.
Alexey: Would be okay with sponsoring exi document, but needs to understand usefulness better.
Carsten: suffixes do not help for CoAP, which uses numbers anyway
Ari: Switch + to - and get done?
Carsten: There are some other docuemnts that would need +exi. Different discussion
Alexey: Milestone was Sep 2016. Get it done.

--

Pub-Sub: https://datatracker.ietf.org/doc/html/draft-ietf-core-coap-pubsub
Michael Koster presenting

New stuff in the draft, need reviews.
Now on GitHub and use Issues there.
Issues: https://github.com/core-wg/pubsub/issues
Related issue to 2.06 Pending
Brokerless case perhaps needs a new OSCoAP Profile (https://tools.ietf.org/html/draft-palombini-ace-coap-pubsub-profile-00)
Reliable subscription as a different draft

Carsten: this is WG draft, would be good to get reviews. Who has read (around 10).
Jaime: which version? Latest? (around 5)

--
Malisa Stateless-Proxy CoAP option

Secure enrollment protocol for 6tisch. CoAP as transport protocol.
(connection breaking up)

Carsten explaining the slides.

Very constrained node doing the proxy. This is used during the join procedure, so we don't know the client.
Problem is that the request creates state in the proxy, generating a DOS vector.

The idea is to have a CoAP option used between Proxy and Server, where the Proxy ships the state (created localy), so that the Server can ship back the state in the response, which helps the Proxy NOT to store the state.

It is not mandatory to use it always - you can imagine case where the Proxy has 5 slots for state, and uses the option only upon exhaution.

Dave T: R column empty, are we doing to do cases where there is no interest to have two proxies?
Carsten: very good question. Should be thought on.
Dave: would need to be repeatable, and perhaps order to be important too

Alex: Seems like functionality where server takes state and gives it back. Can we have more generic one for this purpose?
Carsten: already have token. Limited to 8 bytes so limited use.

Interops: 2nd week of May.
~~~
