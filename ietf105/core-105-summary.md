# CoRE WG - Summary IETF105

(Constrained RESTful Environments WG, Draft Minutes 0.2)

The core WG held two meetings at IETF 105 in Montreal, both of which are summarized in these minutes.

Videos:
: Tuesday (2019-07-23, 1 h): <https://www.youtube.com/watch?v=KkQMFbbjQ1I>
: Thursday (2019-07-25, 2 h): <https://www.youtube.com/watch?v=RHV_E8TTTyM>

Slides: <https://datatracker.ietf.org/meeting/105/materials/slides-105-core-consolidated-slide-set>

Thanks to the note takers!

## 10 years of constrained applications (Thursday)

In a short history reminiscence, Carsten reminded people that the
legendary Bar BOF that ultimately led to the creation of CoRE in 2010
met ten years ago, on 2009-07-28 -- with some actual beer available,
thanks to Zach Shelby and his company (now part of ARM).

The decision was then taken to start work on an application layer
protocol for constrained node networks; the assumption was that work
on a constrained transport protocol would take a decade (so it would
be finished now :-). On December 24th, 2009, the -00 of the
requirements document was published.

Only 4 years after the Bar-BoF, the CoAP specification was approved
with 8 Yes votes (!) in the IESG (and then had to wait another year in
the RFC editor queue before some security area squabble that affected
a normative reference was settled).

## Working Group Document Status (Tuesday)

### Published

* draft-ietf-core-object-security-16 (OSCORE) has been published as
  RFC 8613.

### In IESG Processing

* draft-ietf-core-multipart-ct-03 is in IESG and has a remaining
  DISCUSS to clear (semantics); a revised I-D is needed.

* draft-ietf-core-senml-etch-04 is in AD review; Alexey related two minor
  problems in media type registration at the meeting.

* draft-ietf-core-resource-directory-23 is in AD review; Alexey found
  a few bits that are slightly underspecified.  Also, for some
  references it is not clear whether they are truly informative.

### In/after WG Last Call

* draft-ietf-core-echo-request-tag-05 needs a revised I-D after WG last-call ended.

* draft-ietf-core-stateless-01 needs a revised I-D, waiting for author
  to submit post-WG-last-call -02.

* draft-ietf-core-hop-limit-04 [should now go forward, at the meeting
  we said] probably needs a revised I-D.

### Almost at WG last-call

* draft-ietf-core-dev-urn-03 has expired and needs to be resubmitted
  before it can go directly into WG last-call.

### Adoption calls

* Adoption call for CoRAL, CIRI [now CoRI], ended 2019-07-23 [called
  2019-08-13], waiting for author to submit WG documents.

* Yang-Library: draft-veillette-core-yang-library-05 entered WG
  adoption call on 2019-07-11.  There was thin response on the list
  (with Andy Bierman proposing a different, more complex approach),
  but the sense of the room at IETF105 was in favor.

* Corr-clar had an adoption call, with a thin response, that was never
  closed.  This needs a revisit.

## Active Documents

* draft-ietf-core-rd-dns-sd-05: lags behind resource-directory proper;
  lost an author, but technical direction is now much clearer
  (separation of resource type rt from service type st).  A few items
  came up during discussion that call for a revised I-D, including a
  discussion about authorization.  The timeline is to have the
  discussion finished and a WG-last-callable draft available by
  IETF106.

* draft-ietf-core-coap-pubsub-08: This had been the main subject of the
  side meeting on CoRE applications and hypermedia.  The separation of
  the topic configuration resource from the actual data resource is
  now on solid grounds; some details still need to be understood.
  CoRAL comes in handy as the hypermedia format, but will be kept
  optional for simple situations.  Benjamin Damm argued for good
  scalability in the number of topics.  Several participants discussed
  the need for a hierarchy.  Here, also, authorization is a topic (the
  actual mechanism could be done in ACE).

* draft-ietf-core-dynlink-09: Work on the binding part and its
  architecture is ongoing.  Again, CoRAL can help, but is optional.
  Some discussion on the conditional observe part happened in Friday's
  OMA/T2TRG meeting; this requires more discussion.  In general, we
  need to understand better which of the core-application drafts are
  standards-track in the traditional sense, and which are example
  applications available for copying but not necessarily the only or
  even preferred way of addressing the objectives.

* CoRECONF cluster: draft-ietf-core-yang-cbor-10,
  draft-ietf-core-comi-06, draft-ietf-core-sid-07,
  draft-veillette-core-yang-library-05 (see above re WGA call for the
  latter).  With yang-library a WG document, these can now be WG
  last-called as a cluster.  The four CoRECONF documents will go into
  WG last-call once a few minor details are fixed [as of 2019-08-16,
  stuck in vacationing].

## Active documents, continued (Thursday)

