CoRE WG - Summary IETF99 {#toc_0}
========================

Slides: <https://datatracker.ietf.org/meeting/99/materials/slides-99-core-consolidated-slides/>

Raw minutes: <http://etherpad.tools.ietf.org:9000/p/notes-ietf-99-core>

Summary below, followed by detailed minutes; unfortunately a mishap
with Etherpad create a hole in the latter for Wednesday.

WEDNESDAY, July 19, 2017 {#toc_1}
===========================

Recording: <https://www.youtube.com/watch?v=hHJ3sQedQOk>

## WG status

- RFC 8132 (draft-ietf-core-etch -- PATCH and FETCH Methods for CoAP)
  published

- Core interfaces and dynlink have had a personnel change; expect them
  to be back to speed in the Singapore meeting.

- (Tim Carey asked about status of SenML and Resource Directory;
  Carsten stated that he expects SenML to ship to the IESG soon and
  Resource Directory is making good progress towards being finished
  this year; COMI is a set of drafts some of which may be finished
  this year.)

- draft-ietf-core-links-json-09: this is in IESG processing; however
  its base document, RFC 6690, has a base document, RFC 5988, which is
  getting a bis document (revision) right now, and we probably want to
  make use of the progress there.  (E.g., 5988bis makes clear that it
  is the serialization that would have to manage the target
  attributes, which we may want to add.)  Does this imply a revision
  of RFC 6690?  Make sure we coordinate with SDOs using links-json.

- draft-ietf-core-coap-tcp-tls-09: this is in IESG processing.  One
  IESG comment on -07 was that the "least worst" solution of one URI
  scheme per transport was undesirable, leading to the authors writing
  up a proposal to combine all transports under coap:// and coaps://.
  The WG did not like this solution as it is mostly unworkable in the
  scenarios addressed by CoAP-TCP, so we are rolling back to -07 with
  the mapping of coap to multiple transports (coap+tcp, coaps+tcp,
  coap+ws, coaps+ws).  Discussion on alternatives is available as
  draft-thaler-appsawg-multi-transport-uris-01  (presented by Dave
  Thaler).  A new "all transports" (`coap+at://`) URI scheme to be
  added to the mix, details are being worked on in a separate
  draft. Target of this new work is to have another URI scheme that
  enables the client to choose between multiple transports.

## WG Documents

- draft-ietf-core-cocoa-01: Presented in Chicago, some feedback now
  available from Michael Scharf and Ingemar Johansson.  Need to
  explain that we are heeding the advice of RFC 8085 by content, but
  maybe not by the letter -- we are not *relying* on the Weak RTTs.
  To add more about the reasons for the weak estimator, as well as
  possibly some tunability.  After this, do some editorial
  improvements preparing for v02 and finally WGLC, removing Appendix A
  (new work on Aggregate Congestion Control) but keeping Appendix B
  (Supporting Evidence).

### CoMI

- draft-ietf-core-yang-cbor-04: Document has now been stable for two
  IETFs, will look for new reviewers and ask for implementers'
  feedback on mailing list.  Target is to have WGLC 3 weeks from now.

- draft-ietf-core-sid-01: The SID registry was discussed during CoRE
  and the YANG of Things (YoT) side meeting. Progress has been made
  however issues as to the lifecycle of the registry have been
  raised. Discussion shall continue with YANG experts (and on
  yot@ietf.org mailing list).

- draft-ietf-core-comi-00: Extensive work, thanks to Peter Vanderstok;
  draft now technically complete but needs more reviewers.  Resource
  types renamed; paths updated to avoid conflicts.  Content-Formats
  (media types) defined, some of which making use of "ordered maps".

Alex: Two independent implementations (One in Go, one in C), not quite
synchronized at this time; some implementers in the room.  An interop
is planned for the Hackathon at IETF100.

- draft-veillette-core-yang-library-00: Where should this work be
  done?  Might need three groups of experts: YANG, Constrained and
  specific subject matter.  Henk notes that there is another draft in
  this space which likely will be done in NETCONF.

## Pulled forward from Friday

- draft-arkko-core-dev-urn-04: Draft resurrected after a long period
  of dormancy.  The concept is in active use in a number of
  SDOs. There was a discussion on whether the draft is actually
  describing hardware locators - which can change or can be multiple
  per device - or describing stable IDs.  Alexey stated that he would
  be OK both to AD sponsor this draft or to have it run in the WG.
  There will be discussion on the mailing list how to further handle
  the work.

- draft-amsuess-core-repeat-request-tag-00: The draft presents a
  solution to both (1) the problem posed by the lack of a standardized
  freshness mechanism - by providing the (to be renamed) "repeat"
  option as challenge, giving the CoAP server a way to ask the client
  to freshly re-transmit the request, and (2) the problem posed by the
  weak correlation of payloads making up a block-wise request body.
  The in-room consensus for adopting this document was based on only a
  small number of voices, we will need to confirm WG Adoption on the
  mailing list.

- draft-tiloca-core-multicast-oscoap-02: Provides Object Security for
  group communication (e.g., in multicast networks). It has met with
  interest by the WG and we reached in-room consensus that this should
  be adopted.


FRIDAY, July 21, 2017 {#toc_2}
========================

Recording: <https://www.youtube.com/watch?v=K1B5fy98kCw>

## WG Documents

- draft-ietf-core-senml-10: A few issues have been fixed (five
  revisions).  WGLC concluded on Friday.  Discussion on the use of
  special characters in names; new units of measure.  One more round
  will be taken to the mailing list to confirm the use of the
  registration policy for units.  Plan is to make those changes as
  necessary and then publish to IESG.

- draft-ietf-core-resource-directory-11: New editor Christian Amsüss
  added; regular teleconferences among authors.  Clearing up some
  ambiguities; creating an entity-relationship model of the
  information in the resource directory.  Be more specific about the
  ways a device can find a resource directory, taking into account how
  the device was configured and how the network was configured.

- draft-ietf-core-rd-dns-sd-00: Was recently extracted from the
  resource-directory document, with the intention to finish both
  drafts in unison.  Getting good attention from DNSSD people now
  (e.g., was discussed on Wednesday's DNSSD meeting).  DNSSD service
  types are registered with IANA; name mapping from the resource
  directory poses some interesting questions.

- draft-ietf-core-coap-pubsub-02: No substantial changes since WG
  adoption; keeping protocol simple.  Addressing substantial set of
  comments; Hannes, Michel, Kerry, Peter will add reviews.  Targeting
  WGLC in IETF100 time frame.

- draft-ietf-core-object-security-04: Now includes processing of
  request tag (see above).  OSCON removed to future separate draft.
  Added test vectors.  6 implementations, a set of 15 test cases is
  being tested in interops.  Plan is to do one more update (Dave,
  Kerry, Michael and a few others to review) and then go for WGLC.
  Interactions with RFC 8075 HTTP mapping: OSCOAP needs more exact
  mapping of CoAP codes than defined in RFC 8075; details to be
  defined.

## Other

- Quick advertisement from Laurent for the need to provide some
  end-to-end information about wildly different time scales caused by
  millibit/s available network rates. (Remember Patience option?)
  Avoid potential for misuse for state-buildup DoS.

# Detailed minutes

Thank you to the note takers!

~~~ text/plain
---------------------
╔═╗┌─┐╦═╗╔═╗  ╦ ╦╔═╗
║  │ │╠╦╝║╣   ║║║║ ╦
╚═╝└─┘╩╚═╚═╝  ╚╩╝╚═╝
---------------------

# Core@IETF99

Constrained RESTful Environments WG
Chairs (core-chairs@ietf.org):
Jaime Jiménez
Carsten Bormann

Note Takers
Christian Amsüss
Jaime Jiménez

Jabber
Jaime

## WEDNESDAY, July 19, 2017
0930-1200 Congress H I
------------------------

Intro and advertisements (10)

Some talks moved to Friday.
Alexey: URI TCP protocol talk needs quite some time, can we push it to friday?
CB: What is on the agenda is to show the suggestion and ask whether everything in CoRE still works with that.

Point to DNSSD meeting happening later that day (15:20-16:40) relationship with RD will be discussed.
Side meeting with YANG of Things (YoT) on  Thu 10:00-12:00 (mitigating conflict between netconf and cbor)

Published:
draft-ietf-core-etch now RFC8132
In IESG Processing, more WG input required:
    Actively being used by other documents

- [Minutes lost from Etherpad shutdown]

draft-ietf-core-links-json-09

- [Minutes lost from Etherpad shutdown]

Stuart: The discussion is around service name. The discussions were convoluted
Many service discovery protocols confound two things: discovery and use
At the point of choosing the service, you don’t need to know how to use it
Get a brief summary on the use of the service
Dave: I don’t believe that you can always do selection without transport discovery
How do you make a selection if you don’t know if you can use it? (e.g. compatible underlying protocol)

SC: This is why you asked whether URI’s should be used at all
DT: Some people don’t want to go through the extra step. For constrained devices it’s not good to have multiple
protocols to implement due to limited space.
David: Could people use service discovery for neighbour discovery. Generally yes.
ST:
DT: Some people don’t want to have mDNS inside constrained devices.
SC: 16kb of memory on some devices. 900b of space for mDNS does not seem as a good argument.
SC: DNSSD feedback would be welcome. Many protocols contain 2 steps - discovery and use. E.g. I want a printer,
which ones are available.
David: Selection is once-in-a-lifetime thing, use is a day-to-day thing. We should not bind these two.
Example: sleep proxy :
Service type: sleep-proxy
M2M service discovery for 10 years


draft-thaler-appsawg-multi-transport-uris-01 DT


OCF solves that with ocf://, but you still need to find the actual transport protocol. Some things already use
URIs for hosts (with paths etc); so -07 worked for them. Discovery can be a process or attributes passed when
the name was learned.

OCF example: top-level URI only has UUID, with "ep" pointing to the transport URIs (coaps://, coaps+tcp://
etc). The protocol stack gets that information, but the application only uses ocf://uuid. -07 worked well for
that because it's single-layer, not the same mechanism applied twice in a tree.

Discovery vs. selection: This is mostly about discovery; selection can happen later with happy-eyeballs-style
or what so not.

Discovery: 4 approaches

1. URI scheme hard-codes transport, eg. TFTP

2. Encode everything in a URI, pack all up (ugly).

3. Use a set of URIs, one per transport stacks (-07 submitted to IESG) – but has multiple URIs per resource.

4. Why even use URI? Have the locator in URI format but the per-transport definitions (may be URI for ws://,
may be not like UDP host and port).

Back to CB (but questions right now):

Stuart: (back to slide 19) frustrated by the process – worked a good time on service discovery. Port number is
a historical anomaly in the IP architecture. A hostname only gets you to the hardware, and then leaves the
application. DNS-SD uses SRV records for right that. "Escape the tyranny of well-known ports" is 15 years old
and still not taken up.

DT: I complained about this in the document that I can't put an SRV name in there. The link-format examples
often include IP addresses because no extra resolution is done. Why not DNS-SD? For constrained devices, they
already implement one protocol, and can't afford having a second protocol.

SC: Know the argument, unconvinced. CB: This is about resource, not about service discovery. DT: Could you do
service discovery for resource discovery? Yes, apart from the constrined argument.

CS: Argument is "resource" is different from "service". DT: Arguent is more "We don't want to have DNS in the
tiny devices".

CS: Had a hackathon long time ago, 16k flash devices with 9k data payload had Ethernet and IP and DHCP, and
added mDNS in 900 remaining bytes. On slide 19 in particular: There is a new DNS-SD -00 document, one of the
principles of that: Many self-discovery protocls conflate two steps, "discovery" and "use". Discovery is "show
me the choice of printers". When chosen, IP addresses are not yet relevant. Next step when picked is getting
the contact information.

DT: (doesn't believe that selection can be done w/o knowing whether common transport is supported).

SC: That's a philosophical debate as to what a service is, and what is in the bundle. […] Transport information
may change from day to day, and when it's selected, the transport can have changed already.

CB: The WG is used to input from processes that have humans involved, so it's sometimes hard to link the
experiences to this. SC: Anima said the same, and it is nonsense. Example (10a old, bonjour proxy): Device can
select a Bonjour sleep proxy without any further interaction, use it, and do all that w/o human interaction.

* Kerry:

 1. Not all resources are services, but restful API endpoints can (with some squinting) be DNS-SD services.
 2. Cullen proposed http+srv a long time ago (DT: Yes that works, but needs the scheme to support it and can't
retrofit into an existing scheme)
 3. Dominant paradigm of discovery is knowing ahead what is looked for; only rarely it's a "what can we do?".
The latter is in the minority. (DT: That's for every device, but not for all applications of them.)
 4. Response can be driven by information from the request. […] Addresses in the source field drove addresse
there. link-local addresses not returned when requester asks from a global address.

Tim Kerry: DNS-SD used in several SDOs where no constrained devices are around. Question: Outside of getting
things ahead. Doesn't the protocol negotiation draft solve this problem?

DT: Does that negotiate with http too?

TK: Client and server can negotiate that. DT: If it's equivalent to HTTPbis discovery, it's solved with an
additional rooundtrip. If that data comes from RD, it saves us bandwith. TK: Yes, we can hard-code everything
somewhere too.


 DT: People will use different paths, but we can and should decide what IETF does.

 * CS: The text in the p19 example is bigger than the implementation.

 * CB: Those 900 bytes are an advertiser, not a full client.


SC: Transport information may change from day to day. There is first the selection phase that happens only
once. It’s DHCP may change, other connection details might change, but the selection happens only once.

CB: in this group we are used to people commenting based on experience with humans, and often that’s not the
case.

SC: Other WG (ANIMA) also do have similar claims on Service Discovery “for humans” and it does not apply.
There were some explanations about proxying on behalf of devices that go to sleep to save power.
Bonjour can be used for m2m, I don’t know where the myth that this can not be done came from. We have being
doing this for 10 years now.

Kerry Lynn
I agree that REST api and “service”.
Historically: HTTP+srv

DT: If the URI scheme allows it, you can fit any kind of information into the URI. You cannot retrofit service
names into existing schemesinter

KL: The general conception of discovery is: you know ahead of time what you are looking for the most of the
time. The other is really minority.
Response can be driven by what is in the request.

Tim Carrey: Some constrained devices are using DNSD, so people could consider that as well where they would use
mDNS. Doesn't protocol negotiation draft solve this issue?

DT: Only if it’s not specific to CoAP in terms of what it can discover.

TC: The protocol negotiation draft is supposed to be for C and S to negotiate transports.

CB: We will have time for this discussion later

DT: When you get the data from the directory you save on round-trips and negotiation. So protocol negotiation
with the actual device after discovery solves this but has some downsides like the extra round trip.

TC: could hard code everything too; not convinced roundtrip is necessary

DT: What we see out of the scope of CoRE is that different SDOs have different use cases, we are trying to
figure out what to do with the URI scheme in IETF as that is something we can control.

SC: in terms of number of bytes, the example has more bytes than mDNS implementation
DT: slide content is not literally sent on wire; not good example of that. Wire would be CBOR etc.

draft-ietf-core-coap-tcp-tls-09 CB
Objective: Review possible resolutions around the URI Schemes issue raised by IESG; discuss the related
immediate need for further work on transport indication/protocol negotiation (45).
Target is to have one URI scheme that maps to multiple transports.
Compromise is to revert to -07 and add one new scheme coap+at:// for "all transports" (equivalent to coap://
coap+tcp:// and coap+ws://)
Barry Leiba: Is the intent that coap+at would be the main scheme instead of “coap”?
DT: Yes I believe that would be similar to OCF's use of ocf scheme, which is going to be what application would
use. Unless we are talking about really low level apps.  
CB: the area where we need these additional transport is a niche within CoAP. We could define multiple of these
encompassing URI schemes.
DT: if coap+at was defined would OCF use it? Answer is bordering to no, depending on how you define it. Would
need one that worked for all RESTful protocols, not just CoAP. Security implications too.
Barry: We painted ourselves into a corner with multiple transports. It’d be better to move forward with the new
scheme if we really choose to use it.
DT: My current belief is that it will take a while to work out the details. It’d be better to have it on a
different document. OCF is using URIs as syntax already but others aren’t. We don’t want to slow down the RFC
process on publishing the protocol, especially for those who don’t need the URI schemes.  
Barry: could have document to update this.
DT: W3C architecture encourages different URI schemes when different security semantics involved, so another
example of a detail to work out is whether we also need coaps+at separate from coap+at.  Another example of a
detail is the discovery mechanism, will we need to update the RD document?  The link format document?  Define
how to use DNS-SD?  Those are all non-trivial discussions that will take time.
Alexey: OK to do it in a separate document.
CB: Can we avoid a normative ref so that it’s not left in the queue.
Barry and Alexey: yes, with forward references / update to doc.
CB: This seems the way forward but not pretty.
There are two documents that are related to the discussion.

draft-silverajan-core-coap-alternative-transports-10

Discovery infrastructure needs to provide that information. DNS has SRV, but we need a place to put that w/o
DNS, so we can do that in target attributes.

Look at Bill's draft.

BS: Slides are a bit outdated because thigns happened just now. alternative-transports was chartered for
whether this can be done with other URIs, and then there appeared the problem of finding them. Recent
discussion was useful. Current alternative-transports says why transport data can't be put in URI. coap+at is a
compromise for that. As for protocol-negotiation: should work with or without an RD.

draft-silverajan-core-coap-protocol-negotiation-06
        - target attributes of RD
Bill Silverajan: the reason for two drafts is that when the alternative transports draft started we also notice
the problem of discovering multiple endpoints.
Objective: Review possible resolutions around the URI Schemes issue raised by IESG; discuss the related
immediate need for further work on transport indication/protocol negotiation (45).


WG documents ()

draft-ietf-core-cocoa-01 Carles Gomez
        - presenting feedback on -02 (wasn’t it what will be in -02, still not ready)
Editorial changes:
Adds considerations for application delay.
Properties and reasons for weak estimator added.
7252 references added for unfamiliar readers
Appendix A removed (was not same quality as rest), B stays
Objective: Evaluate positions of related WGs/RGs and go for WGLC (10).

-01 as presented in Chicago, received reviews. -02 should go to WGLC.

Feedback:

* RT estimator uses strong and weak RTTs (the latter are retransmissions), so possibly violating RFC8085 – but
we're not relying on them. Weak RTTs are needed to update the RTO estimates where it otherwise would be
impossible to get that information: Links with high losses have mainly weak RTTs. Networks with spontaneous
congestion can be detected with weak RTTs.
* Link with very large RTTs (> default initial RTO): Need weak RTTs to update RTO accordingly.

Plan for -02: Make impact of strong/weak RTTs tunable (parameters rather than 0.25 and 0.5).

draft-ietf-core-comi-00 (Michelle Veilette)
Summary of COMI Framework
Yang-cbor ready for WGLC?
There is work on creating a SID registry, which might help to improve the draft.
Yang-library in scope of CoRE?
Michelle: what is the right fora for the data model work (yang-library)?
CB: We have tomorrows meeting to find out the division of work (maybe meaning side meeting Yang-of-things).
Perhaps another group has more expertise on building mibs.
Hank : Facing a similar problem – wanted to start CoMI-YANG model for software inventory; are pretty sure to
know how to do the concise representation, but are not netconf experts, so considering doing that in the
netconf group, should be discussed.
CB: You need three groups of exports: YANG, Constrained and specific subject matter.
Presenting COMI updates.
Content formats: different formats have different delta starting points and reference SIDs (in some instances
with data from FETCH, and includes CBOR extensions; uses iPATCH)
Ordered map CBOR tag: requested from CBOR registry; here, it is not explicitly used but inferred from the
content format.
Error handling clarified (CoAP error and YANG errors); the latter modeled after RESTCONF. Proposed CoMI version
only has one error (the first / most important), only one error type and no error-info. Error tags are
extensible.
Alexander: These changes were agreed on earlier IETFs, next steps are implementations. Two independent
implementations are known (Go, C), two other out there. Details need to be synchronized. Interop will happen
over the Internet in August. Interop in person will be in Singapore.
CB: Who here is implementing some of this ecosystem? 3 from Ackl.io.
Alexander: Going for WGLC on CoMI document before Singapore. Needs much input from netmod [?].

Draft-ietf-core-yang-cbor-04 (Alexander Pelov)
Alexander: It’s worked out – can have WGLC now? 3 weeks from now.
CB: three weeks sounds reasonable time to wait. But don't see other things blocking this. Could go for WGLC
after interop. Assuming no major surgery needed. For CoMI document we expect more input and updates to draft
coming.

Draft-ietf-core-sid-01 (Alexander Pelov)
Most open points cleared out, lifecycle remains.
Action points since last time:
Mega-Ranges introduced, NETMOD meeting happened (Thursday YoT 10:00-12:00, yot@ietf.org)
YANG registration consists of mega-range registry (IANA, 1M blocks) to SID range registry. YANG registry is
another registry that keeps the YANG files.
Developer allocates SID range, but there is no process of sharing the YANG files yet. Private YANG files are a
must, so that part should be supported, but people should be motivated to publish their YANG files if they are
not strictly private.
        Public registration should be incentivised. An implementation of the YANG registry exists, and will be
further developed and tested in August. One-step registration should be allowed.
Pascal: When you have an item that is defined multiple times, would you assign multiple sids?
Alexander: Rephrasing the question: if we have mac address somewhere, tell people to inherit from that yang
module and not redefine it multiple times. Could be possible to add some kind of support for this to the
YANG/SID registry. Would be good to be able to use the same SIDs.
Juan Carlos: Would it be automatic or with human interaction.
Pascal: It will be automatic, but how this is done will be very important as some tool will have to scan a huge
amount of other yang/sids and the use of the sids later on will somewhat depend on how this discovery is done.
Michel: SIDs are assigned to fields, (?)
Juan Carlos:
Alexander: It can be a two step process. We want to start with the public registration and we make sure that
the private is still supported, so that it can be added later. There is already some input from industry on
that matter.

Draft-veillette-core-yang-library-00 ()
[skipped]
Objective: Go for WGLC (35).
Related Active Documents (not working group documents):

Draft-arkko-core-dev-urn-04 (JA)
Presenting draft.
Updated for this IETF. Another update coming. Especially on security.
Tim: we use this so we would support this to become RFCs. Is it possible to add identifiers to the draft?
Jari: has capability for extensions. Syntax obvious for that. If have specific ones, can add things now or
later.
Henk: Trusted computing hat on. Positive on this. Would like to see specific integration of this. Finding IDs
hard. Have semantics for OIDs. Could talk about off-line. GE very much interested to plug into right IDs.
Jari: please post to the list
Dave T: good idea, but 1st sentence on slide is not what doing. This is doing hardware locators not IDs. Some
HW devices more than one MAC, or the MAC can might change. If want ID per device, want hash of public key or
such. Would be useful even when multiple MACs. If that, why using URIs as syntax for locators?
Jari: the use case for this involves using as particular pointer for ID. We have other IDs. These are more
straightforward identifiers. More discussion.
Henk: Quoting 4949: IDs for data objects.
Dave: IDs unique and stable. Locators can change or you can have multiple of them. With multiple MAC addresses
you have a locator.
Barry L: have many situations where things have multiple names; not necessarily locators. Question: is mac/ow
part of URN possibly delegated to another organization?
Jari: could define mac urns and define something under that. But question: who is responsible for ID space? For
this doc, we are clear IETF is not responsible. IEEE etc. Just referencing the space, not claiming this doc
would take jurisdiction.
Barry: Could someone get urn:dev:bleep and get rights to assign there?
Jari: possibly, but draft doesn't currently discuss that. Maybe we should.
Alexey: would like to get bit more confirmation if there's interest. Seems to be. Either WG doc or sponsored by
me.
Carsten: sense there is interest in room. Matches with other things. Would expect us to pick this up.
Objective: Discuss further handling (10).

Draft-amsuess-core-repeat-request-tag-00 (Christian Amsüss)
Presenting document. Changed organization between the documents.
Issues:
        Freshness: CoAP has no freshness guarantees. Solution: possibility for server to ask client to
re-transmit the request.
        Blockwise: request body correlation is weak (on purpose). But can cause issues with representation
changes between GETs. Solution similar to ETag.
Can we update RFC7959?
CB: Who has read the document? (4 hands). Who understands the problem statement? (15). Who has read a version
of the document? (3). To be confirmed on the mailing list...
Objective: Ready for adoption? (15).

Draft-tiloca-core-multicast-oscoap-02 (Marco Tiloca)
        - OSCoAP for group communication
Recap of the mechanism: Common context, and multicaster has several recipient contexts.
OSCOAP’s requirements are fulfilled by countersignatures.
Group manager is employed for joining/leaving and handling the key material. New in the current version are
pure listeners. Compressed COSE object like in OSCOAP, with additional flags/fields. Revised synchronization
mechanism.
Additional considerations are there for signed messages in unicast (inspection; because this is what introduced
countersignatures), and low-latency requirements (when asymmetric keys take too long).
ACE joining is described in ace-oscoap-joining.
DT: Good work. Thank you.  “pure listener” – group communication only uses [?] model. Is this now applicable to
SSN model? ...
Carsten: who has read the doc (~10 hands). Good basis (bit fewer hands). No one thinks is not good basis.
Alexey: don't ask yet if should be included
Objective: Discuss updates, find reviewers (10); Slot leader: Marco Tiloca


## FRIDAY, July 21, 2017   
1150-1320 Congress H III
------------------------

Note Takers
mjkoster
Jabber
Jaime


Brief intro (5)WG documents (WG last call completed by Friday)

draft-ietf-core-senml-10

Objective: Process WGLC comments (15).

repeating base values fix alot of issues
added syntax for "must understand" items
added text and examples for actuation
explanations added
TBD:: registration policy question

Carsten ( no hat): Good experience keeping multiple doors open. Should not confuse anyone, lets keep
Alexey: Two ways have caused confusion in the registry. Sometimes people skip directly to IESG approval.
Recommending only expert review
Jaime: We will check on the mailing list and then confirm option a) or b).
Ari: Taking one more round on the mailing list.

Links extension. Reason to have in base spec was to get CBOR tag, but saving one byte not worth it. Will move
to separate document.
Ari: see nodding in the audience.

Names don't allow semicolons, but there are some URI schemes that use it.
Is semicolon a safe character? Database usage etc.?

Kerry: altitude is describing two ways (above sea or ground level), you should have some reference.
Ari: Coordinates are much more complicated than we think. Might need additional document to clarify. May be
part of that document.
Christer Holmberg: Semicolon usually has a special meaning.
Ari: Have special meaning in URIs, but question is whether it's an issue on a DB keys and such
CB: ";" Dangerous when feeding to the shell. Minimize people doing that. But otherwise relatively safe.
CB: On "alt" - pressure might be absolute or relative. Engineers started using different units for this, but
not compatible with SI. One mistake might be, we don't have quantity field (what exactly is measured). Need
more contextual information. Keep it for alt to be done. In the future need to be able to label things. Should
start working on this.
Dave Thaler: Liked CB's suggestion (sarcasm). Note that K and °C is same unit in that sense.
Carsten: "alt" is a quantity, "meters" is a unit additional semantic information about what is being measured
is also needed
Bill: Are there any characters not allowed? Should enable users to have more than one URI format.
Ari: There are others that also have the @ sign. More tricky. So far no objections to adding semicolons; take
it to the list.
Jaime: Have you thought about using ucum and getting expertise from other orgs?
Ari: Yes, we will work with W3C and domain experts.

Carsten: Authors will consider WGLC (?)process after answering these questions.
Jaime: Target Singapore (IESG)?
Ari: Earlier. Will do an update ASAP.
Dave Thaler: The document as is list C and K as separate values, but by Carsten's definition they're the same
"unit".
CB: We have notes on what not to use, but we have experienced that it will be used.
CB: (something is a bug)
Jaime: have quick update on mailing list (celsius units vs kelvin) to verify.


WG documents (after DNSSD first meeting)


draft-ietf-core-resource-directory-11 (Michael Koster)

Added new editor to help polishing: Christian Amsuess
Reduced ambiguitity (ER diagram helped)
RD can be seen as shadow of .well-known/core with additional parameters

Dave Thaler: Fix for terminology: Port is part of the authority component (slide says scheme://authority:port)
MK: right

Will create ASCII art from figures.
Remaining: simplify section on finding an RD
Need to check URI templates for correctness.
MK: target is WGLC before IETF100


Finding an RD CB

2,5 options:
Special config on the device.
Device not specifically configured (network configured via SLAAC, RDAO, DHCP)
Last Resort (RDDNS, ABRO)

CB: DHCP option is not yet defined (possible new work TBD).

Stuart: In a local network you would use DNSSD.
CB: How should DNS-SD be used? not defined.
Stuart+DT: disagree.
Stuart: By UPnP you mean SSDP. Those should be on the non-specifically configured. Seems like an odd choice.
CB: To use mDNS.
Stuart: It is not mDNS. here at IETF, you use wide area DNS discovery, and same on the mesh network 15.4.
DT: If you have a DNS server, you do DNS-SD over DNS, not mDNS. If you can discover a DNS server then it works
just fine. The practice highlighted is a bit more complicated than that.  You can get your RD address the same
way as your DNS address(es) or you can use the DNS server address to get the other addresses (DNS-SD approach).
limiting the choices is something more of a INT area work. DHCP would be for those who want to use that. INT
area (6man) is looking at defining another mechanism, see work on "Provisioning Domains" e.g., where your
router is multihomed to two networks with different RD's and so the RA alone is ambiguous
CB: We want to avoid DNS as mandatory for use on RD.
Bill: I worked on service discovery protocol. Self-discovery meant that there was an active process. Service
lookups would be a specific case. For energy constrained devices multicast is too much. For a simple device
listening to mDNS traffic was too heavy.
Dave Robin: Branch 1 bullet 1 is consistant, the other two bullets should go into branch 2. You are looking for
a service, not specific host.
Hannes: This presentation was for the RD document. INT area has too many mechanisms for interoperability.  
Should RD be silent on these issues. Different orgs will select different mechanisms. Would hurt interop.
CB: Want resource discovery with "batteries included". Client implementations would have default way to find
RD. Would like to decide on a default here.
Stuart: bendig over backwards to avoid using existing solution. RD is a service, why not use existing solution?
Carsten: for win 10 good idea to always include these
Stuart: fail to see the obvious solution
CB: just refuse to use it.
Alex: also constrained networks, not just devices.
Stuart: There are two 6762-mDNS 6763-Service Discovery which does not have to use multicast. Printer as an
example.
Erik Nordman: different assumptions from different people on constrained devices and networks. RPi is an IoT
super computer. Very different from millibit networks. Very different environment. Do we need all of these
things? Even if they fit on RPi, that's irrelevant.
Stuart: if there is such constrain, then it should be written down (CPU, memory size, etc). 15 years ago we had
also very constrained devices. Device had 700 bytes of code space and could fit mDNS there.
Hannes: without security and FW updates
Dave T: See RFC 7228 table 1
Carsten: don't want to make IoT space dependent of DNS. ND is right way in that space.

[ will take it to the list ]


draft-ietf-core-rd-dns-sd-00 Kerry

Kerry: RD can be fairly resourceful. Clients don't need to specify a specific method to find the RD.

Discovery was not in the charter back when we started in CoRE. PvS and I worked on how to use DNS-SD properly
in this environment. CoRE eventually used .well-known and RD. Fallback at that point was how to translate one
system to the other, supporting heterogeneous environments.

Presenting DNS-SD

"rt=", resource type currently a hierarchical namespace, we have the oportunity of making it federated.

Presented on DNS-SD on wednesday, important to get input from both WGs.

Tim Carrey: has the formatting been validated.ent to put it on the right format. DNS accepts a wide format.

[...]

Kerry: Will need to take to list notion of federated name spaces.

Dave: _udp has releationship with draft I presented in core earlier this week. You need to cover coaps vs coap
links, cover udp vs tcp (see the coap-tcp-tls document), and especially cover coap+ws where service names may
not be applicable. I hope draft -01 will cover a more complete solution.  But good work so far.
Bill: hope to be able to map lifetime values with RD.
Kerry: DNS has TTL. Would like to be signaled with target attribute?
Bill: potentially. There is default value though.

Carsten: good start, needs bit more work. Not rocket science. Need few more examples.


Objective: Converge on the emerging information model and the DNS-SD relationship (30).

WG documents (avoid TLS conflict)
draft-ietf-core-coap-pubsub-02
Objective: Confirm progress (10).

Michael: going on well. No substantial changes on what does. Mostly clarifications. Philosophy: keep protocol
simple. No queing in the base spec. Addressed substantial amount of comments from Jim. For reliable
notifications working on extension (see issue #5). Next version will address outstanding comments. Few more
substantial decisions on corner/special cases. Reworked normative language to facilitate test cases. Security
guidance. OSCOAP for pub/sub. Access control. Targeting WGLC for Singapore time frame. New update targeting end
of August.

Carsten: for the next version, good to have people to review that.
 - How many have read (20 or so)
 - who to review (Jim, Hannes, Peter, Bill, Kerry, etc.)


draft-ietf-core-object-security-04 Goran S


4 Interops
6 implementations
15 tests

Tim C: concerns with e2e security. Headers integrity protected. Privacy concerns. Are those issues addressed?
Göran: don't remember exact headers that were discussed. Table in draft that shows which options are
crypted/integrity protected.
Tim: privacy concerns with some integrity protected ones. Will remind off-line.

Carsten: after update need reviews. Should look closely privacy considerations. Plan when next version out?
Göran: concluding after next week. But vacations coming. Let's aim for August.
Carsten: version coming in August, who would review?
 - Dave, Kerry, Michael, Tim, (Edgar)
Carsten: implementors to review? RIOT folks?

Carsten: Appendix A will move to body. Defines HTTP mapping. RFC8075 requires extensions to define mapping.
Change from 8075 here; which assumes that CoAP req/resp codes are similar but not entirely alike. For security
need to make sure you get exactly same, otherwise can't verify. Solution in appendix A: HTTP header field "CoAP
code", which transports the CoAP code through HTTP segments. Not really OSCOAP thing. Other uses of HTTP-CoAP
proxies can use this. Suggesting separate draft on this. There was HTTPbis / CoRE chairs lunch to make sure
things are aligned.
Dave Thaler: coordinationw ith HTTPbis good. Separate doc good. Maybe only needed when the code is not
"exactly" same between HTTP and COAP. So not needed for every single packet.
Carsten: will define cases where value can be inferred

draft-ietf-lpwan-ipv6-static-context-hc Laurent

Timers need to be adjusted with CoAP in LPWAN. For example "keep this longer than usual". Proposing CoAP option
for time scale. To maintain message ID for long period of time to the server.

Carsten: retransmission might come after one hour
Tim: as a server you're asking me to keep per client state info while talking?
Laurent: case now, but only 5 minutes (??)
Tim: want now to wait for one hour while waiting to wake up. Can get complicated with multiple networks. What
do you do with info you want to get? Need to queue? What's fresh / stale info?
Carsten: Requires bit of thinking. There was option called "patience"
(https://tools.ietf.org/html/draft-li-core-coap-patience-option-06). Decided we didn't need it. This could be
resurrecting that. Heads up for this kind of work needing to get done.
Erik: the example you said indicates only one message . Is there a limit so that don't need to store thousands
of these?

Carsten: for a node that is prepared to talk to a node that uses special measures. Who interested to wokr on
this?
(Alex)
Carsten: will implicate Matthias

[Meeting adjourned]


draft-mattsson-core-security-overhead-00
draft-hartke-core-e2e-security-reqs-02
Objective: Confirm progress (30).

No discussion time this meeting:
draft-ietf-core-dynlink-03                        2017-03-13
draft-ietf-core-interfaces-09                        2017-03-13

draft-becker-core-coap-sms-gprs-06                        2017-02-20
draft-groves-coap-webrtcdc-02                        2017-04-19
draft-groves-core-bas-01                        2017-03-13
draft-groves-core-obsattr-00                        2017-02-21
draft-groves-core-rfc6690up-01                        2017-04-19
draft-groves-core-senml-bto-01                        2017-04-19
draft-groves-core-senml-options-00                        2017-03-10
draft-hartke-core-apps-07                        2017-02-12

draft-hartke-core-pending-00                        2017-02-27

draft-liu-core-coap-delay-attacks-00                new        2017-07-03

draft-urien-core-identity-module-coap-02                        2017-06-23
draft-urien-core-racs-09                        2017-06-09

draft-wang-core-opcua-transmission-01                        2017-03-13
draft-wang-core-opcua-transmition-requirements-01                        2017-06-21


~~~
