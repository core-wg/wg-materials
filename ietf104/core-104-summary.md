# CoRE WG - Summary IETF104

## Working Group Document Status

* draft-ietf-core-object-security-16 was approved and is now in the Editor Queue. The option number to be used is `9`.

* draft-ietf-core-multipart-ct-03 is now in WGLC, which ends at 2019-04-08.

* draft-ietf-core-senml-etch has now finished its WGLC, its pending the shepherd's writeup.

* draft-ietf-core-echo-request-tag-03 is in WGLC, already received a chair's review. It is pending a new version due to a submit glitch and few editorial comments, the WGLC ends at 2019-04-17.

* draft-ietf-core-stateless-01 is pending the chairs' review and then it will move to WGLC.

## Security

* draft-ietf-core-oscore-groupcomm-04 had a new revision based on Jim's comments. There are now several implementations which the authors will test at next IETF.

* draft-tiloca-core-oscore-discovery-02 the draft has incorporated the latest RD-group usage pattern and clarified some of the text with examples. The registration of oscore-gid and app-gp are still open points, the use of link format would need to be revised. Concepts from CoRAL Reef could be brought here. More reviews are needed in order to decide for WGA.

* draft-dijk-core-groupcomm-bis-00 the document updates RFC 7390 considering changes brought by blockwise transfer and obseve. The section on REST interface usage for group management will be removed. The target is to finalize the draft by next meeting.

* There was a pubsub security hallway meeting where three challenges where identified: multicast use, ComSec and potential DoS. The AD has to discuss with the SEC ADs where this new work would fit. 

## Data Formats

* draft-keranen-core-senml-data-ct-01 proposes a new SenML field for indicating the Content-Format of the data. It would need more reviews. Brought up the issue of fragmentation of senml documents, and whether it is the time to do it in CoRE.

* draft-ietf-core-senml-etch-03 was in WGLC, now closed. Please provide some more reviews.

* draft-bormann-senml-more-units-00 this draft proposes the creation of a registry for units. Bluetooth has its own unit registry and IPSO uses UCUM, the idea would be to reuse the SenML Units registry that will contain the units.

## CoRECONF

* draft-ietf-core-yang-cbor-07 a latest version was presented with few changes. The group is looking for reviewers. From the discussion, the intention is to get the NETCONF people involved by doing WGLC on the core-yang-cbor document soon, also since YANG is evolving and every change implies a new revision.

* draft-ietf-core-comi-04 no changes since last IETF an interp was arranged during it. No real changes since last IETf, interop at last IETF.

* draft-ietf-core-sid-05 the authors have been working out the details for the SID registry with IANA. There are a lot of little modifications that require finetuning.

* draft-veillette-core-yang-library-04 the document is rather stable at the moment but requires more reviews before adoption.

## CoRE Applications and extensions

* draft-ietf-core-coap-pubsub-08 part of the discussion was on the handling of empty topics and the lifetime of data and topics. Maybe it si time to think about whether extending the architecture to support long-polling is a good idea.

* draft-ietf-core-dynlink-08 is close to WGLC, we are pending a chair's review and contacting OMA to see their opinion on the conditional observation attributes and the binding table.

* draft-ietf-core-interfaces-14 has had little literal adoption but the text might have been overtaken by other work inspired on it. Thus some of the text will be moved to other documents and to be continued on the Research Group.

* draft-ietf-core-resource-directory-20 is mature and under WGLC at the moment. Few errors and clarifications to be added during this time.

* draft-ietf-core-rd-dns-sd-04 was not presented but it is progressing. It has been simplified by introducing explicit service types rather than doing any automatic conversion. A new revision will come by july.

## New Work

* draft-bormann-core-media-content-type-format-00 the document tries to clear the confusion between media-types, content-types, content-coding, content-format, and related terminology. It was found very useful by the group, the WGA call will be confirmed on the list.

* draft-birkholz-core-coid-01 was discussed at SECDISPATCH, the document represents "claim sets" as CBOR Web Tokens to support secure device identification.

* draft-amsuess-core-resource-directory-extensions-00 brings some extensions to the Resource Directory. The bulk of the work is reverse-proxying. While there was limited interest by the group, some of the extensionscould be used by other SDOs.

* draft-jarvinen-core-fasor-00 has IPR licensed as FRAND. The authors were concerned about interest and energy in the group even if the document is adopted. The WGA call will be taken to the list.

* draft-selander-ace-cose-ecdhe-13 proposes an Ephemeral Diffie-Hellman Over COSE (EDHOC) lightweight authenticated Diffie-Hellman key exchange with ephemeral keys. The document could be done in its own WG, the group is invited to join secdispatch.