* draft-ietf-core-oscore-groupcomm-05: The latest updates were
  presented by Marco Tiloca, with a summary of the interop at the
  Hackathon.  Discussion of some technical points.  WG last-call is
  envisioned after vacation period (September).

* draft-tiloca-core-oscore-discovery-03: Updates presented by Marco
  Tiloca.  Discussion about interactions with resource-directory,
  CoRAL (and the link-format legacy), and ACE.  This document
  approaches a WG adoption call and needs reviews; four reviewers were
  identified.  One question is whether this should be done in CoRE or
  in ACE.

* draft-tiloca-core-observe-multicast-notifications-00 is a more
  speculative draft that was presented for the first time by Marco.
  Discussion focused on architectural implications and the role of the
  token.  A design team meeting/workshop, possibly in Stockholm, was
  envisioned to make some progress (probably with an embedded virtual
  CoRE WG interim).

* draft-dijk-core-groupcomm-bis-01 is intended to replace the
  experimental RFC 7390 with a standards-track specification.  Carsten
  asked whether the experiment described in RFC 7390 can now be judged
  as completed; so we can pick from that what we want to standardize
  and leave the rest.  Plan is to have adoptable document at IETF106.
  Five reviewers were identified.

We quickly switched the agenda to avoid a conflict:

* draft-jarvinen-core-fasor-02: Working group adoption of this was
  delayed for a while, during which people could judge the impact of
  the IPR declaration.  This waiting time is now completed and the WG
  adoption call is to be issued.

Back to the usual program:

* draft-keranen-core-senml-data-ct-02 completed its WG Adoption call
  on 2019-07-17 (which was called on 2019-08-21, and has been
  resubmitted as draft-ietf-... on 2019-08-29, so the
  draft-keranen-... still was the one on the IETF105 agenda).
  Recent changes focused on enabling content-type and content-coding
  for combinations that do not have a content-format number, in a way
  that preserves SenML's resolution semantics.  Next step is to add
  examples and go for WG last-call.

Two individual contributions related to SenML were also discussed:

* draft-tschofenig-core-senml-lbn-00 describes the need for a
  technique to satisfy SenML's requirement for globally unique base
  names without needing to carry that necessarily long name in each
  measurement message.  Ari Keränen also has a draft on this.
  The sense of the discussion was to go ahead and solve this,
  otherwise usage of SenML in OMA is likely to simply ignore the
  uniqueness requirement which may actually not be relevant in the
  internal use of SenML in OMA.

* draft-bormann-senml-more-units proposes more units for SenML, but
  also a way to accommodate legacy data models with less controlled
  usage of units in the context of the more disciplined SenML units
  registry.  -03 specifically proposes a secondary registry that
  relates legacy units to the primary SenML units registry using a
  scale factor an an offset.  There was good interest in the room in
  solving this and acting quickly.

## Further work

In the remaining minutes, Christian Amsüss presented some
call-to-action on forward-looking work, including on compressing CoAP
using SCHC, on CoAP library interfaces, and on collecting a CoAP FAQ.

-----------------------------------------------------------------------------

## Detailed minutes:

~~~~
Agenda
0.1.2 Core@IETF105 agenda
Constrained RESTful Environments (CoRE) WG
Chairs (core-chairs@ietf.org):
Jaime Jiménez (not present)
Francesca Palombini (stand-in, thank you!)
Carsten Bormann
Numbers in parentheses are minutes of time allocated.
Please note: Side meeting on CoRE applications:
TUESDAY, July 23, 2019 1520-1650 Collier
TUESDAY, July 23, 2019
1710-1810 Duluth
(conflicts with 6man, tls; Absent: …)

minute takers: Michael Richardson, Christian Amsüss, Ari Keränen, Marco Tiloca, Ivaylo Petrov

* Intro, Agenda, Status

CB presenting the agenda

just had side meeting on CoRE applications / hypermedia

WG and document status
Published: draft-ietf-core-object-security-16 ➔ RFC 8613

Document status:
published RFC8613
IESG review:
    * multipart-ct (discuss to clear)
    * RD and SenmL etch in AD review
last call:
    * stateless: revised I-D needed
    * ERT: need revised I-D after WGLC ends
    * hop-limit: probably needs revised ID

In IESG processing:
draft-ietf-core-multipart-ct-03 IESG Evaluation::Revised I-D Needed

Alexey on AD review:
on etch: Two minor problems in media type registration. Coding details on too high level; supposed to be a choice between few options (7-bit, 8-bit, etc.)Fragment identifiers missing.
CB: media type registrations probably need dedicated review in WG
Alexey: Yeah was requested

draft-ietf-core-resource-directory-23 Publication Requested

on RD: mostly fine, general comments: some bits are slightly underspecified (eg. secure discovery), not always clear whether references are truly informative, maybe to be questioned in a couple of cases.

draft-ietf-core-senml-etch-04 Publication Requested

