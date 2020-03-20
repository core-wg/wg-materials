CoRE WG - Summary IETF101
=========================

* [Slides](https://datatracker.ietf.org/meeting/101/materials/slides-101-core-consolidated-slides/)

* [Raw minutes](https://etherpad.tools.ietf.org/p/notes-ietf-101-core)


## Monday, Mar 19, 2018

* **Intro**

* Draft-ietf-coap-tcp-tls has been published as [RFC8323](https://tools.ietf.org/html/rfc8323).
* Several on IESG review [cocoa](https://tools.ietf.org/html/draft-ietf-core-cocoa), [links-json](https://tools.ietf.org/html/draft-ietf-core-links-json), [oscore](https://tools.ietf.org/html/draft-ietf-core-object-security), [draft-keranen-core-too-many-reqs](https://tools.ietf.org/html/draft-ietf-core-too-many-reqs).

* [draft-ietf-core-links-json](https://tools.ietf.org/html/draft-ietf-core-links-json-10)
still a few DISCUSSes left. RFC 8288 is replacing RFC 5988, that affects RFC 6690
but it is decided to keep using it. The document will require another
IESG review.

* [draft-ietf-core-object-security](https://tools.ietf.org/html/draft-ietf-core-object-security-11) has a new appendix that adds the explanation requested in comments. Suggested to work on a new informational document with usage examples. The request redirect issue affects coap-http proxies in general, httbis chairs suggested to provide support for redirect and core agreed. Minor update v12 fixing DISCUSS in a couple of days.

* [draft-ietf-core-senml](https://tools.ietf.org/html/draft-ietf-core-senml) at IESG, done from the authors PoV. It will be addressed during the IESG review in April and will become RFC after that. Ready for publication after IESG review.

* [draft-ietf-core-senml-fetch](https://tools.ietf.org/html/draft-keranen-core-senml-fetch-00)
had discussion on the use of wildcards in FETCH and PATCH operations that use Senml. Emphasis on not miss-using wildcards. Interest from the group, specially for a simple generic version, without regex or complex operations.Formal adoption when SenML is ready.

* [draft-ietf-core-resource-directory](https://tools.ietf.org/html/draft-ietf-core-resource-directory-13) 102 closed comments since editor onboard, [available on the rd repo](https://github.com/core-wg/resource-directory/). Remote interop to be set, interested parties should contact [Christian](christian@amsuess.com). Some core members to provide reviews. Other SDOs to provide feedback and commit to interop.

* [draft-ietf-core-rd-dns-sd](https://tools.ietf.org/html/draft-ietf-core-rd-dns-sd-01) not so much progress since the last meeting. Draft is to be discussed in the DNSSD WG.

* [draft-ietf-core-yang-cbor](https://tools.ietf.org/html/draft-ietf-core-yang-cbor-06)
reviews of YANG to CBOR are needed, otherwise document ready for LC from authors pov.

* [draft-ietf-core-comi](https://tools.ietf.org/html/draft-ietf-core-comi-02)
F-interop public platform to test CoMI implementations available.

* [draft-ietf-core-sid](https://tools.ietf.org/html/draft-ietf-core-sid-03) reviews are needed.

* [draft-ietf-core-oscore-groupcomm](https://tools.ietf.org/html/draft-ietf-core-oscore-groupcomm-01) has undergone several updates. There are currently several implementations one of the open source. Several people in the group volunteer to read the latest version.

* [draft-keranen-core-too-many-reqs](https://tools.ietf.org/html/draft-keranen-core-too-many-reqs-00) error code 4.29 defined, adoption call done on the list.


## Tuesday, Mar 20, 2018

* [draft-ietf-core-cocoa](https://tools.ietf.org/html/draft-ietf-core-cocoa-03) is at IESG. Few comments need to be addressed by OPSDIR, SECDIR and GEN-ART. RFC5033 guidance might not be so applicable to lock-step protocols. Markku Kojo presented experimental results with default CoAP, CoAP over TCP and various versions of the CoCoA draft. The presentation shows cases of congestion collapse depending of number of nodes. While not applicable to many of the current deployments it suggest actions to be taken on RFC7252 default RTO and COCOA, as well as LPWAN providers.

* [draft-ietf-core-dev-urn](https://tools.ietf.org/html/draft-ietf-core-dev-urn-01) feedback needed on the current version, the author will verify offline the implications of this draft on other SDOs.

* [draft-ietf-core-echo-request-tag](https://tools.ietf.org/html/draft-ietf-core-echo-request-tag-01) the document is mostly ready for publication, some reviews are still needed.

* [draft-hartke-core-pending](https://tools.ietf.org/html/draft-hartke-core-pending-02)
needs a response code to map http 202, which can be used in other cases. This draft specifies a new content format, which creates the question of having application-specific state machines to CoAP. Potential use of a new response code with similar semantics at 202.

* [draft-ietf-core-coap-pubsub](https://tools.ietf.org/html/draft-ietf-core-coap-pubsub-04)  discussion on the use of core.ps and on how topic discovery works on topic trees. In order to move the work forward faster an interim meeting will be set before next IETF.

* [draft-ietf-core-dynlink](https://tools.ietf.org/html/draft-ietf-core-dynlink-04) , [draft-ietf-core-interfaces](https://tools.ietf.org/html/draft-ietf-core-interfaces-11)
Both drafts target WGLC in IETF102, after addressing the new comments and WG review.

* [draft-silverajan-core-coap-protocol-negotiation](https://tools.ietf.org/html/draft-silverajan-core-coap-protocol-negotiation-08)
work on adding FETCH and optional mechanisms for transport negotiation. Interesting to add to other SDOs.

* [draft-silverajan-core-coap-alternative-transports](https://tools.ietf.org/html/draft-silverajan-core-coap-alternative-transports-11)   
discussion on the use of scheme:// and how it would look like. OCF would not use one that ties to a specific application protocol. The authors believe the document is ready for adoption. Discussion to continue with T2TRG, W3C and OCF.

* [draft-toutain-core-time-scale](https://tools.ietf.org/html/draft-toutain-core-time-scale) was presented, discussion on how long to keep the CoAP request on the server, thus adding state. WGA adoption discussion to be taken offline.

* [draft-wang-core-opcua-transmission](https://tools.ietf.org/html/draft-wang-core-opcua-transmission) Discussion touched the issue whether OPC should be doing this or the IETF.  In any case, the authors were encouraged to continue the work, talk to OPC as well and keep IETF involved.


# Detailed minutes

Thank you to the note takers!

~~~ text/plain
-------------------
 ╔═╗┌─┐╦═╗╔═╗  ╦ ╦╔═╗
 ║  │ │╠╦╝║╣   ║║║║ ╦
 ╚═╝└─┘╩╚═╚═╝  ╚╩╝╚═╝
---------------------

Core@IETF101

Constrained RESTful Environments WG
Chairs (core-chairs@ietf.org):
Jaime Jiménez
Carsten Bormann

Slides
https://datatracker.ietf.org/meeting/101/session/core


## Monday

**13:30–15:30 Richm_Chl_Tow**

 * Intro (10)     
* WG and document status     

Carsten (CB) provides the introduction (Note well, etc.)
CB: No changes to the agenda
CB: RFC 8323 published + 3 on IESG
Zach: could the WG buy a beer to all every time there is an RFC published from this WG? :)
CB: presents advertisements  RIOT SUMMIT in Sep 13.

* Published: RFC 8323 (with supporting RFC 8307)     

* Quick recap of related work, pointers

CB: T2TRG coexistence at 17:30 at Waterloo on Monday @ hilton London metropole
CB : RIOT summit

CB: look into new option for stateless proxy in -minimal-security (has been discussed here, but it's good other groups do options too).

 ### In IESG processing  

* Further directions for Links-JSON (10)     
* <https://tools.ietf.org/html/draft-ietf-core-links-json-10>  

CB: There is related work in OCF, further feedback.
CB: proposal to refocus and not inherit the limitations of 6690, but still cover it
CB: Update of RFC5988 to RC 8288, implications on this draft, no need to update RFC6690.
CB: Need to support language tags, but not to support "*".
CB: new piece is <last part in slide 13>
CB: Do we want to replace well-known/core with JSON or CBOR form?
AD: It does relate, IESG review questions the need for multiple formats.
Zach Shelby: Agree on rebase to 8288 and keeping free from 6690 idiosynchrasies. Disagree with mandating 6690.
ZS: Mandatory to implement is "/.well-known/core" (6690) CBOR is not a limitation,
Michael Koster: in RD we required 6690 compatibility and the same is proposed now here in slide 14
AD: Document is 9 months in IESG, return to WG. It also depends on how many changes you want to do and for how long. This document will need another IESG review at minimum.
CB: there were 3 DISCUSSes linked to these issues. Continue discussion offline. Idea is to finish quickly.
CB: Process discussion offline.

* Object security (30)     
* <https://tools.ietf.org/html/draft-ietf-core-object-security-11>
Goran Selander presents OSCORE

New appendix adds explanation requested in comments.
CB: it would be useful to start a document that explains different situations in which OSCORE is being used, so that people understand... Configurations in which we run OSCORE, rationale, etc.
GS: Appendix does have examples.
CB: Should we complete this info with a new document (informational)
CB: who would like to work on this?
GS: authors of the document... others are welcome
CB (from the floor): I don't think we are abusing HTTP. There are different levels of an abuse
GS: [Explaining the request redirect issue]
Cristian Amsuss: Why redirect is a OSCORE issue? it affects coap-http proxies in general.
GS: It is not something we are actually <interested in?>
Jim Schaad: I don't think this is a media type of CoAP
GS: people have been requesting this
CB: ("that's the whole reason"), if specific composite number is needed, then this content type number is necessary
GS: Has core made a decision on HTTP redirect?
AD: HTTPbis cochairs commented that we should support redirect as standard feature. Possible to have proxies on the path that don't need to understad oscore.
Francesca Palombini: it is not a proxy problem rather it is a problem of being redirected to a server that does not have the right key material
JS: in that case the server will answer with a 4xx error code. Not a problem form the http point of view. (AD +1)
GS: Decission to support redirect.
GS: Dave T suggest change of header field name
CB JS: why not OSCORE?
GS: To the mailing list.
AD: Are all issues addressed?
GS: Yes (just few minor TO-DO, should be fixable today or tomorrow).
FP: we are really tracking all the issues (https://github.com/core-wg/oscoap/ ), in general all elements are in the draft. We might want to rephrase some things, but in our opinion, we just need to answer to the emails we got.
CB: Assumption that there will be a -12 in a couple of days. Emails answered sooner.

* SenML (10)
* <https://tools.ietf.org/html/draft-ietf-core-senml-13>   
   Ari Keranen presents the slides. At IETF LC, done from CoRE pov.
   AK: "good IDs" after discussing with experts
   AD: IESG review in April. Do you really need an allocation by 15th April?
   AK: IANA fast diligence not needed if no new comments after IESG telechat.
   AD: let's see what happens in the telechat week
AK: Early assignments for SenML Fields (OMA DM requesting)? Procedure?
AD: No procedure.During last call IANA already prepares the registry and information is available in the background, it would be allocated as soon as the approval is done.
AK: OK.

* SenML, continued (15)     
* <https://tools.ietf.org/html/draft-keranen-core-senml-fetch-00>

Ari explaining usage of FETCH and PATCH for SenML (payload metadata).
Explaining the use of wildcards. Need for PATCH early.

ZS: Wildcard sounds something "nice to have". Granularity. "Give a recommendation on good object design"
AK: is it there interest for this?
JJ: operations and regex out?
AK: yes
Matthias Kovatsch: in industrial systems I would be interested, not specifically the SenML version, rather the more general approach
Padhu: size of the code for a constrained device?
AK: if you already support SenML, the additional code is minimal
Dave: wildcards in the middle of the uri is the evil part. With proper structuring of the data you can avoid using wildcards. restructuring the data is better. better place wildcards at the end.
AK: Agree,specific case for OMA DM Objects.
Alexander Pelov: narrow down to the specific use case for this
CB: Reviewers? (6). It appears there is interest. Formal adoption when SenML is ready.

* Resource-directory + dns-sd (30)     
* <https://tools.ietf.org/html/draft-ietf-core-resource-directory-13>     
 Christian Amsüss presents.
Comments:
https://github.com/core-wg/resource-directory/

Remote interop to be set, contact Christian.

Need for reviews.

Padhu, Mathias, Kerry Lin and Michael to provide reviews.

* <https://tools.ietf.org/html/draft-ietf-core-rd-dns-sd-01>     

DNSSD to be presented on THU

* New: <https://tools.ietf.org/html/draft-amsuess-core-rd-replication-01>   

Jaime: maybe other SDOs that use RD?
CB: Matthias and Ivaylo show up hands. One month until plugtest over the Internet.
CB: who cares about RD replication scenario?
Jaime: I'm interested as I also have a document in the same space (draft-jimenez-t2trg-drd).

CB: RG?
CA: sounds good to me. Maybe I could ask T2TRG.
Stuart Cheshire: we don't want a single point of failure, so this is interesting. No strong opinions wrt solutions.
JJ: Specific use of DHTs to distribute?
SC: No specific way at this point.
AK: very interesting topic.


* Comi: yang-cbor, comi, sids (15)     
* <https://tools.ietf.org/html/draft-ietf-core-yang-cbor-06>     
* <https://tools.ietf.org/html/draft-ietf-core-comi-02>     
* <https://tools.ietf.org/html/draft-ietf-core-sid-03>     
* Status update: <https://tools.ietf.org/html/draft-veillette-core-yang-library-02>

Alexander Pelov presents.
AP: we will need your input, asking for reviews. There are new releases, three main documents.
MK (speaking for W3C WoT): a sensible default should be in place.
AP: we cannot simplify more than it is
AP: F-interop platform can be used to test your CoMI implementations. It is publicly available, user friendly.
AP: comi.space: tools available for sid, etc.
AP: who is willing to review YANG to CBOR?
Henk B: commit to review if he has someone else.
CB: the reason we haven't WGLCed YANG to CBOR yet is that it allows to learn and avoid mistakes. Now people have worked on/with it.
CB: we should be finishing
CB: who would review sid and COMI documents from this WG? - Nobody
AP: request feedback from other WGs?
CB: WGLC , let's try this out with YANG to CBOR.
CB: "Linda" verification needs to be done.

* Group Communication (10)     

* <https://tools.ietf.org/html/draft-ietf-core-oscore-groupcomm-01>

Marco presenting.
Peter Van der Stok. How do you want to get the relationship between ??? Is it via RD, management...?
Marco: different options
Peter: do you want to remove multicast from this document?
Jim S: it could be unicast
Marco: should we just go for the ACE approach? (ACE one is aligned with the general guideline in our doc)
CB: I would like it if the interface that you are assuming here is well documented.
Marco: first steps for an early interop
CB: who has read the mosst recent version of the doc? (2 hands) Who is interested in reviewing this doc? (5 hands)


* Too many requests
     * <https://tools.ietf.org/html/draft-keranen-core-too-many-reqs-00>

   Ari presenting.
   CB (from the floor): good place to remind people that they can send payload formats in responses for more info.
   Ari: agreed.
   Ari: keeping it simple and quick progress seems a sensible way forward. Leaving payload format for future drafts.
   CB: we should do the adoption call on the list
   Peter: I would also like to have the same smoothed process for the other response code documents


* 'Pending' response code

Peter presenting.
Carsten presents his slide "Pushing application-specific state machines into CoAP?"

## Tuesday **09:30–12:00 Viscount**

* CoCoA (25)     
* <https://tools.ietf.org/html/draft-ietf-core-cocoa-03>

Carles Gomez presenting.
editorial update for version -03. A next revision will include additional comments
CB: Could make use of transport supervision provided by AD and Gorry F to comment on the RFC5033 guidance
Gorry Fairhurst: RFC 5033 guidance is meant for transport guidance for new prtocols: TCP, SCTP, DCCP, QUIC, and may be less applicable to lock-step protocols. Guidelines for transport like this is also  provided in RFC 8085. Some of these checklists may not apply. Point #3 does apply: the method needs to not adversely impact standard transports, especial in congestion collapse. e.g.,  if it makes TCP behave differently, this needs to be taken into account. But not all of RFC5033 may apply.

Markku Kojo presented empirical study results.
libcoap with few bug fixes and timer adjustments. CoAP over TCP implemented on Linux stack. With increased congestion, plain CoAP starts to result in much longer flow completion times. CoCoA and TCP adjust timers to fit the longer queue times. In very congested network TCP has much lower amount of re-transmissions. CoCoA -3 has many re-transmissions with infinite buffer. The clients not able to get weak sample.

Protocol actions needed on default CoAP (RFC7252) and on CoCOA. Update draft and new I-D to fix RFC.
CB: default CoAP (should address quickly). No state kept there. If change needed, would need to make for TCP too.
Markku: TCP backs off. Doesn't restore RTT. Keeps exp BO value until ACK without retrans. 6298.

CB: If I open a new TCP connection, I get new state. This is exactly the same problem.
Markku: for random clients TCP is openened and come now and then. With SYN, have time, if delay too much, retrans with BO. Then get ACK.
CB: You never get there if you experience what I described.
Markku: will get if retrans long enough
CB: You are comparing the case where TCP keeps the states?
Markku: CoAP not keeping state, and that's a problem. Then initial RTT of 2s can be way too low. In general, UDP guidelines says 3 seconds. Understand that some constrained devices can't keep state. Should stay in spec that if possible, should keep state. Most devices should be OK today with this.
CB: Default RTO in CoAP is btw 2 and 3 seconds.
MK: It should be reconsider to RTO>3 seconds, as UDP guidelines (RFC8085) say.
CB: Any reccomendation we should be making if you do this to cocoa?
Markku: fine; in CoCoA should do the same as TCP; right now doesn't do
CB: don't need to change in 7252. The current value not going to break Internet.
CB: In respect to CoCoA, I think there are useful observations. If the max retransmit should be used for parameters determination. Upper bound should depend on max.
Markku: if RTO estimate more than 7 seconds, goes off.
CB: number 32 (upper bound for RTO) should depend on max retransmit. And number may not be right for the default value. Other thing aging: simulation based on situation with continious congestion throughout Aging not designed for that but bursts. If burst in network, want to go back to "normal" quickly. Wihtout aging random losses can make reaction time very high if don't have aging. Fundamentally aging idea is right. In deployment no one in their right mind would deploy CoCoA without aging. Random loss would turn implementation to very sluggish one.
Markku: some settign with high delay don't work. Aging incrased RTO value; when close to 3s, timer ages before get weak sample. Not good to age and then sample and recalculate.
CB: I think there is misunderstanding. Aging is supposed to be used when idling.
Markku: understanding with -01; in -03 two examples of aging, especially for below 1s case, retransmitting. Draft doesn't mention that should be only in idle. That should be clarified at least.
CB: aging not to be done while retransmitting. Needs to be fixed.
Markku: 4xRTO too low. If congested, doesn't necessarily go away in 15 seconds; not good to age away. Best solution to try to get samples as often as you can. Weak estimate problematic with retrans. Problem is hard.
CB: agree this is hard. Maybe aging should be more tunable. But moves the problem to poor developer.
Markku : congestion is the first one to be dealt with.
CB: but need also deployable protocol. We have too little information for estimator. Network wihtout replies you don't get enough info. Need to take home: need to make clear that aging only used in idle. Interested to see numbers in that case. Some results may show that.
Markku : That is the results implemented without aging.
 Not retaining back off value the main problem. Mostly fix everything, Then need to reconsider some other modifications.
 Because of aging takes these problems earlier.
CB: need to look why that is not happening. Current RTO esitmate contains BO information. Need to look into more details. Very useful work. Shows that there are limits to default CoAP congestion control. Also limits with parameter set we have defined for CoCoA.
Ilpo Jarvinen: 400 clients the RTT 10/15 seconds is clearly below the 32s, so if the congestion control works well enough, it would not allow this collapse. If Congestion Control causes collapse to happen, RTT rises higher. If have just one request-reply/client, not fully possible with random clients because of forgetting state, but for continuous clients. Then even with 400 clients slightly more than 10 seconds the actual RTT. If can prevent collapse, max RTO not significant anymore. Because only with collapse RTT goes that high.
Markku : every request was retransmitted at least 4 times..
CB: numbers for CoCoA -01 have aging closer to what discussed here? (slide 12)
Markku: Aging implemented same in both cases. In these experiments, if you apply aging only in idle periods. 25% only system does useful work
CB: anomaly in left graph fixed by making clear the aging only in idle period. In right side still have problem.
Markku : We should recommend more than what you said; keep the timer value....
CB: Then you need to add a decay mechanisms.
Markku : you don’t need to add decay mechanism
CB: TCP starts at 3
Markku : Think about Congestion first and then go about rest
Markku: don't have time now but have more results related to this
Carles Gomez: Is it possible that -01 is not the WG one, but CB.
Markku : working group draft. Implemented -01 when the 02 draft came out and then added 03 which was essentially similar
Carles Gomez: I think there was no change...
Markku : maybe not intended, but the result is.
Carles Gomez: Why there is up to 20 in the table on slide 16?
Markku : (slide 16) how many retransmissions needed. Max retransmit of 4, client would fail because of exchange would be aborted and result would be aborted and results are not comparable anymore.. <5% of cases mismatch ?
higher back off factor to be used in order to get rid of congestion factor during the period of study ?
Ilpo Jarvinen: If MAX_RETRANSMISSION was not increased, a lot more client failures would have occured.
Carles Gomez: I understand, but it would have been interesting to test with max retransmissions 4.
Markku :it would not change the final outcome. We can exchange with larger number of clients with every 10sec of so.. the results are the same.
Gorry F: I find this discussion helpful. When pointed to Scott B's document, didn't meant to compare to single packet. For me the effect of congestion collapse in the network is most important. Idle time consideration is important. I think the group should seriously consider any reset RTT time while retransmission is pending, and I personally think should recommend caching the RTT. This has to be really discussed in the document or to address this issue. Please continue to work and think on this topic.
ZS: Do we have the right use case in mind? Did earlier work on CoAP at scale with Matthias Kovatsch. In the industry right now CoAP is being used in a centralized way, we have large cloud providers collecting bigdata. With one centralised endpoint communicating with many contrained endpoints to collect sensor data.
Markku: yes and no, it depends on where and how many bottlenecks there are. When more than one bottleneck offer load there.
ZS: some brainstorming with the operators and LPWAN providers good here to identify such bo


* Dev-urn (10)     
* <https://tools.ietf.org/html/draft-ietf-core-dev-urn-01>
Jari presenting

Looking for feedback for section 3. In particular how to deal with q, r and f components? Perhaps don't need to, but would be good to get feedback. New device schemes suggested by OneM2M and LwM2M. Text suggestions good here. For WoT schema, also other alternatives, but if want unders the dev-urn, more details for structure needed. If don't get more details on the possible assignments, inclined to publish without them since can always extend this.
Dave Thaler: UUID is one of the types?
Jari: already separate scheme for this; not needed here
Padhu: not clear what text needed; in  LWM2M1.1 URLs and URNs under URI. LwM2M can do URI and that can be device ID.
Jari: could look off-line what, if any, is needed here. But if anyone has burning need to add something to dev:urn, please say so now and send text.
(no one running for the mic; seems we're good here)


* Response TAG

Christian Amsüss presenting.
CB: reviews? Jim, Carsten, Jaime, Julian, Francesca, Michael. Should not sit too long on this since solves important problems. Reviews, last call, publish.

* Pending (for EST over CoAP) (15)     
* For: <https://tools.ietf.org/html/draft-ietf-ace-coap-est-00>     
* <https://tools.ietf.org/html/draft-hartke-core-pending-02>

Matthias: what see from two proposals, two different strategies. One in state machine, other mechanics of the state machine we want to define. NEw respose code more meta level. Don't have to think in application. The Maybe proposal needs application design. Are all apps reommended to follow this? We have lots of proposals that use CoAP in more simple way, and not necessarily HATOAS. In particular for pub/sub draft nicer solution would be to have it in meta level. People who want to do pub/sub, won't think in hypermedia terms. Two different strategies.
CB: what position taking here?
MAtthias: no srtong opinion. Would be nice to have more apps in hypermedia approahc. But case of pub/sub, rather have people moving from MQTT to pub/sub where we have more metadata. Then response code is nicer one. Both solutions are valid, but two different domains where they are valid. Haven't thought alot the EST use case. But probably not designing too much hypermedia but using "simple" CoAP.
Peter vdS: Agree with Matthias. If have response code, more general nature than the media format. Media format for client to talk to server as part of one app. No need to export knowledge what the format means. More general serviec with response code. Proxies can be problem, but on the other side client gets response back that doesn't understand.
Alex: like to see one use case / app on how does this map and we use it. Seems like meta problem. What will this serve for?
Koster: agree with idea that this is more app oriented, and status codes more transfer layer. For pub/sub transfers just representaions. Like to see more discussion on what is wrong with response codes.
CB: should we have this kind of discussion every time someone comes with at new application. if we don't come up two apps discussed so far are specific things, and do think we should guide app developers for media types. Agree with Matthias to level, yes decision to be made, but would prefer to have only response codes for things that are universal. What is bad about response codes: in general nothing. We can add 4xx and 5xx codes. Success response code has bit more baggage: assuming that CoAP layer know how to handle this response code. Proxies but also CoAP cachnig layer in client implementation has to know about the response code. Don't want situation where someone can't get app working because CoAP implementation doesn't have the response code yet. We should guide app developers solving this with means of what CoAP has available. On general, having resource that is not quite state of providing useful info -- one property is that server wants to say something about the state. "come back later", "nothing yet, here's default". Fundamentally application specific and calls for app specific media type. Finally, problem we run into in pub/sub, is Observe requires all notifications to have same content format. That may have been a mistake. Maybe want to fix that instead.
Matthias: for pub/sub is as Carsten mentioned. At first glance feels like strong correction / change in Observe. Maybe something drastic like response code is the right answer. Connected to many other decision made. With response codes similar to methods; stuck with minimal set initially, then extended. With response codes: what if "it was processed correctly but nothing to return". With the evidence we have, maybe can collect more evidence and rethink what are the response codes we need. More general than EST and pub/sub space.
CB: new response code would have semantics similar to 205?
Matthias: maybe we need 2xx, no content, that would solve the two issues.
CB: 204 no content has slightly different semantics. "previous content you got is still valid". Really weird that it's called "no content". Can't draw parallel here. One question we should try to decide. What does it mean for this case.
Matthias: 204 also returned if changed something.
...
CB: suggesting new success response code, that is used for representations that were not for what was originally requested, but are somehow useful for progressing.

(anyone else taking notes anymore? or am I disconnected...)

MK: Not cacheable 204 would not be appropriate for the pub/sub case... It is not a redirect ... waht we want to say with pubsub is a similar semantics, success but it is not what you wanted.
AK: We need a response code, something generic and forward looking. Instead of having 3 successful response codes we can have only one that is future-proof. Makes sense to explore this.
CB: There are IoT cases and we can look at them. We could spend some time looking at it. Need to take to the list, also during this IETF.


* Pubsub (10)     
* <https://tools.ietf.org/html/draft-ietf-core-coap-pubsub-04>  

Michael presenting.
Do we require all topics to show up in core.ps?
Conditional Notification for CoRE pub/sub subscribers?
How does Topic discovery work with topic trees?

CB: have used earlier virtual interims, but not recently. Good to get back to habit. What is good time?
MK: Interim next month during April/May. Before July IETF.
CB: mid point some time in May. Could also do two.
MK: we don't have that much to do here, but could be surprised.

CB: how many have read the doc? (Almost 20 hands)
  Reviewers: Jim S, Christer H,

Ari: would be good to discuss where do we want the topic to land? Only under the pub/sub API root?
CA: Do we need to perscribe this as everything is already linked?
MK: you can put relative URI or absolute URI and it will do the right thing
Ari: the broker just deny the request if not OK?
MK: need to clarify this in the draft

* Dynlink + interfaces (10)     
* <https://tools.ietf.org/html/draft-ietf-core-dynlink-04>     
* <https://tools.ietf.org/html/draft-ietf-core-interfaces-11>

MK presenting interfaces
MK: Want to have WGLC at (by) IETF 102 (interfaces)


MK presenting CoRE Dynlink

Dave T: can clarify that when using as band, notify when in/out band?
MK:  yes, you just make lt greater than gt
Dave T: actually opposite to the example on slide (gt and lt)
MK: we'll clarify this in the draft. we need to add examples.
MK: Target is WGLC in the next ITEF.

CB: who has read recent version: Christian, Mojan, Jaime.  Reviewers Mojan, Ari and Christian.

CB: for interfaces, who has read recent version: Christian and Zach. Reviewer: Christian.


* Protocol negotiation, alternative transports  
* <https://tools.ietf.org/html/draft-silverajan-core-coap-protocol-negotiation-08>

Bill presenting

CB: Who has read a recent version? Christian.

CB: currently two separate docs, maybe want to revisit that. Will go to another doc and then discuss.

Jaime: from LwM2M PoV protocol neg sounds like useful feature, as LWM2M has to support multiple transports. When have now OMA DM folks here, could discuss this too. (Padhu, Zach nod)
BS: hoping to put in some text about examples (how OCF uses it)

* <https://tools.ietf.org/html/draft-silverajan-core-coap-alternative-transports-11>     

Bill presenting

CB: draft in weird state, how will we use this next. Left unfinished 8323 how do you do URL scheme that is open on the transport being done. Have unpaid IOU on this. Protocol neg draft will go into that in some for. This will too. But want to specifically define such shceme, coap+at or something. Dave will remind us of the OCF's such URI scheme (ocf://) that is specific to OCF way of naming endpoints. Maybe something to also take into consideration. Have two pieces of raw material here, and unfinished unpaid check.

Dave T: Yes to what Carsten said I'd say. The comment is not specific of ocf, but anytime you have an org or vendor that makes use of coap and of transport specific coap, probably will never use coap+at but rather something like what we have in OCf (ocf://) as it is agnostic of the transport. All the protocol negotiation is hidden at a higher non-coap specific layer. We have to take that into account and whether coap+at would be used. OCF wouldn't.
CB: We rename this URI scheme to rest:// (implying http too?)
DT: exactly what looking for. Can be extended later. Naming things etc.
MK: generalization  

CB: Meeting coming this Friday with OCF, T2TRG, and W3C WoT. This is something we should coordinate there. Who could write a draft by then? Most critical issue is endpoint naming. Need to agree what we do with that.
BS: can perhaps look at this, but not by Friday
CB: have turned the two docs to slightly larger work item. But something that the community certainly could have use for.

* Flextime (25)      

* <https://tools.ietf.org/html/draft-toutain-core-time-scale-00>

Laurent: would like to have WGA. When sending COAP request, how long to keep that in server. With very slow device can be important.

CB: who interested in this option? (5 LPWAN people). To be taken offline.

* <https://tools.ietf.org/html/draft-wang-core-opcua-transmission-03>     
Junrui Wu presenting.

JW: Updated based on feedback. Will contact OPC Foundation in few weeks for input. Need more feedback.

Dave T: agree, next steps getting feedback from OPC-UA. Clearly belongs to OPC. Technical comments/questions: might be more appropriate in OPC. Understanding that OPC defines 3-4 different transports, only one used really is TCP. Here mention COAP, but don't remember if in draft it's over UDP or TCP. But in cloud expect TCP? Have you compared compression?

CB: will continue to be interested what other orgs might be using our protocols for. And what influence that has for future design decisions. Will enourage bringing this info back here. But good to know what OPC thinks about this. And good to have numbers on message size and compression.

~~~