* draft-amsuess-core-rd-replication-02 is an exploratory work on how to scale up resource directories. It might fit better at the T2TRG. It is expected to come back to core eventually.

* CoRAL has been worked at the T2TRG and has reached a level of maturity making it apt for CoRE. it is composed of several documents:
  * draft-hartke-t2trg-ciri
  * draft-hartke-t2trg-coral
  * draft-hartke-t2trg-coral-reef
CIRIs and CoRAL are now stable, with RIOT adding its support during this hakathon. The working group has decided on the WGA of the first two drafts, which will be reported on the mailing list.

* draft-zcao-core-speedy-blocktran-00 specifies a method to speed up block-wise transfer in CoAP. It creates a new option that specifies the window size.

## Other

* The possibility of deepening the use of GitHub in CoRE was discussed. Some discussion topics were:
  * Other SDOs use Github partially.
  * Hard to draw the line on how deep to go.
  * Need for a best practices document.
  * Availability of GitHub and possibility of IETF running its own GitLab.
  * Archiving discussions and following drafts.
The intention is to first try with few documents in agreement with the authors and move forward from there.

* draft-ietf-core-dev-urn-03 Seems ready for WGLC but was not discussed during the IETF 104.

* draft-ietf-core-hop-limit-03 Seems ready for WGLC but was not discussed during the IETF 104.

# Raw minutes

0.1 Core@IETF104 agenda

# Constrained RESTful Environments (CoRE) WG

Agenda: https://datatracker.ietf.org/meeting/104/materials/agenda-104-core-00
Note takers: Ludwig, Jaime, Ivaylo + 4 unnamed

Chairs (core-chairs@ietf.org):

* Jaime Jiménez
* Carsten Bormann

Numbers in parentheses are minutes of time allocated.

# TUESDAY, March 26, 2019
1350-1550 Berlin/Brussels

(conflicts with anima, mls, tsvarea;
Absent: Michael Koster)

## Intro (9)

  * WG and document status
     * Approved (in RFC-editor queue):  draft-ietf-core-object-security-16
     * In IETF Last Call (ends 2019-04-08):     draft-ietf-core-multipart-ct-03
  * Quick recap of related work, pointers

Ivo: Friday some time for the SID draft?
Carsten: Yes, let's see after CoRECONF

* CoRAL: Wed, 1500 - 1700, Tyrolka

Klaus Hartke [KH]: Interest from CoRE, e.g., RD, idea to replace Link-Format with CoRAL
if interested come to T2TRG meeting on Wednesday
Bill Silverjan [BS]: Will discuss this tomorrow, will send mail to organize side-meeting
* PubSub security: Pre-discussion at Hackathon
Chistian Amsuess [CA]: Had some discussions, side-meeting Friday 8--9
Carsten Bormann [CB]: Listing some of the upcoming hallway discussions. 

CB: OSCORE now in RFC editor queue. (Clapping)
Francesca Palombini [FP]: Thanks for help!
KH: Confusion on which option number you want.
All: 9
KH: IANA picked 10
FP: From IANA  we were told to ask the designated expert, thus 9.
CB: Hint for future draft authors: Use TBD (9) to indicate preferences

CB: WGLC for multipart-ct ends soon
CB: WGLC for senml-etch finished

## Documents nearing WGLC

### draft-ietf-core-echo-request-tag-03: (10)
(Please check [github for -04][] version due to a submit glitch, in particular the text for Token processing. ➔ WGLC! until 2019-04-17)
[github for -04]: https://github.com/core-wg/echo-request-tag
Christian Amsuess [CA] Presenting. 
Received Chair review, remaining issue: Token processing
Document now requires to prevent request response mismatch and gives recommendations

CB: sent message to list 30 min ago; mostly editorial comments on sec 5. Then ready for WGLC. Fine with token processing; 2 editorial comments on that.

### draft-ietf-core-stateless-01 (3): (Chairs' review? WGLC!)

Klaus Hartke [KH] presenting.
Draft about how to create CoAP proxies without state. Request from 6tisch. Now draft "stateless". IMHO ready for WGLC. No open issues. Have a look and let know what you think.

Malisa Vucninc [MV]: Thank you for work. Good progress. We're still blocking 6tisch work for other reasons. Will review

## group communication: security and bis

### draft-ietf-core-oscore-groupcomm-04 (15): registry vs. cose-bis, what needs to be integrity-protected?