CB: Finally we're moving documents on.
Now also adoption calls: dev-urn expired in bad timing, but otherwise WGLC. Positive on coral, ciri. Yang-library got negative from Andy B but only one and nothing else. corr-clar had adoption call never closed; will have to check situation.

* Pubsub (KH? MK?) 
* Dynlink (KH? MK?)
* CoRECONF



In Post-WGLC processing:
draft-ietf-core-stateless-01
draft-ietf-core-echo-request-tag-05
draft-ietf-core-hop-limit-04
In WGLC (maybe):
draft-ietf-core-dev-urn-04
Quick recap of related work, pointers

CoRE applications

draft-ietf-core-rd-dns-sd-05 (Peter) (15) 
Objectives: run through example, DNSSD discovery of RD via DNS

PV: in RD, had reference to discovery and moved to RD-DNS-SD.
Changes -04 to -05: moved parts from RD, and now with examples for st.
st was previously inferred from rt, that was a very unhappy thing. st is now explicitly set and needs to be registered.
example (slide 4)
ins is the instance name that is a concept of DNS-SD.(instance/service/domain)

An agent can take data from RD and create DNS records for it.
Still unclear how to find domain in which to publish them.
DNS-SD lookup provides all instances of a requested type.
TXT record can export some metadata from the RD for consumption by the client (not known to DNS)
SRV record gives the host name, and that can be resolved using an AAAA record.

CB: Does it make sense to set st w/o setting exp? PvdS: No meaning.
CB: and if other way round? PvdS: Server won't know what to do.
CB: may be worth thinking about.

McCool: Privacy implications? Who has authorization to scan this?
PvdS: Good remark, also true for RD. Pointing to ACE AS, both documents point to how it can be done. How it's actually done on a particular instance is [...].
Please also read DNS-SD drafts.

On exporting RD to DNS: slightly different. Data from .well-known/core rather than lookup interface, and that does not have host name in link-format document. Instance name determined by authorization server.
Open questions: How specify the 'coap'/'coaps' part. Put it in the service type to be used there. Using _sub to distinguish ... have to see how things can be distinguished, but will see later-on.

Open ToDos: how to derive domain part of DNS-SD; add _coap/_coaps as services.

Stuart Cheshire: Advice on two questions: in discovery proxy code (see hackathon) is default configuration is home.arpa, which can be overridden manually. On second point, if I understand correctly, in SRV there's a _tcp/_udp label; if could go back and do it again do it differently. Service name doesn't have to encode impl details (TLS, UTF8 etc), but is not description of protocol but unique ID to look up in table. Would do _srv instead of _srv._tcp/._udp if using now. _udp now just means "not TCP".

CB: Timeline?
PvdS: End of this year? depends on discussions.
CB: Singapore would be good time.
PvdS: would be good time for lots of things.


draft-ietf-core-coap-pubsub-08 (Michael) (15)

MJK presenting

Changes from pre-deadline meeting and recent days.
Addressing issues around topic handling. New design avoids lots of issues (empty topics, link-format documents, simplify/clarify lifetimes and still keep it compatible with REST APIs)

Topic configuration resource separate from data resource. Pubsub on data resource, creation on configuration. Also helps with including security. Proposal in github repo.
It's a CoRAL document. Had to pick a format, and CoRAL is best coming up for CoRE apps. Can still use link format, but CoRAL helps with sensible defaults. Topic creator does not need to know CoRAL for simple things, but should for better control.

When create topic, get config resource. When publish, create data resource.
Topic not subscribable when not created, returns 4.05 on GET/Observe.
At topic creation, CoRAL document can include content.

Topic metadata (see slides). Hint for what client wants path to look like, server may follow or not.
Topic creation by submitting CoRAL document, getting back CoRAL document with link to data resource. Can also create with link-format document, and still use sensible defaults. Can get link-format document back.
Topic discovery using CoRAL or link format, CoRAL can have metadata. Topics are discoverable but not subscribable between creation and intiial publication. Builtin simple filters similar to RFC6690. For better filtering, use CoRAL FETCH. Both CoRAL and link format are fine for discovery.
CoRAL is fine to set topic/data lifetime. Data lifetimes will likely require tombstone documents; but maybe even w/o one 4.05 can be used on timeout. ("Can't observe it any more because data not there").
Topics that time out result in 4.04.
Configuration for topics managed by GET/PATCH/Observe.
Publish and Subscribe like in current draft (just focused on the data resource): CRUD with GET and PUT, subscribe with Observe. Subscriber doesn't need more than basic CoAP library to do PubSub.

Feature: Hierarchy. Requires topic to be entry point for creating. Child topic can inherit defaults provided with parent. Deleting parent deletes subtopics. Read/Subscribe on them returns all children's data.
Aggregation: Like hierarchy but can have any topic, more like flat aggregation.
Getting just data that has been changed ... seem to be use cases for that, features under consideration.

Roadmap: Get rough consensus on this and proceed with detailed design. Discuss in interim meetings. Drive it to last call.

