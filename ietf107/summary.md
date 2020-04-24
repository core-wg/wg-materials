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
: Wednesday (2020-04-08, 2 h): https://ietf.webex.com/recordingservice/sites/ietf/recording/playback/a9451b0acbba4e55b077165599c3a206
: Thursday (2020-04-15, 1.5 h): https://ietf.webex.com/recordingservice/sites/ietf/recording/playback/28f3df710e074dc69b4653618ad46465

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