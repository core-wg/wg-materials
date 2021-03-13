# Meeting summaries

## CoRE @ IETF 110 (Virtual): Summary and Minutes

The core WG held two virtual sessions during IETF 110 held online.

---

The minutes for the two CoRE sessions are available at:

https://datatracker.ietf.org/meeting/110/session/core

https://codimd.ietf.org/notes-ietf-110-core

Thanks to the note takers Michael Richardson, Göran Selander and Rikard Höglund!

---

The recordings of the two CoRE sessions are available at:

[Monday, March 8, 2021]
https://www.youtube.com/watch?v=GteEGOyW5JI

[Friday, March 12, 2021]
https://www.youtube.com/watch?v=VKhUnOji8XA

---

Slides for the two CoRE sessions are available at:

* https://datatracker.ietf.org/meeting/110/session/core

* https://github.com/core-wg/wg-materials/tree/master/ietf110/slides

# Summary

## WG and document status

Carsten Bormann standing in as chair for Jaime during IETF 110.

Thanks to Barry Leiba as outgoing AD, welcome to Francesca Palombini as new AD.

* Published
    * RFC 8974 (was draft-ietf-core-stateless)

* RFC Editor Queue
    * draft-ietf-core-dev-urn-11

* IESG Processing:
    * draft-ietf-core-resource-directory-28: Approved-Announcement Sent
    * draft-ietf-core-echo-request-tag-12: Approved-Announcement to be Sent::Revised ID Needed

* In Last Call
    * draft-ietf-core-yang-cbor-15:  In Last Call, until 2021-03-17
    * draft-ietf-core-sid-15:  In Last Call, until 2021-03-17

* In Post-WGLC processing:
    * draft-ietf-core-yang-library-03: waiting for shepherd write-up
    * draft-ietf-core-comi-11: waiting for shepherd write-up
    * draft-ietf-core-oscore-groupcomm-11: processed WGLC comments and one more review; ongoing work on open points
    * draft-ietf-core-senml-data-ct-03: processed WGLC comments; synch with draft-bormann-core-media-content-type-format
    * draft-ietf-core-new-block-07: processed WGLC comments

## Groupcomm-bis

* draft-ietf-core-groupcomm-bis-03

Latest updates include: support for reverse proxies; caching of responses, with two types of cache entries at the proxy; a response validation model between client and servers with a new Multi-ETag option, and between client and proxy with a new Group-ETag option. Cacheability with end-to-end security is still possible using the deterministic requests of draft-amsuess-core-cachable-oscore.

It is preferable to move the new part on response validation to a different document, e.g. draft-tiloca-core-groupcomm-proxy. Next steps are about addressing open Github issues; moving some content to the rights places / different documents; implements aspects involving e.g. observe and blockwise.

## Group OSCORE

* draft-ietf-core-oscore-groupcomm-11

Latest updates addressed points raised at IETF 110 and from Christian's review at

https://mailarchive.ietf.org/arch/msg/core/pXEyxhbf-s2wgGDzrDhUNPsHZZc/

Two main open points remain.

1. Admit the recycling of Group IDs, as currently forbidden to avoid problems with long-living observations. This can rely on the Group Manager storing for each group member the GID used in the group when that member joined, and adapting group rekeying processes accordingly. No objection to this update.

2. Related to Github issues #72 and #73, on using the same identity key for both signing and Diffie-Hellman key derivation for the pairwise mode. Not really a common practice, need to be proven secure. Point originally raised by Ben Kaduk

   https://mailarchive.ietf.org/arch/msg/core/ujj_I-LlqW9fq__quh-YqKS0fF0/

   There's a pre-print in progress, to prove that the approach is secure, possibly after minor changes to the exact key derivation steps. A less preferable alternative is to have storage and provisioning of separate signing and Diffie-Hellman keys. More on this point in the next months.

Plan for v -12 is to address the two open points above. That should be a stable version, there are no other known issues.

## OSCORE Group Discovery

* draft-tiloca-core-oscore-discovery-08

This method uses the Resource Directory to discover links to an OSCORE group manager, hence to discover OSCORE groups and how to join them. The latest updates include information on the pairwise mode of Group OSCORE; consider also the signature verifier as possible client; revise the examples.

Marco's implementation has been tested against Christian's RD, covering all the steps defined in the draft.

https://bitbucket.org/marco-tiloca-sics/ace-java/src/master/src/test/java/se/sics/ace/interopGroupOSCORE/CoAPEndpointToResourceDirectory.java

coap://rd.coap.amsuess.com

The next version will have more security considerations and will align with latest additions to the RD document. Plan to integrate the individually implemented steps into the actual joining node and Group Manager. The document needs reviews.

## Multicast Notifications

* draft-tiloca-core-observe-multicast-notifications-05