Benjamin Damm (ITRON): Not sure if protocol does this. MQTT says topics don't exist on server, just names. Could have billions. Protocol here moves to structures where that's impossible.
MK: How is it that topics don't use resources?
BD: not "no resources", set of wildcards that exist, not the topics
MK: Did consider topics for wildcard subscription, but have no proposed design here. Need more discussion on use cases.
BD: happy to do it
MK: want to be scalable

Dave Robin: Mentioned two options, hierarchy and flat list. Not touched on ownership. What about flat list. Is this like a view where deleting it does not delete children.
MJK: that would be more like a view where you don't expect to delete everything
DR: CoRAL defines members, where clients does not define members. Thery are not client-driven?
MJK: more like another topic creation. Would create a topic that contains links to sub-topics
DR: Endless series of interesting conversations. How to change value? Want only one? All things add to complexity.
MJK: and what if lifetimes are in different places, etc.
CA: would be good to point out that many of those things like lists could be extendensions to pub/sub broker and not be required features
MK: not everything needs to be required
PvdS: how do you see relation to ACE and authorization in broker. That draft has to go to LC at the same time?
MK: Are we creating a dependency on ACE? Depend on some CoRAL, not sure whether on ACE.
PvdS: want to keep independent?
MK: Correct solution probably is ACE b/c they build a pattern that can do that.
JS (ace chair, from back of the room): that would not create dependencies to ace
CB: How do you secure that in the document? Good to finish this together with the authorization scheme in ACE.
PvdS: The content of both seems very related, makes sense they finish at the same time.
CB: makes sense


draft-ietf-core-dynlink-09 (Michael? Klaus?) (5)

MJK presenting

Had similar issues. Binding table operations from Christian on architecture, so this is now proposal. Question on observe attributes work with more data consistency across different endpoints is open, will be discussed on list. Maybe add attributes to satisfy this, proposal in repo.

Change: Binding a resource not a link. Binding table has entry point for creating resources, looking into CoRAL to do more sophisticated thigns, but link-format will still do the job.
Binding table [entry] has source, destination and self link. Target attribute issue is now resolved b/c they only refer to the target of that link. Self-link refers to the binding.

Binding table has entry point ... POST to it, returns location. Location allows you to DELETE, with CoRAL can also be PATCHed. Reading the binding table gives links, and maybe with CoRAL more depth to inspect all bindings, or filter.

Conditional observe option: Different clients have different starting conditions, that gets them different updates. Maybe that's OK, maybe not. ... (confused looks in the room).

Roadmap: Add binding table if consensus / no objection. Further discussion on conditional notification attributes. Stay informational? Other ...? (CB: Standards track). 
CB: Time for general discussion of which drafts are standards-track in traditional sense, and which are example applications available for copying but not necessarily only / preferred(?) way.

Documents nearing WGLCCoRECONF cluster (15)
draft-ietf-core-yang-cbor-10
draft-ietf-core-comi-06
draft-ietf-core-sid-07
draft-veillette-core-yang-library-05 (in WGA call until 2019-07-18)
Objectives:
check for any netconf/netmod/yot input that needs to be processed now
clear any remaining hurdles to WGLC (with netconf/netmod involved)


Ivaylo presenting

sid was updated (see slides)
next step for sid: should be redy for WGLC. CB: Let's tal about those at the end of the cluster.

on yang-cbor:
updated with small changes (see slides)
questions: whether examples are better and with more context now (send feedback)
whoever thinks the green part is confusing, please contact over mailing list.

yang-library: in adoption call but Andy Bierman asked about whether that's the best way forward
Seems like discovery size will be reduced, especially for networks without[?] peer-to-peer communication.
Andy commented that it only happens once per device lifetime and thus not worth optimizing.

CB: We spent lot of time to make communication in YANG-CBOR efficient. However, occasionally must do introspection (meta-use of YANG). That we have not optimized. Could YANG-CBOR to have optimized introspection, but maybe it's just easier to say that the kind of introspection on constained sensor is different to NetConf-based router anyway, so maybe it's OK if we have own YANG module for introspetion. That's the difference w/ Andy -- fundamentally there's nothing against standard YANG introspection, but we'll get much larger discovery information than from this optimized library. Andy's view is [...]. For tank it doesn't make big difference whether it's 200 bytes or 2k, but for temperature sensor it does. Maybe that's the explanation for the difference. Personal view is that WG adoption should go ahead. Last-calling these documents will happen with CC to netmod/netconf WGs, and collect add'l input from them during that. Can still stop this if there are good arguments why this would destroy the YANG universe. For me, this looks like right way.

Alexander Pelov (remote): (sorry about the bad audio) it is possible to link to introspection model which to fetch from introspection server. If you're big server/client - you can use the standard YANG introspection library. For very optimized version, only get the SIDs. From Andy's comment, these are not incompatible. We'll need to dive into how the two coexist, no need to map between them.
CB: Nobody sent +1 on WGLC, maybe you still want to do that.
Alexander: will do

