# Meeting summaries

## CoRE @ April 2020 Virtual Meetings (replacement for IETF 107): Summary and Minutes


We have uploaded draft minutes for the two CoRE virtual meetings acting as replacement for IETF107:

[Wednesday, April 08, 2020]
https://datatracker.ietf.org/meeting/interim-2020-core-01/materials/minutes-interim-2020-core-01-202004081500

[Thursday, April 15, 2020]
https://datatracker.ietf.org/meeting/interim-2020-core-02/materials/minutes-interim-2020-core-02-202004161500

As usual, this starts with a summary of what happened (with fewer technical details), followed by more detailed minutes as collected in Etherpad.

Please send fixes and updates to core-chairs@ietf.org or to the mailing list, preferably within the next 7 days or at least before you dive into the holidays.

For easier viewing and commenting, the summary part is replicated below.

# CoRE WG - April 2020 Virtual Meetings (replacement for IETF 107)

(Constrained RESTful Environments WG, Draft Minutes 0.1)

The core WG held two virtual meetings as replacement of IETF 107 in Vancouver, both of which are summarized in these minutes.

Videos:
: Wednesday (2020-04-08, 2 h): https://www.youtube.com/watch?v=Rdwl_l9Tqog
: Thursday (2020-04-16, 1.5 h): https://www.youtube.com/watch?v=tMgxTFGC4PI

Slides:
: Wednesday (2020-04-08): https://datatracker.ietf.org/meeting/interim-2020-core-01/materials/slides-interim-2020-core-01-sessa-ietf107-core-consolidated-slides
: Thursday (2020-04-15): https://datatracker.ietf.org/meeting/interim-2020-core-02/materials/slides-interim-2020-core-02-sessa-core-consolidated-slides-v00

Raw minutes:
https://etherpad.ietf.org/p/notes-ietf-107-core?useMonospaceFont=true

Thanks to the note takers Francesca, Amelia and Thomas!

## WG and document status
  * Published:
    * multipart-ct-04 as RFC 8710
    * hop-limit-07 as RFC 8768

  * In RFC-Editor's Queue:
     * draft-ietf-core-senml-etch-07
     * draft-ietf-core-senml-more-units-06

  * In IESG Processing:
     * draft-ietf-core-resource-directory-24: in Last Call. A couple of comments for Alexey have still to be addressed by authors.
     * draft-ietf-core-stateless-05: in Last Call. Klaus has been processing comments from GENART and the Security Directorate.

  * In Post-WGLC processing:
    * draft-ietf-core-echo-request-tag-09: WGLC last call completed and to be formally closed. Shephers write-up can start right after.

  * WGLC to be issued:
    * draft-ietf-core-dev-urn-04: WGLC will start right after this meeting.

## CoRECONF cluster

Discussed overall outcome of WGLC and remaining relevant issues. The latest versions will have to be sent to other potential reviewers who may be interested. We will do another WGLC when the new documents are submitted.

* draft-ietf-core-sid-12 --- All remarks are still not processed. Text is needed to explain that we are doing the same thing we would be doing in the early allocation process, even if no strict need for early allocation anymore thanks to quick allocations. The disccusion will continue on the mailing list, no major issues remain.


* draft-ietf-core-yang-cbor-12 --- Better to have normative references from CBOR to SID or the other way around? New version to be resubmitted anyway. Previously, unnecessary normative references caused big delays. YANG-CBOR should be a free-standing document, someone who just wants to use YANG-CBOR can do that without referencing other docs. Let's try to process with a minimal amount of normative references. Need to address all comments and feedback, in the next resubmission.

* draft-ietf-core-comi-09 --- It is not clear whether Security Considerations really need to be very extensive, or whether a more general observation is acceptable that authorization requires care. No further discussion followed on this.

* draft-ietf-core-yang-library-01 --- Editorial changes will be ready soon, also considering the feedback from Tom Petch. Need to think about the level of dtail required to solve concerns. The SID-draft may take longer time to work out than the others. We are hopeful it will not be a big delay.

## Groupcomm cluster

* draft-ietf-core-groupcomm-bis-00 --- Document intended to obsolete RFC 7390, updating RFC 7252 and 7641; insecure and secure (with Group OSCORE) communication are in scope. This version took care of Jim's and Thomas' reviews, improved definitions, discussed group discovery with the RD, improved security considerations. There is a distinction between CoAP/OSCORE/Application groups, and they use different types of identifiers. There are some open issues on Github. Discussion also on the list about the port number may change in the server response compared to the port number of the multicast request. Open point on using URI-Host for identifying application groups and on consistency requirements for response suppression.
 
    Next steps are: working on the open issues; process last review comments; test selected functions in CoAP implementations.

    Christian Amsuess, Jim Schaad and Thomas Fossati volunteer for reviewing next version.

