0.1.2 Core@IETF105 agenda

# Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Jaime Jiménez (not present)
* Francesca Palombini (stand-in, thank you!)
* Carsten Bormann

Numbers in parentheses are minutes of time allocated.

Please note: Side meeting on CoRE applications:  
TUESDAY, July 23, 2019 1520-1650 Collier



# TUESDAY, July 23, 2019
1710-1810 Duluth

(conflicts with 6man, tls; Absent: ...)

## Intro (10)

  * WG and document status
     * Published: 	draft-ietf-core-object-security-16 ➔ RFC 8613
     * In IESG processing:
       * draft-ietf-core-multipart-ct-03  	IESG Evaluation::Revised I-D Needed
       * draft-ietf-core-resource-directory-23  	Publication Requested
       * draft-ietf-core-senml-etch-04  	Publication Requested
     * In Post-WGLC processing:
       * draft-ietf-core-stateless-01
       * draft-ietf-core-echo-request-tag-05
       * draft-ietf-core-hop-limit-04
     * In WGLC (maybe):
       * draft-ietf-core-dev-urn-0_4_
  * Quick recap of related work, pointers

## CoRE applications


* draft-ietf-core-rd-dns-sd-05 (Peter) (15)   
  Objectives: run through example, DNSSD discovery of RD via DNS

* draft-ietf-core-coap-pubsub-08 (Michael? Klaus?) (15)

* draft-ietf-core-dynlink-09 (Michael? Klaus?) (5)


## Documents nearing WGLC


### CoRECONF cluster (15)

* draft-ietf-core-yang-cbor-10
* draft-ietf-core-comi-06
* draft-ietf-core-sid-07
* draft-veillette-core-yang-library-05 (in WGA call until 2019-07-18)

Objectives:

- check for any netconf/netmod/yot input that needs to be processed now
- clear any remaining hurdles to WGLC (with netconf/netmod involved)

Σ 60



# THURSDAY, July 25, 2019
1000-1200 Duluth

(conflicts with tsvwg, tls; Absent: ...)

## Intro (5)


## Groups

* draft-ietf-core-oscore-groupcomm-05 (15) Tiloca
    * Latest updates (signed OSCORE option; 2 external_aad; extended sec cons)
    * Discussion - Signature algorithm to use/mandate (issue #7 on Github).
    * Report from Hackathon.
    * Ask for WGLC.

* draft-tiloca-core-oscore-discovery-03 (10) Tiloca
    * Overview of latest updates.
       - Step-by-step example aligned with practical installation procedures.
       - New link target attributes, related to parameters newly defined in ACE
         https://tools.ietf.org/html/draft-ietf-ace-key-groupcomm-oscore-02
         https://tools.ietf.org/html/draft-ietf-ace-key-groupcomm-02
    * Registration of link target attributes such as "oscore-gid" and
      "app-gp" (in what registry?), also related to
      https://hackmd.io/AfjWKj7rRDiQl16WSSIa4w?both
    * Check status of ongoing reviews and way forward.

* draft-tiloca-core-observe-multicast-notifications-00 (15) Tiloca
    - presenting the new idea
    - getting feedback especially thinking of the ["Pub-Sub and Multicast" discussion][1]
    - asking for document reviews

[1]: https://github.com/EricssonResearch/coap-pubsub-profile/blob/master/Pubsub-multicast.pdf

* draft-dijk-core-groupcomm-bis-01 (15) Dijk (Remote presentation)
    * Overview of latest updates (-01)
    * Explain scope and approach of document ( Standards track - Obsoletes: 7390 ; Updates: 7252, 7641, 7959 )
    * Get feedback/consensus if the current approach is right

## SenML

* draft-keranen-core-senml-data-ct-02 (In WG Adoption call until
  2019-07-17) (10)

* draft-tschofenig-core-senml-lbn-00 (Hannes) (10)?

* draft-bormann-senml-more-units-00 (Ari) (10)?


## Related:

* draft-jarvinen-core-fasor-02	ipr (WGA???) (5)?

## Flextime (25)

Σ 120

<!-- 

# IETF 104:

	draft-dorfner-core-simplemetadata	-01			2019-03-24  
	draft-bormann-core-ace-aif	-06			2019-03-29  
	draft-amsuess-core-accept-any	-00			2019-03-25  
	draft-amsuess-core-rd-replication	-02			2019-03-11  
	draft-amsuess-core-resource-directory-extensions	-00			2019-01-10  
	draft-bhattacharyya-core-a-realist	-02			2019-02-05  
	draft-djamaa-core-proactive-rd-discovery	-00			2019-04-01  

	draft-bormann-senml-more-units	-00			2019-02-27  

	draft-ietf-core-interfaces	-14			2019-03-11  	Active

# Unrelated to CoRE:

	draft-yangcan-core-web-software-built-in-cloud	-01			2019-04-25  
	draft-urien-core-blockchain-transaction-protocol	-02			2019-03-04  
	draft-urien-core-identity-module-coap	-06			2019-06-28  
	draft-urien-core-racs	-13			2019-06-14  

 -->
