0.0.2 Core@IETF107 replacement meeting agenda

# Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Jaime Jiménez
* Marco Tiloca

Please note:

[Meeting 1]
Date and time: 8th of April 2020, 13:00-15:00 UTC
Webex link: https://ietf.webex.com/webappng/sites/ietf/meeting/info/12f03cd44d7d4079b925586135df03ee

[Meeting 2]
Date and time: 16th of April 2020, 13:00-14:30 UTC
Webex link: https://ietf.webex.com/webappng/sites/ietf/meeting/info/1ccf8929f40d4ff2a6ff4a6b46521a12

Jabber: xmpp:core@jabber.ietf.org?join

Etherpad: https://etherpad.ietf.org/p/notes-ietf-107-core?useMonospaceFont=true

# WEDNESDAY, April 08, 2020

13:00-15:00 UTC

Numbers in parentheses are minutes of time allocated.

## Intro (10)

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

## CoRECONF cluster (15)

  * draft-ietf-core-yang-cbor-12
  * draft-ietf-core-yang-library-01
  * draft-ietf-core-comi-09
  * draft-ietf-core-sid-11

Objectives:

  - Outcome of WGLC, possible discussion on relevant issues

## Groupcomm (Marco, Christian, Esko) (60)

* draft-ietf-core-groupcomm-bis-00 (10)

    Objectives:
    
    - Discuss updates (addressed reviews and closed TBDs)
    - Discuss open points (handling different group types, reusage of tokens for observation, explicit signaling of multicast messages)
    - Ask for reviews

* draft-ietf-core-oscore-groupcomm-07 (15)

    Objectives:
    
    - Discuss updates (addressed review, sec con, optimized and pairwise mode)
    - Discuss open points (support for pairwise mode, Sender ID for silent servers)
    - Ask for reviews

* draft-tiloca-core-oscore-discovery-05 (10)

    Objectives:
    
    - Discuss updates (addressed review, registration of link to AS, examples in CoRAL)
    - Discuss open points (no re-introduction of group member registration --- BACnet example)
    - Solicit reviews

* draft-tiloca-core-observe-multicast-notifications-02 (15)

    Objectives:
    
    - Discuss updates (congestion control, error response encoding, observation cancellation, alternative retrieval of phantom request)
    - Discuss open points (rough client counting, alternative encoding)
    - Ask for reviews

* draft-tiloca-core-groupcomm-proxy-00 (10)

    Objectives:
    
    - Present new work
    - Christian's comments on the list
    - Ask for reviews

## SenML (Ari, Carsten) (35)

* draft-ietf-core-senml-data-ct-01 (10)

    Objectives:
    
    - TBD

* draft-bormann-core-senml-versions-01 (15)

    Objectives:
    
    - TBD

* draft-keranen-core-senml-base-prefix-00 (10) -> 0???

    Objectives:
    
    - TBD

## If we have time:
 * draft-bormann-t2trg-rel-impl-01

    Objectives:
      * Relation-only vs. add a media-type or two as well?
      * Ready for WGA?
    

Σ 120


# Thursday, April 16, 2020

13:00-14:30 UTC

Numbers in parentheses are minutes of time allocated.

## Intro (5)

## CoRE Applications (Klaus, Thomas, Ari, Jaime, Jim) (75)

* draft-ietf-core-coral, draft-ietf-core-href  (10)

    Objectives:
    
    - TBD

* draft-fossati-core-coap-problem-02 (10)

    * Is this ready for WG adoption?

    Objectives:
    
    - TBD

* Pubsub approaches: draft-ietf-core-coap-pubsub-NN (15)
    * https://hackmd.io/2eqcQ0tWRsGle090mQaJLw?view

    Objectives:
    
    - TBD

* Parameter registration (Klaus) (10)

    Objectives:
    
    - Check status and plan on document about parameter registration.

* draft-amsuess-core-resource-directory-extensions-03 (5)

    Objectives:
    
    - TBD

* draft-schaad-core-reef: (Jim, Klaus, Christian) (25)

    Objectives:
    
    - Discuss ways of representing RD in CoRAL; Christian vs. Jim vs. Klaus

## Flextime (10)

Σ 90