Marco Tiloca [MT] presenting
Revision based on review by Jim Schaad and discussions.

    o Singature bit reverted to Reserved and set to 0

    o New counter-signature parameters, should IANA registry for this go to COSE-bis?

    o Should Context ID be in external_aad

    o Reception of malformed messages

    o Newly created recipient contexts

    o Handle repeated responses on clients

    o Github issue #6 : kid parameter

    o #7 What countersignature alg

    o #8 Use cases with a gateway


    Implementations: RISE, Peter van der Stok, Jim Schaad

    Aiming for more interops at next meetings


    Remaining issues?


CB: About MTI curve: which is it? Need to be careful how we handle this
John Mattsson [JM]: P25519 benefit: speed, P256: good tooling support
CB: Widening the rift between OSCORE and DTLS
JM: Interesting question: What kind of latency do applications need


### draft-tiloca-core-oscore-discovery-02 (12): Points raised by Jim: 

Marco Tiloca presenting

Recap: newly deployed device uses RD to find groups and group manager

Updates after reviews from Jim Schaad (JS) and FP.
o Now based on latest RD-group usage pattern
o difference between app groups and oscore security groups
o oscore-gp -> app-gp
o clarified parameter semantics
o Updated examples

presents example for RD use

Open points: Register oscore-gid and app-gp e.g. as Link Target Attributes
What is the right place to register this?

KH: Usecase beyond what RD was intended for, funky use of link format, needs review (adding base URI as a payload on the lookup response for a multicast addres).
One problem with link format: extensibility story is thin. Trying to improve with CoRAL the extension story. One exercise: how to do the same thing with CoRAL.
CA: Agree that use of attr values is weird, would like to have all as URIs in links. Could look here how CoRAL reef is done.
KH: Discovering multicast IP addr from base URL, that's weird
CA: We have to look into it but it is hard to see how the timescales would easilly allign.
Peter van der Stok [PS]: What is the timeline of CoRAL
KH: if sent review by tomorrow, it's done day after
CB: when want this stuff to be published?
PS: Next year would be good
CB: Obvious question. Who has read a version of this document? 5. And the most recent? 1. Time to start reading it in order to decide for WGA.
KH: If link format works it is fine to use of link format. The document currently needs review. 
CB: Who want to review  (4) Jim, Carsten, Bill and Klaus volunteered to review. 

### draft-dijk-core-groupcomm-bis-00 (10): RFC7390 update (EXP!),
Discuss objectives, 10 minutes: Marco Tiloca; can we remove the REST
interface for managing groups as nobody is using it?

MT presenting:
Update to 7390, What has changed: More CoAP functions (Block-wise, Observe)
Group OSCORE kinda normatively refers to 7390 (which is Experimental) -> need new standards track doc
    
Implementations of 7390:

    o Californium

    o OCF

    
In scope:

    o New use cases

    o CoAP functionalities for groups

    o Both secured and unsecured comm

    o Principles for secure group configuration


Next steps
CB: How many people have read Blockwise? 5 and this document? 3 Who would volunteer to review?
Review volunteers: KH, JS, CA  , Thomas Fossati.

CB: Timeline
MT: Finalize draft by next meeting

MK: How do network groups related to app groups?
MT: We keep the RFC 7390 definition, where network groups only include the servers, unlike app groups, which also include the clients

### pubsub security hallway meeting results (8) Francesca: 
summarize/discuss any results

FP presenting:

Want to use multicast notification in pubSub
Want security mechanisms

Identified 3 challenges:
    
    1. Plumbing = How to make pub/sub work with multicast
    2. Protect against DoS
    3. CommSec
    
Where does it fit? CoRE, ACE?

Dave Wheeler (DW): Is inference considered in the security model? What can attacker infer from victims with this?
FP: Not specifically considered, have a look at slides from side-meeting
FP: Asking the group about interest. Option is to have it in ACE.
MK: We had these Unsolicitied Responses/Notifications, discussed with OCF, but it could be related as an topic. 
Alexey Melinkov(AD): Don't have answer, but mail me and I'll talk to Sec ADs and work it out

## SenML

### draft-keranen-core-senml-data-ct-01 (10): Ari.  Check for adoption.
Discuss potential fragmentation of SenML into many documents.

Ari Keranen (AK) presenting:
    o content-format indication
    o content-type and content-encoding
    o Base value challenge(s)

Does the group think this makes sense?
(some nodding from the audience)

CB: Just now came up with a sick way of solving this problem: define negative content-format numbers
AK: Where to do this? Would like to do it in CoRE
CB: Brought up the issue of fragmentation of senml documents, and whether it is the time to do it in CoRE. 
CB: Who read this? Klaus, Ari and Carsten. Riot implemented it, look there