IP continuing:

on comi: no big changes.
updates (see slides) no big change

CB on cluster -- what ready for WGLC? Still waiting for update on yang-cbor. Need to resubmit yang-library as WG library document.
PvdS: maybe Michael wants to make the same remark; looking forward to publication of this document, still worried about (Unclear) values change. How is this supposed to be arranged, e.g. with IANA?
IP: For changes, that's why there is preallocation. That can be handled. Can discuss offline.
PvdS: Seen five places where ?
MCR: Discussion with M Cauton? suggests that all YANG models we depend on may need SID values attached. SID files we create, we believe we need to pass them to IANA. Don't know how to do that. Put YANG modules them in document and extract them. Should we do that with SID files? When comparing to approved modules, may discover issues/conflicts. May need to do that at a point between WGLC and IESG to convince them everything is good. No process for that, and don't have code upstreamed into YANG so IANA can mechanically check it out. Except that we need to explain in IANA ... but that's a WGLC comment, so let's have WGLC.




THURSDAY, July 25, 2019
1000-1200 Duluth
(conflicts with tsvwg, tls; Absent: …)

Intro (5)Groups

CB: Agenda bash: moved FASOR earlier. Re-defined-time issues in the agenda slide. Couple of ideas from Christian planned in the end (not shown on agenda slide currently).

CB: 10 years ago 6lowapp bar BoF with actual beer (thanks Zach!). Started application layer protocol work. December 24th 2009 requirements doc -00 published. CoAP draft approved 4 years after bar-BoF. One year waiting for security reference to finalize (office politics).