This method enables a server to send multicast notifications to a group of clients. Possible to also use Group OSCORE. The server sends a phantom observation request to itself; observe notifications are responses to that request.

This version has a new encoding for informative error responses to the clients; a new encoding for expressing addressing information in the informative responses; optimization for a server self-managing its OSCORE group and for having the phantom request as a deterministic request (see https://datatracker.ietf.org/doc/draft-amsuess-core-cachable-oscore/). Next steps include considering also reverse proxies and deterministic requests used together with proxies. All main components are already in place.

In-room consensus for adoption: +13 in favor, no objections. To be confirmed on the mailing list.

Will review: Esko, Göran

Planned implementations: Christian, Marco

## Groupcomm proxy

* draft-tiloca-core-groupcomm-proxy-03

   - Discuss updates and open points

The document describes a signaling protocol with two new CoAP options, to enable proxies in group communication.

This last version has especially revised the encoding of server's addressing information conveyed in one of the options; and has added also support for reverse proxies (with two examples).

Appendix A defines "OSCORE in OSCORE" as useful here for the proxy authenticating the client before forwarding, but it is actually forbidden by RFC 8613. Now we have use cases for it, but it would require proper definition, analysis and update of RFC 8613.

Support to move out "OSCORE in OSCORE" and have it in a separate dedicated document. Possible collision of identifiers would be possible to address leveraging differences in transport information.

Next steps are about addressing raised points raised and covering the case where client and cross-proxy talk HTTP.

Earlier promised reviews: Christian and Carsten.

## Cacheable OSCORE

* draft-amsuess-core-cachable-oscore-01

This method enables caching of OSCORE-protected responses; all group members can act as a deterministic client with a well-known Sender ID and Sender Key. The exact encryption key is derived for each different request. The key derivation process is similar to the one in the pairwise mode of Group OSCORE. One trades some security properties with enabling cacheability. This also improves the way things work in https://datatracker.ietf.org/doc/draft-tiloca-core-observe-multicast-notifications/

During the hackathon, Marco and Christian interoped and decrypted each others' deterministic requests. Finding from the hackathon improved some design aspects, already in the editor's copy.

Next steps are more interop, process the feedback and then go for a proper review with security in mind.

## OSCORE with EDHOC

* draft-palombini-core-oscore-edhoc-02

This method combines the last EDHOC message to establish an OSCORE security context together with the first CoAP request protected with that OSCORE context.

The last version has determined one specific approach based on a new EDHOC option with zero-length; and added an optimization, i.e. only part of the EDHOC message goes on the wire, while the rest can be reconstructed by the server, saving at least 2-4 bytes.

Next will be to keep this in synch with the main EDHOC document; some specific point can better fit in this document.

In-room consensus for adoption: +9 in favor, one "not raise hand" (not against, but not sure either), no objection. To be confirmed on the mailing list.

## AEAD limits in OSCORE

* draft-hoeglund-core-oscore-key-limits-00
   
This considers the AEAD cipher limits defined in https://datatracker.ietf.org/doc/draft-irtf-cfrg-aead-limits/ , and defines additional actions for OSCORE. Need to count key usages and renew the OSCORE context of the two peers when a limit is passed. One limit 'q' is about performed encryptions with a key, while 'v' is about failed decryptions using a key. Plan to cover more algorithms than CCM_8 and give optimizations for constrained devices and implementation guidelines.
   
* https://mailarchive.ietf.org/arch/msg/core/h5JHgX5wTBkJtrKl_ezswiCdUBI/

The above is important to happen in OSCORE. Renewing the security context might also be useful to do for other reasons like for counteracting key compromise, especially if the rekeying provides perfect forward secrecy.

The original procedure used to compute the limit considers arbitrary assumptions that yield the actual limits now considered in the draft. It's also unfair to some particular algorithms. It would be good to have an overall revision of that procedure. OSCORE in particular may consider more appropriate values.

The possible revision of the procedure belongs to somewhere else; the document above can still recommend better values to use, with some short explanations.

## CORECONF Comi

* draft-ietf-core-comi-11

The CORECONF documents core-sid and core-yang-cbor are in last call. Got comments for core-sid on the intentional creation of a new global naming system; good to get views from the security community.

For core-comi issues came up during the shepherd write-up preparation: from netmod on incompatibility between uint8 and int8; string that may not be URL-safe; definition of "CBOR key"; key vs. CBORencode(key). Also required for minor clarifications when using blockwise transfers and pagination, and about leading zeros in base64 encoding of SID numbers.

A revised version is needed as addressing these points. Changes to the above encoding should not be an issue for implementations.

Then to be checked if a new Working Group Last Call is needed.

## SenML Versions

* draft-ietf-core-senml-versions-02

This version addresses comments from Jaime (e.g. approach to bitmapping a number). Ari added to his SenML validator the bit for additional units. Ready to move on.

We will start a Working Group last call.

## SenML Data CT

* draft-ietf-core-senml-data-ct-03

This version provides editorial clarifications and decompression bomb security consideration.

Still having a normative reference to draft-bormann-core-media-content-type-format (MCTP), which seems to require some time to become an adopted document, based on the Monday discussion in DISPATCH.

Proposed to remove MCTP as normative reference, and include into senml-data-ct only the minimal set of things needed from MCTP.

This seems good and straightforward, but better to first wait for more discussion in DISPATCH before deciding. The two documents can anyway separately proceed in parallel.

Next step is to have a a Pull Request on the senml-data-ct document to gain time and be ready to take the new direction.

## New Block

* draft-ietf-core-new-block-07

Addressed WGLC comments and further follow-up comments from Christian. Other than technical refinements, this version provides better clarifications on being specific for the DOTS use case.

Available implementation based on libcoap, to which a PR has been submitted. Has been tested in DOTS environment and behaving as expected.

Reviewers largely happy with the current version. This can be seminal material for a possible blockwise-bis.

The document will move forward; Marco will be shepherd and start the shepherd review and write-up soon.

## Dynlink (Bill)

* draft-ietf-core-dynlink-13

This version incorporates latest feedback also based on discussion at the latest interim.

The Conditional Attributes have been separated into Conditional Notification Attributes and Conditional Control Attributes. New attributes "edge" and "con" have also been added.

Required harmonization for the use of the attributes "band" and "con", having in mind the use that LwM2M does of the defined parameters.

http://www.openmobilealliance.org/release/LightweightM2M/V1_2-20201110-A/HTML-Version/OMA-TS-LightweightM2M_Core-V1_2-20201110-A.html#Table-512-2-lessNOTIFICATIONgreater-class-Attributes

The first part, about the parameters, is pretty mature now. The second part on the dynamic link concept needs more discussion and work. The two parts are independent.

Agreement in the group to split the current document into two different documents about the two different parts above. The dynlink document will be the one focused on the link material.

Work is needed also on covering a case with proxies, looking at interactions as end-to-end or hop-by-hop. So far the hop-by-hop approach has been privileged. In either case, the impact of possibly present proxies has to be considered.

## RD extensions and protocol negotiations

* draft-amsuess-core-resource-directory-extensions-05

* draft-amsuess-core-transport-indication-00

The first document defines RD extensions as to what you can do with the RD without changing the spec. This includes the reverse proxy extension, for asking the RD to provide a publicly reachable name and act as a reverse proxy. Often used (also during the IETF 110 hackathon); most of LWM2M uses a similar mechanism. The RD may also partially partner with a proxy.

The undesirable side effect is URI aliasing, which can be avoided if devices use the RD only as proxy. Similar problem in protocol negotiation case, coap+tcp:// and coap:// both collapse to a same resource.

To avoid that, the second document suggests an approach for proxy discovery. A server announces that it has a proxy at a location, by using link-relations. Everything hosted on this host is reachable via a specific proxy. No URI aliasing in the application (possibly only on the wire).

Next steps are to gather feedback, tuning relations, and update the RD extensions to show how it can be used. Some security considerations can be further elaborated by building on some from the HTTP working group.

## A Data-centric Deployment Option for CoAP

* draft-gundogan-core-icncoap-00

This draws parallels between ICN and CoAP deployments, already shared with the ICN community. ICN allows not specifying a server endpoint, but rather focuses on content delivery, using name-based stateful forwarding and content caching.

Possible to use object security end-to-end protection (also to cached content); all hops on the path creates state, which is consumed when a response traverses back. This can also prevent traffic amplification (DDOS). Caching is hop-wise, so retransmission can originate from any intermediate entity in the path, which reduces link traversals.

Tried already with OSCORE, using cacheable OSCORE, see https://datatracker.ietf.org/doc/draft-amsuess-core-cachable-oscore/. It worked quite good, with improvement of success rates in lossy network.

A related paper from 2020 considers a CoAP deployment similar to an ICN deployment using only standard CoAP features.

Most ICN systems support multiparty communication (mostly using request aggregation and response fan-out, or request fan-out and response deduplication). Ongoing work to provide more results with multi-party communication. Future work to allow dynamic proxy discovery. The Resource Directory can help to discover links and as announcement point for routes (especially to a particular good next-hop proxy).

This is an unconventional way of deploying CoAP but worth exploring in CoRE; it's not out of scope. It can also be discussed in T2TRG.

Since firmware update is a good use case, also the SUIT Working Group can be interested. This approach allows to retrieve an update from the closest location, rather than always from a certain update server.

For the multi-party case, there are building blocks for this too as work in progress in CoRE.
