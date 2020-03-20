CoRE WG - Summary IETF100
=========================

* [Video Recording](https://youtu.be/wd_kXam1lIw?t=0m55s)

* [Slides](https://datatracker.ietf.org/meeting/100/materials/slides-100-core-consolidated-slides/)

* [Raw minutes](https://etherpad.tools.ietf.org/p/notes-ietf-100-core)


## Monday, Nov 13, 2017
### WG ITEMS

* [draft-ietf-core-links-json](https://tools.ietf.org/html/draft-ietf-core-links-json-09) was not discussed at the meeting.  It is in
IESG processing, with a few DISCUSSes.  Resolving these was delayed
as technical questions needed to be addressed, including the fact
that with RFC 8288 replacing RFC 5988, the ground on which RFC 6690
was built is shifting a bit (and this draft essentially complements
RFC 6690).  Some good input was provided by OCF at the 2017-11-10
OCF/T2TRG meeting, which will now enable these changes to be made.
Another WGLC should then follow.

* [draft-ietf-core-coap-tcp-tls](https://datatracker.ietf.org/doc/draft-ietf-core-coap-tcp-tls/) is in IESG processing, waiting for Mirja's
DISCUSS to clear [it is now clear that this will be in December
after her vacation].  The first interop on Saturday had 2.5
implementations (libcoap, augustcellars and coap.me), with a CoAP GET
performed on /.well-known/core (which exercises a lot of the machinery
already).  Editorial input from the interop should lead to a -11 soon.

* [draft-ietf-core-cocoa](https://datatracker.ietf.org/doc/draft-ietf-core-cocoa/) WGLC has been started on the mailing list
the authors also request feedback from ICCRG and TCPM.
Dec 14 is the extended deadline.

* [draft-ietf-core-resource-directory](https://datatracker.ietf.org/doc/draft-ietf-core-resource-directory/) has seen quite a lot of progress in
the last few months. Developers should start updating their implementations
as interop would be call on Q1 2018. Work over multiple transports and new
schemes still to be done. The increased work needs to transfer to
sister document draft-ietf-core-rd-dns-sd now. We expect to pass WGLC by
IETF101.

* [draft-ietf-core-yang-cbor](https://datatracker.ietf.org/doc/draft-ietf-core-yang-cbor/) is stable, but hadn't had enough interop testing
to enable a WGLC. Initial testing happened during the IETF100 hackathon now.  
Interop is intended for IETF 101, after which WGLC will be issued.

* [draft-ietf-core-comi](https://datatracker.ietf.org/doc/draft-ietf-core-comi/) and draft-ietf-core-sid need some more
finishing touches, also probably with fixes coming from the interops
(bi-weekly meetings to be continued).  There was some discussion
about cutting the plethora of request types in basic COMI down to
just FETCH and PATCH (possbly with GET added), to be continued on
the list.  Completion expected quite soon. Tools to visualize SIDs
would be necessary.

### NON-WG ITEMS

* [draft-birkholz-yang-push-coap-problemstatement](https://tools.ietf.org/html/draft-birkholz-yang-push-coap-problemstatement-00) was presented; the WG
now needs to have a look into how YANG Push and telemetry
requirements are going to relate to COMI and CoAP Observe.

* [draft-hope-bailie-http-payments](https://tools.ietf.org/html/draft-hope-bailie-http-payments-00) was presented as a heads-up; several
participants stressed the relationship of the subject matter to ACE
work.


## Tuesday, 14th Nov, 2017
### WG ITEMS

* [draft-ietf-core-senml](https://datatracker.ietf.org/doc/draft-ietf-core-senml/) finished WGLC and needs some remaining minor
updates, to be submitted to IESG in November.

* [draft-ietf-core-object-security](https://datatracker.ietf.org/doc/draft-ietf-core-object-security/) will be ready for WGLC with some
impending minor fixes in the next version.

* [draft-ietf-core-coap-pubsub](https://datatracker.ietf.org/doc/draft-ietf-core-coap-pubsub/) is sailing along and could get ready for
WGLC with the next version.  Implementation status to be collected.
Early adoption of the new 4.29 response code (as requested by
implementers of the OCF specification) was non-controversial;
discussion centered around the best way to add response codes (a
short draft for 4.29 could also include some other new response
codes, if they are as non-controversial).

* [draft-ietf-core-dynlink and draft-ietf-core-interfaces](https://datatracker.ietf.org/doc/draft-ietf-core-dynlink/) had been in
limbo for a while.  With a new editor, the remaining editorial
issues can be fixed.  The documents are best kept separate.

### NON-WG ITEMS

* [draft-vanderstok-ace-coap-est](https://tools.ietf.org/html/draft-vanderstok-ace-coap-est-01) poses a problem that
[draft-hartke-core-pending](https://tools.ietf.org/html/draft-hartke-core-pending-00) solves by proposing a new response code.
Discussion centered around ways that a combination of existing
response codes could be used instead (5.03 and 2.02), possibly with
defining semantics for the Retry-After option for the access to a
Location - provided with a 2.02 - this would avoid adding another
"success" response code.

* [draft-tiloca-core-multicast-oscoap](https://datatracker.ietf.org/doc/draft-tiloca-core-multicast-oscoap/) had in-room consensus for
adoption as a WG document in Prague already; this was newly
confirmed; validation of the adoption decision will be sent to the mailing list.

* [draft-liu-core-coap-delay-attacks](https://datatracker.ietf.org/doc/draft-liu-core-coap-delay-attacks/) proposes a time-based approach to
the freshness problem solved with a nonce in
[draft-ietf-core-echo-request-tag](https://tools.ietf.org/html/draft-ietf-core-echo-request-tag-00); there was some good discussion
that the authors were encouraged to use for a next version.  More
information about use cases that benefit from time-based freshness
would be good.

* [draft-becker-core-coap-sms-gprs](https://tools.ietf.org/html/draft-becker-core-coap-sms-gprs-06) hadn't reached the threshold for WG adoption earlier; there is some renewed interest. Coordination with LWM2M work will be needed.

* [draft-arkko-core-dev-urn](https://datatracker.ietf.org/doc/draft-arkko-core-dev-urn/) had in-room consensus for WG adption, to be confirmed on the mailing list.

* [draft-wang-core-opcua-transmission](https://datatracker.ietf.org/doc/draft-wang-core-opcua-transmission/) was presented as a way to map
OPC/UA on CoAP.  Discussion touched the issue whether OPC should be
doing this or the IETF.  In any case, the authors were encouraged to
continue the work, talk to OPC as well and keep IETF involved.

* [draft-toutain-core-time-scale](https://datatracker.ietf.org/doc/draft-toutain-core-time-scale/) was presented, with some discussion on
whether this should be per-request information or whether there
could be some state.  Hannes has a slide deck on how LWM2M handles
sleeping nodes, which pose similar problems.  Laurent promised to
continue the work.

# Detailed minutes

Thank you to the note takers!

~~~ text/plain
---------------------
╔═╗┌─┐╦═╗╔═╗  ╦ ╦╔═╗
║  │ │╠╦╝║╣   ║║║║ ╦
╚═╝└─┘╩╚═╚═╝  ╚╩╝╚═╝
---------------------

Core@IETF100

Constrained RESTful Environments WG
Chairs (core-chairs@ietf.org):
Jaime Jiménez
Carsten Bormann

Note Takers
Mathias
Marco
Alexander
Jaime
Ari Keränen
Solomon Kembo

MONDAY Nov 13 2017
1330-15:30 Congress H I
------------------------

Intro (10)
Post WGLC TCP (15)

    https://tools.ietf.org/html/draft-ietf-core-coap-tcp-tls-10


Status update, finishing WGLC.
All but one IESG DISCUSS cleared
Impl in libcoap (from Hackathon) - 2,5 implementations; libcoap, augustcellars, coap.me
Open issues collected (e.g., missing hyphen in Option name, talk about release mechanism)
Will be addressed in -11, but mainly done

Tim Carey: Timeframe? Editor's queue this year?
Carsten: Yes. "CES in Las Vegas is the ultimade deadline".

Up for WGLC CoCoA (10)

    https://tools.ietf.org/html/draft-ietf-core-cocoa-02


Carles presenting

Now at -02 (last) - addressing comments received from ICCRG, TCPM, CoRE (from WGLC)
Presenting the updates from -01 to -02

Now adjustable weights for strong and weak estimators
Most work on -02 was editorial
Explaining area of application and the wide spectrum of RTTs
Added references to RFC 7252 and security considerations
Changes in most of the sections that provide more context on the reasons why a work is done + readability.
Revised appendices: focus on pseudo-code, examples, analysis

Hannes: Open from review: main motiviation is to go beyond stop-and-wait?
Carsten: CC does not take away stop-and-wait behaviour.
CG: Document does not modify NSTART (number of parallel outstanding requests). RTO is computed on the basis of RTT samples.
Hannes: ? For what should I go to have multiple outstanding requests, also considering complexity? CoCoA, TCP?
Carsten: Need to look into this to provide text.
Hannes: A text was there, but mayber it got stripped out?
Carsten: The use of TCP depends on the end-device and the application.
Hannes: The overlap between LWIG TCP doc, CoCoA is not clear (e.g. using tuned TCP may approach complexity of CoAP with CoCoA).

Carsten: Do not have numbers on complexity -- only subset of concrete implementations.
Carsten: Advice: if you have space to store a couple of variables + process power for a couple of formulas per peer, you should go with CoCoA.
Carsten: WGLC to be done soon and keeping tcpm in the loop. AD processing after WGLC.
Alexey: Mirja to be the responsible AD, document was expired, will pick it up again.
Carsten: check the points raised by Hannes and go with WGLC.

Resource-directory + dns-sd (40)

    https://tools.ietf.org/html/draft-ietf-core-resource-directory-12



Remotely presented by Christian Amsuess

Now define what the RD should do.
DNS-SD is not in the scope of the considerations presented here.

Links have proper anchor and rel attributes with some default values (rel="hosts", anchor=""). When link is in RD, anchor must equal hosting endpoint [Post-presentation comment from Christian: I hope I didn't say it that way, because that's only true for links that don't originally have a non-empty anchor attribute.]
There are other entities in RD: endpoints and groups. Endpoints provide the entities that are managed, and groups are groups of endpoints.
Added information model that underlies the link management, querying, and link results.
Next steps: add "up" and "down" links
Need to register an all-rds multicast address
Think through group members registered at other RDs
Interface versioning

Want to go for WGLC soon -- need more reviews!

Carsten: Now is the good time to implement RD. LWM2M uses RD but only a subset (for the moment)
Hannes: On the changes - there is a removed all methods that modify links in an exsiting registration - if I do a re-registration, would that work ?
Christian: re-registration is semantically equivallent to re-sending the links. If I want to remove a link what happens?
CA: yes you would have to remove everything
Hannes: need to look into this. In LWM2M we do not want to resend everything, in particular when lifetime expires
CA: on life-time expiry you don't need to resend the links. You can do an empty POST on that Resource.
Carsten: Right now there is no media type to PATCH registrations.
Michael (chat only): We need a select-merge patch. It needs to select a link or links to apply the merge document to. this keeps both link query semantics and merge patch semantics. an empty merge part results in the selected links being removed; i can make this proposal.
Hannes: At the time RD was initially defined, there was no PATCH. The hope was that when we have PATCH we will go back and add this to RD's Registration Interface.
Carsten: The decision was to define media types on a different document, we had a discussion in OCF on how to do that.
Jim: Worried about about how to interact with new URL schemes (refereing to the changes in the url shceme on multiple transports). If something is registered with several schemes, how do you distinguish them?
CA: Registering with multiple transports leads to a single registration. Can resolve link to preferred transport. Related to protocol negotiation draft.
Jim: Means a lot of changes to impl?
CA: Should be minor changes.
Dave: What is the current situation with protocol negotiation? The point is: if this is ready for WGLC, is the other one also? (summary: Protocol negotiation affects links registrations, when doing updates with PATCH, it's not clear how would that work over various transports).
Carsten: Needs discussion, as this is a blocking point. There are roughly equivalent transports that are easy to deal with.
Carsten: there are other cases, some that are more or less equivalent (like UDP, TCP) and others that are not equivallent (such as CoAP over UDP and SMS) - not sure this one is equivalent.
Carsten: How many implementations of RD? 2 OCF/LWM2M (ARM, ERICSSON, Eclipse Leshan, others), 1 old (Cf), 1 current (CA)

DNS-SD: https://tools.ietf.org/html/draft-ietf-core-rd-dns-sd-00

Porting links to DNS-SD requires some support from the origin server.
All data is provided (from RD and /.well-known/core)
Description of the DNS-SD record.
If name not DNS-based, it needs to be derived from other info, e.g., from RD.
Dave: question on the SDO part: the example given has an rt=sdo.temp - with only one dot. Is there a problem if there are multiple dots in the rt attribute?
CA: no problems, dots are part of DNS naming and this fits well in the way DNS-SD mapping works
Carsten: sounds brittle
CA: personally doesn't like very much, but it works, so..

Dave: rt values can contain multiple dots. How to decide at which dot to split?
CA: open issue about that. Exporter needs to be aware of how to handle individual rt types
??: The exp and ins attributes where to be generic, so that the node exporting them does not need to know about dns or other lookup schemes.
Open issues:
    - unregistered/unknown rt
    - Interface versioning

Tim: if we expect a server to know the instance names - then have a way to derive the service name, why not expect the server to know the service name? Exporters might not know about SDO-based resources rt="sdo.temp"
CA: It is a possibility.
Tim: rt seem to get hierarchical (?).
Carsten (as author): Little progress only at meetings however looking at the github now, there has been a significant progress. Now, the goal is to wrap it up.
Timeline - not before end of year, probably by IETF 101.


Comi: yang-cbor, comi, sids (30)

    https://tools.ietf.org/html/draft-ietf-core-yang-cbor-05

    https://tools.ietf.org/html/draft-ietf-core-comi-01


Alex presenting

yang-to-cbor draft has not moved since IETF97, waiting for others
sid stable since IETF98

Existing implementations: 2 proprietary, 2 partial also proprietary
Interop at Hackathon 100 did only work out partially (implementors could not come): 2 implementations tested remotely
Issue with FETCHing three values and YANG-CBOR container
Lessons learned:
    - ietf-system not a good test set --> need basic YANG modules (NETMOD does not have those)
    - Debugging hard due to complexity --> possibility to disable delta encodings for testing
Carsten: Can do, but don't tell, because it will appear in production systems. Better to fix tools.
Alex: Don'T see long-term problem
Carsten: Long-term problem is that this would appear in production systems, and it will affect interopereability. You need to have tools that allow to see SIDs.
Peter: Increasing complexity to reduce complexity is not a good idea.
    - No minimal set that covers all CoMI functionality --> define minimal and extended set?

Started open source impl at Hackathon. Chosen YANG libs turned out bad for CBOR encoding. Now using YDK.
Again at Hackathon 101, London

Next steps:
    - Bi-weekl meetings
    - Interop at Hackathon 101
    - CBOR Option 39 not to be added.  
    - Improve CoMI docuemnt

Carsten: current document shows how to use YANG-CBOR with COMI. It adds a lot of complexity and it is not solving a sepcific problem. It might make sense to add GET (?) as a new method. We wouldn't have two sets.
Alex: In GET you have a uri. getting one item with one SID there is no problem, bot on a list.
Carsten: For "complicated" cases (list) use FETCH. GET is only for simple cases.
Alex: it is complicated in some cases.
Carsten: Let's go through examples to evaluate use case for GET. No need to support full REST just because it's there.

    https://tools.ietf.org/html/draft-ietf-core-sid-02


SID: Number, file format, policies
File lifecycle still open. Should not block whole document.
Set up SID registry during Hackathon (as not yet at IANA) at http://sidreg.acklio.com:5000/ (should be up publicly soon)

Carsten: Normal thing to do to provide initial population.
Michael (via Jaime): Something select proposal (?)

WGLC on SID draft?

Carsten: Last IETF we said it's ready, but want to see interop. Continue with virtual interop for a couple more days and send report to mailing list.
Carsten: Send yang-cbor first to WGLC.
Alex: We use YANG schema to define file format.
Michael: Can we use CoMI to allocate SID ranges?
Alex: Sounds cool, need to look into it.


YANG Push (over XMPP) related

    https://tools.ietf.org/html/draft-birkholz-yang-push-coap-problemstatement-00


Henk: YANG PUSH design team.
Telemetry - the datastore contains a state. This state can change over time; In the past, you would be using SNMP. Now is the time to bring this to YANG.
Sometimes we may want to have a subset of a module (e.g. instead of having 1000 leaves, have only 2-3).
In the end - have data in motion - which is self-described.
This will enable a lot more scalability on devices.

Call Home: The datastore may want to find a suitable client.
CoMI is not yet visible in the NETMOD world - we are doing this now.

Hannes: XPath is _the_ XPath?
Henk: Subtree concept based on SID.
Eric: Intentionally did not limit XPath becasue hard to choose what is useful.
Hannes: Interoperability issue due to power. this would probably need to be worked out. XPath is like a scripting language.
Eric: If not supported a pointer to what is supported is returned.
Henk: Targeting less volume on wire and constrained devics. This is not only for IoT - you can have powerful routers that have no problems to run full XPath.
Eric: YANG Push allows for filters. These filters can be applied to "transport" protocol (e.g., NETCONF). You can then limit the type of subscriptions you will be using depending on the transport.
Tim: Normal nodes have exising mechanisms. In IoT world we have Observe. PUSH seems rather heavy for something constrained. What does this mean for a constrained device that only needs Observe.
Henk: this also touches the topic of call-home. At some point you want to send .. data. This approach allows slimed-down semantically interoperable way to do it.
I.e. you do not have to deploy the heavy bulk that constitutes all the layers of push, event streams, subscribed notifications & notification messages & bundles. You can have very concise (means NOT HEAVY) purpose-specific code
that emits (un-)solicited notification messages with only a few lines of code - retaining the full semantics of YANG notification messages that are the data in motion.
Eric: DDS works on IoT devices - so YANG PUSH will also work.
Carsten: Underlying question: "is YANG good for you?" Not yes for all. "Can we make it scalable?" Can we make this work for devices (not necessarily a sensor or light switch, but slightly stronger). I am optimistic.
Henk: We have all the building blocks there and we might be able to build something useful from them.
Hannes: What about Tim's question on Observe vs PUSH Framework? There are already filters on Observe.
Henk: This proposal uses CoAP Observe. The problem statement already contains several proposals. There are examples out there.
Matthias: Asking to understand how the whole thing fits in the YANG PUSH / Telemetry / XMPP observe schema presented in the beginning.
Henk: Ignore the XMPP part of the Hackathon slide - that is unrelated to the propblem statement and only a pointer to the increasing visibility and appilication of YANG Push as a reference.
Henk: there are quite a lot of modules out there (2000). It is a waste not to use it. The goal is to embed the efficiency provided by CoMI to the global YANG ecosystem.


Payment over CoAP

Presented by Adrian Hopa-Bailie


[1] https://datatracker.ietf.org/doc/draft-hope-bailie-http-payments/
[2] https://www.w3.org/TR/payment-request/
[3] https://www.w3.org/TR/payment-method-id/

W3C work: Web Payments WG
Defined standard for requesting a payment with a browser API.
Headers in 402 Payment Required and payd Request/Response messages.
This will continue in the W3C for a while (re-charter in 2018), but might also be interesting for CoAP.

Carsten: Also related to ACE work.
Adrian: Data model can work with static responses, so can fit constrained environments.
It can produce the payment request message (probably in a token) and forward it to a different system.

Hannes: It sounds related to ACE, but does not use it.
Adrian: It is possible. Open to use ACE if people come and help doing it ?
Ekr: What is the assumption? What set of actions are required between client and server? the case is different if the client is a browser or a constrained device.
Adrian: Depends on the payment method. Could be tokens or whatever. It is decoupled.

Pubsub – status, vs. yang-push (15)

    https://tools.ietf.org/html/draft-ietf-core-coap-pubsub-02


Postponed to Tuesday


MONDAY Tue 14th Nov
13:30-15:30 Bras Basah
------------------------

Note Takers:
Solomon Kembo

    intro (5)


    Finishing senml (15)

    https://tools.ietf.org/html/draft-ietf-core-senml-11


13:30
Ari presented updates since -10.
Lots of editorial changes. Changed registry policy fo expert only. Clarified use of version field with resolved records and why both Celcius and Kelvin are OK as units.
Things to be done: Move security considerations from media type registrations to the security considerations.
And publish as RFC (AD gave thumbs up).


    Pending (for EST over CoAP) (10)

    https://tools.ietf.org/html/draft-vanderstok-ace-coap-est-02

    https://tools.ietf.org/html/draft-hartke-core-pending-01


13:35: Pending for EST (PV)
Goes with BRSKI
Plans to do same with CoAP-EST in ACE
Request to wait for a result

In BRSKI you may want to have a second voucher, so you may need to do operations that take time. In the server, you can have several servers that come and go (waiting for their respective answers).


Carsten: like "Created" but don't want to be looked up immediately but later. Wondering if retry-after together with "Created" would solve this?
Peter:There are several notes to the server. The client can ask the server what was the (response)


Carsten: when doing enrollment get location. Creation of resource was successful but can't access yet? Response code 3.03(?) try after. Would solve problem without new response code?
Peter: happy to follow that line.
Dave: Normally a resource is created after a POST. This is a GET. It should not create a resource.

Peter: client usually expects voucher back. Get back location where can ask again.
Dave: get back and answer. The response payload should have a new location, or the data itself (the voucher or URI where to go). Solve the problem in the body of the application (applicaiton level); confuses to have both

Peter: follows HTTP rules
Carsten: This is about the Get resquest?. I think we have a few ideas to solve and we will need to discuss this further on the list.



    Object security (30)

    https://tools.ietf.org/html/draft-ietf-core-object-security-06


Franceca presenting OSCORE.
OSCORE - new name (used to be OSCOAP)

FP: I will provide the status of the draft, a high-level discussion
Hannes: if want to be totally correct, not object security. It's CoAP message signing.
Dave: OS in same sense as COSE and JOSE
Alexey (AD): Rat-hole!
Hannes: Is not Object security is Object signing.
Göran: There are no signatures.

Francesca: We now protect CoAP which is now encrypted. Simplified the oserve process based on Christian's update. Partial ID does not to be sent in but major. We had Christian and JIm at the Hackathon. Have updated test spec which will be available soon. One issue outstanding is about observation renewal. Plan on fixing minor isses by end of this week.

Dave: Summary of the OCF discussion. We had a joint meeting between t2trg and ocf. Would OSCORE suffice for OCF, outcome is positive. Editorial suggestion to be added. As far as anyone knows, draft meets OCF needs. Table with header fields with what is encrypted and what isn't would be nice for readability.
Please complete the worka and publish. IETF to consider how to protect the headers confidentiality-wise. Like ID of final destination. What's the IETF recommended way to "tunnel OCF/OSCORE" to achieve this. Document to describe how to do this would be nice.
Carsten: Where are we with regards to security reviews?
Francesca: last couple of meetings asked for more CoAP expert reviews. Was maybe missing. Can be done in WGLC.
Carsten: Who has actually reviewed this document from July or later  - 3 hands, Christian in remote.
Alexey: do you need crypto review?
Francesca: OSCORE uses COSE. So that part would be covered there.
Jim: Nothing really major (as covered in COSE).

Carsten: The thing that considered was that you fiddled with the nonce
Francesca: I didnt have any problem with that.
Carsten: During IETF and WGLC we will look for people but it'd be good to have more people have a look.
Jim: Fiddling with the nonce is not a security problem, it guarantees that, as we approach a group document, we have complete separation of the nonce space.
Göran: the change in nonce construction is an improvement and its now more clear,
Francesca: will submit new version and then ready for WGLC. New version end of this week time frame.

13:56

    Multicast OSCOAP (2)

    https://tools.ietf.org/html/draft-tiloca-core-multicast-oscoap-02

Carsten: In Prague had in-room consensus for adopting this but since then got security related discussion.
Marco: Details now available in Appendices and improved the readability in Version 04
Carsten: How many people would be willing to do a review of this? (5 hands)
Hannes: IPR notice on ACE document. Wondering about IPR on this.
Marco: not aware of any.
Göran: Not aware of any IPR either.
Hannes: Would be worthwhile to check.
Göran: Setting is that in this room working on communication part. In ACE key distribution.
Hannes: in ACE my doc did both.
Carsten: Does the work have sufficient clarity on this document?
Alexey: Hannes, missed ACE, can tell more about the IPR? Who is patent holder?
Göran: Ericsson has declared IPR on a draft that does key distribution for ACE.
Hannes: is this document solution for symmetric or asymmetric?
Göran: This draft provides a solution for multicast security which is based on adding a signature for COSE objects. In principle you could set it to zero and use it also for symetric only.
Hannes: So in ensence this would be the solution to the problem I have in ACE.
Carsten: What I think is we have a consensus in the room and can verify that on the list.

Dave: current status of the multicast draft?
Carsten: WG document to be validated on the list. Existing inroom consensus.

14:04 Pub/sub
Pubsub – status (15)

    https://tools.ietf.org/html/draft-ietf-core-coap-pubsub-02


Michael: How do we do the sharing of the slides? The status is basically is as it was when we presented in Prague. When are not adding anything to the protocol. We do not have the next update at this time. We will do version 3 addressing comments from Jim from the last meeting and we basically incorporating these changes. We still targeting what we have revised and we looking at still trying to come up with something by London IETF and I havent spoken with the other authors.

Carsten: implementation status?
Michael: two or three, but need to collect those again. One implementation quite some time ago. GE health care was asking questions around implementation. Some issues on how to find a server etc, but don't see fundamental changes needed for pub/sub. What need to do with implementations?

Carsten: just good idea to know what are out there. So, want to do -03, then good idea to round up those implementations and maybe have even an interop. Then could go to LC. That's the sequence of event here.

Michael: That sounds good

Early registration of 4.29 (too many requests)?
Carsten: should agree that this is stable. Will continue to look like this. Modeled after well-established HTTP code. Maybe CoRE specific considerations to address before registration?

Dave: don't know if registration request came from OCF or specific company. But set of users want to use this code outside of RD (meaning Pubsub). What's the right way to specify? Split to different doc that coul dgo

Michael: Intention is to have it registered as a parallel thing to HTTP.
Dave: Reviewing the rest of RD would take time. Response code for 4.29 requires IESG approval.
Alexey: Have it on a document, it's better. Split document preferred.
Michael: Agrees.
Ari: Agrees too. And this is actually in the pub/sub doc not in RD
Dave R: 308 message seems to be also missing. Suggestion to have 308 and 429 in other document.
Carsten: 429 is in no way controversial.
Ari: Volunteers for that.
Carsten: seems non-controversial and we could combine with other non-controversial response codes
Ari: sure, but if those others end up being non-non-controversial, we should prepare to take those out so that they don't delay the pub/sub broker. Often end up being more complicated than you think.
Alexey (off-mic): agree
Peter: Good idea to combine drafts.


Echo/request tag (15)

    https://tools.ietf.org/html/draft-ietf-core-echo-request-tag-00

    https://tools.ietf.org/html/draft-liu-core-coap-delay-attacks-01


Christian presenting echo-request tag draft.

Carsten: more details on how to restructure echo part?
John M: clear requirements on -- making the echo part so that client is not looking at that.
Julian: who is authorised to set the threshold for the echo?
Christian: the application is the one deciding. Could be split in time; "can't accept older than 2 seconds". Underlying library to act on that.
Carsten: The document should be specific as to how the application is supposed to interact with that mechanism.
Göran: WGLC after restructuring and editorial changes. (volunteers fo review ari, francesca, jim, julien, Carsten..)

Mitigating Attacks

    https://tools.ietf.org/html/draft-liu-core-coap-delay-attacks-01

With draft-mattson, with too small threshold normal requests may be discarded. Two round trips increase delay. Propose another mechanism. Client sets time window for message, contains time duration. If message is received before the time window it should be responded until the time window is met, if therequest is received during the time window it may be acked immediately. Otherwise discarded. Cases like AGV, multiple messages passed but can work on one request. Has to process requests 1 by 1 in sequence.

Göran: Thanks for this contribution. The problem statement you are looking at is different from the echo draft. There is not so much coverage in the use cases, you could expand to see which different cases you have. Also, it'd be important to know how much should be added in core and how much is part of the application.

Dave T: Do you require time sychronisation?
Jintao Zhu (Julian): That is a comment that Göran has already addressed.
Christian: Do the sequence relate to single resource or multiple resources.
Julian: single resource
Christian: did you evalute use of if-match for this?
Julian: will look at this after the sesssion
Carsten: good feedback, it's not clear which the use cases are. The application needs to control the freshnes and with the echo option we find a place for a common behaviour in multiple applications that can be factored out to a common option. Would like to see can we arrive in common behavior that multiple applications can use? Currently a shopping list rather than consise list.

Göran: what are next steps for echo request tag? After restructing should have few reviews and go for WGLC.


    Sms (5)

    https://tools.ietf.org/html/draft-becker-core-coap-sms-gprs-06

Carsten: We have drafts that have been around but that we need to move such as SMS, there is an undespecified banch of the spec.

Tim: LwM2M in the spec has gone ahead and done that piece. CoAP push mechanism for SMS. LwM2M already progressed. Just if want to do something else we should incorporate those changes. They utilize for SMS WAP push 3GPP mechanism. Progressed and solved the problem.

Jaime: a couple of weeks ago in OMA meeting was interesting demo from AVSystems. They committed to contribute to SMS IETF draft. Some of the features that LwM2M could be adopted to this draf or vice versa.
Tim: no matter what we do, we have to align, but LwM2M spec wise they don't care. They have in the spec what they are doing for SMS.
Jaime: maybe want to align in this space. Can also discuss in detail in the OMA group.
                 Carsten: SMS is being used in LWM2M.

    Dynlink + interfaces (10)

    https://tools.ietf.org/html/draft-ietf-core-dynlink-04

    https://tools.ietf.org/html/draft-ietf-core-interfaces-10


Bill: Its been in limbo for a while. In general both drafts are in good shape. There are editorial issues that need to be fixed. Examples need to be made much clearer. There are 4 issues outstanding: 1 on error handling, 2 on absorbing work done on draft-groves-core-obsattr and draft-groves-core-bas, 1 on adding a new link relation.

Carsten: who has read a recent version of this document? (4 hands).
Carsten: Volunteers to review (hannes, alex, tim, peter, ari, christian a)
Bill: Good idea to keep interfaces and dynlink separate.

    Dev-urn (10)


    https://tools.ietf.org/html/draft-arkko-core-dev-urn-05


Jari Presenting dev-urn.

Changed the syntax for component part delimeter from " ; " to " _ " to accommodate for SenML. Got feedback that "/" could also be used.
New organizational code part. Considered also FQDNs but org code seemed better. Soliciting feedback for delimeter change and device IDs. Got feedback from Nokia guys (Tim) about BBF, OneM2M and L2M2M use of IDs. Could be useful to add?

Dave: delimeter part; said that humidity part of device. Is this device ID, resource ID, or what? Part of device doesn't make sense.
Jari: part of device can be device.
Dave: maybe need different term
Jari: origanally went for device IDs, but then people wanted to point to parts of device
Dave: part of device or resource? Understand use case for those two, but don't get for the component part.
Jari: one physical box with two separate circuits
Tim: saw some of this in OneM2M. Not sure if same case. Blood pressure monitor, each need to be identified. Question: BBD USP protocol already in their own name space. Org for name space; used PEN, very clear what is the format; private EN or what. They used PEN and OUID.
Jaime (hat off): at the moment URIs for IMEIs etc. But not dev URNs other than for TR69. AFAIK.
Jari: using subtypes of what?
Jaime: not sure, UUIDs preferred.
Jari: another spec. Are they building something on this?
Tim: use number of namespaces, from dev they use only "dev.ops".
Jari: OK, something from dev space. That's fine. Need to ack in some fashion and allocate those.
Dave: got the use case for device ID, but ambiguous; what different orgs call device varies. For some orgs the physical thing. For some orgs a specific role it runs. In OCF platform the physical thing with multiple devices. Device as term ambiguous. But probably talking as device as OCF device as part of platform. For normal developer not device ID. Need to be clear what is the use case. Or something that varies per use case and ecosystem. OCF have their own name space. LwM2M specific urn scheme or general -- either one OK but need to know which one. Just want answer before draft adoption.
Jari: I am not sure I can answer the LwM2M question.
Tim: In LwM2M it is an endpoint identifier. Sometimes OUID.
Jari: The goal of the work is to identify hardware addresses and different organisations use different terms for the same thing. Only discussion now is the terminology and question of delimeters came from the SenML work actually.
Dave: HW identifier doe snot imply one HW identifier per device, you cna have multiple addresses or identifiers.
Ari: One use of urn componet part have seen in the senml context.
Dave: Clarifying on deployments. Of the different ariation
Jaime: I believe that in LWM2M the most common is UUID. URNs are used when using IMEI, ESN or others, most commonly for TR69 devices.
Hannes: depends on what kind of devices you have; for those in cellular space say as Tim said. We use UUIDs for WiFi devices and such.
Jari: other organizations already allocating things in the dev scheme. We should get this done soon.
Carsten: have already consensus to work on this; need to pull different parts together so that we know what's out there

    Flextime (20)

    https://tools.ietf.org/html/draft-wang-core-opcua-transmission-02


Junrui Wu: Our motivation is clear that OPC UA - Data exchange standard for interoperability in industrial settings.
OPC UA - data exchange standard abd platform-independent industrial communication.
Foundation - transport mechanisms and data modeling.
HTTP-CoAP Proxy for OPC UA.

Dave: familiar with CoAP and OPC UA. Find this interesting. Can give feedback offline. But don't know off-hand what is the use case. Given there is already OPC over UDP and TCP, what's the use case for CoAP? Tentatively in favour if reason to do this. Willing to review etc one there is use case. Techical point on slide 130; secure layer on top of TLS. If there is lower layer security OPC security not used in OPC architecture. But can follow up on these later.

Tim: why isn't this being done in OPC?

Dave: good question; if OPC want to do this with CoAP? Regardless which org you are in, I'm in both, can review in either. But good question where this belongs. Good argument for OPC.

Tim: nuances to protocol where to have the experts involved.
Dave: do in OPC and have IETF review.
Dave R: BACnet plans to do BACnet over CoAP. Will come to IETF to get reviewed.
Dave: did that with OCF. Thank you for coming here. Please go also for OPC if not there yet

Jianqiang Hou: Also interested in this and use cases

    https://tools.ietf.org/html/draft-toutain-core-time-scale-00


Laurent Toutain
Slow reactive devices - slotted devices, or devices that are working on duty cycle.
Example: devices that need to send a message in order to allow a response to be sent.

Have a way to indicate to the server - how long to keep the message_id (or other related CoAP parameter) valid in the server.

Mohit: it doesn't increase the number of messages, but this would still increase the memory usage because you need to keep it. Have some information about the device you are talking with.
Laurent: need to have things like message ID anyway. Just few bytes more.

Hannes: option indicates when device is expected to send messages?
Laurent: no, how long have to keep request in memory for reply
Hannes: how relates to Q mode and sleeping proxy? Not sure how it does. Is the granularity of single CoAP message useful? In LwM2M indicate with Q mode that you are in a network that behaves like this. Not sending with each CoAP message but only once. Have you looked at that? Can send a slide deck.

Christian: (time scale option slide) careful to consider proxies here. What this is proposing is message level, terminated at proxies. Agree with Hannes that should be per device/link and not per request.
Laurent: more complex to memorize per device/link than repeating for each request

Laurent: next steps; working on the doc

Carsten: and we can finish one minute early!

~~~