* draft-ietf-core-oscore-groupcomm-08 --- Second update since IETF 106, addressing open points and two reviews from Jim. New pairwise mode of operation, using derived pairwise keying material for one-to-one exchanges (useful for Echo and Blockwise). Overview of several open points and plan to address them. Next steps are: closing presented open points; do more testing of message protection in pairwise mode, and then go to WGLC.

    Need to decide on a single signature algorithm to be MTI. If pairwise mode is supported risk to support both Montgomery and Edwards implementation in HW. A draft in LWIG talks about EdDSA with mapped coordinates for both key agreement and signing. This can be the MTI algorithm. -- https://datatracker.ietf.org/doc/draft-ietf-lwig-curve-representations/

    Discussion in the mailing list on making this document update OSCORE, to relax that only HMAC-based HKDFs are fine in OSCORE. Should it be in this document? That would be fast, but if it's in this document there'll be an "Updates" link that gives the wrong impression of Group OSCORE being mandatory for OSCORE now.
    
    Jim Schaad has succesfully tested multicast + observe.

    Christian Amsuess volunteers to review the next version of the document.


* draft-tiloca-core-oscore-discovery-05 --- Just deployed nodes may miss information on how to join an OSCORE group through the Group Manager (GM). The CoRE Resource Directory (RD) is used to find thouse groups, providing links to the GM for joining them. This works even if the GM is not deployed yet. Addressed Jim's review, added also provisioning of the link to the ACE Authorization Server associated to the GM. Clarified relation between application and security groups (need to improve across documents). Added examples in CoRAL. There is a long example from BACnet, where group membership is used while not explicitly defined by the RD. Better to remove that part of the example out or can confuse, it may go to a separate document. Of the promised reviews, one was received and processed. More would be needed.

    Jim Schaad volunteers to review the document again. Waiting for promised reviews from Klaus Hartke, Carsten Bormann and Bill Silverajan.


* draft-tiloca-core-observe-multicast-notifications-02 --- This allows the distribution of resource updates over multicast, to a lot of subscribers all observing the same resource on the server. It aligns well with the pubsub scenario. The group of clients as a whole "controls" the multicast IP address and the Token value used for all the multicast notifications. This starts from a common "phantom request" as sent *from* the multicast IP address of the group, that the server creates, sends to itself and provides to the clients in an error response. Added also: discussion on congestion control; more explicit encoding of phantom request to the clients; cancellation of the group observation based on estimation of alive clients; retrieval of the phantom request in different ways, e.g. pub-sub when discovering a topic, or introspection during network debugging by querying the server. As next steps: think more about alternative serializations inside the error response.

    Current examples are mainly in CBOR, they can well be also in CoRAL. Thomas' error draft (now using CBOR) is somehow related with respect to the error response and may be considered. This is an interesting topic for an interim where to discuss relations among draft-fossati-core-coap-problem, draft-core-coap-pubsub and this draft draft-tiloca-core-observe-multicast-notifications.

    Jim Schaad would be interested to try and implement this when the details are more nailed down.

* draft-tiloca-core-groupcomm-proxy-00 --- This describes how handling a request from a client, that has to go through a proxy and be forwarded over multicast to multiple servers. This approach takes the responses from the different servers and send them back to the client individually (no aggregation). Group OSCORE is used for security. The client uses one new CoAP option to indicate to the proxy it is fine with all this. Each server uses a second new CoAP option, to indicate its own IP address all the way to the original client. The proxy identifies the client, set a timer for how long to wait for responses (observation is handled). Eventually, the client can retrieve the address of each of the servers from their response.

    Received a review from Christian Amsuess, now there are open points as to an alternative use of the two CoAP options and their properties. This seems also a use case opening for "nested OSCORE" between client and proxy. Main next steps are about addressing open points and Christian's review.

    The current approach seems to assume there is no address mapping involved, if the server provides its address but it's behind a NAT. The alternative approach suggested by Christian would address this.

## Other documents

* draft-bormann-t2trg-rel-impl-01 --- This defines diagnostic information about running implementation (not deployments), in a discoverable way. Good to checking that we have enough energy to do this. It's not about returning the actual information but a link to it, then we need a link relation type. The document defines this link relation type, not media types (yet), and gives security considerations (also a bit on DDoS mitigation). Possible relation also with draft-foudil-securitytxt , intended for reporting vulnerability. Need more discussion to decide if this document cover this aspect too.

    Asked to consider for adoption, if we agree that we don't have to go for media types now. Two people are in favour. Decided not to do adoption call right now, but to have more discussion on the list first.
    
