CoRE WG - Summary IETF97

Slides: https://www.ietf.org/proceedings/97/slides/slides-97-core-consolidated-slides-06.pdf

Raw Minutes: http://etherpad.tools.ietf.org:9000/p/notes-ietf-97-core

Summary below, followed by detailed minutes.

# Wednesday 2016-11-16

## WG status

* draft-ietf-core-block ➔ RFC 7959 [✔]

* draft-ietf-core-http-mapping still processing some DISCUSSes; will
move to Proposed Standard status to clear one of them.

* draft-ietf-core-etch submitted to IESG. Waiting for Alissa's DISCUSS
[now cleared]. Next is to get it to implementors.

## WG drafts and related work

draft-ietf-core-object-security current draft stable; reviews, 2
implementations available. 15 people read some version, 5 have read
latest. Need more feedback from implementors before WGLC. Target is to
have an interop mid-January 2017; we'll label one of the net drafts as
"implementation draft".

draft-ietf-core-coap-tcp-tls addresses issues since IETF 96, currently
on WGLC. Discussion on whether to make TLS a must or to open option
for alternative security mechanisms (e.g. OSCoAP). Interesting
insights on vendors' usage of certificates. Authors to set up a call
addressing Security and remaining issues about 2 weeks after
IETF. Target is WGLC about 4 weeks after IETF.

draft-silverajan-core-coap-protocol-negotiation now using RD instead
of .well-known/core. 3 people read the document and 7 will read it.

draft-ietf-core-resource-directory moving forward. Authors to address
remaining issues. OCF to organize a call. Text on DNS-SD requires
feedback, might be published as a different draft.

draft-ietf-core-dynlink no time ➔ Friday

draft-ietf-core-interfaces no time ➔ Friday


# Thursday 2016-11-17

We used an informal "hallway" meeting to have time for some informal
discussions about upcoming work and/or potential revisiting of old work.

draft-ietf-core-links-json Presentation about status and
updates. Proceeding further as planned.

draft-vanderstok-core-coap-est and draft-pritikin-coap-bootstrap: how
to use EST over CoAP.  To be done in ACE WG.  Issue for CoRE: Do we need a new 2.06?

draft-tiloca-core-multicast-oscoap Solves RFC7390 issue with securing
multicast but independent of use case.

draft-cao-core-delegated-observe enables delivery of observe responses
to different addresses than where the request came from. Feedback: of
interest to others. Security (spoofing) is an issue. Documentation of
the problem can be done as draft-ietf-lwig-coap addition or T2TRG
topic.

draft-groves-coap-webrtcdc: like CoAP-TCP/Websockets, but over WebRTC
data channel.  Should go ahead after CoAP-TCP is completed.

draft-ietf-core-coap-tcp-tls:

* Do we want to make additional mandates on how a peer has to pong on
a ping?  E.g., timeliness.  Discuss on mailing list now.
* CSM was made mandatory in IETF96, SDOs should be aware of that (no
need for a compatibility mode, though).  Exact state machine still undefined.
* Fixing the bug in scheme naming. Still a bikeshed.  Still a bug.

# Friday 2016-11-18


## WG status, continued

* draft-tcs-coap-no-response-option ➔ RFC7967 [✔] (independent
submission), need to show independent submissions on coap.technology
page, too.

draft-nottingham-rfc5988bis-01 revision is coming. CoRE should be
aware of new changes, now is the chance to affect them.

## Interfaces and spun out dynlink

draft-groves-core-dynlink about 3 people have read the draft, the
group should read it and provide feedback.

draft‐ietf‐core‐interfaces it's decided to remove the "function set"
concept since people do not consistently use it. There should be
allignment with SDOs in the space, like OCF.

## SenML

draft‐groves‐core‐senml‐bto about 3 people have read the draft. One
problem is that there are only few people who know how EXI works, in
W3C.  Discussion on BTO support and how to announce it to clients.
Extensions to be left out of the main SenML draft.

draft-ietf-core-senml new discussion on fragmenting, registrations for
copy-pasting SenML (easy to do, so probably should) and metadata
labelling (strong support).

## COMI (Management)

draft-ietf-core-yang-cbor to be tagged as an implementation draft,
next steps are to submit final version by January, interop in February
and in IETF98.

draft-ietf-core-sid the point of the draft is to use global
identifiers assigned to YANG items for different
functionalities. There was interest by DTN folks to use this work
too. There was discussion on flat vs hierarchical namespaces. Open
issues are the reservation of SIDs in the namespace. Target is
IETF99. WGLC March 2017.

draft-vanderstok-core-comi from v09, adds usage of SID, iPATCH/FETCH
support, YANG to CBOR, Content format (WIP) and new query
parameters. About 10 people have read and wanted to adopt this
document. To be taken to the mailing list for discussion.

## New work

draft-thaler-core-redirect intention is to redirect from non-secure
server to secure one. Main problem is that it misleads the
client. Better way would be to spend more time on hypermedia formats
to get this right. Problem is general, several contributors
volunteered to work on this.

draft-groves-core-rfc6690up-latest issues with RFC6690 IANA
registration procedures for (rt) and (if). On the one hand it is a bad
idea create different namespaces as it does not help
interoperability. On the other you don't want to squash innovation,
SDOs like OCF need to register their resource types. For now a good
way forward is to help with more expert review recommendations and
with a high threshold prefix registration.

# CoRE WG meeting minutes, IETF97

Agenda: https://datatracker.ietf.org/meeting/97/agenda/core/

Meetecho: http://www.meetecho.com/ietf97/core/

Taking notes (thank you!)
============

