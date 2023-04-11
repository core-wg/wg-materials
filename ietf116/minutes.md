# IETF 116 - Agenda for Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

Please note:

Date and time: Tuesday, 28th of March 2023, 04:00 – 06:00 UTC

Meeting materials: https://datatracker.ietf.org/meeting/116/session/core

Notes: https://notes.ietf.org/notes-ietf-116-core

Meetecho video stream:
https://meetings.conf.meetecho.com/ietf116/?group=core&short=core&item=1

Meetecho for onsite participants:
https://meetings.conf.meetecho.com/onsite116/?group=core&short=core&item=1

Audio stream: https://mp3.conf.meetecho.com/ietf116/core/1.m3u

Zulip stream: https://zulip.ietf.org/#narrow/stream/core

* * *

# Tuesday, March 28, 2023

04:00 – 06:00 UTC

Minute takers: Christian Amsüss, Matthias Kovatsch

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (10)

* WG and document status

Presented slides:
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-chairs-slides-01.pdf

MT doing introductions.

MT: The CORECONF slot is moved to whenever Rob Wilton shows up.

MT: Document overview (p7..10)

* -sid in AD-Followup, completed third WGLC, close to fully addressing
  Rob's DISCUSS.
* -target-attr: publication requested (Shepherd: Marco)
* -comi: Authorship and shepherding changes; ongoing, will likely have a
  new WGLC
* -yang-library: will follow -comi
* -oscore-groupcomm: waiting for Shepherd write-up
* -groupcomm-bis: waiting for Chair Go-Ahead following WGLC (Shepherd to
  be Carsten)
* -conditional-attributes: Revision expected based on WGLC
* -oscore-edhoc: waiting for Chair Go-Ahead following WGLC (Shepherd to
  be Carsten)

MT: Other documents (p11)

* transport-indication
* fasor (after years, now addressing comments) resubmitted, will be at
  an interim meeting
* groupcomm-proxy: re-bumped, pending WG adoption call

MT: More documents (p12)

* Updated and new individual submissions, please read and comment on the
  mailing list
* pd-body-error-position: At some point we may want to consider whether
  we need to do more here

MT: Interim planning (p13): Same cadence (every other Wednesday,
14:00-15:30 UTC) unless objected to. Plan to resume on April 26; to be
confirmed on the mailing list.

## Constrained Resource Identifiers (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides (p14-17):
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-yangcoreconfcomi-crihref-00.pdf

CB presenting.