* draft-bormann-core-responses-00 --- Different applications have come up with the need for unsolicited responses, not strictly triggered by a request. Sometimes these responses are even considered over multicast for observe notifications. The rationale for the server is: I send you this response as if you have sent a request to me. This involves also having some kind of agreement between client and server on the Token to use, through out-of-band agrement or new options. This is not about defining the protocol, but the model and the vision. Orthogonal problems to handle at this level are congestion control, message semantic and token space. It may be useful for this work to continue at this level too, rather than leaving individual use cases to find their way. It's mostly about responses to (not really happened) GET and FETCH requests. Worth checking what the WG should do. 

    The multicast notification work of draft-tiloca-core-observe-multicast-notifications relies on having a token space agreed for that, it's more efficient. This document instead is about contexts and usages that we have in mind, we may end up concluding that the multicast notification is the most useful to focus on.

    This may help also with the recent discussion from DOTS on particular usage of the Block2 option. If we need something working under attack like for DOTS, we may want to craft something specific for that use case, so probably this cannot be of general use.

    The discussion will continue on the list to identify the 2-3 use cases related to this, though they won't necessarily fit in the same detailed solution. This may lead to improve the current document.

## Resource Directory Discussion

* draft-ietf-core-resource-directory-24 --- The latest comprises points discussed at previous meetings. Got reviews from Secdir and Genart. The simple things are fixed. On DDoS it should be sufficient to point at recommendations from RFC 7252. Latest current text will be checked by Alexey. Need to add security considerations on simple registration coming from a fake sender. Need for guidance on randomly generated endpoint names, e.g. discussing their size, and on what can actually be used from a certificate. Jim Schaad, Alexey Melnikov and Michael Richardson can help with input on certificates.

    Still need to answer about authorization at the RD. Worth adding a short paragraph with guidance, e.g. on relevant documents/approaches that can me considered. Specific things can happen in other documents and groups. The RD is a protocol usable by different applications, with different authorization requirements. Those applications should not be defined in the main RD document. We have ACE as a possible thing to use, but the RD document should be free from this stuff.

    Wish for one or two separate information documents, covering certificate aspects and authorization. Even though in this way, at least one authorization approach has to be defined. If the model is "any device can just be unauthenticated and can modify settings for any other", then it is not going to work.
    
* draft-amsuess-core-resource-directory-extensions-03 --- The document describes things that are possible to do with the RD, as additional features and extensions, also to not slow down the main RD document. Examples are reverse proxy and lifetime age for RD replication. There are also more suggested points that might be of interest to the WG, asked people to provide feedback to possibly do/continue work on thos points. Some more things/features are not strictly addressed in this document but related, e.g. RD-DNS-SD, CoRAL reef, RD replication, group membership and protocol negotiation.

    Interesting points to consider seedm to be complex queries for the lookup interface and topics related to multicast. We can cover this at the upcoming virtual interims.

## CoRE Applications

* IANA registries clarification + link attribute registry --- No draft published yet, but the topic was discussed before. This is about link format and link attributes. Jaime started to collect link attributes on a HackMD. We don't have any IANA registry for them, but we do for other things. Plan to write a new informative draft as already discussed at interims, also to clarify expert review rules for what we have already, but also to create the registry for the link attributes. This is useful why not urgent. No objections, the direction sounds sensible, it is doable to have the draft for the next IETF.

* draft-ietf-core-coral and draft-ietf-core-href --- Published 2 revisions of the draft since last IETF. Lots of clarifications and details added. It might be useful if people could take a look now. Need one more revision before we can have an implementation version and do interop in an interim. One experiences overhead with respect to URIs, especially due to ":" and "/", it's just necessary overhead. Idea were presented for reducing that overhead. Open point if it is actually worth adding more encoding/decoding processing than one already has in CBOR, to avoid introducing a third encoding, but rather either stick to CBOR or reuse 7252 option encoding.

* draft-xxx-app , draft-hartke-core-apps-08 and draft-schaad-core-reef --- Trying to understand how the structure of these apps should look like. Klaus would like to have machine-readable descriptions from documents. Two main approaches may be followed. One is link-based, as HTML does. The second is more object-oriented, like the equivalent programming. If you go for the link way, you leverage relations and you know how to handle a link, e.g. as collection related. The object way makes think more of items with properties that you can access and delete. Three main applications to address now: 1) the pub-sub broker; 2) reef, essentially on how to use the RD; and 3) in the ACE working group, the Administrator client for the OSCORE Group Manager. There are lot of common points, that should be defined and documented once, to be reused. Comments? Preferred ways?

    Need to consider possible further patterns. Good to have some common guidance, especially to better move towards CoRAL. The reef content type schema is possible additional point, these things can go on the list. These points will be also become clearer after more discussion at the virtual interims.
    
* draft-fossati-core-coap-problem-02 --- This was presented also at a side-meeting in Singapore, now thinking more broadly of next steps. The goal is to standardize error reporting format for CoAP. Two different spaces/categories, i.e. global and local. Identify the error and common fields to support, then per-namespace extensions. Codepoints can be public or private, renumbering can happen smoothly when/if the API goes public. We have open issues on localization (default language, language tags), and private-to-public migration plan. We have one more open point on having the diagnostic payload under the problem structure.
 
    Open questions: Is this common enough and needed enough as usage pattern? Do we need to standardize this? Is this ready for adoption? CoRAL or not CoRAL?
    
    4 people plus authors read the draft; 3 people would support adoption. We will bring this to the list.
    