### draft-ietf-core-senml-etch-03 (10): Ari. WGLC will have closed 24:00 CET on Monday, March 25, 2019.  Please review.

### draft-bormann-senml-more-units-00 (3): Carsten.  Adopt?

AK presenting: At the moment there are other SDOs, in particular OMA that have a unit resource. The reference for that resource is UCUM, but there is no registry for that. The idea would be to reuse the SenML Units registry that will contain the units.  Have unit attribute in LwM2M and IPSO.SenML units registry would be good fit. 
AK: For the time being we could collect these units on the drafts. 
Hauke Petersen (HP): there is a registry on the bluetooth. 
AK: We are looking for short strings instead of integers, also need to add units that may not be interesting for Bluetooth. But need to align long term. There are other registries too like UCUM we looked at.
MK: In terms of converge, this ucum work was of interest but somehow never progressed. I see now that UCUM has been implemented, and will arrive to the JDK, so that you can also work with scale factors, converting between units, etc. Interesting for m2m for compatibility.
AK: Discussed in OMA what the right place to express the scales, some env don't support floats very well, but having scale in number is rather easy using the exponent in SenML JSON/CBOR formats. Don't need floating point implementation for that.
CB: Different registries good way to learn how to arrive at different conclusions for similar problems. Also to see how different registries work, for example UCUM has several different definitions for thermal units, due to the evolution and how they have changed. UCUM is big in a way that maybe we don't like, they are also missing some units. However the IETF is not in that business, it would be better to export to someone else. ISO8000 is the group that needs to do that, and it needs to be translated into ASCII.

## CoRECONF

### draft-ietf-core-yang-cbor-07 (3): Ivaylo.
Ivaylo Petrov (IP) presenting, asking for reviews. 

### draft-ietf-core-comi-04 (3):
No real changes since last IETf, interop at last IETF 

### draft-ietf-core-sid-05 (4): Ivaylo. (Get misunderstandings with IANA out of the way.)
Received comments from Peter, adapted draft accordingly
Discussions with IANA to simplify things.

Non-editorial changes: 
    Moving things to appendix that are non-normative
    Removed section 5 -> was potentially confusing

Michelle Cotton (MC): We might change where we put the SID model, discussion ongoing
Alexander Pelov (AP): Talking with IANA people to understand how things work. There are a lot of little modifications that require finetuning. 
IP: Will have to revert some of the commits. 
CB: Complexity comes from having different stakeholders with subgroups

### draft-veillette-core-yang-library-03 (4): Adopt?

IP presenting

rather stable, modulo recent reviews (multiple enums inside unions)
How do we resolve this? Proposal by CB
AP: CBOR getting interest, people were doing things that were not well defined, figuring out problems in Yang2CBOR
CB: Now RESTconf people found out CBOR would make servers faster and want to use it. In our interest to have the communities onboard so we get much better software support. What's going on with annotations sub-module?
IP: have not looked into yet. No solution worth mentioning yet.
AP: question to chairs; how we proceed with YANG2CBOR. Leave it open until get more questions from YANG people? Or freeze and when have new things there will be new revision? So we can focus on something.
CB: Good question, if we come up with solutions that require changes in SID files we need to do that now. If can stick with same SID files may have partial solution. Still in the process of finding out. Last time said ready for WGLC except for interop testing. How much further with that?
AP: Late on interop, did 1 year ago, then changed, not done new tests yet. Focus on that before the next IETF. 
CB: To parallelize: get Netconf involved by doing WGLC (to get their attention)
AP: Yang keeps also changing and at some point we need to release this. WGLC and in case the NETCONF people give feedback then we proceed with the changes. 
IP: SID document will require some work, by the end of the week it will be ready. 
AP: IANA move non normative text to the appendix. To me it is all done, minor review and ready by the end of the week. 
CB: plan is to WGLC this. Little detail: YANG library doc. Not even WG doc yet. Hard to do LC for such. Who has read? (1,5 hands) Better to have more people for that.
AP: very straightforward doc. YANG model that tells you how you get info of models. Place more in CoRE since we know how to interact with constrained devices. Logical continuation of CoRECONF.
CB: Expect resubmission, we try to be ready by end of week
[NOTE: draft-veillette-core-yang-library has apparently expired.]

## New work

### draft-bormann-core-media-content-type-format-00 (3) Worthwhile?
CB presenting: 
    
