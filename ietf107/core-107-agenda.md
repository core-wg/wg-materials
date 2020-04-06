0.0.4 Core@IETF107 replacement meeting agenda

# Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Jaime Jiménez (jaime at iki dot fi)
* Marco Tiloca (marco dot tiloca at ri dot se)

Please note:

Jabber: xmpp:core@jabber.ietf.org?join
  * For the virtual microphone queue, you may want to say "help q"

Etherpad: https://etherpad.ietf.org/p/notes-ietf-107-core?useMonospaceFont=true

[Meeting 1] Date and time: 8th of April 2020, 13:00-15:00 UTC.
  * Webex link: https://ietf.webex.com/ietf/j.php?MTID=m355f196a763aa1549467110e081b5b76
  * Meeting number (access code): 616 017 942
  * Meeting password: constrained

  * Join by Phone: 1-650-479-3208 Call-in number (US/Canada)
  * Join by Phone: 1-877-668-4493 Call-in toll free number (US/Canada)
  * Access code: 616 017 942
  * Toll-free calling restrictions: https://www.webex.com/pdf/tollfree_restrictions.pdf


[Meeting 2] Date and time: 16th of April 2020, 13:00-14:30 UTC.
  * Webex link: https://ietf.webex.com/ietf/j.php?MTID=m5191b3eadadd36af2b5cbc2599bb3175
  * Meeting number (access code): 613 591 591
  * Meeting password: constrained

  * Join by Phone: 1-650-479-3208 Call-in number (US/Canada)
  * Join by Phone: 1-877-668-4493 Call-in toll free number (US/Canada)
  * Access code: 613 591 591
  * Toll-free calling restrictions: https://www.webex.com/pdf/tollfree_restrictions.pdf


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

## CoRECONF cluster (Ivaylo) (15)

  * draft-ietf-core-yang-cbor-12 --- Ivaylo
  * draft-ietf-core-yang-library-01 --- Ivaylo
  * draft-ietf-core-comi-09 --- Ivaylo
  * draft-ietf-core-sid-11 --- Ivaylo

Objectives:

  - Outcome of WGLC, possible discussion on relevant issues

## Groupcomm (Marco, Christian, Esko) (60)

* draft-ietf-core-groupcomm-bis-00 (10) --- Esko

    Objectives:
    
    - Discuss updates (addressed reviews and closed TBDs)
    - Discuss open points (handling different group types, reusage of tokens for observation, explicit signaling of multicast messages)
    - Ask for reviews

* draft-ietf-core-oscore-groupcomm-07 (15) --- Marco

    Objectives:
    
    - Discuss updates (addressed review, sec con, optimized and pairwise mode)
    - Discuss open points (support for pairwise mode, Sender ID for silent servers)
    - Ask for reviews

* draft-tiloca-core-oscore-discovery-05 (10) --- Christian

    Objectives:
    
    - Discuss updates (addressed review, registration of link to AS, examples in CoRAL)
    - Discuss open points (no re-introduction of group member registration --- BACnet example)
    - Solicit reviews

* draft-tiloca-core-observe-multicast-notifications-02 (15) --- Christian

    Objectives:
    
    - Discuss updates (congestion control, error response encoding, observation cancellation, alternative retrieval of phantom request)
    - Discuss open points (rough client counting, alternative encoding)
    - Ask for reviews

* draft-tiloca-core-groupcomm-proxy-00 (10) --- Esko

    Objectives:
    
    - Present new work
    - Christian's comments on the list
    - Ask for reviews

## SenML (Ari, Carsten) (35)

* draft-ietf-core-senml-data-ct-01 (10) --- Ari

    Objectives:
    
    - TBD

* draft-bormann-core-senml-versions-01 (15) --- Carsten

    Objectives:
    
    - TBD

* draft-keranen-core-senml-base-prefix-00 (10) -> 0??? --- Ari

    Objectives:
    
    - TBD

## If we have time:
 * draft-bormann-t2trg-rel-impl-01 --- Carsten

    Objectives:
      * Relation-only vs. add a media-type or two as well?
      * Ready for WGA?
    

Σ 120


# Thursday, April 16, 2020

13:00-14:30 UTC

Numbers in parentheses are minutes of time allocated.

## Intro (5)

## CoRE Applications (Klaus, Thomas, Ari, Jaime, Jim) (75)

* draft-ietf-core-coral, draft-ietf-core-href  (10) --- Klaus

    Objectives:
    
    - TBD

* draft-fossati-core-coap-problem-02 (10) --- Thomas

    * Is this ready for WG adoption?

    Objectives:
    
    - TBD

* Pubsub approaches: draft-ietf-core-coap-pubsub-NN (15) --- Jaime
    * https://hackmd.io/2eqcQ0tWRsGle090mQaJLw?view

    Objectives:
    
    - TBD

* (-) Parameter registration (10) --- Klaus

    Objectives:
    
    - Check status and plan on document about parameter registration.

* draft-amsuess-core-resource-directory-extensions-03 (5)  --- Christian

    Objectives:
    
    - TBD

* draft-schaad-core-reef: (Jim, Klaus, Christian) (25)

    Objectives:
    
    - Discuss ways of representing RD in CoRAL; Christian vs. Jim vs. Klaus

## Flextime (10)

Σ 90
