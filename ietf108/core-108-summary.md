# Meeting summaries

## CoRE @ IETF 108 (Virtual): Summary and Minutes

The core WG held two virtual sessions during IETF 108 held virtually.

---

The minutes for the two CoRE sessions are available at:

[Tuesday, July 28, 2020]
https://www.ietf.org/proceedings/108/minutes/minutes-108-core-202007281410-00

[Friday, July 31, 2020]
https://www.ietf.org/proceedings/108/minutes/minutes-108-core-202007311410-00

Raw minutes for both sessions:
https://codimd.ietf.org/notes-ietf-108-core

Thanks to the note takers Niklas, Ivaylo, Francesca and Michael!

---

The recordings of the two CoRE sessions are available at:

[Tuesday, July 28, 2020]
https://www.youtube.com/watch?v=rBmhQ_IkDQc

[Friday, July 31, 2020]
https://www.youtube.com/watch?v=vli7kn7YoiU

---

Consolidated slides for the two CoRE sessions are available at:

[Tuesday, July 28, 2020]
https://www.ietf.org/proceedings/108/slides/slides-108-core-sessb-core-consolidated-slides-v00-03

[Friday, July 31, 2020]
https://www.ietf.org/proceedings/108/slides/slides-108-core-sessa-core-consolidated-slides-v03-00


# Summary

## WG and document status
  * Published:
    * senml-more-units-06: RFC 8798 !!
    * senml-etch-07: RFC 8790 !!

  * In IESG Processing:
    * draft-ietf-core-resource-directory-25: IESG Evaluation
    * draft-ietf-core-stateless-06: IESG Evaluation::Revised I-D Needed. A few comments remaining, Klaus is processing them.

  * In Post-WGLC processing:
    * draft-ietf-core-dev-urn-07: AD Evaluation::Revised I-D Needed. After some discussion, publication was requested as Standards Track.
    * draft-ietf-core-echo-request-tag-10: On Shepherd's Writeup (Marco).
    * draft-ietf-core-oscore-groupcomm-09: WGLC finished last week now comments to be processed.
    
  * In WGLC:
    * draft-ietf-core-comi-10
    * draft-ietf-core-sid-14
    * draft-ietf-core-yang-cbor-13
    * draft-ietf-core-yang-library-02

    The WGLC ended on July 29. Carsten will proceed with shepherding the documents on mid-August.

## Echo-Request-Tag

* draft-ietf-core-echo-request-tag-10

   This latest versions addresses comments post WGLC, related updates have been presented, concerning both the Echo and Request-Tag option, as well as other document improvements. Ongoing shepherd writeup, plan to request for publication soon after this meeting.
   
   No comment from shepherding, the write up will be written up next week, then request for publication. 
   
## Resource Directory

* draft-ietf-core-resource-directory-25

This latest version addresses review comments and adds especially security considerations, related to security policies and to the use of Echo for amplification mitigation and client identity in simple registrations.

There have been a few interims, some about authorization and use of RD. Not found anything that could be applied to the RD today, bu we will continue with the current state and ship it. There are some ongoing discussions about authentication/authorization with the RD, but they are outside the scope of this current specification.

## CoRE Applications

* draft-ietf-core-problem-details-01

Updates were presented and open points discussed. Plan to work on Girhub issues for following revisions. Everyone is free to join the draft repo https://github.com/core-wg/core-problem-details and provide input.

From this version, it's just about CoRAL. Discussed how identifiers should be compact, with a low entry barrier. Ongoing research for different approaches to ID schemes. Naming things in a distributed way is one of the two hard problems in computer science. Looking for a way that works well for Problem Types and CoRAL in general. Ideas and suggestions are welcome. Need also to address when a registrant goes away.

## Dynlink
    
* draft-ietf-core-dynlink-11

Presented updates and planned way forward. Most recent updates incorporated feedback and added small changes. A small group of people has been working on small set of features.