* draft-bormann-core-senml-versions-01 --- Asked to start an adoption call.

    Six people would support adoption. None is against. We will raise call for adoption on the list.
    
* draft-ietf-core-senml-data-ct-01 --- No time left for discussion. This will be covered at the virtual interims.


---
# Meeting Minutes

# WEDNESDAY, April 08, 2020

13:00-15:00 UTC


Note takers: Francesca, Amelia, Marco, Jaime
Jabber scribe: Jaime, Marco
Queue manager: Jaime, Marco


Numbers in parentheses are minutes of time allocated.

## Intro (10) 13:00

Note well presented. 

Agenda reviewed (no objections).

Introducing Marco as new chair. Welcome Marco, thank you Carsten!
New AD: Barry.
New: interims every other week. Time will be 14:00UTC and meeting docs will available at core-wg.github.io 

  * WG and document status
    * Published:
        * multipart-ct-04: RFC 8710 !!
        * hop-limit-07: RFC 8768 !!

    * RFC-Editor's Queue:
        * draft-ietf-core-senml-etch-07
        * draft-ietf-core-senml-more-units-06
    
    * IESG Processing:
        * draft-ietf-core-resource-directory-24: In Last Call
            * draft-ietf-core-stateless-05: In Last Call
      
    * In Post-WGLC processing:
      * draft-ietf-core-echo-request-tag-09

    * WGLC to be issued:
      * draft-ietf-core-dev-urn-04

## CoRECONF cluster (Ivaylo) (15) 13:18

  * draft-ietf-core-yang-cbor-12 --- Ivaylo
  * draft-ietf-core-yang-library-01 --- Ivaylo
  * draft-ietf-core-comi-09 --- Ivaylo
  * draft-ietf-core-sid-12 --- Ivaylo

Objectives:

  - Outcome of WGLC, possible discussion on relevant issues
  * draft-ietf-core-sid-12 --- Ivaylo
    
All remarks are still not processed. 

Carsten Bormann (CB): the intention is that we are doing the same thing we would be doing in the early allocation process. Is that correct representation?
Ivaylo: yes
CB: then we probably need a little bit of text because the early allocation is aimed at IESG and DE does not operate exactly how IESG does. Need text for that.
Esko: You don't need an early allocation anymore because you get a quick allocation now. 
CB: Bug or feature? Early allocations are reviewed after a year and go away if nothing happens. Provisional allocations would be very quick and get back them back if nothing happens, which is different than permanent.
Esko: OK, I see the intention.
CB: SIDs aren't quite as scarce as other things we're seeing in allocation. Was just trying to explain what we gain by having an early allocation process.
Ivaylo: Let's continue discussion on mailing list. 
Jaime: continue the discussion in the mailing list, pretty mature and no major things.
Ivaylo: yes.


  * draft-ietf-core-yang-cbor-12 --- Ivaylo
  
Do we want to have normative references from CBOR to SID or the other way around? 

Jaime: You have to submit another version of this document regardless. Do people have opinions on normative references?
Ivaylo: Yes.
CB: I have very strong opinions on normative references. In the past normative references that were not necessary caused big delays to our work. Since YANG-CBOR is a free-standing document, even if it sits on YANG, it doesn't need all the other machinery that we are creating. Let's try to process with a minimal amount of normative references, keeping in mind that the document should be free-standing in the sense that someone who just wants to use YANG-CBOR can do that without referencing other docs.
Jaime: did you reply to Tom Petch for the feedback he gave for this?
Ivaylo: I might have missed it?
Jaime: let's make sure all comments are adressed in next resubmission.

  * draft-ietf-core-comi-09 --- Ivaylo
  
It is not clear whether Security Considerations really need to very extensive, or whether a more general observation is acceptable that authorization requires care.

No further discussion.

  * draft-ietf-core-yang-library-01 --- Ivaylo

Jaime: Actually the comment from Tom Petch was here, not on CBOR. Do you have a time-line for resubmissions?
Ivaylo: Will probably have all the editorial changes by tomorrow or end of the week. The other changes depend on the level of detail required to solve concerns. The SID-draft may take longer time to work out than the others. We are hopeful it will not be a big delay.
Jaime: Bear in mind to send the latest versions to other potential reviewers who may be interested. We will do another WGLC when the new documents are submitted.

## Groupcomm (Marco, Christian, Esko) (60) 13:44

* draft-ietf-core-groupcomm-bis-00 (10) --- Esko

    Objectives:
    
    - Discuss updates (addressed reviews and closed TBDs)
    - Discuss open points (handling different group types, reusage of tokens for observation, explicit signaling of multicast messages)
    - Ask for reviews
    
