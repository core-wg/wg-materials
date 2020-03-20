0.2 Core@IETF104 agenda

# Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Jaime Jiménez
* Carsten Bormann

Numbers in parentheses are minutes of time allocated.

# TUESDAY, March 26, 2019
1350-1550 Berlin/Brussels

(conflicts with anima, mls, tsvarea;
Absent: Michael Koster, Peter van der Stok)

## Intro (9)

  * WG and document status
     * Approved (in RFC-editor queue): 	draft-ietf-core-object-security-16
     * In IETF Last Call (ends 2019-04-08): 	draft-ietf-core-multipart-ct-03
     * Ready for WGLC:
       * draft-ietf-core-hop-limit-03
     * Ready for chairs' review, WGLC:
       * draft-ietf-core-dev-urn-03
  * Quick recap of related work, pointers

## Documents nearing WGLC

* draft-ietf-core-echo-request-tag-04: (10)
➔ WGLC! until 2019-04-17

* draft-ietf-core-stateless-01 (3): (Chairs' review? WGLC!)

## group communication: security and bis

* draft-ietf-core-oscore-groupcomm-04 (15): registry vs. cose-bis, what needs to be integrity-protected?
* draft-tiloca-core-oscore-discovery-02 (12): Points raised by Jim: Marco Tiloca

* draft-dijk-core-groupcomm-bis-00 (10): RFC7390 update (EXP!),
Discuss objectives, 10 minutes: Marco Tiloca; can we remove the REST
interface for managing groups as nobody is using it?

* pubsub security hallway meeting results (8) Francesca: summarize/discuss any results


## SenML

* draft-ietf-core-senml-etch-03 (10): Ari. WGLC will have closed 24:00 CET on Monday, March 25, 2019.  Please review.
* draft-keranen-core-senml-data-ct-01 (10): Ari.  Check for adoption.
Discuss potential fragmentation of SenML into many documents.
* draft-bormann-senml-more-units-00 (3): Carsten.  Adopt?

## CoRECONF

* draft-ietf-core-yang-cbor-07 (3): Ivaylo.
* draft-ietf-core-sid-05 (4): Ivaylo. (Get misunderstandings with IANA out of the way.)
* draft-ietf-core-comi-04 (3): 
* draft-veillette-core-yang-library-03 (4): Adopt?

## New work

* draft-bormann-core-media-content-type-format-00 (3) Worthwhile?
* draft-birkholz-core-coid-01 (5) will have been discussed in secdispatch on Mon 1350-1550


Σ 120

# FRIDAY, March 29, 2019
0900-1030 Grand BR

(conflicts with 6man, cacao BOF)

## Intro (5)

## CoRE Applications

* draft-ietf-core-coap-pubsub-08 (15):
(Changes still needed, left over issue: see github; new github version
by Monday! Michael Koster -> Friday)

* draft-ietf-core-dynlink-08 (5): Update now with clear separation; needs review -- close to WGLC

* draft-ietf-core-interfaces-14 (10): Last call for burying?

## CoRE Applications: RD

* draft-ietf-core-resource-directory-20 (20): WGLC til April 17th!
two interops done, meet again at IETF104 hackathon, report

* draft-ietf-core-rd-dns-sd-04 (10): Peter van der Stok; how to get DNS context into RD

* draft-amsuess-core-rd-replication-02 (3)
(Will have been discussed in T2TRG meeting, quick feedback)
* draft-amsuess-core-resource-directory-extensions-00 (5) Christian: \[5—10 optional]
target: informational; collection of things that might have been
specified in RD but don't need to be part of RD proper

* CoRAL side meeting results (7) Klaus: summarize/discuss any results

## New work

* draft-zcao-core-speedy-blocktran-00 (10)

Σ 90

# Hallway discussions envisioned

* protocol negotiation: Bill.
* on pubsub security: Francesca.
This work was done in ACE, but might fit better in CoRE than in ACE.
"group oscore" vs. the construction of pubsub.
Francesca: summarize hallway meeting if there is a result, 10 minutes

* observation and pubsub: Christian

## IETF103:
	draft-bhattacharyya-core-a-realist-02			2019-02-05
	draft-bormann-core-corr-clar-00			2018-10-23
	draft-hartke-core-apps-08			2018-10-22
	draft-jarvinen-core-fasor-01	ipr		2018-10-22
	draft-jhjung-core-sensor-streaming-00			2018-10-22
	draft-mattsson-core-coap-actuators-06			2018-09-17

## Unrelated:
	draft-yangcan-core-web-software-built-in-cloud-00			2018-10-23
	draft-urien-core-blockchain-transaction-protocol-02			2019-03-04
	draft-urien-core-identity-module-coap-05			2018-12-27
	draft-urien-core-racs-12			2018-12-12