Open points are about: observed notifications to reflect restful state change; behavior of pmax in the presence of proxies; possible support for epmin/epmax already used by LwM2M (discussion in Github issue #18).

There is one IPR disclosure from Qualcomm, on the current draft not containing epmin/epmax. To keep in mind for future discussions.

Next step is to reflect editorial changes and state transfers. Plan to continue discussion in small discussion group, synchronize with Bill if interested to be invited. Meetings over Jitsi. This topic will be also covere in interims after summer.

## SenML Documents

* draft-ietf-core-senml-versions-00

Summarized concept of versions signaling as set of features, through a bit array. This doc is also used by RFC 8798 (senml-more-units). It should be ready for WGLC, more reviews would be appropriate. Feature deprecation is hard to predict, but it shouldn't be a problem.

People who will review: Bill, Jaime.

* draft-ietf-core-senml-data-ct-02
    
Indicate the Content-Format of the binary data in the SenML record, so that it can be interpreted correctly. This version removes the must-understand ct_ until a way to use is found. The document will go on a 2-week WGLC.

## Blockwise for DOTS

* draft-bosh-core-new-block-04

DOTS creates challenges where there are DDoS attacks and needs mitigation, which is problematic in lossy environments given the large body packets. Proposed two new CoAP options for blockwise transfer, Block3 & Block4 akin to Block1 & Block2.

BLOCK3 can send packets without waiting for response, and introduces congestion control to avoid DDoS. GET and FETCH with BLOCK4 trigger BLOCK4 responses provided that the response is big enough.

Need for possible better clarification of the document scope, while it claims already that this is not a generic solution, but rather specific to the DOTS use case.

The draft discussed at two interim meeting. This latest version incorporates all received comments. The authors request adoption as a WG document. Assessed support for adoption to be confirmed on the mailing start. A call for adoption will start.

Christian will provide a review.

## AIF

* draft-bormann-core-ace-aif-09

This work was originally for both CoRE and ACE, now ACE has picked it up by ACE, but it is also interesting for CoRE.

AIF models access control as a control matrix, with subject and set of permissions. Protection of capabilities is not in scope.  The capability list is an array of pairs, it takes RESTful case as starting point, but other cases can be specified (e.g. MQTT). Objects are paths, while permissions are expressed as bitmaps. This is good for most applications. Good for static resources, but dynamic action resources can also be around, for which permissions are derived from the base resources, by doubling the bits.

First version in 2014, now in WG adoption in ACE. Ben Kaduk asked if there is anything else like this. Most web services have more complicated needs, so AIF is probably too simple. On the other hand, when done, this might be used elsewhere, so we should not block such uses.

The AIF pattern is very similar to IPSO (CRUD instead of REST). It's worth writing up for CRUD so a new set of registration bits is not needed every time.

A possible extension can provide also dynamic permissions; model the difference between resources that have been created or could have been created by a subject; model time aspects such as the lifetime of an Access Token vs. the lifetime of the resource (e.g. pub-sub topic). This may intersect with identity management.

## EDHOC+OSCORE

* draft-palombini-core-oscore-edhoc-00

Based on a discussion started at IETF 106, this new work proposes different approches to combine an execution of EDHOC with the first OSCORE exchange following it. The different approaches can also be signaled in different ways. Essentially, the EDHOC verification on the client is merged with the first OSCORE request protected with the derived security context. This optimization would reduce the overall number of roundtrips. The goal is to select only one approach signaled in one way.

Approach 1. EDHOC in OSCORE
    - Define new CoAP option indicating that message is both EDHOC and OSCORE
Approach 2. EDHOC in OSCORE
    - Use the OSCORE option and a new flag bit to tell that the payload contains both   
Approach 3. OSCORE in EDHOC
    - Define new CoAP option indicating that the message is both EDHOC and OSCORE
Approach 4. OSCORE in EDHOC
    - Signal with new content format. 

Approaches 1 and 2 seem preferred, with most preferences for Approach 2. If defining a new option, a short-enough EDHOC message can go in the option. Carsten and Klaus can provide feedback on this point.
            
People who will review: Christian, Carsten, Jim.
            
## Group Communication

* draft-ietf-core-groupcomm-bis-01

Discussed current Github issues and other open points. Agreement regarding port number in responses; criteria consistency for response suppression; usage of URI-host for naming application groups; usage of admin-local scope; rationale for mapping between security groups and applications groups. Next version will focus on closing these open points.

People who have read this or a previous version: Jim, Christian, Francesca

People who will review: Carsten, Jim, Christian

* draft-ietf-core-oscore-groupcomm-09

This last versions addresses all open point raised at the April virtual meeting.

More open points were discussed (mostly coming from the WGLC), requiring more thinking:

    - For the pairwise mode, it should be possible to signal the curve used for the secret derivation, e.g. Montgomery or Weierstrass. It should work to have it as additional information in the security context. Then the same MTI as today can be kept.

    - It's convenient to reset the SSN after group rekeying, which becomes easier to detect.
    
    - For observations, useful to store the Context ID of the original request. This would prevent notification misbinding across group rekeying if the SSN is reset. There may be further ways to look into.
    
    - New proposal for separated PIV spaces, for the group mode and the pairwise mode. Early discussion of pros/cons to be continued. Impact on communication overhead, space synchronization with the Echo option, and privacy implications. Some people expressed concerns.
    
People who have read: Jim, Christian

People who will read: Carsten

* draft-tiloca-core-oscore-discovery-06

The document defines a method to use the Resource Directory to find links for joining OSCORE groups at their Group Manager (GM). Now it has full support for Link Format or CoRAL. The Fairhair example was polished and also translated to CoRAL.

The next version will address some open points, and align with other GM administrative drafts.

A future document collecting all target attributes can include also the ones defined in this document.

Possible interest can be discussed with Fairhair/BACnet and others. T2TRG can a good venue, with CoRE invited.

* draft-tiloca-core-observe-multicast-notifications-03

The document defines a method to send observe notifications to a set of clients observing a same resource at the server, by using multicast responses. This latest versions updates the encoding of the informative error response to the clients; the mechanism for roughly counting the active clients; and alternative ways to obtain the phantom request associated to the group request.

Feedback would be needed on having optional or mandatory also the latest notification sent inside the informative response. Next updates will be about adapting the approach to work also with proxies.

People who will review: Jim, Göran, Jaime, Carsten

* draft-tiloca-core-groupcomm-proxy-01

The document defines a method to have proxies working in a group communication setting. It addresses the issues in the groupcomm-bis document. The proxy forwards back to the client the individual responses from the servers. The client distinguishes the servers originating the responses and learn their addresses. Two new CoAP options are defined.

An appendix describes "Nested OSCORE", to further protect with OSCORE (client to proxy) the group request already protected with Group OSCORE (client to servers). This allows the proxy to still identify the client (as required), as an alternative to DTLS as a separate protocol on the Client-Proxy leg.

Next steps will focus on chains of proxies and HTTP headers analogous to the two new options, for cross-proxies.

People who have read or are interested: Jim, Christian, Carsten, Francesca

* draft-amsuess-core-cachable-oscore-00

The documents defines the concept of "Consensus Request", protected with Group OSCORE but yet enabling proxies to serve cached responses to it. Related paper: https://arxiv.org/pdf/2001.08023.pdf

A possible type is a "Ticket Request" generated by the server, of which the phantom request used for multicast notifications is a particular case.

Another type is a "Deterministic Request", that all clients have to be able to generate as a one and same request. It becomes tricky with Partial IV and key to use. A possible way is proposed based on a "Deterministic client". Some encryption algorithms might have to be ruled out, none of them are in COSE.

Next version will give clarifications and more details.

Positive feedback on CoRE being the right venue and the importance of the problem

---

# Meeting Minutes

# TUESDAY, July 28, 2020

Participants: 14:17 - 54, 15.20 - 52, 15:40 - 46

Etherpad: https://codimd.ietf.org/notes-ietf-108-core

Meetecho video stream: https://meetings.conf.meetecho.com/ietf108/?group=core&short=&item=1

Audio stream: http://mp3.conf.meetecho.com/ietf/ietf1081.m3u

Minute takers: Niklas Widell, Ivaylo Petrov

Jabber scribe: Francesca

**14:10 - 15:50 UTC**

Numbers in parentheses are minutes of time allocated.

## Intro (10)

Jaime Jiménez (JJ): Welcome to Core WG, chair together with Marco. Note well, introduction, rules of engagement, going through agenda. 

JJ: Agenda bashing?

Christian Amsüss (CA): Let's move ERT as first, since that's referred by other. 
 
JJ: Use queue request on Meetecho, try not to interrupt.

 
* WG and document status

* Published:
    * senml-more-units-06: RFC 8798 !!
    * senml-etch-07: RFC 8790 !!
    
    JJ: Congratulations to authors. More units already used in OMA. 

* IESG Processing:
    * draft-ietf-core-resource-directory-25: IESG Evaluation
    * draft-ietf-core-stateless-06: IESG Evaluation::Revised I-D Needed. 
    
    JJ: A few comments remaining, Klaus is processing them.
    
* In Post-WGLC processing:
    * draft-ietf-core-dev-urn-07: AD Evaluation::Revised I-D Needed
    
    JJ: Done. There was some discussion on having it Informational or Standards Track. Barry confirmed Standards Track is fine and already gave comments. Now new draft needed.
    
    * draft-ietf-core-echo-request-tag-10: On Shepherd's Writeup
    
    JJ: Marco to writeup.
    
    * draft-ietf-core-oscore-groupcomm-09: WGLC comments to be processed
    
    JJ: WGLC finished last week, now comments to process.

* In WGLC:
    * draft-ietf-core-comi-10
    * draft-ietf-core-sid-14
    * draft-ietf-core-yang-cbor-13
    * draft-ietf-core-yang-library-02

    JJ: WGLC ends on July 29th (tomorrow). Please add any comments you could have before Friday

## Resource Directory (Christian) (5)

* draft-ietf-core-resource-directory-25

   - Overview latest updates
     - above probably w echo, right (comments)

    CA:
    - Major change on security policies (how -> what, rule ->options). Suggest use of echo for amplification mitigation and client identity in simple registration
    - Minor clarifications and editorial changes

    JJ: have had few interims, some about authorization and use of RD. Didn't come up with anything that could be applied to RD today. Will continue with current state and ship it.

    CA: There are some discussion for auth with RD, but they are outside the scope of the current specification.

    JJ: AIF later today.

## Echo-Request-Tag (Christian) (5)

* draft-ietf-core-echo-request-tag-10

   - Overview latest updates
   
   CA: Draft has not been presented for a year. Has passed WGLC. 
   - echo for amplification mitigation 
   - updates 7252 for the amplification mitigation
   - Echo: allow shorter values
   - Echo Proxies may process echo, should avoid deteriorate freshness
   - Request-Tag: don't solve all problems with stateless proxy blockwise problems
   - Better structured introduction, added privacy & security considerations
       - Suggest concrete numbers to IANA
       - Waiting for shepherd's writeup for more comments to process

    Marco Tiloca (MT): no comment from shepherd, the write up will be written up next week, then request for publication. 
       
## CoRE Applications (Klaus) (10)

* draft-ietf-core-problem-details-01 (10) --- Klaus

   - Present updates and discuss open points
   
   - KH: Draft that provides payload format for coap based apis
       - editorial: rebuilding doc, focus on expressing error details using CoRAL (instead of having it as exploration in appendix). Leave out things that are not sure to resolve.
       - GH repo with issues (https://github.com/core-wg/core-problem-details/issues), will work on those in the following revisions (not included in this version). 
       - Extensions for special use cases. 
       - Base: small set of common fields (error type, error description, human-readable details).
       - Feature: extensions per use case (tracing, log pipeline, 3rd party error reporting).
       - Everyone: feel free to join repo (https://github.com/core-wg/core-problem-details).
       - In -01 version, CoRAL all the way. Naming protocol elements is exciting. CoRAL has way to define new vocabulary, e.g, use URIs-as-identifiers as is done in the semantic web. -00 had custom scheme for new identifiers. 
       - Identifiers should be compact, low barrier to entry (people should not need to register elements in an IANA registry - too complicated for normal applications), stability, private-public transitions, popularity /familiarity to REST API developers
           - why not use current way as was proposed - minor disadvantages that make them suboptimal
       - Survey: started looking in Singapore at different approaches to ID schemes. Naming things in a distributed way is one of the two hard problems in computer science. Examples include IANA registries, LwM2M, Bluetooth, ISBN etc. This remains a work in progress, hope to find a creative way that works well for Problem Types (and CoRAL in general). Please speak up if you have ideas!
   - CB: A new idea being tested is to use Github repo with IANA registration. Do PRs to add to registry.
   - KH. On our radar, but might be too much to ask. If developers have to register every error type, even throuh Github repo that might be too much to ask
   - CA: There should be some kind of hierarchical part of this, should be some kind of namespacing. E.g., able to set base URIs.
   - KH: What happens when registrant goes away? Please contribute.
   - JS: Started playing with this, need to look at privacy and security, how applications report errors. 
   - KH: Anything specific beyond what is in the "Problem Details for HTTP APIs" RFC (RFC 7807)?
   - Jim: Did you expect me to read that draft?
   - KH: We can take it to the list.
   - JJ: Thanks for the presentation.

## Dynlink (Bill, Michael, Klaus, Jaime) (10)
    
* draft-ietf-core-dynlink-11 (10) --- Bill

   - Updates and way forward.
   
    - Bill Silverajan (BS): Very short update on Dynlink, currently v -11. 
       - Substantial changes, primarily restructuring and reformulating aspects. 
       - From -08 --- -11, have been able to incorporate feedback.
       - From -10 --- -11, small changes. Small group of people has been working on small set of features.
           - 1. Editorial: current draft observed notifications reporting values, should instead reflect notifications as restful state change.
           - 2. The behaviour of pmax: pmax impacted when there are proxies. Working consensus to let pmax influence server's Max-Age. 
           - 3. Proposal from Alan/OMA: to support two attributes (epmin, epmax) (min/max evaluation period) already used by LwM2M. Discussion in Github issue #18.
           - Carsten Bormann (CB): I'm not so interested in the new parameters. Are there IPR disclosures that we would need to look at?
           - BS: Yes, Qualcomm has declared.
           - CB: Before epmin/epmax?
           - BS: IPR raised against current draft, which do not contain them. 
           - CB: need to keep in mind in the future discussion.
           - JJ: Maybe we should not discuss the IPR now. Topic is very interesting. 
           - BS: ??
           - Ari Keränen (AK): Given that LwM2M is the biggest user of dynlink today, it would make sense to have them in the spec. 
           - Barry Leiba (BL): Clarification on the discussion on IPR issue. Not appropriate to discuss if the IPR itself applies, but it is proper to discuss the impact of the IPR on progress of the specification. 
           - JJ: Should split the conversation, focus on pmax for the moment. 
           - CA: I have an issue with the binding site?
           - BS: there is the thing about binding links ...
       - Dynlin next steps: v -12 will reflect editorial changes to reflect state transfers. Plan to continue discussion in small discussion group, please ping Bill if you want to be invited. Meetings over Jitsi.
           - JJ: Fine to send Jitsi inviation to the list to have a biger audience and involvement. Also, this will be material for the next series of interim meetings planned for after summer.

## SenML Documents (Carsten, Ari) (20)

* draft-ietf-core-senml-versions-00 (10) --- Carsten

   - Status and open points
   
   - CB: We have talked about SenML versions before, will do quick recap.
       - SenML defines version number, it does not define how it is used.
       - Objective is extensibility, sometimes using extension points, sometimes other ways. Version is unitary declaration, stating that given features are needed in order to process a given Pack.
        - Version numbers are stupid, not always best ways to handle the problem. Has been discussed in many places. Have a mechanims to define required features (must-understand fields), however it becomes less useful as that list for a given Pack grows.
        - Ari proposed using a bit array to compactly describe features. 
        - 53bits in JSON integers? Evil number? There are currently 48 left, can limit the way the bits are allocated. Not sure how many are needed
        - That was the background, defines a feature system, specification required.
        - Updates RFC 8428, now a WG draft.
        - Used by senml-more-units (FC 4 = more units).
        - Ready for WGLC, but would be good to have some reviews.
        - Request for folks that can do review (Bill, Jaime Jimenez)
    - JJ: Also read the draft. Thought on deprecation of features, how often will it happen?
    - CB: Hard to say and predict.
    - JJ: Any implications if things are deprecated?
    - CB: The good thing is that you simply will not need to use the features that are deprecated.
    - JJ: Bill and Jaime will review the document.


* draft-ietf-core-senml-data-ct-02 (10) --- Carsten
    
   - Present updates and discuss open points
   
   - CB: can have binary data in SenML record, the idea is to introduce Content-Format indication so it can be interpreted correctly. 
       - -02 is different from -01, removed ct_ which created problem with must-understand, so removed until a way to use is found.
       - CA: Good riddance.
       - CB: Ready for WGLC.
       - JJ: Reviewers needed?
       - CB: Minor change, not needed.
       - JJ: Will issue a 2-week WGLC.

## Blockwise for DOTS (Jon, Mohamed) (15)

* draft-bosh-core-new-block-04 (15) --- Jon

   - Present the draft, status checkpoint, check for adoption
   
   - Jon Shallow (JSW): DOTS creates challenges where there are DDoS attacks, needs mitigation. 
       - Talking about large body packets, problem in lossy environments. Two solutions, Block3 & Block4 (I thought one solution, but Block1 and Block2 are replaced by Block3 and Block4 ...). 
       - Sample target development (see RFC 8782).
       - DOTS inferred CoAP requirement
           - need to transfer body w multiple payloads
           - handle packet loss
           - cannot rely on getting responses
           - want to keep CoAP way of working with this
       - BLOCK3 has BLOCK1 characteristics
           - can send packet without waiting for response, people can increase NSTART in order to allow more packets to be in the pipe
           - introduces congestion control to avoid DDoS, set MAX_PAYLOAD to 10, ...
           - Example shown
       - BLOCK4 has BLOCK2 characteristics.
           - GET and FETCH with BLOCK4 trigger BLOCK4 response provided that the response is big enough. 
           - Example shown
       - Draft discussed at two interims, have incorporated comments.
       - Request adoption as a WG document.
   - CA: Sorry for not sending review. Still missing out where this should go, either bespoke solution to blockwise not being able to do everything, or a generic solution. Needs clarification on that. Can then start with layering violations, etc
   - JS: Direction is that in addition to. If someone in the chain does not understand new options, then go back to old.
   - CB: Good solution, few nits to be worked as WG doc. Supports adoption. Need to ensure that all CoAP components are actually used correctly. Good for implementers what the result will be. Also need work on applicability statement. 
   - Mohamed Boucadair (MB): The document does say that it is not a generic solution.
   - JJ: For all those who participated to the interim meetings, tend to be supportive of adoption. Let's HUM. HUM Result PIANO (some interest). Enough to adopt as WG document. Please share the objectives etc. More comments? Authors will have to send a new version, can you work with github?
   - MB: There is already a version on GH, can move that.
   - CB: Chairs setting up repos is a great service! Take also this on the mailing list.
   - JJ: Thanks Jon and Mohamed for the patience to progress the draft. The decision to be validated on the ML.
   - Action item: start call for adoption; CA to send review.

## AIF (Carsten) (10)

* draft-bormann-core-ace-aif-09 (10) --- Carsten

   - Present updates and way forward
   
   - CB: Pretty weird name, was originally both CoRE and ACE. Picked up by ACE, but also interesting for CoRE.
       - Access control and authorization. Access control matrix, map subject and object to a set of permissions. Commonly sliced into a ACL (Access Control List)
       - This draft slices by capabilities (c-list). No protection of capabilities, draft concerned with access authorization list
       - Represent C-list as array of pairs. Speced for RESTful case, but can be specified for other cases (e.g. MQTT). Objects are paths. Permissions - simple bits. A bit coarse, but good for most applications.
       - Good for describing static resources, but iot devices often have action resources, leads to dynamic action resources. Instead, derive permissions from the base resources. Done by doubling the bits. That way a person might not be able to delete the base resource, but do actions on its children (?). Deleting an action stops it for example.
       - Status: it has been around since 2014, came out of DCAF and was in the ACE BOF at IETF 89. ACE is looking at WG adoption, is there anywhere else where this can be used? On ACE agenda for tomorrow, will conclude result from adoption call.
       - Ben Kaduk asked if there is anything else like this. Most web services have more complicated needs, so AIF is probably too simple. On the other hand, when done, this might be used elsewhere, so we should not block such uses.
    - JJ: The AIF pattern is very similar to IPSO (CRUD instead of REST).
    - CB: Worth writing up for CRUD so a new set of registration bits is not needed every time.
    - JJ: intent to add additional protocols in LwM2M, everything there maps to CRUD.
    - CA: Is there room still for expanding this, e.g., to apply dynamic permissions?
    - CB: that would be a significant extension.
    - CA: Would not go in the same document (dynamic resources).
    - CA: There are lots of bits available.
    - JS: A difference between things I did create, and the ones I could have created. Also time aspect, e.g., pub-sub-topic, time might run out on the Access Token with the permissions, before one would want the topic to go away. Is it the same subject coming back again to act on the same child resources it created before?
    - CB: Management of subject identities is an interesting topic. Yes, the Access Token can be time-limited. Then the client gets a new Access Token with a new temporary identity. This seems more about managing identities than authentication. We can discuss tomorrow at the ACE meeting.
    - JS: On the agenda, but needs slides.
    - JJ: Any other questions/thoughts?

## Flextime (15)

- MT: opportunity to pull in a document that would be presented on Friday.

* draft-palombini-core-oscore-edhoc-00 (10) --- Francesca

   - Present the new work
   - Ask for reviews

- Francesca Palombini (FP)
    - Combining EDHOC and OSCORE.
    - Started in IETF 106, brought to CORE since EDHOC is now in LAKE. Idea is to reduce number of roundtrips to run EDHOC. LAKE is scoped to produce one lightweight AKE. Document is an optimization, combine EDHOC and OSCORE sequentially. 
    - Question, can the three 3 RT exhcange be optimized? Yes, we can merge EDHOC verification and OSCORE request.
    - How to send two messages together?
        - Send EDHOC in OSCORE or vice versa
        - Figures shown
    - How to signal which alternative is used?
        - 1. EDHOC in OSCORE - 
            - Define new CoAP option - Define new CoAP option indicating that message is both EDHOC and OSCORE - Start with EDHOC, then do OSCORE
        - 2. EDHOC in OSCORE
            - Use the OSCORE option - Use the OSCORE flag byte to tell that payload contains both
        - 3. OSCORE in EDHOC - by the number of elements 
            - Define new CoAP option indicating that message is both EDHOC and OSCORE
        - 4. OSCORE in EDHOC - by the number of elements
            - Signal with new content format. 
    - CB: EDHOC message size? Delimited?
    - FP: Message size around 20 bytes. CBOR encoded, so known where it ends.
    - CB: I prefer alternative 2.
    - FP: Option 2 would save the most bytes, not using specific option and specific URI Path.
    - Göran Selander (GS): How does it work with FETCH?
    - FP: The ciphertext contains the method and the URI.
    - CA: Strongly in favour of first options, for 1 & 2 it is plain response to what is in the payload. Suggest to put EDHOC in an option, only if EDHOC message is short so that it fits.
    - FP: Not sure if option size is enough.
    - Ivaylo Petrov (IP) (on chat): +1 for option 2.
    - FP: Way forward is to get feedback and incorporate, signals preference for option.
    - JJ: Who will review?
    - Action item: Christian, Carsten and Jim to review. 
    - FP: Jim brought up using multipart-core, has the same problem as Christian brought up.
    - FP: Please send comments, Klaus or Carsten please inform on length of options.


JJ: This concludes the session, thanks for joining, remember ACE tomorrow! See you on Friday.
    

Σ 100

---

# FRIDAY, July 31, 2020

Etherpad: https://codimd.ietf.org/notes-ietf-108-core
Meetecho video stream: https://meetings.conf.meetecho.com/ietf108/?group=core&short=&item=2
Audio stream: http://mp3.conf.meetecho.com/ietf/ietf1081.m3u

Minute takers: Michael Richardson, Francesca Palombini

Jabber scribe: Francesca Palombini

**14:10 - 15:50 UTC**

Numbers in parentheses are minutes of time allocated.

## Intro (5)

Trying to start on time.

## CoRECONF Documents (Ivaylo) (10)

* draft-ietf-core-comi-10
* draft-ietf-core-sid-14
* draft-ietf-core-yang-cbor-13
* draft-ietf-core-yang-library-02

   - Highlight from concluded WGLC, presenting the slides

"SID" -> "YANG SID", or "YSID"

CB: I'm the shepherd and I am a bit behind, will do soon, and will ping some people to answer WGLC.
JJ: YANG validation warning, for nits.
MCR: have read the docs (not the last iteration), not all of them.

JJ: Carsten do you have a timeline in time?
CB: I can do next week, but need to ping more people. Hopefully mid-august.
JJ: We'll keep an eye on the ml.

## Groupcomm Documents (Marco, Christian) (65)

* draft-ietf-core-groupcomm-bis-01 (10) --- Marco

   - Discuss updates, addressed reviews and open points

Any issues with \#1 (admit change of port number in responses) --- hearing none.
Any issues with \#2 (response suppression) --- hearing none.
Any issues with \#3 (URI-Host) --- CA says it is good to allow. CB +1

sl.7, point on admin-local scope:
JS: need to go back and look at the original message.

sl.7, mapping of app and sec groups: no objections to add text aligned with the proposal in the slide.

JJ: Who has read this or a previous version: Jim, Christian, Francesca

Carsten, Jim, Christian volunteered to provide a review.

* draft-ietf-core-oscore-groupcomm-09 (15) --- Marco

   - Discuss updates and relevant open points from WGLC
\[14:38] (3 min behind schedule -- 17 min flex left)

sl. 6 poin 1
No objections to removing replicated info from the security context.

sl.6 point 2
MT: add Wei25519 and ECDH25519 as hightlighted alternatives or have them even as new MTI?
JS: Don't have a preference. Lwig people may have a preference. I don't know if there is a way to indicate the choice of curve.
MT: what we have now as MTI is safe and stable. Something else will require more time for implementation and testing.
JS: Doc needs to be clear that's what it's doing.
MT: Would it work to add this indication in the security context while keeping the current MTI?
JS: Yes.
MT: will add some text.

sl.6 point 3
CA: why are we talking about wrap around?
MT: we use exhaustion in the draft.
JS: might be a bad point, not what I was thinking about.

sl.7 point 1
JS: it can be useful in case the stored 'kid' has a relevant meaning only for some particular 'kid context' value.
MT: so it's a second layer of checking when matching notifications with the original observation request. Ok we can store it.

MCR: counter signature in COSE - change should not impact here, is that correct?
MT: yes, no impact, but we would have to point to the different document when that happens.
MCR: any preference? Also don't believe you need to point to a new document.
MT: we point now to struct-bis.
MCR: Ok

sl.7 point 2
CA: wouldn't that mean that 2 requests could have same kid and same external aad that the response could match to? This could endanger request response binding.
JS: reset of seq numb makes detection of key rollover easy. 
CA: if client sends Obs req with the same seq numb both before after rekey, they would share the same data in external aad
JS: key context in ext aad? sl.6 point 3: when it gets to the max value?
MT: yes.
JS: everytime I rekey I keep moving to the max value
MT: yes, until exhaustion. then get a new sender ID or rekey.
JS: How do I tell the difference between the 2 rekeys?
MT: 1st case directly to the node, second case to all nodes.
JS: as the server, it might be difficult to tell. that's why prefer to have ssn reset to 0.
JS: Christian concerns will be valid either way and we need to think them through.
MT: So, if we reset SSN to 0 after rekeying, the two options seem to be either have also the stored kid context of the observation request also in the external_aad, or kill observations in case of rekeying.
CA: Or a 3rd option: including the n of the key generations in the external aad, but this requires more thinking through pen and paper.
MT: Ok to think more.

Sharing space of Sequence Numbers

CB: sequence number moving might be disclosing something.
MT: good point.
JS: might say that you respond, not how.

GS: might want to take a step back. The main point of pairwise mode was to reduce overhead of the many responses, avoiding the signature. This would add back some overhead, for the pairwise PIV to possibly add to responses.
CA: at least for code reuse and saving 1bit per message, separate SSN is not to follow up. Also look up to CB point.
CB: we should document the problem at least.
MT: we'll continue the discussion to assess pros and cons.

Who has read: Jim, Christian
Who will read: Carsten

* draft-tiloca-core-oscore-discovery-06 (10) --- Christian
\[15:07] (17 min behind schedule -- 3 min flex left)

   - Discuss updates, addressed reviews and open points
   - Ask for reviews

Method to use the Resource Directory to find links for joining OSCORE groups at their Group Manager (GM). Now full support for Link Format or CoRAL. Polished Fairhair example, also translated to CoRAL. Plan to address some open points, align with other GM administrative drafts.
   
JJ: New link attributes defined in a new doc. This also has more, maybe we should sync.
CA: yes, fine to cover parameters to that new doc.
JJ: maybe this could just use CoRAL.
JS: +1 in jabber about just using CoRAL.
CA: something to keep open considering also how CoRAL advances.

JJ: if there is interest for collaboration also with Fairhair/BACnet mentioned in the example, T2TRG can be a good venue with CoRE invited.
CA: to check with Peter also about possible changes in the use case.

* draft-tiloca-core-observe-multicast-notifications-03 (10) --- Christian
 \[15:18] (18 min behind schedule -- 2 min flex left)
 
   - Discuss updates and open points
   - Ask for reviews

Method to send observe notifications to a set of clients observing a same resource at the server, by using multicast responses. These are responses to a phantom request that the server creates.

This latest versions updates the encoding of the informative error response to the clients (including also the phantom request); the mechanism for roughly counting the active clients; and alternative ways to obtain the phantom request (e.g. as metadata of a pub-sub topic).

Feeback would be needed on having optional/mandatory also the latest sent inside the informative response.

Next updates will be about adapting the approach to work also with proxies.
   
GS: fantastic work.
CB: +1 (from jabber)

Jim Göran Jaime Carsten volunteered to review.

* draft-tiloca-core-groupcomm-proxy-01 (10) --- Marco
 \[15:29] (19 min behind schedule -- 1 min flex left)

   - Discuss updates, addressed reviews and open points
   - Ask for reviews

Method to have proxies working in a group communication setting. It addresses the related issues raised in the groupcomm-bis document. The proxy forwards back to the client the individual responses from the servers. The client can distinguish the different servers originating the responses and learn their addresses. Two new CoAP options are defined.

An appendix describes "Nested OSCORE", as a way to further protect with OSCORE (client to proxy) the group request already protected with Group OSCORE (client to servers). This is convenient to allow the proxy to still identify the client (as required) will avoiding DTLS as a separate protocol on the Client-Proxy leg.

Next steps will focus on chains of proxies and HTTP headers analogous to the two new options, for cross-proxies.
   
JJ: anybody interested or have read a version of the draft?
Jim, Christian, Carsten, Francesca

* draft-amsuess-core-cachable-oscore-00 (10) --- Christian
 \[15:39] (19 min behind schedule -- 1 min flex left)
 
   - Present the new work
   - Ask for reviews

This is proposing the concept of "Consensus Request", as protected with Group OSCORE but yet enabling proxies to serve cached responses to it.

A possible type is a "Ticket Request" generated by the server, of which the phantom request used for multicast notifications would be a particular case.

Another type is a "Deterministic Request", that all clients have to be able to generate as a one and same request. It becomes tricky when it comes to the Partial IV and key to use. A possible way is proposed based on a "Deterministic client".

Next version will give clarifications and more details. Is CoRE the right place for this work?

Related paper: https://arxiv.org/pdf/2001.08023.pdf

FP: Yes CoRE is the place imo. Will read and review after update.
JS suggests in the that: on the second method, there is a class of encryption algorithms for which it is not going to be doable. There was a discussion about whether or not this constitutes nonce re-use.

JJ: Clarify about ticket request in the error response?
CA: That's how it would work with multicast notifications, and observations is the only case where it make sense to consider that way.
JJ: So probably a normative reference to this doc would be required.
CA: This is the strawman proposal to get from one step to the other.

JJ: Will put this too in my bucket list of reading.

CB: Solving this problem would be great

JS: Can't use some encryption alg, because they use some randomness during the encryption process
CA: Are there criteria related to them, or columns in COSE registries?
JS: no such algorithms in COSE at the moment. There may be 1 or 2 in CFRG, will have to check them. We have to also avoid altogether another class of algorithms that don't have any IV.
CA: But then they're not usable with OSCORE in the first place, right?
JS: Right.

## Wrap up
    
JJ: interim in September, syncing up with other SDOs, WGs, etc...

Σ 100