Esko: intended to obsolete RFC 7390, updating RFC 7252 and 7641; insecure and secure (with Group OSCORE) communication are in scope
Esko: Taken care of Jim's and Thomas's reviews, improved definitions, discussed group discovery with the RD, improved security considerations
Esko: Distinction between CoAP/OSCORE/Application groups, they use different types of identifiers, example figure
Esko: open issue #1 on Github, the port number may change in the server response compared to the port number of the multicast request, discussed on the list
Esko: open issues #26 and #35 on Gitlab, on using URI-Host for identifying application group and for consistency requirements for suppression of responses
Esko: Next steps are working on the open issues and process last review comments. Test selected functions in CoAP implementations. 

Jaime: issue 35 what is that?
Esko: a non WG-adopted draft issue, see https://gitlab.com/crimson84/draft-groupcomm-bis/issues.
Jaime: reviews by Thomas and Jim, sufficient or more reviews needed?
Esko: Always good with more reviews. Maybe next update.
Jaime: Any volunteers to review current or next version? Please indicate in chats on Webex or jabber. 
Christian Amsuess , Jim and Thomas Fossati volunteer for next version. 

* draft-ietf-core-oscore-groupcomm-08 (15) --- Marco 13:55

    Objectives:
    
    - Discuss updates (addressed review, sec con, optimized and pairwise mode)
    - Discuss open points (support for pairwise mode, Sender ID for silent servers, remove IANA registries from signature+key params, appendix E.2 on client sequence number)
    - Ask for reviews

Marco: We hope to do more testing of message protection, and then to go to WGLC
Jim: number of issues. sl.10. Basenline sync, it should be optional to discard the first baseline request. If you do pairwise: problem with EdDSA MTI since both montgomery and edwards implementation would have to be MTI in HW.
Christian: E2 appendix: careful to differentiate between application's freshness requirements and requirements for reusing the sequence number.
Jim: draft in LWIG that talks about EdDSA with a mapped coordinates where you can do both key agreement and signing, which could become the MTI -- https://datatracker.ietf.org/doc/draft-ietf-lwig-curve-representations/
Francesca: there is a discussion in the mailing list on making this document update OSCORE. : There's a requirement of HMAC-based HKDFs in OSCORE, which may not really be necessary. Could have sentence in Group OSCORE about "Any [H?]KDF is fine"; is doing it in this document the best option? Want to do it fast, but if it's in this document there'll be an "Updates" link that gives the wrong impression of Group OSCORE being mandatory for OSCORE now.
Jim (on Jabber): I have succesfully done the multicast + observe as well
Jaime: If anyone wants to review, say now. 
Christian (on jabber): raises his hand for reviewing the next version of groupcomm


* draft-tiloca-core-oscore-discovery-05 (10) --- Christian 14:16

    Objectives:
    
    - Discuss updates (addressed review, registration of link to AS, examples in CoRAL)
    - Discuss open points (no re-introduction of group member registration --- BACnet example)
    - Solicit reviews

Christian: just deployed nodes may miss information on how to join an OSCORE group through the Group Manager (GM). Then we use the CoRE Resource Directory (RD), it works even if the GM is not deployed yet.
Christian: addressed Jim's review, added to the link to the group also the link to the ACE Authorization Server associated to the GM. This spares the client from an unouthorized access just to learn of the AS.
Christian: clarified relation between application and security groups (but still to finalize across documents)
Christian: Examples added also in CoRAL, the link to the AS cannot be formally "navigated", it's metadata.
Christian: we have a long example from BACnet, where devices start from scratch. Right now the RD is not expressing nodes' membership to a group, but this example is doing that out of the blue. It's just an example though. Better to just pull that part of the example out or can confuse, can be defined just in a separate document.
Christian: we got 1 of the promised reviews, we would need more.

Jaime: on the first example, that's a registration?
Christian: yes, it would look very similar in a look up
Jaime: on the payload?
Christian: on the payload the GM announces one of its join resource, to join one of its OSCORE groups?

Jaime: in the payload the group and the token to register with?
Christian: the AS.

Jaime: volunteers to review. Jim volunteers on Jabber.


* draft-tiloca-core-observe-multicast-notifications-02 (15) --- Christian 14:26

    Objectives:
    
    - Discuss updates (congestion control, error response encoding, observation cancellation, alternative retrieval of phantom request)
    - Discuss open points (rough client counting, alternative encoding)
    - Ask for reviews

Christian: allow the distribution of resource updates over multicast, to a lot of subscribers all observing the same resource on the server. Aligns well with pubsub.
Christian: the group of clients as a whole "controls" the multicast IP address and the Token value used for all the multicast notifications.
Christian This starts from a common "phantom request" as sent *from* the multicast IP address of the group. The server creates it and sends it to itself. Then it's serialized and sent to the clients to align them, as included in an error response to the clients as they come to try observing.
Christian: added discussion on congestion control, more explicit encoding of phantom request and other information inside the error response to the clients
Christian: described alternatives to retrieve the phantom request in different ways, e.g. pub-sub when discovering a topic, or introspection during network debugging by querying the server