- Thomas Watteyne
- Alexander Pelov
- Jaime Jimenez
- Christian Amsüss
- Francesca Palombini
- Ari Keränen

WEDNESDAY
=========
* [13.32] meeting starts
* [13.32] intro (chair)
    * jabber, blue sheets, etc
    * Note Well
    * Agenda presentation and bashing
        * Thursday meeting is not an official
        * [Ryan] can we move object sec before
        * [Christian Groves] last item on dynlink has 0 minutes.
        * [Carsten] if time left, otherwise push
    * milestones/doc status
        * a little bit late on some items (see slides)
        * core-block ➔ RFC7959
            * last interop was in London, nice it's finished now
        * http-mapping: at IESG
            * [Akbar] reviewers was proposing proposed-standard. Does that make sense?
            * [Carsten] we did have that discussion, between the lines, we agreed we would keep informational but a lot of people also thought it could be PS. Does anyone have a problem to moving to PS?
                * nobody in the room
                * [Carsten] So authors can go ahead with proposed PS status
            * [Akbar] on security, we will meet again with sec AD (Stephen) to discuss issue about mandatory client authentication when proxy used.
            * [Carsten] Can pick up on topic later as it will be related with reliable transport issues.
            * how HTTP mapping happens with FETCH/PATCH is used? this needs to be cosidered.
        * core-etch
            * one discuss pending, draft 48h old
            * should be resolved very soon
            * we need to get feedback from implementers
            