Who has read this document? > 8+1 Of the readers:  who did not like it? 0
KH: It is useful and helpful and clarifies things that were not clear in the past. Maybe it is better to expand the audience. 
CB: important for getting interest from other people is to not load too much IoT. Then could get HTTPbis involved.
AK: Found very useful, very good terminology
JJ: WGA on the mailing list

### draft-birkholz-core-coid-01 (5) will have been discussed in secdispatch on Mon 1350-1550
CB presenting
SECDISPATCH was meeting yesterday, who attended (9 hands).

Can we explain how to express assertions as CWTs?
Two documents about similar looking things: this & (draft-raza-ace-cbor-certificates-01)
Raza draft translates ASN.1 X.509 to CBOR and back, also profiles X.509
Which WG should do this? ACE and CoRE charters don't fit well. Will be a bit delayed until we know where to do this
Who has seen any of the two drafts? 7 people
Who would contribute to get a new WG going? 6 people

### draft-amsuess-core-resource-directory-extensions-00 (5) Christian: \[5—10 optional]
target: informational; collection of things that might have been
specified in RD but don't need to be part of RD proper

CA presenting

Largest part: reverse-proxying
Other part: registering with infinite lifetime, can be extension
Question: Is there interest in the WG?
CB: Who has a problem solved by these extensions, no answers
JS: About infinite lifetime. 3rd party puts device into RD, makes sense to let lifetime be infinite instead of forcing device to renew registration.
JJ: Will review, infinite lifetime seems useful for OMA LWM2M client registration.




CB concludes

