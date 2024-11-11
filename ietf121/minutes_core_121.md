# IETF 121 - Agenda for Constrained RESTful Environments (CoRE) WG

Chairs (core-chairs@ietf.org):

* Marco Tiloca (marco dot tiloca at ri dot se)
* Jaime Jiménez (jaime at iki dot fi)
* Carsten Bormann (cabo at tzi dot org)

Date and time: Tuesday, 2024-11-05, 09:30-11:30 UTC

https://www.timeanddate.com/worldclock/fixedtime.html?msg=CoRE%40IETF121&iso=20241105T0930&p1=78&ah=2

Meeting material: https://datatracker.ietf.org/meeting/121/session/core

Notes: https://notes.ietf.org/notes-ietf-121-core

Recording: https://youtu.be/NsigfgTo7E4

Zulip: https://zulip.ietf.org/#narrow/stream/core

Note takers: Christian Amsüss, Rikard Höglund

Chat monitor: Marco Tiloca

* * *

Numbers in parentheses are minutes of time allocated.

## Intro, agenda, status (Chairs) (10)

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-chairs-slides-00.pdf

MT doing introductions

MT (p7-p17): Status of documents of this and other Working Groups.

CB (p18): on draft-ietf-core-corr-clar. This is an unusual document
type, prototyped in ROHC WG -- running / standing WG document collecting
corrections and clarifications, so there is some level of WG agreement.
It was adopted as a WG document last month. We are collecting issues on
GitHub, and processing them in interim meetings (or other time). We have
the recent PR [#40][1] -- for which we are recording the WG position.
The PR is about amplification and 0-RTT. There are two related
documents: one in CoRE and one is in T2TRG. Compared to other documents
on this point, the content of this PR is more about an overview. CA
provided an update, it would be good to process this quickly because
draft-ietf-core-dns-over-coap needs to reference this.  
MT (p19): We plan for upcoming interim meetings: one on December 18,
then a series starting from January until IETF 122. We will send a mail
to confirm this.

## CORECONF (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-comi/
* https://datatracker.ietf.org/doc/draft-ietf-core-yang-library/

Presented slides:

* https://datatracker.ietf.org/meeting/121/materials/slides-121-core-coreconf-href-00.pdf
* https://datatracker.ietf.org/meeting/121/materials/slides-121-core-ietf-yang-library-augmentedby-00.pdf

CB presenting.

CB(p1): It's a cluster of 4 documents -- 2 got published ("How to do
YANG in CBOR", "Management of the integer namespace").  
CB: Next up: COMI, i.e., "How to do all this with CoAP". Finally, an
addition in the form of a YANG module is needed to find out server
capabilities.  
CB: The original module is probably too complicated for constrained
servers, so we are defining our own. The work on this has been stalled
due to other things. We now have a contribution from Zhuoyao Lin which
we may want to look at.  
ZL ("Augmented-by" slide deck): This is a document in NetConf, defining
augmentation lists. It is motivated by a concrete use case.  
ZL (p2): The use case is the YANG Kafka architecture. The YANG schema is
visible to multiple parties. We used libnetconf2, which has a default
action for "getting all YANG libraries". When testing with real routers,
we found that this default action takes minutes to complete, and thus
does not meet real-time requirements.  
ZL (p2): Disabling the get-all module does not solve things either; the
bottleneck is due to augmentations and deviations. There are two
possible solutions: using the default action, or live-parse the message
(and learn from the prefix) to gain knowledge of the augmentation.  
ZL (p4): The second approach might miss data, unless the augmentation
list is exposed in the library.  
ZL (p5): The intent is to first parse the "subscription started" message
and then load the subscribed modules based on that.  
ZL (p6): We are proposing this feature here to see from implementors'
perspective whether it is useful. As to gaps: is a YANG file required
along with SID? Also, will the number of modules be the same as for real
routers?

CB: Which working group will you present this in?  
ZL: NETCONF on Friday.

AP: This is an interesting read. For IoT devices, things can be slow
even for 1-2 modules.

MCR: If I understand correctly, you get some YANG and management device
pulls up extra modules. With SID, you may not know what to map it to
without knowing all the allocations. Do you want to access the Internet
in order to get that, or a local database?  
ZL: That is what I want feedback for.  
MCR: A full database of SID files may be around 100 MB, so that could be
reasonable.  
ZL: The question is whether augments are used or are just a module in
itself. But it is not just about augments, it is also about imports and
includes.  
MCR: My experience is that augment was a disaster and should not be
used. But this is context-specific as to how we are doing things.  
MCR: We had multiple things to augment and that caused multiple copies
of the augmented thing, which did not work. Trapezoidal dependencies. I
am not sure that that is a common pattern in general.  
CB: YANG is being developed by different WGs with different
perspectives. We have a different perspective from NETCONF.  
MCR: I see this problem.

AP: In SCHC we use YANG to configure constrained devices and we use
augment. This is a possible use case.

AP (on chat): An interesting resource: https://coreconf.manojgudi.com/

CB (p2 continuing on YANG-CBOR slides): Ramping up towards launch

CB (p5): Version -19 of draft-ietf-core-comi is out. Some open points
remain from the T2TRG interim meeting in May, regarding simplifications.
If this is done right, it can be very simple. We need time to discuss,
possibly during a future interim meeting.  
CB (p6): What about scaling COMI? For example, for access methods
applied to devices more complex than temperature sensors. Are accessors
for subsets of the information good enough? This can be done in a
separate draft. More support for retrieving subsets would be in this new
scaling draft. That would definitely be in the CoRE Working Group
because it is about the interaction.

## Constrained Resource Identifiers (Carsten Bormann) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-href/

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-coreconf-href-00.pdf

CB (p8): In CoRE, we decided not to modify the Web's URI concept at
first (we can reuse everything from the REST world). But CoAP has
Options for URI components such as path segments in its information
model. In RFC 7252, we described the translation between URIs and CoAP
options, and thus created an information model without being aware of
it.  
CB (p9): On CRIs, there is ongoing implementation work, to create test
vectors. This is still work-in-progress.  
CB (p10): Zone identifiers: RFC 4007 left many things open. We provide a
way to add a zone-ID close to an IPv6 address, based on RFC 6874 (how
zone identifiers are put in URIs). The browser vendors agreed to not
implement this, looking for plan B. Also, RFC 6874 will just go away --
at least that's the idea in 6man.  
CB (p11): How to handle this? One way is to continue unchanged because
6man has only a draft at the moment. Another way is to entirely remove
the possible use of zone identifiers from this document.  
Question: Are we using zone identifiers in our deployments? If so, the
second option does not work.  
Proposal: Keep zone identifiers in the model, but do not say how it
relates to the URI model. We can still accommodate future developments.
It seems better than expunging it.  
CB (p12): What is a zone identifier? (See the slide). Seems that some
things are broken, e.g., as to the character set to use.

CA: In CRIs, we do already accommodate things that were there in URIs
but deprecated (e.g., passwords in userinfo), for the sake of expressing
the full URI space. Keeping zone identifiers in the model is consistent
with this approach. A URI with a zone identifier can then be converted.

## Conditional Attributes for Constrained RESTful Environments (Bill Silverajan) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-conditional-attributes/

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-conditional-attributes-for-constrained-restful-environments-00.pdf

BS (p1): This work builds on CoAP observation (RFC 7641) and adds
metadata so that clients do not get notifications necessarily for every
change in state, but can influence it. The document is past WG Last Call
and had an IOTDIR early review.  
BS (p2): Version -08 was submitted before the cut-off. There were no big
changes between versions -07 and -08; the update was mainly editorial
and with some clarifications. The processing of the review comments is
ongoing.   
BS (p2): We added a distinction between notification and control
attributes.  
BS (p3): What is left: IANA considerations work; clarifying registration
procedures; editorial changes.

MT: Open issues are marked as editorial fixes and will be included in
the next version. Can we have all addressed in the next 20 days, so that
we can follow with the Shepherd write-up and request publication by the
end of the year?  
BS: I will address some points this week. The plan sounds reasonable.  
MT: Jaime, does it Work for you as Shepherd to request publication by
the end of the year?  
JJ: Yes.

MG (on chat): Thanks for your hard work on the Conditional Attributes
draft. At OMA, with LwM2M we find this work very useful.

## DNS over CoAP (DoC) "bundle" (Martine Lenders) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-dns-over-coap/
* https://datatracker.ietf.org/doc/draft-ietf-core-coap-dtls-alpn/
* https://datatracker.ietf.org/doc/draft-lenders-core-dnr/

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-dns-over-coap-doc-dns-service-binding-records-with-coap-01.pdf

ML (p1): Covering 3 drafts.  
ML (p2): Updates since IETF 120. We have addressed the review from
Thomas Fossati on draft-ietf-core-dns-over-coap. The companion document
draft-ietf-core-coap-dtls-alpn was adopted by the Working Group. There
are no updates for draft-lenders-core-dnr (the problem statement around
OSCORE).  
ML (p3-4): Overview of cross-references; it is easier when looking at
normative references only.  
ML (p5): We need help related to OSCORE/EDHOC and SVCB expert review.  
ML (p6): draft-ietf-core-dns-over-coap and
draft-ietf-core-coap-dtls-alpn, should be ready for a WG Last Call after
this week.

MT: If I recall correctly, the reference from
draft-ietf-core-dns-over-coap to a yet-to-appear
draft-ietf-core-corr-clar is indeed the only thing to fix before a
proper WG Last Call. When doing that, we will keep DNSOP and DPRIVE in
the loop. A second, early review was requested to DNSDIR but we have not
got it yet.

## CoAP Transport Indication (Christian Amsüss) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-transport-indication/

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-coap-transport-indication-00.pdf

CA (p2): How can different transports for CoAP be used automatically?
This document describes the path forward for coap+... schemes. It
provides prerequisites and guides for new standardized transports (e.g.,
CoAP over GATT, CoAP over CAN) and CoAP over MQTT is already used.  
CA (p3): The document has been restructured. The key is to use the
concept of proxies, then different transports are considered as
supported by (local) proxies to services. These proxies and the
transports that they support can be discovered by links, SVCB, or other
means. The proposal is to have a unified \_coap service, and not both
\_coaps and \_coap (feedback is welcome!)  
CA (p4): Open questions: a \_coap SVCB record could be a new resource
record for CoAP (like HTTP did). That would mean either
\_coap.dev.example.com in SVCB or dev.example.com in CoAP.  
Open points to move forward: the SVCB edhoc-cred and edhoc-info
parameters could be moved out. "IP literals with extra data" is
proposed, but it is going at a slower pace, so I propose to move it out.
Do people agree? If so, where to move it?  
CA (p5): Showing example of the IP literals with extra data.

MT: Go ahead and we will see how it looks when done.  
ED: I wonder how many understand this, personally I do not.  
CA: What about using an interim to go over this in more detail?  
ED: Yes, and the topic seems important.

ML (on chat): wrt to name vs. type in SVCB records for
-transport-indication: There was a similar discussion in DELEG yesterday
(\_deleg name vs DELEG type). There was no real consensus, but there
seemed to be some preference for type.

## A publish-subscribe architecture for the Constrained Application Protocol (CoAP) (10) (Jaime Jiménez)

* https://datatracker.ietf.org/doc/draft-ietf-core-coap-pubsub/

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-a-pubsub-architecture-for-coap-00.pdf

JJ (p2): Recapping content. A CoAP server acts as pub-sub broker
allowing pub-sub functionality.  
JJ (p3): Topic-collection resource (for topic creation by a manager).
Topic resource (for topic configuration by a manager). Topic-data
resource, with the actual content for CoAP clients acting as publishers
and subscribers. Topic properties are within the configuration for a
topic in the corresponding topic resource (e.g., rate limiting etc.)  
JJ: Gone over recent document updates. Updated to support also iPATCH,
added more examples, and editorial updates.  
JJ: Changes from version -14 to version -15: Fixed bug in
implementation. Updated examples to align format with RFC 9594. Explicit
cancellation of subscription to a topic. Also topic history
(configurable by a manager).  
JJ (p6): Examples updated (no particular standardized format; many RFCs
use different presentations, now we follow RFC 9594).

JJ (p7): Can we have a WG Last Call? In parallel, there is work in ACE
for pub-sub profile applicable to this pub-sub architecture (see
draft-ietf-ace-pubsub-profile).  
JJ: During the Hackathon, we also discussed with Esko Dijk, who accepted
to be Document Shepherd.

FP (as individual): I am almost done with my review. Go for WG Last
Call, I will send my review during the WG Last Call.  
AP: Yes, do the WG Last Call please.  
MT (as individual and Contributor): I will also review the document, and
think it is largely ready. As a pre-WG-Last-Call comment: slide 3 shows
the architecture, which is analogous to that in
draft-ietf-ace-oscore-gm-admin. There is a resource handler of the topic
resource that uses PUT. In fact it has, as intended, the semantics
expected for POST. Like done in the ACE document, we should consistently
change the method from PUT to POST. The specified semantics is already
fine and as intended.

## Group Communication for the Constrained Application Protocol (CoAP) (Esko Dijk) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-groupcomm-bis/

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-group-communication-for-coap-draft-ietf-core-groupcomm-bis-00.pdf

ED presenting.

ED (p2): This document is intended to replace the previous Experimental
RFC 7390. It also covers newer CoAP features when using group
communication (observe, Block-wise, security with Group OSCORE,
No-Response).  
ED (p3): Summary of post-WGLC Updates. Thanks to Christian Amsüss for
the recent review comments. Several updates, plus clarifications and
simplifications.  
ED (p3): Support for the Block2 Option was added also to group requests
following the first one for the same body, under certain circumstances.
We simplified and explained the handling of identical ETAGs from
different servers in the CoAP group. We moved the content on the issues
due to proxies into two new appendices. The reference to RFC 7967 for
the No-Response option is now normative, as it is in fact used
normatively. We revised the list of methods for naming application
groups: we removed those methods that nobody ever tried, and we now
focus on recommended methods while not trying to be exhaustive.  
ED (p4): We are waiting for the Working Group, Christian Amsüss and
Carsten Bormann to confirm the updates from their reviews. A first WG
Last Call happened. Is another one needed?

CB: I can parallelize my answer by doing a new WG Last Call.  
ED: It makes sense. Everyone flag us about CoAP features we may have
missed.  
ED: Group communication via proxy is also covered, but details are
specified in a separate document (see the next presentation).

AP: I do not want to delay this document (it is important to be
shipped). In SCHC, we use CORECONF to manage SCHC endpoints. Looking at
group communication, it is not always CoAP over UDP/IP. How should we
handle different situations? Will there be a bis document to this one?
The natural way would be to use CoAP group communication with CORECONF
on top.  
ED: So over non-IP transports? This document focuses on UDP over IP
multicast on purpose. Other transports are out of scope.  
AP: So should we have a separate draft?   
ED: Yes, or a bis.  
CA: If CoAP for group communication is used over something that is not
UDP/IP, we should describe such transport.  
AP: An example is LoRAWAN. SCHC over LORAWAN is described. We mapped
IPv6 multicast to LORAWAN multicast with SCHC.  
ED: Yeah, if it is IPv6 then it is in scope.  
AP: I wanted to raise this and ask how we should proceed. It seems
better to ship your document and then take it from there.

## Proxy Operations for CoAP Group Communication (Marco Tiloca) (10)

* https://datatracker.ietf.org/doc/draft-ietf-core-groupcomm-proxy/

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-proxy-operations-for-coap-group-communication-00.pdf

MT presenting.

MT (p2): Scope – The client has a dialogue with the proxy, to have group
communication with a group of servers through the proxy deployed in
between. The proxy waits for responses for a time set by the client and
forwards back individual responses to the client (with information about
individual servers).  
MT (p2): This document updates the caching and validation model of
responses from RFC 7252, to work at this sort of proxy.  
MT (p3): Gist of the protocol: the client sends a unicast request to the
proxy that forwards it to a group of servers over IP multicast. Two new
CoAP options are defined: Multicast-Timeout added by the client in the
request to the proxy (telling the proxy for how long it should wait for
responses to forward back), and Reply-From added by the proxy in a
response (indicating addressing information pertaining to the origin
server that generated that response, e.g., the unicast IP of that
server). A client can send follow-up requests using the address
indicated in Reply-From and by doing so reach the server. The details
are such that this is outcome also if the proxy is a reverse-proxy
hiding individual servers in the group.  
MT (p3): A secure association is needed between client and proxy, in
order to identify and authorize the client. One can use (D)TLS or such,
but also OSCORE as defined in draft-ietf-core-oscore-capable-proxies.  
MT (p4): Summary of updates. Added security considerations for the
Reply-From Option. For Multicast-Timeout, it was clarified that the
option is empty on the wire if it has value 0, due to the recommended
encoding, but its format is formally "uint".  
MT (p5): We made RFC 7967 normative, and generalized some points to be
aligned with draft-ietf-core-groupcomm-bis and comments received for
that document. The examples of message exchanges with a reverse-proxy in
Appendix A have been fixed.  
MT (p6): We completed the definition of error handling for two cases:
failure by the proxy to identify the client, and unsuitable values in
the Multicast-Timeout option which trigger error messages and re-tries
by the client or by a proxy in the chain receiving the error response.  
MT (p7): We also updated the conversion between two CoAP options and the
corresponding HTTP header fields, using the structured field values from
RFC 9651. That applies to both Reply-From and Group-ETag (the latter
requiring how this group-revalidation works in the HTTP-to-CoAP proxy). 

MT (p8): Next steps: enabling a client to early-stop the proxy from
accepting and forwarding back responses; enabling an HTTP-to-CoAP proxy
to forward back to the clients HTTP responses in a stream-like fashion
(just like a CoAP-to-CoAP proxy would do), by using
Transfer-Coding:chunked. I'd like to enable validation between proxy and
server; this would need to define the ETag option to be outer for
OSCORE, which can better be done in draft-amsuess-core-cachable-oscore
since this assumes that the proxy caches OSCORE responses in the first
place. The Reply-From option may change name again (see issue #3)
because it provides something similar to other not-yet-existing options
that are desired and can be clustered together.

JJ: The Transfer-Coding Chunked is the one from HTTP, right?  
MT: Yes, it allows delivery of HTTP responses in a streamlined fashion
for an HTTP-to-CoAP proxy, like we do for CoAP responses where using a
CoAP-to-CoAP proxy.

## Key Update for OSCORE (KUDOS) (Rikard Höglund) (15)

* https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-slides-kudos-core-ietf-121-00.pdf

RH (p2): Recap on what KUDOS is about. Also mentioned the related
documents on key usage limits and OSCORE ID update, see
draft-ietf-core-oscore-key-limits and draft-ietf-core-oscore-id-update. 

RH (p3): The KUDOS message flow is fundamentally an exchange of nonces
within the OSCORE option, resulting in deriving a new Master Secret for
the new OSCORE Security Context.  
RH (p4): Updates since the previous version. We considered a parameter
for advertising KUDOS support in the OSCORE profile of ACE (RFC 9203),
but we concluded that KUDOS is incompatible with that ACE OSCORE
profile, since the ACE access token remains bound to the old, replaced
OSCORE Master Secret. However, such an advertisement works with the
EDHOC and OSCORE profile of ACE (see
draft-ietf-ace-edhoc-oscore-profile), and we will add text related to
it.  
RH (p5-6): Also added more text on the importance to run KUDOS with
margin (i.e., start a key updated ahead of time, especially when using
CoAP in space or in other long-exchange use cases). This is because
ongoing exchanges must be terminated when KUDOS is used.  
RH (p7): On KUDOS resource type: core.kudos. Clarify why this is done.
That marks resources that result in *no* application level processing on
the server.  
RH (p8): We enabled pure servers to work in reverse message flow. They
can send a protected response (KUDOS Response #1) without decrypting an
incoming request from the client.  
RH (p9): Next steps on documents that were previously split out. Key
limits: keep following draft-irtf-cfrg-aead-limits (updates have been
regular made to that document, but with no recent content changes). ID
Update: Add more examples and split long sections for readability.  
RH (p10): Next steps on main document; specific open points. 3 remaining
points from Christian's review.

CA(on p8): I think that there are even cases when a pure server can send
non 4.01 when its recipient key is OK but its sender key is not (more on
that later).  
RH: Thanks for the feedback. Yes, let's discuss this more.

(CA, note to self for later comment): Doesn't derived key still PoP ACE
OSCORE key?  
(CA, note to self for later comment): GET / Block2:0 No-Response:26 is
also guaranteed to not trigger actions in the application.  
(CA, for later presentation): KUDOS in reverse flow on a pure server
might just make things easy for stateless.

## Constrained Application Protocol (CoAP) over Bundle Protocol (BP) (Carles Gomez) (10)

* https://datatracker.ietf.org/doc/draft-gomez-core-coap-bp/

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-coap-over-bp-00.pdf

CG (p2): We presented 2 previous versions of this document in CoRE and
DTN (Delay tolerant Network). DTN defines the bundle protocol and the
related ecosystem. The main update is its support for CoAP message
aggregation using a Payload-Length option.   
CG (p3): 2 new subsections related to message aggregation.  
CG (p4): New terminology: "Single message" and "Aggregated message".  
CG (p5): The new Payload-Length option is introduced. It indicates the
size of the payload of a CoAP message.  
CG (p6): We clarified the lifetime of the encapsulating bundle. As
future refinement possibilities, we can consider aggregation delay.  
CG (p7): Various updates to the document related to the No-Response
option, timing (new requirement for application to learn timestamps),
Observe and URI scheme (DTN and IPN name patterns both used in DTN).

AP: You talk about wild timeouts; do you see particular adjustments to
the state machine that need to be specified?  
CG: Modifying the operation of the protocol? The best would be to set
parameters and see if it works. But not modifying the core protocol
operations. So far, we have not seen a need to change the state machine.
Congestion control point is open and may affect this. Also, most
parameters are for CON messages; maybe we want to rely more on
underlying layers to handle congestion and flow control.

CA: You can take the UDP state machine for CoAP over UDP and use those
parameter values, if it works for you for CoAP-over-BP. If the
underlying transport has that flexibility, all good. If you need
explicit use of CON messages, do it.  
MG (on chat): +1 to that.  
CG: We do not know what will be below BP. Keeping all options and
allowing flexibility seems best.

AP: To follow-up on that: maybe you can describe best practice for
CoAP-over-BP. That is, if you want to communicate all the way to the
moon, then you need this.  
CG: We are also interested in research side. The Deepspace meeting
yesterday provided insights. Simulations are also an option.

ED: Maybe simulate before you send a message to the moon :-). If there
is any simulation, I am interested.  
CG: We are starting to build a testbed for emulation.   
ED: Is using "coap" as URI scheme correct? So no "+" involved like in
"coap+tcp"?  
CA nodding.  
ED: In that case, consider the example with security in there.  
CA: Thumbs up.  
ED: It might be OSCORE or something. DTLS may not be practical to
Jupiter.  
CG: Security will need work, open to get help. Security can be at the
CoAP level, but there is also BPSec.  
ED (on chat): For CoAP over BP, app-layer security may not be needed on
point-to-point links. But it may be needed on the planetary multihop
internet.

JJ: During the hackathon, Marek Serafin showed nice extensions for Node
Red. You mentioned simulation. That will be published soon, try it out.

AP: There is the Deepspace BoF, on putting IP in space. You have a draft
there too.  
CG: I did not present CoAP-in-Space. Similarities exist, but differences
too.

(CA, note to self for offline comment): Is it Payload-Length, or
There-Is-A-Piggybacked-Request-In-The-Payload-after? (Gotta think this
through further) ... and safe-to-format, we will have to check. (Then
all responses can only be bundled together.)

## Stateless OSCORE (Christian Amsüss) (5)

* https://datatracker.ietf.org/doc/draft-amsuess-core-stateless-oscore/

Presented slides:
https://datatracker.ietf.org/meeting/121/materials/slides-121-core-stateless-oscore-00.pdf

CA: Why should one do it? This started from seeing a RIOT summit
presentation about what NTP can do. Thought: Let's enable this in
OSCORE.  
CA: You may have an arbitrary number of clients interacting with a
server that has memory constraints.  
CA: OSCORE has the building blocks. Just avoid storing per-peer keys. An
internal secret at the server can be used to derive per-peer secrets (as
input, use also each Recipient ID at the server, i.e., the Sender ID of
each client). Then, when receiving an OSCORE request, the server
re-derives the per-peer keys to decrypt it, from the internal secret and
the 'kid' in the request specifying the client's Sender ID.  
CA: This would only work for safe operations, so practically GET and
FETCH requests. Also the keys must be sent explicitly to the clients.
Limitations on usage of global key, and consider that a global sequence
number would be needed.  
CA: Not sure where exactly to use this. Let me know if you want it
usable. Let me know if you have any use cases. We can make this work.

JJ: DOTS comes to mind as they use CoAP for signaling.  
CA: In theory, you can do it also for methods other than GET and FETCH,
if the requests are guaranteed to be safe in the REST sense.  
AP: In interstellar communication, you may not have so many devices, but
long-lived devices. So you may want to have 1 key and able to use it for
years.  
CA: With few devices, per-device keys can be stored, so stateless OSCORE
does not help.  
AP: I am thinking of IoT satellite communication using mostly uplink
communication, with no downlink. You set up devices and then do uplink
only traffic.  
CA: You may run into limitations, as you can practically only do FETCH
and GET, which are strange if not followed-up by a response.

Σ 120

* * *



[1]: https://github.com/core-wg/corrclar/pull/40
*[AB]: Andy Bierman


*[AF]: Alex Fernandez


*[AHF]: Alex Huang Feng


*[AK]: Ari Keränen


*[AP]: Alexander Pelov


*[AS]: Alan Soloway


*[BS]: Bilhanan Silverajan


*[BSc]: Ben Schwartz


*[CA]: Christian Amsüss


*[CB]: Carsten Bormann


*[CG]: Carles Gomez


*[DN]: David Navarro


*[ED]: Esko Dijk


*[FP]: Francesca Palombini


*[GF]: Giuseppe Fioccola


*[GS]: Göran Selander


*[HB]: Henk Birkholz


*[IvP]: Ivaylo Petrov


*[JJ]: Jaime Jiménez


*[JPM]: John Preuß Mattsson


*[JT]: Jernej Tuljak


*[KH]: Klaus Hartke


*[KZ]: Koen Zandberg


*[LT]: Laurent Toutain


*[MCR]: Michael Richardson


*[MG]: Matthew Gillmore


*[MJK]: Michael Koster


*[MK]: Matthias Kovatsch


*[ML]: Martine Lenders


*[MN]: Massimo Nilo


*[MT]: Marco Tiloca


*[MW]: Matthias Wählisch


*[NW]: Niklas Widell


*[RH]: Rikard Höglund


*[RML]: Rafael Marin-Lopez


*[RW]: Rob Wilton


*[ST]: Sean Turner (here)


*[TF]: Thomas Fossati


*[TG]: Thomas Graf


*[ZL]: Zhuoyao Lin