draft-ietf-core-oscore-groupcomm-05 (15) Tiloca
Latest updates (signed OSCORE option; 2 external_aad; extended sec cons)
Discussion - Signature algorithm to use/mandate (issue #7 on Github).
Report from Hackathon.
Ask for WGLC.

Marco presents the updates.

slide 4
Jim: are both of the algs mandatory to implement or one only
Marco: One only.

CB: have mandatory ti in base core, if want to move to different set of curves, should be done in coordinated fashion. Good thing to do reality check on what we can do with implementations. Assumption: no overwhelming technical advantage of one over another
PVS: no technical advantage, but will need negotiation
CB: We need agility
Ludwig (side note in Jabber): Note that the DTLS profile of ACE also makes Ed25519 MTI

(slide 5)
Marco: format of group id? example or recommended?
Jim: keep as example, don't want to recommend
Marco: OK.

(slide 6)
Jim: don't understand why not a MUST. Otherwise with KDC could be really hard. With single group manager permitted to provide Group IDs. Will not make people happy. Can get this thing and suddenly need to talk to KDC to know key material has changed.
Marco: We will think about it
Ludwig (jabber): MUST makes more sense
Ludwig again: If group ids collide, authorizations referring to that group need another unique ID

Ludwig: (as to the key rotation for a clients protecting a request with an old context then received at the server that already switched to the new context) better solution, say you are this client that is using this old context and had just send a request when you discover new context. Why not say that instead of keeping around your old context, you resend your request.

MT: think you may risk double processing at the server. 
Francesca (hat off): for implementations may be crossing sec and app layers. Need to know that you keep ctx and application will have to send 2nd request. Not sure that's a good idea.

Ludwig: In the other case the application needs to know that the context has changed? Worth thinking security implications. Feels fishy.

Dave R: re-keying and distributing takes possibly long time. Need lots of forgiveness. May be minutes or longer to get context to all. Having overlap for reasonable time frame with old keys (10 min? hour? day? app dependent). But need to allow in protocol lengthy time.
Carsten from the floor: we are trying to limit the risk by giving a time limit, but if we have a way to communicate this time as part of the re-keying, this is as safe as we can go.
PvdS: not worried about sec as much as ordering of messages. If have several key sets and want to go to new one should not allow messages with new key set before lifted out old key set.
Jim: one of the problems is we currently do not have any standartised way for the KDC to tell the group members the key has rolled over we should not forbid the server, but we should tell that receiving an "Unauthorized" is acceptable.
MT: good!

CB: changes would benefit for another round of interop?
MT: not needed for the changes in the draft 
Jim: when we did the changes, we wrote the changes in the interop.
Carsten: Moving towards WGLC. What is the timeline?
MT: can do next week, but probably later
Carsten: we are approaching vacation period.
Marco: September sounds good


draft-tiloca-core-oscore-discovery-03 (10) Tiloca
Overview of latest updates.
Step-by-step example aligned with practical installation procedures.
New link target attributes, related to parameters newly defined in ACE https://tools.ietf.org/html/draft-ietf-ace-key-groupcomm-oscore-02 https://tools.ietf.org/html/draft-ietf-ace-key-groupcomm-02
Registration of link target attributes such as “oscore-gid” and “app-gp” (in what registry?), also related to https://hackmd.io/AfjWKj7rRDiQl16WSSIa4w?both
Check status of ongoing reviews and way forward

Presents updates
Open points:
    slide 6 - new link attributes registry?

Jim: Q1: is this expected to be used for preconfigured groups or not? Commisioning system would put all key material in the device. No KDC. 

MT: It's not covered yet, it handles the case where the KDC is not deployed yet.

Jim: But still planning to use KDC (yes). As ACE co-chair, should this be in ACE? This is all ACE work.

MT: it is aligned with ACE draft, but as it is related to RD. Could be ACE as well.

CB: this chair has opinion: RD is application we have defined here. But not all that uses it needs to be defined here. Since subject matter is mostly security, could see this being done in ACE

Jim Q3: we had a side meeting in core and we discussed that we need to define some ACE grammar for CoRAL. Do you think this is a reasonable document to do that?
MT: yes, need to think lots of details

FP (from floor): CoRAL would be used in the doc for sure if it was defined. Is it reasonable to define *in* this document, not sure

Jim: I would assume that the CoRAL language will be a superset of the link language

PvdS: not that I prefer link-format over CoRAL, but for those using it short term and more used to link format, that should be part of this.
CA: agreeing

FP: folks who made comments, please check out the Etherpad we captured those correctly (seriously!)

Summary and next steps:
    Slide 7 - Outcome from IETF 104
     --- "Time to start reading it in order to decide for WGA"
     --- People volunteered to review (Jim, Carsten, Bill, Klaus)

Marco: if I understand correctly, the conclusion is to get reviews as previously promised and possibly move this to ACE, correct?

CB: We can do the work where the work is right now and we don't need to wait for now.

Jim: comment was relative to the line "we need to decide on WGA". People should read and comment on it anyway.

CB: all questions chairs need to ask. Good to have day-time model (?) with ACE. As WG strategy need correctly handling CoRAL transition and not dump link-format to floor just yet.


draft-tiloca-core-observe-multicast-notifications-00 (15) Tiloca
presenting the new idea
getting feedback especially thinking of the “Pub-Sub and Multicast” discussion
asking for document reviews

Marco presenting

slide 4 - Contribution
CB (on the floor): gets interesting because tokens are client name space in CoAP. When say managed by the server, very weird b/c client may be talking with multiple servers. Would need to coordinate across token space. Another problem with obs and multicast is that multicast isn't reliable. Hard to have eventual consistency without keepalives or something. Managing token space more difficult. Client of multicast resp is the group not a single node. The group needs to agree the token relates to a request. Architectural view. Explaines why not quite there yet understanding what doing here.

CA: on client management of the token, what matters is tokens are related to the .. involved. All definitions are currently related to unicast. We need to extend to multicast. We will need to do in a larger context than this document.

CB: said "token and extended" in the sentence. We are extending the token right now in another place. Related?
CA: not in the sense of extending the lenght, but the scope. When we have it in the new place need to define the semantics. The unicast semantics are probably not directly extendible.
FP: this slide is hinting what the problem is. We have more details later
Klaus: want to briefly explain why this slide makes sense. When defined original group com draft were puzzled what it means to send multicast request in terms of REST. Came up with distinction "if you're sending same identical request unicast to everyone in group - and just optimize the many unicast messages as one multicast". This makes lots of sense. Lots of clients who want to receive notifications, would observe and send response. If each client would send 100% identical requests, could optimize. Had discussion in hackathon last IETF. 

CB: as long as possible we should stay inside this fiction. THe fact that the client is a member of a multicast group is orthogonal to that server then starts to respond. We need to see how this is coordinated.

MT presenting more slides

FP: see some sceptical faces in the audience

Klaus: want to rule out other solutions first before we do something like this
CA: I would like to come back on the picture of the unicast msgs, I am not talking of the token. The token indicated back is the token saying to the server I imagine you might have sent this through multicast. I am now sending msgs on the assumption that such msgs have been sent earlier.

CB (floor): this slide (19, "Range of Token values") raises red flags. If you think you need it, you're doing something wrong. Something not right in the architecture. Need to think of the client group that is tied to the multicast group. Need someone who stands in for the group. The entity that represents this client group manages the token space. Saying that "we could use server as the entity for that". Not the worst answer, except have to make sure how the server gets into position to speak for the client. May be security question in the end. Main point: multicast group and set of client joined that group is the entity we should be thinking about. How this group makes decisions. No problem dedicating to entity but needs to talk for the whole group. 

Jim: Except the fact that I have no idea how to fix the proxy problem, did you look at the possible solution where the server registers to the RD the resources it offers to be observed with multicast observation as available for discovery, and by the way here is the token that you need to take first to get multicast notifications.

MT: first part yes, second part no, makes sense to consider

FP: (to Klaus) when said would like to see other solutions first, was specifically for reserving ranges?
Klaus: overwriting mechanism. Very short answer why I don't like it is that this mechanism can easily fail if you lose messages. We need somebody/entity to manage this coordianation. We have questions when all observers go away, how does the server know where to stop. This simple module of 1 entity is not very stable as if this single entity goes away, the whole group goes down.
Cluster of problems and need to solve all of them. Not easy.

CA: discussed earlier reliability and everyone away topic. Would need message in multicast, every 10th or so, that solicits interest from the clients.
CB: sending to multicast is trimming resources. In various reliable multicast protocols have techniques for group management. For instance have random members of group respond to setting parameters, need group size estimate. Can be derived from current size estimate + how many responding. But issues with transients in the group. And so on. All are problems that are solved for reliable multicast. Everything we can do to scope the problem so that we don't need these mechanisms is good but maybe we find out in the end we want to inherit some of these.

Klaus: going back to the question how does a client determines that the message is for him, can it be done through the security context - piggy-backed on it
(yes, no, don't know from the room)

CA: not sure sure have a problem. When client receiving the response on multicast message, it will be aware of having requested something from that particular server. Would not ignore. Would be scoped to MC address. There tokens managed. Don't see how can be ambiguity on which message related.
CB: this particular  client didn't put in a request
Marco: what do you piggy-back - the token
KH: maybe token does not need to be unique in whole space but just the security context

CB: need to take to the list

MT presenting security part

CB: have had most sec discussion already. Client, multicast group etc need clarified model
More reviews would not help; more useful to have some ideas on how to recreate CoAP modeling in this context. Klaus knows how to do that.

Klaus: could use some CoRE interims for this. Since many based in Stockholm, could have full day f2f WS on this. Could be even CoRE interim day.
CB: it worked well for SUIT. They had 2 day interim that ended with the Berlin? hackathon and it worked very well for them.

draft-dijk-core-groupcomm-bis-01 (15) Dijk (Remote presentation)
Overview of latest updates (-01)
Explain scope and approach of document ( Standards track - Obsoletes: 7390 ; Updates: 7252, 7641, 7959 )
Get feedback/consensus if the current approach is right

Esko Dijk presenting remotely

CB: aware of anyone using the experimental rest?
Esko: No
CB: experiment completed?
Esko: that's possible

CB: seeing some nods in the room. maybe can consider experiment completed, will ask on the list. Timeline?
Esko: intial idea was to progress fast. Can come back to this Aug/Sept. Next IETF could have next version and WG adoption.

CB: interested in reviewing?
 - Jim, Christian, Klaus, Carsten, Jiye


Related:
draft-jarvinen-core-fasor-02        ipr (WGA???) (5)?

Markku presenting.

Markku: Is this ready for WG adoption?
CB: discussde last time. PRoblem with WGA was that we didn't know IPR delcaration. Now have detailed declaration. Everyone had to think about it. Went out with that from Prague. Could have done WGA rigth away, didn't do that. People have had 4 months of time to look at the situation. Do we have new data? Do we get new data at  Anybody lookked at this? 2 people nodding

Ari: I had a look at it, looks fine
CB: I think we should do the adoption call now

SenML
draft-keranen-core-senml-data-ct-02 (In WG Adoption call until 2019-07-17) (10)

Ari presenting

recap: binary values can be there (base64 in JSON or binary in CBOR).
New content format indicator to be added.
Content format as string as well? Tricky with content coding. @suffix seems to be suitable to express media type and encoding
Variable-type options are not liked in SenML. Quoted ASCII string number? Only compared anyway.
Questions

* String numbers OK?
* @-style OK? (It's illegal in media types, so it's safe)
* must-understand? Can be either-or so application can pick?

CB from the floor: would you ever not send the must understand semantic
Ari: would be up to application; could be e.g. middleboxes/storage that can safely ignore this
CB: hard time how a configurator of SenML would make that decision
Ari: Probably out of band condiguration
Robin Wilton: It's a nit, but ad prefixes: Had "v" for numeric value and "vs" for string. Cognitive dissonance, why not "vn" for numerical value?
Ari: made for efficiency, but that was already RFC so not something we can change now

CB: Raises same problem where we had elective and critical, and at some point found that's good for end systems and not for proxies, and split to safe-and-unsafe for proxies. Would storage nodes react to must-understand fields? Figure they'd just store them.
Ari: Depending on applications. You might have storages that need or don't need to understand.
CA: as soon as the storage system does anything it must understand the option in there
CB: the resolution is defined in such a way that you don't need to understand the field semantics
CA: yes but we have already considered the MUST understand field like time offset?
Ari: seems that we have an agreement on adding must understand feature, but maybe we will need to add more clarification how this is going to be used.

Asking about whether @-syntax is OK, looking at AD:
Alexey: Looks like an elegant hack. Need to check allowed characters, pro'ly OK. 
CB: "@" not allowed in media type, but allowed in parameters. Left part is a content type! 
Alexey: Would someone just parsing it as a media type, would they be confused by it?
CB: if you are actually trying to parse it, you need to look at the parameters too. Parameters could have @-signs, but only in quotes, but consumer would need to fully parse that. Optional parameters occur before the @-sign
Alexey: text/plain;parameter="foo@utf8"@deflate ? Please do add an example. Then can tell whether good idea.
Ari: will generate examples

Dave Robin: Does beg the question of why not "cd" along with "ct"? Don't like parsing strings. Also don't like the number as string too much. As long as numbers are small overhead is small, for 4892 it's more bytes.
Ari: 16 bit number space of content-format IDs. If you use the "ct" feature you are likely to put 100s of bytes in the SenML payload, so a few bytes here are generally not a big issue.
DR: but ignoring the numbers, ad "cd" and "ct"
Ari: Was previous design. Run into problems b/c interwork with base values, eg. base from numeric type and then later another with string causes complications. Could come up with precedence rules, but no simple way of undoing base values. Rules would be complicated, that's why we went for this version. But yes check out the previous draft.
DR: It's nicely atomic, but annoying.
Ari: Number as string did concern me as well, and many others, but seems to be kind of an engineering compromise that makes sense.


Additional point on SenML (not in original slides and agenda) - slide 131

Ari on SenML base values and must-understand values in general

We can define base value as "must understand" or "don't need to understand", and same for regular.
Slide shows possible combinations of these. But how are they resolved? Needs clarification

Carsten: You asked for WGLC, but it's not WG document. Could call for adoption but can't do myself.
Ari: WGA finished the 17th
CB: this needs to include examples for Alexey, etc and then we can WGLC.
Ari: So next version is WG document?
CB: If adoption went through (Jaime's call) then one more version to fix these issues

draft-tschofenig-core-senml-lbn-00 (Hannes) (10)?

Hannes presenting

Use of SenML in OMA was based on earlier drafts; RFC demands unique base name.
Overlooked consequence of RFC is that base name carried in each measurement, that's unfortunate b/c wasting lots of bytes. We use SenML as encapsulation technique, and fits purpose b/c it allows taking a bunch of readings, merging couple of requests to be shipped. Now need to carry in all messages uniquely identifying information.

Reached out at IETF/IRTF OMA meeting. Would be nice to define local base name. Can still use SenML and enhance if makes sense in context, and can still arrive at global name. Consequence is saving lots of bytes.

Recent point (not in document yet): Cases where we create an object on device, that requires us to construct the whole path, and require complete string to be present but don't know object instance allocated by client. [OMA client, LwM2M server; scribe's remark]. We could query first and ask for most recent one, even then there's no requirement on consecutive numbers. So there's more to that.

So I suggest to enhance SenML with local base name.

Ari: yes, it makes a lot of sense. We definitely need to address. There are different ways to do that with different pros and cons, but it makes a lot of sense.
CB: (This would need to be bln and not lbn to not affect only one record.) We do have the idea of Base URI in REST. Could tap on that. SenML has avoided that, but that's b/c it was meant for a certain area of application.

Ari: fully agree. THere is a new draft that I submitted on monday, which gives a way to send basename. There is IPR declaration coming, once that is cleared I will send a pointer to the core ML. ... that is an alternative way of doing it.

CB: Take-home-message is to accept the issue, but some alternative approaches to look at. What's the timeline to fix that?
Hannes: ideally yesterday. I understand that we need to see alternatives and we don't want to need to create a new revision. We'll need to ref / bugfix our specification because we currently don't properly use SenML.
Ari: It's violating a MUST there, but the reason is not applicable. It's kind of OK internally in OMA, but it's useful to fix this to be able to interoperate with other systems that have the assumption of globally unique names.


draft-bormann-senml-more-units-00 (CB) (10)?

Carsten presenting

intro to Units problem set. Useful set of units that also other SDOs are picking up. But have units that SenML registry don't have.

Do not want to break SenML's clean approach, but present additional approach and registry w/ big "SHOULD NOT" on it. "Relaxed units" with prescribed translation formula to SenML unit. Details in the draft. 

CB (from the floor): I see nodding. If we want to go forward with this, we will need to move quickly with it.
CB: how many care about this topic?
(lots of hands in the room)


----
CA presenting some enw things.

* use SCHC to compress CoAP options that seems to be somewhat bloated

CB: it might be good to have context for the usecases as SCHC relies on static context.

* Most of the coap libraries are working on msg level, not higher level
CA: I would love to work with lib authors
CB: it can become a wiki or if it is sufficiently stable, we can turn it into informational RFC.

* there is now CoAP-FAQ that collects all kind of questions. If you'd like to participate please come forward.
CB: it needs to be stated that it's authors from individuals
CA: it is already there

Flextime (25)


Σ 120
~~~~