* [13.43] draft-ietf-core-object-security-00 (Francesca Palombini)
    * intro to OSCOAP
    * background/related work: slide with link on figure on how different draft depend for one another
       * OSCOAP dependent on COSE and CoAP
       * COSE dependent on JOSE and CBOR
       * several draft that make use of OSCOAP (profile (ACE), 6tisch, DTLS profile, Mutlicast COAP
    * draft status is stable.
    * 2 open sources implementations
    * What's new: content definition, context derivation, Cid➔64bits pseudo random, optional senderID.
    * contexts
        * there are two contexts: sender and receiver
        * lists the input params for context establishment, with example
        * why sender/receiver ID: for the case where roles are inverted between sender/receiver
    * multicast support ➔ see dedicated presentation on Thursday information CoRE session
    * minor modification after reviews
        * see slide for details
        * these issues are tracked by GitHub issue tracker
        * thanks Malisa, Jim, Martin and Joakim
    * implementation
        * related as open-source at IETF96
        * new implementation in C (Contiki+Erbium), removed external dependencies, dynamic memory usage removed.
        * implementation still WIP, but open and tracking changes in the draft
    * summary
        * draft stable, sec reviews, 2 implementations
        * welcome further reviews and implementations
    * [Jim Schaad] last IETF use case was presented with integrity only (not encryption)
    * [Francesca] don't remember use case, let's see back up slides. 
    * [Jim] a meter sends results to corporate HQ, house wants to be able to read the contents
    * [Francesca] Not yet addressed, please forward offline.
    * [Carsten] How are sender and receiver IDs produced?
    * [Francesca] they are input parameters present there already. There is other draft (e.g. EDHOC presented in ACE) that sets them in place
    * [Carsten] what are the uniqueness requirements?
    * [Francesa]Context Identifier is globally unique, sender-recipient identifiers are locally unique in the group using the same security context
    * [Carsten] Who would set that up?
    * [Francesca] A group manager could set it up beforehand.
    * [Carsten] several rounds of discussion. We need to understand the relationship of the identifiers.    
    * [Carsten] Who has read the draft? 5 people have read the latest version, 15 people have read some version. We need more feedback. Definitely not ready for WGLC. Instead we should recommend to implementors to implement so that we get further feedback before continuing. 
    *  [Francesca] All the github issues are closed.
    * [Thomas] they have started an implementation. 
    * [Thomas] what was the question for the implementation draft?
    * [Carsten]: We would need to get a call out on the mailing list, flagging this as an implementaiton call (1 week after IETF) and then perhaps run an interop (mid-January?)
    * [Christian Amsuss, through Jabber] +1 on mid-January date will try for an online interop (coordinated through e.g. Google hangout).
    * [Carsten]: Details on mailing list. Need to chose specific mode and interop details.
* [14.01] draft-ietf-core-coap-tcp-tls–05 (Brian Raymor)
    * Two versions since the Berlin meeting.
    * Version tls-04 addresses issues since IETF 96.
    * Currently WGLC
    * Will be tracking last call comments through github creating issues for comments.
    * [Carsten] shows issues on the screen (https://github.com/core-wg/coap-tcp-tls/issues)
    * Target to have WGLC 2 in 4 weeks (3 weeks after IETF).
    * Already has addressed several issues in an iterative pull request just hasn't "pushed the trigger". Many of issues left are editorial.
    * Should we make TLS a must? There was a feeling that application layer security OSCOAP wasn't well considered in making TLS a must.
    * We should maybe have the discussion today.
    * [Hannes] Depends what we're trying to accomplish. We have DTLS that provides some services. Do we want to reuse them, now that we have OSCOAP? A potential problem is when there is too much choice left to the implementer (Goran seems to want to avoid MUSTs); If we have too many choices 
    * [Francesca] We are not trying to NOT mandate security, we agree it must be mandated but there are more options now. It'd be important to at least give the option for other kinds of security.
    * [Goran Selander]: Remotely . Reiterating discussion on mailing list. The question is not wether we mandate security or not. The issue is that some devices might not support multiple protocols. If we mandate TLS+OSCoAP or DTLS+OSCoAP might be too much for some devices to implement. The other issue is which is the right security protocol for which case. There was also discussion on the meaning of ON by default. Which draft will specify the security protocols to be used. We still don't know which scenarios will use which type of security. That needs further work.
    * [Hannes]: Discussion of Mandatory Security. From the interoperability point of view, something needs to be specified. DTLS is intentionally similar to TLS. CoAP+DTLS, adding CoAP+TLS is not such a huge effort. That's what drove the work on this draft.   Agreed that OSCoAP is mature but is not at the same status. Doing something like TLS at App layer, then we do not want it mandatory at transport layer.
    * [Goran] agreed, but not the point was trying to address. There is a point of using application sec on both UDP and TCP.
    * [Hannes] TLS provides more than application security. danger is that we rebuild TLS at the app layer. Maybe we should rethink app-layer security and run TLS 1.3 at application layer. It has 0-rtt exchange like other application security mechanisms.
    * [Goran] comment on Hannes' statement. If we do TLS over app layer, we don't want to mandate TLS. Agreed that OSCoAP is mature but is not at the same status. Doing something like TLS at App layer, then we do not want it mandatory at transport layer.
    * [Hannes] when attempted a app-layer sec in OAuth, since sec terminates at different end points, you may want to have both transport and application layer security. They may determined at different points on a processor.
    * [Carsten] TLS is highly intricated with web sec; relatively inflexible. app layer is a bit more multi-faceted given additional capabilities. Wrote TLS over CoAP, you can extract the handshake protocol and run OSCoAP with the keys you obtain. Not so happy to have a mandatory implementation for transport security. Good decision to keep RFC7252 open and keep a mode which is non security at transport layer so we have flexibility. Summary: following guidance of RFC7252 would be good, doing something different would require a lot more rationale.
    * [Juan Perez, Jabber] one of reasons to use TLS is able to use of the open internet rather than the edge. JP does see that constrained devices may not be able to have multiple security implementations.
    * [Jim]: running TLS over app would solve problem with proxying. Using TLS for transport the endpoint wouldn't see security leakage at the proxy. No objection to mandating it as long as it does not interfere with each other. 
    * [Ari]: CoAP did a lot of work to keep a small implementation footprint. Implementing TLS is a large part of the footprint. Implementing only OSCOAP for class 1 devices may be advantageous. 
    * [Hannes]: Comparing a signed message at the application layer that provides the same level of the security. TLS provides more (e.g. crypto agility) if you ask for the same level of security at the app layer it should offer those features. 
    * [Carsten]: Should we just concentrate on the TCP draft? 
    * [Ari] Trying to implement both OSCOAP and TLS on a class 1 device may run out of memory.
    * [Hannes] Looking at the TLS over application layer makes sense
    * [Goran] +1 to Ari on implementation, comment on OSCOAP being sold as a lightweight protocol. Using PSK means no need for a handshake. Managed to do object security on Arduino and not DTLS. If you want to do e2e security using OSCOAP on constrained devices means you may not be able to support TLS.
    * [Carsten]: No one said we should n't do e2e security.  2 layers of security may be want you want but there are cases where you have limited resources and you can do only one. 
    * [Hannes] Do you want to mandate support of psk (rpk)?
    * [Carsten] 
    * [Hannes] In our experience Certificates is what seems to be more popular. People are familiar with it and they do not seem to care much about the code size.
    * [Thomas] In our experience they use PSK. Thousands and thousands of deployments. People understand it.. 
    * [Hannes] Different experience as they distribute the keys automatically.
    * [Thomas] both view are OK but not every one is going for certificates. Some networks can transport lots of packets other cannot. Often issue is not size of packets but how many.
    * [Hannes] is ps secret used or something else?
    * [Thomas] In WirelessHART, neither TLS nor DTLS is used, but a custom application level security similar to OSCOAP.
    * [Hannes] Did we learn something from the work?
    * [Carsten] Another thing happening is ACE.
    * [Juan Perez (Jabber)] From what I have seen from several cloud providers, their min bar is to use TLS. So these cloud providers would end up requiring TLS, even if the standard does not require it. That may push the non TLS use case closer to the edge.I've seen both Cert and PSK. I agree, much use of certs when I expected more PSK (for smaller devices)
    * [Carsten] RPK priority of three years ago seem to be different today. 
    * [Dave]: We had symetric keys, we even used CA and it went in that direction (use of certificates). Companies wanted to use the certificate systems they already had.
    * [Carsten/Hannes]: Side discussion (couldn't hear) 
    * [Jaime]: don't see full conclusion on the topic. Don't know how to continue/conclude.
    * [Carsten]: pick up on friday? We want to get this by the IESG
    * [Juan Perez]: Cloud providers now have TLS often as a minimum bar. There is a threat of segmentation.
    * [Carsten] talk about TLS over CoAP tomorrow
    * [Alexander Pelov] lacking part over understanding about what we assume about TLS (TCP, all options, etc?), we should not MUST the use of TCP
    * [Hannes] we have CoAP over TCP doc, for devices that run TCP to the device. Now doc needs to be finalized, what do we write in sec. Various options, how far do we want to go with recs on the sec side: you have to implement TLS? use TLS (and what type of credential)? up to you?
    * [Pelov] we will still be needing OSCOAP for UDP
    * [Jaime] let's talk later.
    * [Carsten] useful slides about guidance, encourages people to look at slides offline before Thu/Fri CoRE meetings
* [14.45] draft-silverajan-core-coap-protocol-negotiation (remote from Bill Silverajan)
    * recap: we used .well-known/core, at Berlin discussed not a very good idea. Now followed path to use RD.
    * now, using RD, 
    * removed 'tt" link attributes
    * now registered as a list of URIs at the RD with the at= parameter; all resources can be accessed via those alternate transports
    * transport types available can be queried from the RD using the tt= parameter (?tt=tcp&ep=node1)
    * benefits: consistent API, optional for endpoints, works with commissioning tools, DNS-SD integration possible
    * group functions yet to be explored
    * disadvantage: RD required (will go away again in next draft with direct discovery), lifetime of transports is still equal for all, no management for enabling interfaces
    * [Hannes] Two SDOs (OMA,OIC)/architectures already use RD. Are those changes in line with their use? Will people use RD stand alone or according to their framework.
    * [Bill] Will check that work.
    * [Carsten] Can we have information in .well-known/core and RD?
    * .wk/c is not right place, previous ways of describing it were not correct, needs to be done right in .well-known but not .wk/core
    * [Carsten] chat with MK over the ML? (also from
    * [Bill] agreed, looking for reviews
    * [Carsten] who has read last version? 2 + 1 on jabber people.
    * [Carsten] who wants to read it? 6-7 people.
    * [Carsten] encourage to read, thanks.
* [14.55] draft-ietf-core-resource-directory (Carsten)
    * moving forward
    * interesting question raised by Hannes, how do we develop it such that it makes since with other SDOs which use it?
    * LWM2M use registration interface only, no Lookup available.
    * [Michael] in OCF, we are still in process of specifying how RD will work, co-development
    * [Carsten] how to get this organized?
    * [Michael] through me if you want?
    * [Carsten] virtual interim meeting / RD conf call?
    * [Michael] yes, will work with Carsten to schedule
    * [Carsten] OCF can prepare it?
    * [Michael] yes
    * [Christian G] we should have more interims with other SDOs (OCF, OMA)
    * [Carsten] text on DNS-SD integration. how do we get feedback? is anyone using this? been implemented?
    * [Peter]: DNS-SD no feedback on implementation but still needed.
    * [Carsten]: Should this be published as a separate draft?
    * Call for contributions as a different draft. Need to have more feedback.
* draft-ietf-core-dynlink
    * no time
* draft-ietf-core-interfaces
    * no time
* [15.00] wrap up
    * hallway meeting in Park BR 3 on Thursday 13.30
    * no Meetecho, but Google Hangout on Carsten's iPad

----

THURSDAY 
========

(Informal meeting.)

13:30–13:30 Intro

* agenda bashing: Ok.

13:30–13:40 Links-JSON (CB)

* Presentation about status and updates. No comments.

13:40–14:00 CoAP in ANIMA (BRSKI, EST-coap) (PV)

* Presentation of motivation
  * The draft defines how to use EST over CoAP and DTLS
  * Is there interest to continue this work? Feedback?

~~~ text
[Jim]: I am familiar with EST. What is BRSKI on top of EST.
[PV]: BRSKI uses EST to transport all the key information.
[Carsten]: We could discuss here the overall approach.
[PV]: BRSKI approach is quite heavy. Still ongoing discussion how to do this.
[Carsten]: We could also discuss Media Type in EST and type response over EST that is not there yet. 
[PV]: human looking at the security is optional. 
[Carsten]: why need 2.06?
[Jim]: it may take time to produce the answer.
[PV]: may go back to manufacturer or something more complex where the reply comes from
[Carsten]: What timespan are we talking about?
[PV]: not absolutely sure; from half a second to some minutes
[Carsten]: wonder if something for CoAP needed for slow answers
[PV]: draft suggests way to handle this, from Klaus Hartke. Not sure where to do this work. CoRE has already many items
[Carsten]: Maybe the right working group would be Ace
[Jim]: much more ACE kind of thing
[Carsten]: except for 2.06. Rest look like ACE issues. ACE meeting right after this. Who in room familiar with EST? >3 people
[Ari]: I am not familiar with EST, so I don't have a feeling if this is good or bad
[Jim]: EST is basically a HTTP based protocol that uses well-known endpoints for posting PKCS#10 certificate requests to.  It has some additional end-points that can be used to get CRLs and do revocation.
[Ari]: How does this compare to LWM2M?
[Jaime]: LWm2M has bootstrapping and after the DTLS or TLS session is placed the manager can update security credentials on the devices.
[PV]: Not seen any immediate attachment, but in OMA you also have the problem on how to secure a new device.
[Jim]: Has Anima group looked at MUD?
[PV]: Good question.
[Brian ???]: MUD URI can go into the manufacturers certificate, it works very well with the BRSKI bootstrapping.
[PV]: lots of discussion of using MUD in ANIMA
[Brian]: Don't know.
~~~

14:00–14:10 Object Security for multicast (FP)

* Francesca presented OSCOAP for multicast. Solves RFC7390 issue with securing multicast but independent of use case.

~~~ text
Carsten: (on slide 83) what is in the message?
FP: same as OSCOAP. 
Carsten: how context becomes a context?
Jim: multicast enrollment protocol
Carsten: how parties learn context?
Francesca: context must be pre-established before communication. Foo-context is established based on input parameters (see OSCOAP preso). Would include base key and context ID and algorithm. Now also pub/priv key pair. Everything else derived from there.
Carsten: Does receiver 2 have to know that receiver 3 is there as well? (slide 83)
Francesca: no. Each listener is only aware of itself and broadcaster. Broadcaster need to now listeners to verify responses.
Carsten: if you have pairwise symmetric keys btw broadcaster and listener can those be used to send the response?
F: Yes.
Carsten: can do PSK in one direction and RPK other?
Francesca: Yes. PSK is used all the time and counter-signature too for source verification. It is easy to do source verification but don't need to (following wg decisions). 
~~~

14:10–14:20 Delegated Observe (ZC)

* Zhen Cao presenting. Way to deliver observe responses to different address than where request came from.
* Two scenarios: Multicast and Delegate to the cloud
* Would like to ask for feedback and others interested in working on this

~~~ text
Matthias: hinted that 2-3 years ago with Klaus talked about multicast notifications. Sending serial unicasts to large number of of observers costly. Multicast tricky so no real work so far. For original Observe wanted to avoid delegation to avoid bombarding with messages random nodes; didn't feel good design.
Carsten: if you look at this example (Delegate Cloud): don't see why an end device cannot tell the cloud to do the Observe
Dave Robin: The cloud server cannot go through the firewall, but a device in the same network can go out. Classic BACNET problem. New version(RESTful): add a message "it wasn't me"
Michael: working on similar thing on CoRE interfaces; binding. Working on generalizing with "monitor".
Dave: the one doing the binding is not necessarily one of the parties in communication. Three party thing. The one doing the binding is not necessarily interested in the data.
Michael: Could be a configuration tool. We should come up with a single approach to solve this problem. Will review this draft.Will need to review what's in CoRE interfaces and binding.
Carsten: one of the problems apart from the authentication is that this figure (Recap: direct Observe slide) is incomplete because the token is missing. The notification has to carry a token that the original sender of the request has allocated. Device may allocate a token for reply but the receiver don't understand what's the token about.
Zhen: But token is optional?
Carsten: No. There is always a token. There is nothing in the response message that tells you what the request was about except for the token. This needs to be solved for the delegate observe case. Who manages the token space. [Explaining how HTTP2-push solves the problem of one way communication without solicitation safely] 
...
Michael: HTTP2 solves that with the push promise. 
Dave: My answer is that the URI is actually very long token that includes a lot of data.
Carsten: Originally we didn't do this cause it makes it bigger and its easy to spoof. If you have some security it's harder. In NoSec mode it'd be a problem. The 32bit token gives some security against off-path attackers. Token in Security Consideration of RFC7252. This is not in CoAP today because (this has been discussed and) .. Which parts do we want to add to make these scenarios work?
Zhen: In normal home network case it's solved by having sensors sending directly to cloud. To send data to anothe cloud service, this could be a good fit. Benefit of this can have some node in the home network to tell to different destination. Can take discussion to the list.
Carsten: Who in this room thinks that there is a problem that we should solve at some point? 
~10
Carsten: So the rest doesn't care?
Anna: we're not using multicast
David Robin: Separate use case: I may not need the multicast scenario but I may need the other.
Laurent: Concern on security this enables DDOS.
Carsten: Important to analyze security and how to keep same level of sec by the token.
Matthias: It is quite open to say: yes we want to solve it but most may not understand exactly what is the problem, can we define this? How does this work with intermediaries? This document is more of a specific architecture solution.
Ari: this is only one case of the general pattern.
Matthias: Is this the small thing we solve or would it be better to have a discussion on the big picture? Architectures with intermediaries or more than one client have gotten very little attention so far.
Jaime: In OMA similar issues arised, and they have solved them within the SDO for their use cases. IETF CoRE is seen as a tech component maker.
Michael: (to Matthias) There is a number of problems that arise with Observe, like conditional observations, and need to be looked at. Many are very related to what you say. All of these things (limitation to observe pattern) need to be looked at in the context of the overall system. 
Alex: Agree with Ari, solve this problem of 3 nodes, one telling second to talk to third; this is already difficult.
Dave R: About complexity: this simple case is the piece we need to solve. We should start with this and solve it. Need solutions for the attacks; many ways to do that. Simple 3-party thing has plenty to work on.
Carsten: What you could do (Zhen) is to tell the local device to open a DTLS connection to IoT Cloud server and the server then sends the request to receive notifications (i.e., CoAP server is DTLS client). We agree there are problems but several ways to address them. Good to document the solutions that come in mind and see what can be solved with today's tools and what needs new tools.
PV: All the solution depend on the tools you use
Christian A: As far as I understand, everything now being talked about is rather about the multicast use case than for the cloud server firewall-piercing use case. Do you see the need for the latter? IMO, this should rather be solved via some kind of RD or TCP.
Carsten: Valid opinion, we need more documentation on the solutions. Document that describes these would be useful. Matthias do you want to add this to the draft-ietf-lwig-coap?
Michael: Could this also be a T2TRG research topic?
Carsten: Yes. Very valid topic.
~~~

14:20–14:30 CoAP over WebRTC DC (CG) 

* Christian presenting.
* Is this interesting for CoRE? (We think Multimedia systems may be applied to CoRE scenarios)

~~~ text
Carsten: Can I implement that or do I have to wait for the browser vendor to implement that?
Christian: can implement, just indicate with sub protocol. There is already one implemented for CoAP.
Carsten: What WebRTC implementations using today over DC?
Christian: MSRP, BFCP, and one more
Michael: would be appropriate for transport control? stop, pause, back, etc. Can use those with CoAP? At OCF transport control device mapped to CoAP. Would make sense to use this?
Christian: Yes potentially, you could use these. Wouldn't solve the channel problem. Original idea for gaming etc. 
Michael: it would be a sub-channel that would take care of (...missed it)
Matthias: why included new features with stream based CoAP? Is WebRTC stream based? 
Carsten: there's SCTP
Christian A: Camera control could be an application too -- think of what we're doing with the meetecho cameras
Christian: true, already controls for that, but this can be used too
Carsten: W3C is also working on browser API for sensors. CoAP could be intersting in that context.
~~~

14:30 - on  Flextime

* CoAP over TCP: mostly editorial issues

* Issue #69 at the Github tracker:What exactly is the mandate on ping
  pong messages. Right now is: "there is a ping, and pong is the
  answer" doesn't tell you MUST answer pong. What are people expecting
  ping pong messages to do? Other uses? One use may be RTP messages
  (only works if the other side reply quickly).
  
~~~ text
Ari: Is there a use to delay the pong?
Carsten: If there is things in the queue to do before. Right now it does not say anything. Should we say more? Makes sure we define it in a useful way.
Christian: It depends on what the sender wants to do.
Carsten: interesting phrase: "without undue delay" used in RFC7252.
Brian: Common pattern used in websockets and HTTP2. There is a bit too much "CAN language" in my opinion. Different uses; for RTT or if messages have been processed. Overloading this here.
Carsten: keep thinking about how to use ping and pong and bring this discussion to the mailing list.
~~~

*  Capabilities and settings messages was made mandatory on IETF96. What is the expectation with respect to the state machine? Goal is that the server does not have to send something just because someone opens a connection. Are we trampling on OCF again?

~~~ text
Dave Thaler: OCF has a reference but this functionality not in certified 1.0. So it's OK to change this. But if this becomes way to do versioning, maybe this should become the way to do versioning with OCF. OCF clear that RD and TCP are not certified but are experimental. 
Michael: agree
~~~

* Scheme names.

~~~ text
Brian: Bikeshed from IETF96. Either Priviledging CoAP or WS. 
Carsten: It is going to confuse implementers for years ahead.
Brian: could solve with coin toss
~~~

* Evaluation of Aggregate Congestion Control: please check this offline.
* Same for DTLS over CoAP slides. Have implemented this and very cheap.

Carsten: will prepare some slides summarizing what was said today and present on Friday.


----

FRIDAY 
========

Latest slides at https://www.ietf.org/proceedings/97/slides/slides-97-core-consolidated-slides-06.pdf

### draft-tcs-coap-no-response-option ➔ RFC7967

Akbar: will this be pointed out in the WG and coap.technology pages? 
Carsten: those running sites about CoAP should make sure that happens. It's in options registry, but otherwise a bit hidden perhaps

### RFC 5988bis

Mark N: have been working on weblink bis for a while. RFC5988bis Ready to become more formal. If you have needs for something in this doc, get in contact. But bis doc so only limited changes planned.
Carsten: one issue; too few registries in the weblinking.

Carsten: Leftovers from Wednesday will consume "flextime". CoAP over reliable transports will be discussed at the mailing list.

### draft-groves-core-dynlink

* Christian G presenting updates
* Looking for feedback on new attributes related to initialization and bands.
Carsten: who has read the most recent version of this draft? (3 people). Everyone should spend 10 minutes to read this.

### draft‐ietf‐core‐interfaces

  * Christian G presented updates. 
  * presentation of issues left:
* Function sets not easy to understand. Could remove function sets concept. 
* RFC6690 introduces "if" attribute, but does not say what should be on a description model, question on whether it should be elaborated.
* RD and OCF terminology alignment also needed

* Should remove function sets? Separate doc?
~~~ text
Michael K: hallways discussion consensus: remove function set. People not using consistently. Rather use few words to describe in place what is actually meant. Either update everywhere or remove and replace with description language. Interface description: we might want to focus on whant an interface does, and then give an OCF as example. Already OCF registrations. We should not register new ones that do what OCF ones do. Example ocf.ll already registered, should not register core.ll?
Christian G: need to consider in naming the registered prefixes and suffixes
Carsten: good way forward. Update the draft
~~~

###  draft‐groves‐core‐senml‐bto‐00

* Extension to SenML. Testing also extensibility of the spec. Time offset between records.
* Presentation of issues
* CBOR more easy to extend, seems to imply optionality for CBOR but not for EXI

~~~ text
Carsten: who has read a version of this draft? ~3
Ari: thanking for work. CBOR and EXI analysis correct. CBOR can parse a document even when there is extension not present before. Any EXI experts?
Carsten: General problem is that there are only few people who know how EXI works in W3C. We should try to find experts.
Cristian G: BTO support
Ari: If you support video and .. you also support BTO. There is a difference between understanding parsing and handling.
Cristian G: Problem with CBOR
Ari: Schema vs BTO
CarsteN: The schema should imply "i can decode this" not "i implement all options"
Ari: new issue: Do we need an option for "I saw something (could parse) but I didn't understand it (don't know how to handle it)."
Dave Robin: If I see BTO but don't support BTO I have to reject the message somehow. On BACNET optional functionality not supported message. The client can then fallback to prev version. When you extend and there is a fallback is good to be more explicit on the response.
Carsten: Is BTO a useful extension?
Ari: Yes. how do we indicate it?
Dave: "MUST understand" from SOAP signifies that the request needs to be rejected if not supported.
Ari: adds complexity.
Carsten: No need to solve this here. For the authors to solve.
Michael K: Is it there a notion of SenML validation? We should find a better solution than the one in the text. We talked about other things like extending for URLs. TBD.
Ari: Other option we don't do it at all. Keep it very simple. But it's a tradeoff, because this would make this kind of extension impossible. We want SenML out, it's been out too long, I propose we keep it single.
~~~

### draft-ietf-core-senml 

* Ari Presenting updates. New name, Sensor Measurement Lists (SenML)

Carsten: This is a feature that a CBOR to JSON can have but not vice-versa. 

* Ari presenting URI fragment IDs

~~~ text
Michael Koster: Does this impact the statement in RFC6690 about not supporting fragments?
Ari: Don't remember what 6690 says about fragment IDs. Will look into that.
Michael: RFC5988 has guidelines about that.
Carsten: RFC2616 had a bug on text on fragments and that bug was copied in RFC7252. Fixed in RFC7230 (more recent).
NOTE: RFC7252 section 4.6 talks about fragmentation.
Christian G: ?
Ari: This idea came up a few ideas ago
Henk: People might use batch mechanism to transport something else than readings. Might be used on the pubsub draft.
Ari: does not apply. this requires something else on server.
Michael Koster: It would be useful feature (fragment).
Ari: Some value on it, but maybe needs a real use case. Lets take it to the mailing list.
~~~

* Copy-pasting Senml. (Audience: shrugging and nodding) -- won't do harm, let's register identifiers

* Metadata "m" label

~~~ text
Christian G: Are there existing attributes that you'd need to update the character set.
Ari: No, this would be the only one.
Christian G: concerned about updating an existing attribute.
Jari: Support the idea, we can extend it later.
Ari: Seems to be support from people to do this as extension.
~~~

##  Management (10:17 )

Presentation by Alexander Pelov. 
  Introduction: CoMI the main draft. CooL for more advanced features and future work.

### draft-ietf-core-yang-cbor (10)

* Quick description of content
* Updates description 
* next steps submit final version by January, interop in February and in IETF98.
~~~ text
Carsten: Do we want to tag next version as an implementation draft? Trigger to hand over to NETMOD. 
Alexander: Yes, in January. Now the right time to have a look at the draft.
~~~

### draft-ietf-core-sid (10)

* Description of the document.
* Global identifiers assigned to YANG items for different functionalities.
~~~ text
Rick Taylor: I like it, looking from DTN side. Liked to use YANG but can't handle massive IDs.  What I didn't realize from the you have a flat ID space, everything is uniquely named. Might generate so many SIDs.
Alex: discussed this topic lot, want to have complexity at compile time. Registry system where register all these things in efficient way. It's 32 bits, so pretty large. 
Rick: with dotted notation can refer to part of the directory. Can talk of just little sub tree. Especially good for constrained environment. We do this with delta encoding. Everything is 1-2 bytes on wire. 
Alex/Carsten: we do this with delta encodings. 
Rick: Does it work if I extend the model and I have lots of SIDs, my delta would be just as big as the original value. 
Alex: in this case delta could be quite big (not more than the bytes for the sid itself). When you have a list of operations, your delta will be really small.

Edward Birrane: EPL another question is: Is there a reserve name spaces? What if some identifiers needed to be added in later on? Will they get a further position in the registry.
Alex: excellent question. What we want is a very lean draft. You will be able to reserve for (future) consecutive IDs. Wouldn't want to overspecify, would like to finalize this draft without wasting months to think about the algorithms.
Edward: The comment is that identifying groups is something useful. Large text names have grouping mechanism.  
Peter VDS: I sympathize with the hierarchy argument but it is too complex. SDOs can prepare their own modules and reserve the space for them
Carsten: If you really want a hierarchy you can use ASN1 object IDs. With SID we try to make flat spaces work. You can also save few bits for expansion. For toaster example, even if we have only few types of bread today, we can reserve for future types.
Rick Taylor: To finish here. Although we have similar use cases they are certainly different, in DTN the payload is much larger. We do not have the same compression limitations. Thanks for the explanation. 
Alex: Happy if you can reuse. 
Rick: I think MAYBE.
~~~

* Presenting allocation system. 32 bits initial + different chunks (IETF, YANG, First Come First Serve).
* Trying to avoid human-driven registry. IANA assigns chunks. 
* Requires .sid file generation.
* Public registries should be machine discoverable. Target is IETF99. WGLC March 2017.

~~~ text
Carsten: if skeptical of approach, we have running code 
Rick T: Is YID being discarded instead of SID? Carsten I just found your YID draft, is this discarded in favor of SID?
Carsten: This is what we are discussing here.
Rick Taylor: YID draft can be used on the DTN domain.
Alex: explaining how to do YID with SID.
Rick: I see the advantage of SID. But depends on how you do the CoAP management protocol. If you want to do e.g., "give me everything under this" or xpath selecting, with sid it will be very difficult.
Alex: YID has constraint that range is size power of 2 (last bits).
Rick: I think you are losing the structure.
Carsten: Rice-Golomb encoding can be used if you need more structure, but that uses more bits too
Rick: On DTN use cases we are happy to leave the compression in exchange for more power. 
~~~

### draft-vanderstok-core-comi (20)

Peter Van Der Stok

* Updates from v09. Usage of SID, iPATCH/FETCH support, YANG to CBOR, Content format WIP, new query params...

* Differences with RESTCONF

~~~ text
Carsten: who has read a recent version? ~10 Who wants to adopt this document? ~10 Who doesnt? 0 hands. So positive outcome, we will confirm this on mailing list.
Rick Taylor: YANG push for disconnected verifications?
Peter VDS: No opinion.
~~~

### draft-thaler-core-redirect (20)

* Dave Thaler presenting about OCF input. OCF wants to use stuff defined in CoRE; not fork to its own direction.
* Presenting redirect (from NoSec to DTLS)
* Carsten pointed out should not be able to redirect to random destination. In OCF can only redirect to yourself (same IP address) and only works in the same subnet with multicast
* Absence of 404 is privacy sensitive potentially. Two options: payload with 2.05, or 3.01 (moved permanently). If do 2.05, how to encode. Link format exists already so makes sense to use. But is 3xx or 2xx better? Link format or new option types better?

~~~ text
Carsten: two reasons for not redirect. 1) don't want the state machine 2) re-direct is circumventing state machine. Server leads the client. In HTTP most implementations do this automatically; client does not think about this. Violation of REST. Application should decide whether to follow lead. Will run into all problems or redirect in HTTP world. Stack redirected to do something can be exploited in wonderful ways. Adding state machine now seems wrong. The two figures are equivalent. How do we expect developers to implement this? Big danger around re-direct. How to do non-redirect solution? You could do this link format to any type of discover request. Not revealing OCF specifics. Link format one interesting additional point: it can add attributes on how this thing can be executed. Link format sounds like a good way to handle this. The disadvantage: address and path need to be repeated.
Dave T: Agreed.
Matthias Kovatsch: Not sure redirect is the right solution, a lot of changes that should be applied. Can imagine similar problems in other applications dealing with OCF. Would prefer having the information on the payload itself . At T2TRG working on this. Content format suitable for linking (e.g., CoRAL). About other issue: maybe 4.00 what you want to return. Leave the control & decision to client.
Carsten: You don't respond with 4.00 to a multicast.
Matthias: OK, more details to multicast, may want to apply something similar though. More flexible solution would be better (link format or new approach). Would recommend on investing time on exploring solutions.
Dave T: You are arguing for link format due to existing extensions, right?
Matthias: better to invest more time on hypermedia formats to get this right.
Michael Koster: link relation can be used to solve ambiguity. Can make explicit informing client what to do.
Dave Robin: Point to Auth Server is helpful but is also a Privacy problem. Can point to authentication server to do stuff.  Dangerous to add such a feature.
Dave T: Good point. Furthermore, what happens in the DTLS exchange is a job for the CFRG.
Dave T: What I'm hearing is general feedback to use 3.00 and link format. Is there a task for this WG or not?
Carsten: Example yesterday: proposal for 2.06 response code "talk to me later". We could have a draft where the server leads the client to do something. Informational type of document.
Brian Rosen: Your problem is not unique to OCF. PII is a general issue. 
Dave T: Correct.
Ari: +1 to avoid forking. General mechanisms like this should be done at the IETF.
Carsten: Contributors: Several (Erik, Christian, Zhen, Dave, Michael, Matthias?,  ... others?) 
~~~

### draft-groves-core-rfc6690up-latest (10)

* Christian explaining issues with RFC6690 IANA reg procedures for (rt) and (if).
* Proposal for a org prefix to be added. MUST comply to RFC6690.
* Proposal for prefix "x"

~~~ text
Carsten: Can already use URIs
Dave T: OCF does not use URI for compactness. OCF has much more coming and would be load for the designated expert.
Carsten: was reacting to the "x", which does not add any value.
Dave T: right now vendors  use point based because is more compact than using URI. 
Carsten: you save few characters, not big of a differences. Nothing prevents com.ibm.foo to register that. There's RFC that explains that using X-prefix is a bad idea
Brian R: Bad idea to create different namespaces. OIC.temperature sensor is different than OTHER.temperature sensor. We shouldn't balkanize the namespace. If we have a processing problem let's fix the processing problem.
Brian R: Lousy answer. Then we shouldn't use the registry if there is no solution.
Carsten:  (slide 210) "SHOULD provide a reference to where registrations can be found" it should be MUST and the org should provide interfaces or machine readable interfaces for usage.
Dave T: OCF question is about resource types not interface types. Nr of RTs could be very large. If designated expert is willing to take that effort, OCF is fine, but could be a lot.
Pete Resnick: Amplifying Brian's comments. Should try to avoid balkanizing the namespace. We should not create a protocol that decreases interoperability. Let's not do this.
Alexander: Agree that we shouldn't allow registering anything. however OCF might go for something else if we do not help. What is their roadmap.
Dave T: OCF is an org that standardized resource types, a long list. This is just a procedure for registration.
Christian G: Currently no guidance for designated expert than see that it's a valid string
Alexander: impression is that if we say no they'll continue duing as before (registering anyways).
Michael Koster: agree on the problem. Here we need to make a choice if we are going to enable or not enable that. I am not proposing a solution but agree on a problem.
Carsten: same problem in many registries. The expert does not work just by the letter but asks few questions. Is this needed? Have to be careful with pushback. Don't need to use codepoint because could use different than rt. Not winning much with pushback.
Brian Rosen: Sympathize with designated expert problem. Can perhaps help. 
Maybe we need to rethink this process: anybody can come up with any name is maybe not the right solution. We need to come up with a better answer. Can help figuring out a better answer.
Tim Carrey: you want to put the weight on the admin authority. Semantic interop is different issue. Support easing admin burden from expert. Encourage the group to think about this problem.
Dave T: agree, the problem Carsten raised should not be underestimated. Could happen same than with URI schemes. Wikipedia list used to be where people "registered" schemes. Now took it to IANA.
Dave Robin: BACNET had similar problems. We don't want to squash innovation, so we allow namespaces and multiple tags per registration. Also we had a big repository mapping. We did go through that process and the conclusion is that we let vendors use their own registry.
Christian: had same discussion in the semantic interop ws
Alexey Melnikov: Still trying to figure out potential actions, for example increasing the amount of people on the expert review team. Think about WG recommendation for the expert review. Should we come up with WG recommendation for expert review? I don't hear consensus to change the registration procedure. Need more discussion whether we want first come first serve or else.
Carsten: good way forward is more expert review recommendations and high threshold prefix registration....
Alexey: hear some tension on "do not do it" (to Pete who shook his head). 
~~~