Jaime: related to Thomas's error response draft. are you aware of that draft?
Christian: yes, not exactly the same problem but may be possibly considered. 
Jaime: do you have CBOR or CoRAL examples?
Christian: now mainly in CBOR, pointing that they can well be also in CoRAL.
Thomas: the last "problem draft" is also mainly in CBOR.
Jaime: sounds like an interesting topic for an interim. We need to schedule a discussion for later on, on the connection between different documents: draft-fossati-core-coap-problem, draft-core-coap-pubsub and this draft draft-tiloca-core-observe-multicast-notifications.
Christian: then it's about how the server can cancel a group observation. We propose a CoAP option that the server can use to communicate and update its own estimation of the group size. If the updated count falls below a threshold, the server can cancel the group observation. 
Carsten: you may make a probabilistic estimation on the group head.
Christian: isn't this what we are doing?
Carsten: you may send a sense to select a small subgroup to send a response. You need to maintain a group size estimate at the group head. Based on that, you can choose the size of the head.
Christian: pretty much what we are doing, we just describe it based on random events to fall within a range.
Carsten: that's good.
Christian: we want to spend more time thinking about alternative serializations inside the error response, possibly with more serialization of content intended to go on the wire.
Jim (on jabber): It will be interesting to try and implement this when the details are more nailed down.
Jaime: I have no additional comments. If no one else has any comments maybe we can move on. We will have to move some stuff until Thursday.


* draft-tiloca-core-groupcomm-proxy-00 (10) --- Esko 14:44
    Objectives:
    
    - Present new work
    - Christian's comments on the list
    - Ask for reviews

Esko: handling a request from a client, to go through a proxy and forwarded over multicast to multiple servers
Esko: we condsider an approach where the responses from the different servers are sent back to the client individually (no aggregation). Group OSCORE is used for security.
Esko: the client uses one new CoAP option to indicate to the proxy it is fine with all this. Each server uses a second new CoAP option, to indicate its own IP address all the way to the original client.
Esko: presenting the two new options and their properties.
Esko: presenting the workflow, client --> proxy (which identifies the client, set a timer for how long to wait for responses, observation is handled) --> server --> proxy --> client (that can retrieve the address of each of the servers from their response).
Esko: got a review from Christian, we have open points as to an alternative use of the two options and their properties; it seems also a use case opening for "nested OSCORE" between client and proxy
Esko: main next steps are about addressing open points and Christian's review.
Jim: this seems to assume there is no address mapping involved, if the server provides its address but it's behind a NAT
Marco: the alternative approach suggested by christian would address this.
Esko: If the proxy is also the nat, the client can reach the proxy then through the proxy it can access the devices even if the addresses are changed. 
Christian: the client has to find out anyway in some way that that particular address is usable. It's premature to think of this particular interactions. Addresses that come back even from a proxy will make sense.

Jaime: We don't have any time for further presentations so we will have to move them to the next session. Thank you all for your time! Hope to see you next Thursday at the same time.



Σ 120



# Thursday, April 16, 2020

13:00-14:30 UTC

Note takers: Thomas, Marco, Jaime
Jabber scribe: Jaime, Marco
Queue manager: Jaime, Marco

Numbers in parentheses are minutes of time allocated.

## Intro (5)

## Other (Carsten, Christian) (15):

* draft-bormann-t2trg-rel-impl-01 (10) --- Carsten 13:05

   Objectives:
     * Relation-only vs. add a media-type or two as well?
     * Ready for WGA?

Carsten: diagnostic information about running implementation in a discoverable way. Thecking that we have enough energy to do this. It's not about returning the actual information but a link to it, then we need a link relation type. The document defines this link relation type, not media types (yet), and gives security considerations (also a bit on DDoS mitigation).

Carsten: Possibly related with the controversial proposal draft-foudil-securitytxt , intended for reporting vulnerability. Should this document cover this too?
Michael R: great idea, security should be covered, I'm concerned of HTML (don't want to have the ability to inject JS)
Christian: if CoAP is used for DDoS, this can be used to pin down the implementations that need upgrading/fixing
Christian: fine with all media types, further discussion can be there
Klaus: if I run a libcoap server, I assume the link would point to the libcoap homepage? does this help with discovering who's responsible for enabling the amplification attack?
Christian: At least it's some information; expect that a CoAP library's "libcoap/version" would be set to something application specific in most cases.
Klaus: it's interesting and useful to discuss
Jaime: on the security part, it's just a list of emails about the persons responsible for security. is this something to be provided by companies and manufacturers of devices?
Carsten: it's about implementation information, not deployment
Jaime: for the security part, you have pointers to persons aware/related to security reporting
Carsten: I'd like to separate implementation info and deployment info (e.g. firewall configuration), for now I don't think we can go that far with the latter.
Carsten to Michael: What is the relationship between this an MUD?
Michael R: even if you can't retrieve, you may examine and know who built it
Michael R: I'd discourage putting *only* libcoap in there: we want to know who uses the library, not the library itself
Carsten: if we agree that we don't have to go for media types now, I ask for adoption
Jaime: let's not do adoption call right now, move it to the list (mcr and ca in favor from the Jabber)