CB (p14): URIs are text-based and complex; CoAP has a nice URI format,
CRI extracts the URI data model for carrying them around.  
CB (p14): We want short scheme names. Now using negative integers
(because positive integers are used for something else in CRIs).  
CB: After lots of back-and-forth: Registering numbers for all the ~300
schemes around. Technically done, procedural questions remain open.
(We'll get back to that)  
CB (p15): On extensibility. Basic CRIs do everything that CoAP can do,
but they may still need other usages (e.g., percent encoding of
delimiters to not have their meaning). Section 7 went from doing
percent-encoding to being about extensions in general, with 7.1 doing
PET. The handling of unknown extensions is clarified in PR (not much
different from handling a URI scheme that you don't understand, or a
name that you can't resolve).  
CB: More comments on [PR#62][1] would be useful.  
CB (p16): Both absence and empty array needed (the latter to override a
path), so it's a toss-up.  
CB (p16): Empty CRIs are not useful.  
CB (p16): On UTF-8 checking vs. PET, recipients are burdened with
checking expected validity, while the implementation doesn't really need
to and might not be able to in constrained devices; the current view in
[#44][2] says that checking is only on demand (but generators still need
to produce valid values).  
CB (p17): Next step: Decide on the open points above; we could need
mailing list discussion on the boring stuff to avoid pain when done
wrong. Aiming at having a prepared discussion at the 1st interim, 1
month from now, on April 26.

Please read.

## Conditional Attributes for Constrained RESTful Environments (Bill Silverajan) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-conditional-attributes/

Presented slides:
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-conditional-attributes-for-constrained-restful-environments-00.pdf

BS presenting.

BS (p2): Has some history of splitting. Will have -07 this week,
factoring upcoming discussions.  
BS (p3): Two major issues. The first one is from the IoT-dir review. Any
objections to have this document Standards Track instead of
Informational?

CB: What's the difference? From an IETF point of view, Standards Track
implies that this is The Way we expect to do this. An Informational
document describes A Way. (No hard boundary). Within procedures,
difference in IESG efforts (Informational is faster). On consumer side,
some SDOs maybe want to only use Standards Track. If we know that, that
could affect the decision.

MK: The content for this has already been picked up (e.g., LwM2M, KNX
IoT); the issue with deciding is that there are implementations out
there. This is a continuation of an earlier intent, and we have things
using this that are out there and that don't work together. I'd like to
see this as Standards Track, but that would need work with the users to
show how to convert.  
BS: Do we have liaisons?  
MK: JJ is active in one.  
BS: We will have a discussion with them.  
JJ: That's in OMA / DSME meetings. We can also present and raise this
(or take it offline asynchronously).

MK: How urgent is finishing this? It has been around since Zach started
it; consolidating it may be better than rushing it to be done.  
BS: I think we're on the final stretch; it's nasty to wait two months
more, but a quick decision would be fine.

BS (p4): The other major issue is from Klaus' review, on how the
mechanism clashes with Observe.  
BS: As it's written right now, it alters how Observe notifications are
sent, meaning that some clients don't get the normally intended
notifications.  
BS: The proposal was to define updates of state through projections of
resource states.  
BS (p6): Showing what state projections are, basically a virtual
resource.  
BS (p7): Showing an example using a message diagram.  
BS: A slight rewrite can do this.

BS (p8) on observe cancellation.  
BS: Cancellation needs to have the URI-Query options. Would that be
sensible?  
CA (via chat): Yes, it is very sensible.

BS (p10): More, small things also to be fixed.

## Using EDHOC with CoAP and OSCORE (Rikard Höglund) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-edhoc/

Presented slides:
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-using-edhoc-with-coap-and-oscore-ietf-116-00.pdf

RH presenting.

RH (p1): reached -07.  
RH (p2): Recap since last IETF: WGLC completed, reviews processed into
-07.  
RH (p3): Title changed. Payload format changed, reducing the overhead.
Message and error processing around message 3. Error handling
future-proofed.  
RH (p4): Many changes to web-linking part, including registering in
upcoming registry. Using well-known resource in example now. New
registry for ed-cred-t. Some points from WGLC reviews deferred to EDHOC.

RH (p5): Updated security considerations; removed appendix on
performance considerations when using Block-wise.  
RH (p6): WGLC addressed, no further issues known -- authors consider it
ready for Shepherd review and write-up.

GS: On EDHOC issues, are they on issue tracker yet?  
RH: Not yet.  
GS: Please add those.

MT: Next step is on the Chairs for moving the document forward.

## Key Update for OSCORE (KUDOS) and OSCORE Key Limits (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-limits/

Presented slides (key limits):
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-key-usage-limits-for-oscore-ietf-116-00.pdf

RH (p1): Content on the cipher limits split out from KUDOS, and now a
separate WG document. It describes what is excessive use in terms of
encryptions or failed encryptions, as a reason triggering a key update. 

RH (p2): This stems from CFRG work (cfrg-aead-limits). It defines
counters and actions to take when limits are reached.

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/

Presented slides (key update):
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-key-update-for-oscore-kudos-ietf-116-00.pdf

RH (p1): This is the document from which the former was split out. Two
parts remain: the KUDOS procedure renewing the OSCORE Master Secret and
Master Salt (possibly achieving forward secrecy, inspired by the
procedure in Appendix B.2 of RFC 8613); update of OSCORE
Sender/Recipient IDs, either stand-alone or within a KUDOS execution.  
RH (p2): This uses an extended OSCORE option.  
RH (p4): Clarified that the use of an EDHOC EAD item is optional, only
for learning capabilities and KUDOS modes when running EDHOC. It's not
needed as such to enable or run KUDOS.  
RH (p5): an "active rekeying" can be performed at any time; clarified
message exchanges related to request/response (use of old vs new
context). Differences in context between request and response are OK  
RH (p6): well-known KUDOS resource where to send KUDOS messages; added
EDHOC-KeyUpdate to OSCORE's list of existing methods for rekeying;
defined hard limits for rekeying  
RH (p7): Dead-lock prevention; overhead of KUDOS messages.  
RH (p8): Partial IV in response, preventing nonce-key pair reuse
otherwise possible following a key update. This fix is now general,
updating OSCORE. (Its other updates to OSCORE are deprecating Appendix
B.2 and expanding the OSCORE option).  
RH (p9): On preserving observe relationships when updating OSCORE
Sender/Recipient IDs.

RH (p10): Next steps: address pending points (see issue tracker),
walkthrough of examples on updating OSCORE Sender/Recipient IDs,
implementation.

## A publish-subscribe architecture for the Constrained Application Protocol (CoAP) (Jaime Jiménez) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-coap-pubsub/

Presented slides:
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-a-publish-subscribe-architecture-for-the-constrained-application-protocol-coap-02.pdf

JJ presenting.

JJ (p2): One of the senior drafts (WG adoption in 2016). Consolidating
work, pushing it forward. Consolidating coap pubsub with design choices
from Klaus' and Marco's drafts.  
JJ (p3): Recap: publishers and subscribers are both clients.  
JJ (p4-p5): New thing: Broker API / resource structure (collection with
topic resource(s) with properties, then associated topic data
resource(s)). It will be trivial to update for earlier implementations,
but one has to change topic configuration.  
JJ (p6): Clarification: Topic lifecycle between the two resources.
Half-created first, then fully created when the first publication
occurs.  
JJ (p7): Skipping workflow example in interest of discussion time.  
JJ (p8): Implementation during the Hackathon, about 200 lines of Python,
now easier to do than back in 2016. MIT licensed version. The code may
be easier to grasp than the lengthy draft.  
JJ (p9): Discussion topics:

* Which topic properties do we need? Which are relevant?
* Names -- do we need it?
* How to treat max\_subscribers: When broker is denying a subscription,
  Observe says 2.05 with content. But could also be interpreted as an
  error. (problem detail structure?)
* (read for your own ... questions and comments)

CA: I don't see how max\_subscribers maps through the stack of protocol
mechanism up to application ... Observe is equivalent to many-GETs.
Authorization properties would be better suited.  
JJ: I agree.

## YANG Schema Item iDentifier (YANG SID) and COMI (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-sid/

* https://datatracker.ietf.org/doc/draft-ietf-core-comi/

Presented slides (p1-13):
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-yangcoreconfcomi-crihref-00.pdf

(shuffled to this point where Rob Wilton is in the room)

CB presenting.

CB (p1): RFC 9254 is published, telling how YANG is represented in CBOR
(efficiently by using SIDs). Allocation of these is topic of the
presentation. And then there's COMI and YANG-LIBRARY. Spent 2h on the
2023-03-15 interim meeting, made much progress there.  
CB (p2): Doing "impossible" work :-). More a people issue than a
technical issue. So many changes from IESG review that new WGLC was done
(and completed).  
CB (p3): YANG toolscape is a bit empty, needing updates to PYANG tool.  
CB (p4): Not all nodes are used for representing data. / Examples may
generate incomplete SID sets; more PYANG work needed.  
CB (p5): Example given for missing SIDs generated.  
CB (p6): Does both the process and the registries. There will likely be
regular process and application specific processes. For example, LPWAN
people need more control over SID allocations. This will not be the
normal thing, but there will be cases. How does a Designated Expert
check a document (again: in terms of correctness and completeness)?

RW: If you manually allocate the SID files, and then run it through
PYANG, would that verify things?  
CB: Yes, good point.

CB (p7): Also got IANA question; IANA differentiates private and
experimental use, and synchronization points (related to timing between
RFC and registry publication), and versioning (new version of SID file
for existing version of YANG module) (CB suggesting just overwriting).

### COMI

CB (p8): COMI (YANg over CoAP) is equivalent to RESTCONF (YANG over
HTTP). This started in 2015. Implementer feedback motivated
simplifications (dedicated branch on Github).  
CB (p9-10): Getting rid of URI encoding of instance identifiers -- use
FETCH and iPATCH. Just one query parameter left (but SIDs, not instance
identifiers).  
CB (p11): Open question -- do we need these? Full data store access
(read and write), which looks different from everything else. Same
problem for the error response. What are the use cases for full data
store access?

RW: I can't answer whether it is needed, but providers often do "config
replace" change with complete configuration, to be sure that it's as
expected. It may be different in this space, but new config may be
small.  
CB: We don't *need to* do the simplification.

CB (p13): We will gather more feedback; this will need another WGLC.
Then we can ship it.

## DNS over CoAP (DoC) (Martine Lenders) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-dns-over-coap/

Presented slides:
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-dns-over-coap-doc-00.pdf

ML presenting.

ML (p2): Motivation.  
ML (p3): Use of CoAP features: encryption (OSCORE or DTLS), block-wise,
sharing code that's already on the device.  
ML (p4): Short update because not everything is done yet.  
ML: The DNSDIR review was addressed.  
ML (p5): Addressing DNSOP comments is work in progress; cross-proxy is
not sufficient, but it can address the question of how to translate
(possibly generalizing on FETCH proxying).  
ML (p6): Answers to questions of default paths. SVCB spun off a few
discussions.  
ML (p7): Next steps: Feedback; pick Content-Format.

CA: One of the more blocking aspects of the SVCB issues has already
received positive feedback, so I expect this to go smoothly.

## Constrained Application Protocol (CoAP) Performance Measurement Option (Giuseppe Fioccola) (10)

* https://datatracker.ietf.org/doc/draft-fz-core-coap-pm/

Presented slides:
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-coap-performance-measurement-option-draft-fz-core-coap-pm-04-00.pdf

GF presenting.

GF (p2): Motivation.  
GF (p3): Focusing on two particular mechanisms, based on spin bit and
square bit.  
GF (p4): This is a base proposal, extensions can be discussed later.  
GF (p5): Comments from the interim meeting have been addressed; now the
draft includes content about scenarios and use cases, and it details
scenarios with a proxy.  
GF (p6): The new PM Option is elective (it can be ignored by endpoints).
Proxies may terminate performance measurement ...  
GF (p7): ... or not terminate it, if not caching responses (the option
is proxy-unsafe; non-caching proxies can simply treat it as if was
safe-to-forward).  
GF (p8): Summary of changes.  
GF (p9): Next steps. WG adoption?

MT: Who read a recent version? 2 on site, 1 in chat.  
MT: Poll with raise-hands tool. Ready for WGA? Raise if agreeing, don't
raise if disagreeing.  
Result: 11 raised hands. 0 non-raised hands.

CA: Thanks, the different cases are now sound. I would prefer if it were
handled in IPPM.  
I am concerned that this would give the perception that this is
something endorsed. I would not recommend it to be used but I am not
objecting it either. I just think it's better done in IPPM.  
GF: We are sharing IPPM experience: e.g., 6man managed IPv6 bits. When
adoption call is started, I'll recommend keeping IPPM in CC.  
CB: With respect on which Working Group where to do it -- we tried, IPPM
pushed back, they think it's the applications that define the actual
documents. Fundamentally the RFC is not going to tell you the Working
Group where it came from.   
CB: When it's in the document, we may want to have some precautions in
the text as to where it is applicable, as we know the properties of CoAP
traffic.  
(CA, on chat): Fine with me.

## CoAP over GATT (Bluetooth Low Energy Generic Attributes) (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-amsuess-core-coap-over-gatt/

Presented slides:
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-coap-over-gatt-00.pdf

CA presenting.

CA (p2): Recap: Alternative non-IP transport, but widely available, even
in Web browsers. Motivation similar to CoAP-over-WebSockets.  
CA (p3): Summary of implementation experiences.  
CA (p4): Updated use of CoAP token based on GATT properties. Single byte
header. Single bit as Message ID due to BLE channel.  
CA (p5): Discovery from the browser on a BLE enabled device. Need to
click through all peers and find out individually. Existing discovery
mechanisms could be extended. Not easily done.  
CA (p6): Multicast via Beacons? SCHC for signaling?  
CA (p7): The addressing did not change.  
CA (p8): Roadmap and asking for WG interest.

JJ: Tested browser implementation and discovery was working. Little
issues on the Safari browser but I would like to test more as guinea
pig.  
GS: Great work, would like to see it continued and adopted.  
IP (via chat): +1.  
CB (via chat): +1 for adoption soon (not this version).  
CB: +1, but let's get a little bit more implementation experience (i.e.,
not adopt this version yet). Hard to answer adoption now.  
FP (via chat, as individual): +1 on adopting this  
MT: I've read the last version. It seems to me that, conceptually, all
the foundation concepts are there. We can revisit and progress this
soon, also during interim meeting. No need to wait until IETF 117.

## A YANG data model for SDN-based key management with EDHOC and OSCORE (Rafa Marin-Lopez) (10)

* https://datatracker.ietf.org/doc/draft-marin-yang-edhoc-oscore/

Presented slides:
https://datatracker.ietf.org/meeting/116/materials/slides-116-core-a-yang-data-model-for-sdn-based-key-management-with-edhoc-and-oscore-01.pdf

RML presenting.

CB: Do you need full data store access?  
RML: Our assumption is that, when the device is constrained, CoMI
information will be sent to the thing. Right now, POSTing it using the
XML.  
CB: We will take this offline.

## Flextime (5)

MT: Thanks, meeting adjourned.

* * *



[1]: https://github.com/core-wg/href/pull/62
[2]: https://github.com/core-wg/href/issues/44
*[MT]: Marco Tiloca


*[JJ]: Jaime Jiménez


*[FP]: Francesca Palombini


*[JPM]: John Preuß Mattsson


*[CB]: Carsten Bormann


*[CA]: Christian Amsüss


*[KH]: Klaus Hartke


*[RH]: Rikard Höglund


*[TF]: Thomas Fossati


*[DN]: David Navarro


*[GS]: Göran Selander


*[BS]: Bilhanan Silverajan


*[AS]: Alan Soloway


*[MCR]: Michael Richardson


*[AK]: Ari Keränen


*[MJK]: Michael Koster


*[NW]: Niklas Widell


*[ED]: Esko Dijk


*[HB]: Henk Birkholz


*[ST]: Sean Turner (here)


*[ML]: Martine Lenders


*[MW]: Matthias Wählisch


*[KZ]: Koen Zandberg


*[GF]: Giuseppe Fioccola


*[MN]: Massimo Nilo


*[LT]: Laurent Toutain


*[AB]: Andy Bierman


*[JT]: Jernej Tuljak


*[RML]: Rafael Marin-Lopez


*[AF]: Alex Fernandez


*[MK]: Matthias Kovatsch


*[RW]: Rob Wilton


*[IP]: Ivaylo Petrov