(hallway on observation: see <https://etherpad.ietf.org/p/notes-ietf-104-core-observation?useMonospaceFont=true>)

Σ 120

# FRIDAY, March 29, 2019
0900-1030 Grand BR

(conflicts with 6man, cacao BOF)

## Intro (5)

CB: Agenda bashing. Some unscheduled stuff right after intro.

core-fasor: Has an IPR on the datatracker. Not enough information in it, stopped discussing it at IETF103. Since statement has been updated with assertion of patent claim, and claim owner makes it available for essential parts of IETF standard, ie. would only work with standards track document. So far congestion control was informational, but can be made standards track. Defensive patent construction (license expires when Huawei sued). Job of WG to decide whether can continue persuing. Not deciding now, but do we have enough info to make decision? Congestion control is fringe topic and so are patents, but anyone in intersection?
CB: My opinion is that construction has been used and has been deemed acceptable, so I think we are in position to take decision. To list.
Markku: Not commenting on the IPR, but case WG decides to take up document: how are we able to get enough interest among ppl in WG given this is congestion control where experise is in transport? Should be more liaison in transport, also w/ COCOA. Concerned about interest and energy in WG for document, if at all passes IPR questions.
CB: Next step is WG adoption call. 
CB: Hesitant to pass it on because it's our protocol. So far done things here by pulling in transport area, and should continue.
MG: Just posing the question, not asking to push over.
CB: For COCOA Alexey even delegated IESG shepering to transport AD, expect same to happen here.
CB: Adoption call on list, would ask room but we all need to consider IPR first.

EDHOC

CB: Underlying background: had DTLS as mandatory-to-implement 6y ago, but now have OSCORE which needs key exchange to cover what DTLS does.
Have discussed EDHOC as a proposal (also in ACE) but never found official home. Security and ART area have dispatch working groups that dispatch documents to WGs or start groups with community input, and secdispatch had interim meeting for EDHOC a few weeks ago, and ADs have since taken in results and are now proposing short-term WG with EDHOC as starting document.
CB: On interest, join secdispatch list and file support.
CB: In-room consensus to support individual WG or want to keep this in?
Ivaylo: Good way to go.
PvdS: If have OSCORE, EDHOC should be there. No opinion on dedicated WG or here.
Lauren Toutain LT (adapted for LPWAN): 
AK: Good way to go.

CB: Who things it is the right way to go? 15 hands + 2 on jabber
CB: For another better arrangement? [nobody]


Github use on CoRE

JJ: comparing approaches of TEEP (issue tracker rather than mailing list, but list curated by author into what to present), CoRE (preliminary tagging but kind of ad-hoc and no discuss tags), HTTP (discuss tags, topic based tags, using milestones)
Proposing track documents over lifetime over Github, could have batch mails every week or so, can assign issues to expert, could have milestones based on draft lifetime, start using tagging ("discuss" for asking WG, "editorial" etc). Not supported by IETF, but possible future could also be having IETF run Gitlab server.
Trial with guineapig documents.
DT: Comment on discussion on github. WG needs to decide where active debate happens. Either can be done, WG decide, some WG say active debate on ML and summary in github (policy in TEEP but not followed). This WG should specifically decide where arbitrary responses, inline quotes etc go to.
JJ: Some items are now on Github where authors collaborate, nothing formal yet. Should formalzie.
CB: Dave, what experience do SDOs have, what do we best use to get their data in? List, github?
DT: From OCF perspective, no significant difference. They don't use github for issue discussion right now. OCF uses mailing lists and document management system. Maybe github for data models. IoTivity: Uses mailing list and github and issue tracking on mailing list, but has no good issue tracking mailing list.
JJ: OMA uses github and had painful transition. Drafting and discussion on github, some on lists but moving to github.
BS: Much confusion on how we can use github. Could come up with best practice in WG, guidelines change btwn WGs. Getting a discussion fromlist into issues is hard. Have been using tagging and it's good to have more than issue tracking in github. Continuous integration, activity on drafts. Hard to draw line how deep to go in.
JJ: Reason for tryout: See what is outcome, feasibility, do experimentation, not switch everything.
JS: Two concerns about issue discussion. I don't know if IETF policy on archiving of discussion on mailing list has changed. Don't know that I need to go and follow new project when starts up. Could never find out if anything goes on. If it's big project with all on tracker. If different project for each document, then don't see discussions. That worries me.
JJ: if all docs in same repo, that would be a mess
Barry Leiba (BL). AD interrput, HTTPbis WG has handled by having separate mailing list and have GH sending all notifications to that list. All archived. And don't have to go to 15 repos. May not work for everyone though. Also the new wg "git" looking into this.
JS: SACM made a list observing the repos, that was also a bit messy

Brendan M: github has not always been available to everyone. Most of the time it is, but not alwasy.
JJ: This is why having our own gitlab will make a lot of sence.
CB: should not second guess here results from git wg; will wait to hear more from their results. As WG we could start our own small experiment. Not swapping the model completely but setting small experiment. Would propose RD draft. Handling LC comments could be easier that way.
Christian Amsuess (CA): There is already tagging and the discussions are already been duplicated on the tracker, so that would be fine for me.
DT: I was at git WG. Should not expect guidance "WGs should do X". Don't need to wait for anything from them. Mostly providing guidance for git n00bs. 
BL: didn't mean to imply that either
PvdS: It should not change the process and it should be very clear to everyone how this will work.
JJ: not planning to change any of IETF process
CB: (?)


## CoRE Applications

### draft-ietf-core-coap-pubsub-08 (15):
(Changes still needed, left over issue: see github; new github version
by Monday! Michael Koster -> Friday)

MK presenting via meetecho:
Issues: no new status code and figure out how to handle empty topics

Empty topic: created but not published to. Response could wait with result CON. Application layer would work that out.
Problem: Pubsub only transmits representations, and can't construct empty payload. Depend on things like Accept-All / application/nothing-to-see-here documents. With SenML can have empty payload []; don't think there's any severe issue. Can explain that in document.
Topic lifetime: query parameter tlt on topic creation, counting down from publish or create repetition. Topic removed at zero.

Data lifetime: Max-Age, already in place. Default is 60s as per CoAP. dlt= additional option to have long-lived values.

Topic contents lifetime: Max-Age=0 still sent but cache can't re-use. [???] Cache subscribing to broker could use max-age as supposed.

Proposed profile: broker won't respond until data is there, topic creator should send empty representation soon.
Defaults for tlt and dlt. [???]
If tlt, topic will be removed when no updates sent. Subscribers get 4.04 and end of subscription.

KH: @profile1: we have talked about pub/sub conf; if we have things like publishining interim thing; may make sense to update this rep at later date. One idea is to spread topic to two resources: one config resource and a data resource (where pubs and subs done). You create the config resource but if no content the data resource not there yet. Would give you CRUD resource for creating and deleting topics. Second comment on (2) max age: when published hasn't published for some time, say no data after 24 hours. Do we want to say "I can't give resp now, unlikely to get soon, you should not cache this". We should be able to tell apart and not generaate unnessecary traffic.
CA: I think on having empty representation it can be done more smoothly. Either as options for the creation or ... 
CA: Could be testament, last will, that would align nicely with metadata on resources that are not topics. 

CA queueing notes: tlt in metadata? Tombstone in metadata? Dont understand Data lifetime != max-age

CB (hat off): profile (1), we seem to be extensing architecture with long polls. May or may not be good thing, good to be conscious. Having broker not immediately responding might be right thing. Could also be topic create and 2 days later data; we have to consider whether that is evolution of architecture we like. Another observation on arch: if pub needs to include dlt query option, that's in URI and hence cache key. Doesn't replace any caches. Having no-cache-key option could make sense. Adding option also impacts the architecture. Obs 3) having control and data resource might be a good thing. If I would design from scracth, would make control resource multi-part core, could have control and initial value there.