(I don't object to libcoap/x.y.z, I just don't want that to be *all* that there is.
I don't mind of libcoap tries to determine ARGV[0], if this was Unix of the program, or also utsname)

* draft-bormann-core-responses-00 (5) --- Christian 13:21

    Objectives:
    
    * Warm-up the draft again, in the light of the latest discussions on the list about blockwise transfer with unsolicited responses.

Christian: different applications have come up with the need for unsolicited responses, not strictly triggered by a request. Sometimes these responses are even considered over multicast for observe notifications. The rationale for the server is: I send you this responses as if I had if you have sent a request to me. This involves also having some kind of agreement between client and server on the Token to use, through out-of-band agrement or new options. I think this work should continue at this level too, rather than leaving individual your cases to find their way. It's mostly about responses to (not really happened) GET and FETCH requests. What should we do about this?
Jaime: what is the state?  Expired right?
Christian: yes, since 1 year
Carsten: there's an alternative as a lo-hanging fruit. it's not about defining the protocol, but the model and the vision here. Happy to re-open the discussion again and improve the document.
Christian: recent mail from DOTS, on particular usage of Block2. This may be a way to help.
Göran: how does this relate to the work on multicast notification?
Carsten: this is part of the discussion. multicast notification relies on having a token space agreed for that, it's more efficient. We are discussing contexts and usages that we have in mind, we may end up concluding that the multicast notification is the most useful to focus on. On the block2, if we need something working under attack, waht DOTS people need, we may want to craft something specific for that use case, so probably this cannot be of general use.
Christian: congestion control use, message semantic and token space are three orthogonal problems all related to this.
Carsten: let's continue on the list and identify the 2-3 use cases -- they won't necessarily fit in the same solution


## Resource Directory Discussion (Christian) (10) 13:30

* draft-ietf-core-resource-directory-24 (5) -- Christian

     Objectives:
    
     - Discuss RD GENART comments. 
     
Christian: version -24 comprises points discussed at previous meetings. We got two reviews, i.e. Secdir and Genart. The simple things are fixed. On DDoS it should be sufficient to point at recommendations from RFC 7252. Need more sec cons on simple registration coming from a fake sender.
Carsten: from a procedural pov so we don't create a dependency, it is sufficient to point to the relevant section in 7252 -- even though it's a bit inefficient, it works.
Christian: need guidance on ramdomly generated endpoint names, e.g. discussing their size.
Jaime: is endpoint name or the security context that is used for identification?
Jaime: also dev URN draft provides a possible solution to the problem of picking unique endpoint names
Christian: need for feedback/guidance about what can actually be used from a certificate
Jim (on Jabber):  I could provide some of this help
Alexey (on Jabber): I can help with X.509 related stuff [Also MCR]
Carsten: I think it's misguided to have anything in this document talking about certificates. Not happy of having a separate later document, though maybe there's a reason. The RD is a protocol usable by different applications, with different authorization requirements. Those applications should not be defined in this document. We have ACE as a possible thing to use, but the RD document should be free from this stuff.
Jim (on Jabber): +1 on not making it specific on how to do the authorization policy and naming in it
Christian: personally I'd be happy to get rid of all that, but there's the question about the authorisation model that we still need to answer; maybe this is for the application to define
Jaime: maybe worth adding a short paragraph with guidance, e.g. on relevant documents/approaches that can me considered. Specific things can happen in other documents and groups.
Alexey: need to re-read the current text, I will do in a couple of days
Berry: just following the discussion and waiting for results
Jim (on Jabber): one or two Informational documents on some *ways* might be valuable.
Alexey (on Jabber): Yes, at least one way has to be defined. If the model is "any device can just be unauthenticated and can modify settings for any other", then it is not going to work


* draft-amsuess-core-resource-directory-extensions-03 (5)  --- Christian 13:43

    Objectives:
    
    - Ask which parts WG is interested in.

Christian: the docuemnt describes things that are possible to do with the RD, as additional features and extensions, also to not slow down the main RD document, e.g. reverse proxy, lifetime age for RD replication (see slides).  The doc contains a bunch of suggestions that might be of interest to the working group. I'd like for people to read it and tell me whether there's shared interest to do/continue work on one or more topic. Some things/features are not strictly in this document (outside the bag), e.g. RD-DNS-SD, CoRAL reef, RD replication, group membership and protocol negotiation.
Jaime: some of the points there will be discussed later in the session.  Complex queries for the lookup interface would be something that I'd be interested in, but I'm not sure it is in your doc.   Other topics of interest for me are the multicast ones.   Maybe something to talk through in the upcoming interim meetings.


## CoRE Applications (Christian, Klaus, Thomas, Jim) (45) 13:50

* IANA registries clarification + link attribute registry (5) --- Klaus

    Objectives:
    
    - Check status and plan on document about parameter registration.

Klaus: there's no draft about this yet, but the topic was discussed before. This is about link format and link attributes. Jaime started to collect link attributes on a HackMD. We don't have any IANA registry for them, but we do for other things. I plan to write a new draft already discussed at interims, also to clarify expert review rules for what we have already, but also to create the registry for the link attributes. No draft text yet due to lack of time.
Jaime: I find this useful, it's a recurring problem.
Klaus: yes, useful but not urgent, that's why going slow.
Jaime: this doc status would be?
Klaus: informative
Jaime: Any negative opinion on this?
Klaus: it was discussed before, it's really about having a document written to be considered for adoption
Alexey (on Jabber): the direction sounds sensible so far
Jaime: so we can have it for the next IETF
Klaus: yes, that'd be nice

* draft-ietf-core-coral, draft-ietf-core-href  (10) --- Klaus 13:55

    Objectives:
    
    - Updates on coral and href latest versions.

Klaus: since last IETF, 2 revisions of the draft. Lots of clarifications and details added. It might be useful if people could take a look now.  Need one more revision before we can do an implementation draft and do interop in an interim.
Klaus: one experience overhead with respect to URIs, especially due to ":" and "/", it's just necessary overhead. Presenting idea for reducing the overhead.
Carsten: I wonder if it is actually worth adding more encoding/decoding processing than one already has in CBOR; we shouldn't introduce a third encoding: either stick to CBOR or reuse 7252 option encoding 


* draft-xxx-app , draft-hartke-core-apps-08 and draft-schaad-core-reef: (Jim, Klaus, Christian) (20)  14:08

    Objectives:
    
    - Discuss ways of representing RD in CoRAL; Christian vs. Jim vs. Klaus

Jim: i'm trying to understand how the structure of these apps should look like. Klaus would like to have machine-readable descriptions from documents. Two main approaches may be followed. One is link-based, as HTML does. The second is more object-oriented, like the equivalent programming. If you go for the link way, you leverage relations and you know what to do a link, e.g. this is related to a collection. Thinking in an object way, you more of items with properties that you can access and delete.
Jim: we have three main applications to address now: 1) the pub-sub broker; 2) reef, essentially on how to use the RD; and 3) in the ACE working group, the Administrator client for the OSCORE Group Manager. There are lot of common points, that should be defined and documented once, to be reused. Comments? Preferred ways?
Michael Koster: are there other patterns?
Jim: maybe, happy to listen to more ways
Michael Koster: how do you want to deal with the high-level resource represented at the collection?
Jaime: good to have some common guidance, especially to better move towards CoRAL
Thomas: could you elaborate on diffences/similarities, also in terms of open API?
Jim: no, I don't know them well enough
Klaus: with open API ???, with hypermedia we discover anything else from server responses
Jim: there's also the reef content type schema as possible additional point, these things can go on the list
Michael Koster: I agree to come with some common thing
Jaime: it will be also become clear after the interims