CA: if understand correctly, control resource is implemented using different contnent format. Doing that has been problematic in RD. Having separate resource makes sense. Frees also pub/sub to use link format data on the topic.

PvdS: still intend to use broker proxy for sleeping nodes. Seems to be disappearing. Hope still can do that.
Ari: There is a subscribe and read interface. The latter is exactly for that use case. The idea of this update was to simplify the procedures so that vanilla CoAP client can be used for the basic functionality. 

PvdS: something about observe??
AK: Mostly talking about the observe interface, but read is still there and left and just same thing w/o observe, but the observe is more complicated due to lifetime issues and therefore discussed a lot.


### draft-ietf-core-dynlink-08 (5): Update now with clear separation; needs review -- close to WGLC

BS presenting.
big chunk of work finished. Much activity after joint call w/ OMA LwM2M, current draft reflects that.
Clarifications done that restructured draft into conditional attributes and ….
pmin and pmax changed to decimal for fractional.
Question for when notifications sent was clarified.
LwM2M discussion about band attribute, anyone here from there? Consensus was for info from LwM2M whether contribute.

Binding table changed, introduced rt rather than if.

Table in -07: resource collection POSTed to; still looking at it.
Right now discover entry point, GET/PUT.

Next: link bindings completed, binding table needs work. Looking for input from the LwM2M folks.

CA: like to point out that should be mail in the list about particular binding types that were not comprehensive. 
BS: also use of pmin was clarified on which value should be sent when it expires

CB: When ready for WGLC?
BS: Should have been ready, needs work on binding table and listen to LwM2M; two weeks for updated binding table maybe?

CB: procedure: we wait for next version, in parallel chairs' review and contacting OMA people. 
BS: Don't anticipate much problems.


### draft-ietf-core-interfaces-14 (10): Last call for burying?

CB on core-interfaces.

One of the first drafts, from ~2012. Early draft that consolidated our ideas about how this was going to work. Has been influential, taken over by SDOs that adapted it, changed and enhanced. No literal adoption, just standing there with recommendations overtaken by events.
Looked at it, found some useful text, eg. on collection -- would fit into T2TRG documents that non-normatively describe restful design. Charter mentions this document as place for interaction with research group -- interaction here is to push the good parts over.
Want to hear opinion of the room. Asked on list and have one response. 
BS: as having worked on it: Think this is a good idea. Well-written and small and easy to understand, some ideas fit well with T2TRG, others are well taken by SDOs.
PvdS: have found the doc very useful in early days of work. Fantastic text on that. Should be maintained. 
CB: we all agree around these lines. Taking over to RG and publish it there in different form.
BS: Not burying it, throwing over to RG.


## CoRE Applications: RD

### draft-ietf-core-resource-directory-20 (20): WGLC til April 17th!
two interops done, meet again at IETF104 hackathon, report

CA: Klaus has requested additions to the security considerations section. Should not pose problems to update. Still found some errors in the draft examples, will fix them.

Multiple interops done, found issues that have been fixed. Now looking into using CoRAL for RD. No spec issues. 

BS: thanks for the good draft; clarified lots of things. And good discussions in OMA meeting. Some text in RD that says about cardinality of registration. May want in future to have multiple base values. High chance that protocol neg will not have multiple base values. Our semantics might be a bit different for base.
CA: case for forward reference; we should adapt to state of the art and possible remove from the doc.


### draft-ietf-core-rd-dns-sd-04 (10): Peter van der Stok; how to get DNS context into RD

PvdS: Will be done by July

### draft-amsuess-core-rd-replication-02 (3)
(Will have been discussed in T2TRG meeting, quick feedback)

CA: was earlier decided this work fits better to RG. Possible to replicate RD using many RDs meshed together. Mainly notifying this is going on at the RG.
PvdS: some text in the front what is the purpose of the replication for would be good. Very different consequences.
CA: coping with great load, tolerance to failure, and third one (don't remember now). Will make sure the doc outlines *why* this is done. Will leave to protocol neg the part on integrating crypto IDs to have URIs across interested ---- in the overlap area of this group and RG. Some things to be address how can be done luke URI aliasing. Trust mode that allows switching transport without getting to problems. Github repo on this. If interested in topic whatch the repo https://github.com/t2trg/transports. Will eventually be relevant to CoRE again but now in RG since variety of directions this could go. Some experimentation needed. 

* CoRAL side meeting results (7) Klaus: summarize/discuss any results

KH: at RG have been working on CoRAL. Four drafts. CIRIs and CoRAL getting interest in use in CoRE apps. Idea is to move these to CoRE WG. CIRIs: CBOR encoding of URIs similar to CoAP options. Want constrained devices be able to do URI arithmetics, including corner cases. Could also be used outside of CoRAL, like SenML CBOR format or SUIT. 

CoRAL is link format on steroids. Can also describe operations on resources with forms. CoRAL doc tells what is the resource, what can you do with it, and how it relates to other resources. Also fixes bunch of link format issues. Like weird rules of link anchor. CoRAL comes with two serialization formats: CBOR for constrained devices (typical doc only few bytes and can be used by devices with minimal RAM), and compact textual format for examples that is more human-friendly.

CIRIs and CoRAL stable. Two meetings this IETF: hackathon (new parser, RIOT OS support, examples and uses cases done, thing description conversion and python implementation updated). Also side meeting where discussed using CIRIs and CoRAL RDF-link format interop. Discussed also if real hypermedia apps are feasible and WG adoption.

Klaus showed CoRAL examples of link-format, Carsten's coffee machine, and TD in CoRAL. For TD example, if assume using CoAP, the representation comes nicely much shorter. Also IPSO vocabulary for CoRAL based apps. Conclusions: CoRAL works! Also did interop between two RD implementations. Also github repo with examples with CDDL and ABNF, test vectors for unit tests. Plan to create more examples and tutorials. Started collecting issues.

CB: given we have reached the state as reported, is it time for WG adoption? Lots of docs, not all for this group, but the two docs we see candidates for going for engineering phase are CoRAL and CIRI docs. Are we ready for adopting? 9 yes +2 jabber, no one against.
CB: To report on mailing list to verify consensus.

PvdS: About rd-dns-sd. Progressing well. Simplified a lot by introducing explicit service types rather than doing any automatic conversion. Should be done by July.

## New work

* draft-zcao-core-speedy-blocktran-00 (10)

Needs to request continuously, exact segment every time, many round trips.
Can we speed that up when loading a large file onto a device, and [other case].
Server may be more capable and more stateful in handling these.
Proposeing to speed up block option. Speed-up option specifies window size. Sever sends several segments.
More tricky when client is constrained [??].
Each five segments, the client ACKs and server can send more. Speeds up conversations and keeps clients constrained.
Certainly more can be done (speedy block option etc).

[CA queuing up: Looked into NSTART>1? Nontraditional responses?]
CA: two things, see the use cases, have run to them myself, but think this could profit from looking into two areas: using NSTART > 1. Was always envisioned possible. Would simplify model by simply sending many requests. Would not give all the efficiency but might give speedup without making the model more complicated. If then turns out not enough, maybe want to have look at non-traditional responses. There all topics of "which token to reply etc". Would not need to come to this with NSTART > 1 for 80% of apps. With that don't need to lock-step.

ZC: is that solution documented anywhere?
CA: not aware of docs that would describe this

Hannes T: did you do analysis on performance improvements?
ZC: have done some simple evaluation. Obvious benefits. 

Hannes Tschofening: [...] This is a congestion control issue, transport could be interested in that. I don't think, rather am sure, it's not easy.
ZC: On TCP you don't need to worry.
HT: So TCP only?
ZC: Also UDP with COCOA.

CB: some interest in the group to explore this space and alternative approaches


CB: Announcing interims (late Wednesday CEST) in schedule with other WGs (weekly but not each WG every week)



Σ 90

# Hallway discussions envisioned

* protocol negotiation: Bill.
* on pubsub security: Francesca.
This work was done in ACE, but might fit better in CoRE than in ACE.
"group oscore" vs. the construction of pubsub.
Francesca: summarize hallway meeting if there is a result, 10 minutes

* observation and pubsub: Christian

## IETF103:
    draft-bhattacharyya-core-a-realist-02           2019-02-05
    draft-bormann-core-corr-clar-00         2018-10-23
    draft-hartke-core-apps-08           2018-10-22
    draft-jarvinen-core-fasor-01    ipr     2018-10-22
    draft-jhjung-core-sensor-streaming-00           2018-10-22
    draft-mattsson-core-coap-actuators-06           2018-09-17

## Unrelated:
    draft-yangcan-core-web-software-built-in-cloud-00           2018-10-23
    draft-urien-core-blockchain-transaction-protocol-02         2019-03-04
    draft-urien-core-identity-module-coap-05            2018-12-27
    draft-urien-core-racs-12            2018-12-12