* draft-fossati-core-coap-problem-02 (10) --- Thomas 14:19

    - Is this ready for WG adoption?

    Objectives:
    
    - TBD
    
Thomas: presented also at a side-meeting in Singapore, now thinking more broadly of next steps. The goal is to standardize error reporting format for CoAP. Two different spaces/categories, i.e. global and local. Identify the error and common fields to support, then per-namespace extensions. Codepoints can be public or private, renumbering can happen smoothly when/if the API goes public.
Thomas: open issues on localization (default language, language tags), private-to-public migration plan. One more open point on having the diagnostic payload under the problem structure. is this as usage pattern common enough and needed enough?
Thomas: do we need to standardize this? ready for adoption? CoRAL or not CoRAL?
Jaime: impressions on who read the draft and would support adoption? Will bring this on the list --- 4+authors read it and 3 supporting adoption

## SenML (Carsten) (15)

* draft-bormann-core-senml-versions-01 (7.5) --- Carsten 14:29

    Objectives:
    
    - Checkpoint and way forward
    
Carsten: can we start adoption on this?
Jaime: how many have read the draft? --- 2 on webex and 4 on jabber are fine with adoption
Jaime: anyone against adoption? --- none against
 six for adoption
Jaime: will raise call for adoption on the list


* draft-ietf-core-senml-data-ct-01 (7.5) --- Carsten

    Objectives:
    
    - Solutions for the challenges with mixing mandatory-to-understand safe-to-ignore SenML fields.

Not discussed today, will be at interims.


## Flextime (0)

Σ 90
