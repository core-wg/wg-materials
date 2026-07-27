
<!DOCTYPE html>



<html data-bs-theme="auto" lang="en">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <title>minutes-126-core-00</title>
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link href="https://static.ietf.org/fonts/inter/import.css" rel="stylesheet">
        <link href="https://static.ietf.org/fonts/noto-sans-mono/import.css" rel="stylesheet">
        <link rel="stylesheet" href="https://static.ietf.org/dt/12.69.0/ietf/css/ietf.css">
        
        <script src="https://static.ietf.org/dt/12.69.0/ietf/js/theme.js"></script>
    </head>
    <body class="m-2 bg-transparent">
        <h1 id="ietf-126-constrained-restful-environments-core-wg">IETF 126 - Constrained RESTful Environments (CoRE) WG</h1>
<p>Chairs (<a href="mailto:core-chairs@ietf.org">core-chairs@ietf.org</a>):</p>
<ul>
<li>Marco Tiloca (marco dot tiloca at ri dot se)</li>
<li>Jaime Jiménez (jaime at iki dot fi)</li>
<li>Carsten Bormann (cabo at tzi dot org)</li>
</ul>
<p>Date and time: Thursday, 2026-07-23, 12:00-14:00 UTC</p>
<p><a href="https://www.timeanddate.com/worldclock/fixedtime.html?msg=CoRE+%40+IETF+126&amp;iso=20260723T12&amp;p1=1440&amp;ah=2">https://www.timeanddate.com/worldclock/fixedtime.html?msg=CoRE+%40+IETF+126&amp;iso=20260723T12&amp;p1=1440&amp;ah=2</a></p>
<p>Meeting material: <a href="https://datatracker.ietf.org/meeting/126/session/core">https://datatracker.ietf.org/meeting/126/session/core</a></p>
<p>Notes: <a href="https://notes.ietf.org/notes-ietf-126-core">https://notes.ietf.org/notes-ietf-126-core</a></p>
<p>Recording: <a href="https://youtu.be/zNrCp2768QQ">https://youtu.be/zNrCp2768QQ</a></p>
<p>Zulip: <a href="https://zulip.ietf.org/#narrow/stream/core">https://zulip.ietf.org/#narrow/stream/core</a></p>
<p>Note takers: Christian Amsüss, Rikard Höglund, Mikolai Gütschow</p>
<hr>
<p>Numbers in parentheses are minutes of time allocated.</p>
<h2 id="intro-agenda-status-chairs-10">Intro, agenda, status (Chairs) (10)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=44">https://youtu.be/zNrCp2768QQ?t=44</a></p>
<ul>
<li>WG and document status since IETF 125</li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-chairs-slides-02">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-chairs-slides-02</a></p>
<p><abbr title="Marco Tiloca">MT</abbr> doing introductions (no agenda changes). Going over the Chairs<br>
slides.</p>
<h2 id="uri-path-abbreviation-in-coap-christian-amsuss-10">URI Path Abbreviation in CoAP (Christian Amsüss) (10)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=535">https://youtu.be/zNrCp2768QQ?t=535</a></p>
<ul>
<li><a href="https://datatracker.ietf.org/doc/draft-ietf-core-uri-path-abbrev/">https://datatracker.ietf.org/doc/draft-ietf-core-uri-path-abbrev/</a></li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-uri-path-abbreviation-in-coap-02">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-uri-path-abbreviation-in-coap-02</a></p>
<p><abbr title="Christian Amsüss">CA</abbr> presenting.</p>
<p><abbr title="Christian Amsüss">CA</abbr>: This document is in post WG Last Call. Next step: Shepherd review by<br>
Carsten Bormann.</p>
<h2 id="conditional-query-parameters-bilhanan-silverajan-10">Conditional Query Parameters (Bilhanan Silverajan) (10)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=680">https://youtu.be/zNrCp2768QQ?t=680</a></p>
<ul>
<li><a href="https://datatracker.ietf.org/doc/draft-ietf-core-conditional-attributes/">https://datatracker.ietf.org/doc/draft-ietf-core-conditional-attributes/</a></li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-conditional-query-parameters-for-coap-observe-00">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-conditional-query-parameters-for-coap-observe-00</a></p>
<p><abbr title="Bilhanan Silverajan">BS</abbr> presenting.</p>
<p><abbr title="Bilhanan Silverajan">BS</abbr> (p3): This document is in post WG Last Call. In the latest version,<br>
added tentative value if="core.conditional", indicating server support<br>
for the conditional query parameters.<br>
<abbr title="Bilhanan Silverajan">BS</abbr> (p5): Message flow example for unsupported conditional parameter. The<br>
server ignores non-understood parameters and processes the rests of the<br>
request.<br>
<abbr title="Bilhanan Silverajan">BS</abbr>: Ready to progress? Questions?</p>
<p><abbr title="Marco Tiloca">MT</abbr>: I have provided editorial nits offlist. They can be processed when<br>
processing the Shepherd review.<br>
<abbr title="Jaime Jimenez">JJ</abbr>: Do we need another submission for title and nits?<br>
<abbr title="Marco Tiloca">MT</abbr>: Not needed before the Shepherd review. We will have a new version<br>
addressing that review and the nits.</p>
<p><abbr title="Carsten Bormann">CB</abbr>: The document title is fine. The document name is not fully aligned,<br>
but changing that would be quite traumatic.<br>
<abbr title="Marco Tiloca">MT</abbr>: Then we can proceed with the Shepherd review and write-up.</p>
<h2 id="key-update-for-oscore-rikard-hoglund-10">Key Update for OSCORE (Rikard Höglund) (10)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=1066">https://youtu.be/zNrCp2768QQ?t=1066</a></p>
<ul>
<li><a href="https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/">https://datatracker.ietf.org/doc/draft-ietf-core-oscore-key-update/</a></li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-slides-kudos-core-ietf-126-00">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-slides-kudos-core-ietf-126-00</a></p>
<p><abbr title="Rikard Höglund">RH</abbr> presenting.</p>
<p><abbr title="Rikard Höglund">RH</abbr> (p3): Inspired by Appendix B.2 of <a href="/doc/rfc8613/">RFC 8613</a> (OSCORE).<br>
<abbr title="Rikard Höglund">RH</abbr> (p7): Focus: Implementation Status, 2 implementations interoperated<br>
during the Hackathon.<br>
<abbr title="Rikard Höglund">RH</abbr> (p11): On key and context derivation findings from the interop,<br>
helpful pieces of information will be restated in the draft for clarity.</p>
<p><abbr title="Rikard Höglund">RH</abbr> (p12): Asking for WG Last Call.</p>
<p><abbr title="Carsten Bormann">CB</abbr>: On interop tests: are we really done? Do we need more?<br>
<abbr title="Rikard Höglund">RH</abbr>: We want to do more; we can do that with Francisco again across the<br>
Internet. (E.g., to confirm multiple executions of KUDOS in a row)<br>
<abbr title="Carsten Bormann">CB</abbr>: Should we set a date in September for (remote) interop tests?<br>
<abbr title="Rikard Höglund">RH</abbr>: Good idea.</p>
<p><abbr title="Christian Amsüss">CA</abbr> (on chat): please rename the x byte to something related to what it<br>
does</p>
<h2 id="observe-multicast-notifications-marco-tiloca-10">Observe Multicast Notifications (Marco Tiloca) (10)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=1694">https://youtu.be/zNrCp2768QQ?t=1694</a></p>
<ul>
<li><a href="https://datatracker.ietf.org/doc/draft-ietf-core-observe-multicast-notifications/">https://datatracker.ietf.org/doc/draft-ietf-core-observe-multicast-notifications/</a></li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-observe-multicast-notifications-00">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-observe-multicast-notifications-00</a></p>
<p><abbr title="Marco Tiloca">MT</abbr> presenting.</p>
<p><abbr title="Marco Tiloca">MT</abbr> (p2): Recapping the protocol.<br>
<abbr title="Marco Tiloca">MT</abbr> (p3): Two new versions since the last presentation. Minor updates<br>
also to the companion document not covered today<br>
(<a href="/doc/draft-ietf-core-multicast-notifications-proxy/">draft-ietf-core-multicast-notifications-proxy</a>), whose content was<br>
previously stripped out from the present document.<br>
<abbr title="Marco Tiloca">MT</abbr> (p4-7): Covering a lot of updates done in prior versions.<br>
<abbr title="Marco Tiloca">MT</abbr> (p8): In the payload of the 5.03 informative error response,<br>
typically tp_info is included. However, the semantics of the payload<br>
was changed to define that parameter as formally optional. For example,<br>
there are cases with proxies (see companion document) where including<br>
that parameter would not be strictly needed. Those are special cases.<br>
Normally, like in this document, that parameter is present.<br>
<abbr title="Marco Tiloca">MT</abbr> (p9): Also added a section about operational considerations.<br>
<abbr title="Marco Tiloca">MT</abbr> (p10): There is a working implementation in Java, tested both without<br>
and with security. The implementation is at<br>
<a href="https://github.com/adriankastrati/californium-thesis-work/tree/multicast-notifications">https://github.com/adriankastrati/californium-thesis-work/tree/multicast-notifications</a></p>
<p><abbr title="Marco Tiloca">MT</abbr> (p11): Ready for WG Last Call?</p>
<p><abbr title="Carsten Bormann">CB</abbr>: Just 1 implementation? Interops with itself?<br>
<abbr title="Marco Tiloca">MT</abbr>: Yes; it took a lot of work to produce it.<br>
<abbr title="Carsten Bormann">CB</abbr>: How to recruit more implementers?<br>
<abbr title="Christian Amsüss">CA</abbr>: I plan to implement it too.</p>
<p><abbr title="Carsten Bormann">CB</abbr>: So the next step is gaining implementation experience. I think that<br>
we want one more round of implementation testing before the WG Last<br>
Call.</p>
<p><abbr title="Alexander Pelov">AP</abbr> (on chat): I would be interested in giving a try on implementing<br>
this. @Marco, is there a git repo I can clone and try to run some code<br>
against?<br>
<abbr title="Marco Tiloca">MT</abbr> (on chat): @Alex, that would be great! Please see the repo that was<br>
linked in slide 10:<br>
<a href="https://github.com/adriankastrati/californium-thesis-work/tree/multicast-notifications">https://github.com/adriankastrati/californium-thesis-work/tree/multicast-notifications</a></p>
<h2 id="non-traditional-response-forms-carsten-bormann-10">Non-traditional Response Forms (Carsten Bormann) (10)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=2372">https://youtu.be/zNrCp2768QQ?t=2372</a></p>
<ul>
<li><a href="https://datatracker.ietf.org/doc/draft-ietf-core-responses/">https://datatracker.ietf.org/doc/draft-ietf-core-responses/</a></li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-coap-non-traditional-response-forms-00">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-coap-non-traditional-response-forms-00</a></p>
<p><abbr title="Carsten Bormann">CB</abbr> presenting.</p>
<p><abbr title="Carsten Bormann">CB</abbr>: The previous talk was an example of this.<br>
<abbr title="Carsten Bormann">CB</abbr>: In 13 years, we did things that now need finding commonalities. We<br>
might have common code in implementations.<br>
<abbr title="Carsten Bormann">CB</abbr> (p2): Non-matching: e.g., a response to a multicast request does not<br>
have a source address showing the target where the request was sent to. </p>
<p><abbr title="Carsten Bormann">CB</abbr> (p3): This draft is a general discussion about this particular<br>
responses plus proposed CoAP options.<br>
<abbr title="Carsten Bormann">CB</abbr> (p3): Beyond these general options, others pre-exist (e.g., Q-Block).<br>
The Respond-To Option would need many security discussions for specific<br>
cases, so maybe it is better to just have per-case CoAP options and keep<br>
specifically the Respond-To Option in the backburner for now.<br>
<abbr title="Carsten Bormann">CB</abbr> (p4): Current proposal from the authors.<br>
<abbr title="Carsten Bormann">CB</abbr> (p5): Are we ready to go forward with the Response-For Option?<br>
<abbr title="Carsten Bormann">CB</abbr>: The Leisure-For-Responses Option means "send me up to N more<br>
responses, in addition to the requested response"; we could have extra<br>
variations that mean "I will be ready to receive for N seconds".<br>
<abbr title="Carsten Bormann">CB</abbr>: Implementation question; so we will not finish this next week.</p>
<p><abbr title="Marco Tiloca">MT</abbr>: On the Leisure-For-Responses Option: the mentioned variation is<br>
being specialized in <a href="/doc/draft-ietf-core-groupcomm-proxy/">draft-ietf-core-groupcomm-proxy</a> with the<br>
Multicast-Timeout Option intended to a proxy, by which the client says:<br>
"For this number of seconds, I am happy to receive multiple responses to<br>
this request that I am asking to be proxied over multicast". So there is<br>
a partial overlap.<br>
<abbr title="Carsten Bormann">CB</abbr>: We can point to it.<br>
<abbr title="Esko Dijk">ED</abbr>: We could rename the option in <a href="/doc/draft-ietf-core-groupcomm-proxy/">draft-ietf-core-groupcomm-proxy</a> to<br>
make it more general...<br>
<abbr title="Carsten Bormann">CB</abbr>: The Leisure-For-Responses Option indeed rather fits with timeouts<br>
instead of with counting.<br>
<abbr title="Christian Amsüss">CA</abbr> nodding vigorously.<br>
<abbr title="Esko Dijk">ED</abbr>: Still, we can generalize. At the same time, the Multicast-Timeout<br>
Option in <a href="/doc/draft-ietf-core-groupcomm-proxy/">draft-ietf-core-groupcomm-proxy</a> is for requests to be proxied<br>
over multicast. I do not think that we defined an analogous semantics<br>
for fully unicast requests.<br>
<abbr title="Christian Amsüss">CA</abbr>: It makes sense for unicast, we will just require an option to make<br>
the responses non-matching. We have it in Onion CoAP: "I am sending you<br>
this message but the hostname is actually YYY". We should generalize<br>
that, we have ways of using it already in a number of drafts.<br>
<abbr title="Christian Amsüss">CA</abbr> (on chat): Correcting myself from earlier: The option for unicast<br>
sensibility is in multicast-proxy; the options in Onion OSCORE are<br>
related but not right the ones we need here.</p>
<p><abbr title="Esko Dijk">ED</abbr> (on chat): Also: are we happy to keep the last option on the<br>
backburner - yes ok for me! We can describe its general design.</p>
<h2 id="coreconf-comi-yang-library-yang-metadata-carsten-bormann-15">CORECONF: COMI, YANG Library, YANG Metadata (Carsten Bormann) (15)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=3159">https://youtu.be/zNrCp2768QQ?t=3159</a></p>
<ul>
<li>
<p><a href="https://datatracker.ietf.org/doc/draft-ietf-core-comi/">https://datatracker.ietf.org/doc/draft-ietf-core-comi/</a></p>
</li>
<li>
<p><a href="https://datatracker.ietf.org/doc/draft-ietf-core-yang-library/">https://datatracker.ietf.org/doc/draft-ietf-core-yang-library/</a></p>
</li>
<li>
<p><a href="https://datatracker.ietf.org/doc/draft-ietf-core-yang-metadata/">https://datatracker.ietf.org/doc/draft-ietf-core-yang-metadata/</a></p>
</li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-coreconf-unified-datastore-00">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-coreconf-unified-datastore-00</a></p>
<p><abbr title="Vojtěch Vilímek">VV</abbr> presenting.</p>
<p><abbr title="Carsten Bormann">CB</abbr>: Vojtěch will cover most of this slot, except for the topic of YANG<br>
metadata. Who knows what YANG metadata are? (5 hands raising)</p>
<p><abbr title="Vojtěch Vilímek">VV</abbr> (p1-5): Introducing the topic, giving examples.<br>
<abbr title="Vojtěch Vilímek">VV</abbr> (p5): Utilizing RESTful design; a message is a transaction performed<br>
automatically.<br>
<abbr title="Vojtěch Vilímek">VV</abbr> (p5-6): For constrained environments, a transaction is<br>
resource-heavy.<br>
<abbr title="Vojtěch Vilímek">VV</abbr> (p7-8): Solution proposal with respect to encoding.</p>
<p><abbr title="Christian Amsüss">CA</abbr>: I have no experience with YANG, but, for implementing CoAP servers<br>
and CBOR, having that list seems very useful.</p>
<p><abbr title="Carsten Bormann">CB</abbr>: For context: COMI is pretty old (~2013). It took time to find how to<br>
optimize it with SIDs, but the rest was clear early. NMDA was created in<br>
parallel in NETCONF; it was ignored until a reviewer asked about it. Use<br>
cases did not touch on the problem points, and the unified store was<br>
created. But it disagrees with reality and make-before-break is<br>
realistic.<br>
<abbr title="Vojtěch Vilímek">VV</abbr> (later): The list can still be indefinite-length.</p>
<p><abbr title="Esko Dijk">ED</abbr>: If one of the items fails, it is skipped it. Is there any feedback<br>
given?<br>
<abbr title="Vojtěch Vilímek">VV</abbr>: The structure of the response is not yet decided. The tentative idea<br>
is to give feedback.</p>
<p><abbr title="Carsten Bormann">CB</abbr>: The CoAP toolkit has two things: <a href="/doc/rfc8710/">RFC 8710</a> on multipart<br>
Content-Format, and <a href="/doc/rfc9290/">RFC 9290</a> on concise problem details. Instead, in<br>
COMI, we invented YANG-based problem details, which received<br>
not-so-happy comments (probably we need problem-details anyway). We<br>
might throw out the part of that because we have new tools now.</p>
<p><abbr title="Alexander Pelov">AP</abbr>: We are working in this area for 13 years now. Can we just ship<br>
something simple and then do transactions/NMDA like "and here is how you<br>
do it"?<br>
<abbr title="Vojtěch Vilímek">VV</abbr>: We want to strip out the transaction semantics. The current text<br>
would require rolling back, hence we are proposing those solutions. Then<br>
we can fix atomicity in a later document.<br>
<abbr title="Carsten Bormann">CB</abbr>: Atomicity would be an extension, while doing simple thing first.</p>
<p><abbr title="Ivaylo Petrov">IP</abbr>: So, now we can get into an inconsistent state, but people should be<br>
careful how they implement things?<br>
<abbr title="Vojtěch Vilímek">VV</abbr>: Yes, but the server should not care, and the client should create a<br>
message that does not create inconsistencies (and if it does, it gets<br>
repaired in the response).</p>
<p><abbr title="Esko Dijk">ED</abbr>: If you do not want PATCH, you can also use POST, and a future<br>
document does proper PATCH.<br>
<abbr title="Vojtěch Vilímek">VV</abbr>: This in p8 uses PATCH. A POST would be connected to the YANG RPCs<br>
and actions (i.e., POST is used for something else).<br>
<abbr title="Esko Dijk">ED</abbr>: We can just avoid PATCH now and other-PATCH with different<br>
semantics.<br>
<abbr title="Vojtěch Vilímek">VV</abbr>: Semantics should be from options in the message.</p>
<h2 id="oscore-capable-proxies-rikard-hoglund-10">OSCORE-capable Proxies (Rikard Höglund) (10)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=4122">https://youtu.be/zNrCp2768QQ?t=4122</a></p>
<ul>
<li><a href="https://datatracker.ietf.org/doc/draft-ietf-core-oscore-capable-proxies/">https://datatracker.ietf.org/doc/draft-ietf-core-oscore-capable-proxies/</a></li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-oscore-capable-proxies-slides-core-ietf-126-00">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-oscore-capable-proxies-slides-core-ietf-126-00</a></p>
<p><abbr title="Rikard Höglund">RH</abbr> presenting.</p>
<p><abbr title="Rikard Höglund">RH</abbr>: Scope.<br>
<abbr title="Rikard Höglund">RH</abbr>: Completed addressing a review from Christian (two points were still<br>
not addressed).<br>
<abbr title="Rikard Höglund">RH</abbr> (p4): To address one point, we improved the presentation of the<br>
algorithm for processing incoming requests. The logic and outcome of the<br>
algorithm have not changed.<br>
<abbr title="Rikard Höglund">RH</abbr> (p5-6): For the other point, we have described how a proxy can<br>
determine when establishing/using OSCORE with an origin server. That<br>
includes discovering support/capabilities of the origin server, which<br>
can rely on DNS discovery and new SvcParamKeys. Register SvcParamKeys?<br>
<abbr title="Rikard Höglund">RH</abbr> (p7): We also included one more example of message exchange, with two<br>
proxies in a chain.<br>
<abbr title="Rikard Höglund">RH</abbr> (p8): There are two implementations (one in Java and one in Contiki<br>
NG) that successfully interoperated.<br>
<abbr title="Rikard Höglund">RH</abbr> (p9): Next steps: handling of multiple responses a-la Group OSCORE;<br>
operational consideration.</p>
<p><abbr title="Marco Tiloca">MT</abbr>: About next steps (related to p5), we can also define actual<br>
SvcParamKeys to be registered (they are simple compared to other ones we<br>
defined in other documents). Seeking feedback about it.</p>
<h2 id="kem-for-group-oscore-marco-tiloca-10">KEM for Group OSCORE (Marco Tiloca) (10)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=4695">https://youtu.be/zNrCp2768QQ?t=4695</a></p>
<ul>
<li><a href="https://datatracker.ietf.org/doc/draft-tiloca-core-group-oscore-kem/">https://datatracker.ietf.org/doc/draft-tiloca-core-group-oscore-kem/</a></li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-kem-for-group-oscore-00">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-kem-for-group-oscore-00</a></p>
<p><abbr title="Marco Tiloca">MT</abbr> presenting.</p>
<p><abbr title="Marco Tiloca">MT</abbr> (p1): See also the Monday presentation in ACE:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-ace-20260720-ace-oscore-gm-kem-00">https://datatracker.ietf.org/meeting/126/materials/slides-126-ace-20260720-ace-oscore-gm-kem-00</a></p>
<p><abbr title="Marco Tiloca">MT</abbr> (p2): Motivation for needing this. In the pairwise mode of Group<br>
OSCORE, the derivation of pairwise keys is currently not quantum<br>
resistant.<br>
<abbr title="Marco Tiloca">MT</abbr> (p3): Goal: Make the Group OSCORE pairwise mode quantum resistant.<br>
<abbr title="Marco Tiloca">MT</abbr> (p4): New way to derive pairwise keys using a KEM (e.g., <abbr title="Martine Lenders">ML</abbr>-KEM).<br>
Most things in the derivation stay the same; the only change is using<br>
two different secrets (i.e., one per pairwise key), derived through the<br>
KEM used in the group. The Group Manager facilitates the exchange of KEM<br>
public keys and KEM ciphertexts among the group members (similar to the<br>
support for exchanging public authentication credentials).<br>
<abbr title="Marco Tiloca">MT</abbr> (p5): Detailed functionality.<br>
<abbr title="Marco Tiloca">MT</abbr> (p6): Requirements for GM that supports this. These are kept at a<br>
high-level in this document. The details depend on the specific<br>
realization of Group Manager. An example is given in the ACE document<br>
presented on Monday. That document is<br>
<a href="https://datatracker.ietf.org/doc/draft-tiloca-ace-oscore-gm-kem/">https://datatracker.ietf.org/doc/draft-tiloca-ace-oscore-gm-kem/</a><br>
<abbr title="Marco Tiloca">MT</abbr> (p7): There is a placeholder section to be completed, intended to<br>
provide details and guidelines when the KEM used is specifically <abbr title="Martine Lenders">ML</abbr>-KEM.<br>
That can take the same style and approach used by other documents about<br>
the same topic.</p>
<p><abbr title="Christian Amsüss">CA</abbr>, clarifying: What's the attack that a quantum computer can do? It<br>
would break into the pairwise mode, but it still needs the group key, so<br>
it would "just" defeat source authentication and limit confidentiality<br>
from the pair to the group? (As IIRC that goes into the pairwise key).<br>
The group Master Secret is still protecting group confidentiality as a<br>
whole?<br>
<abbr title="Marco Tiloca">MT</abbr>: Yes. Good point to clarify in this security considerations.</p>
<p><abbr title="Renzo Navas">RN</abbr>: I will gladly review this document, latest before the next IETF<br>
meeting.</p>
<h2 id="yang-sid-discovery-using-dns-laurent-toutain-10">YANG SID Discovery using DNS (Laurent Toutain) (10)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=5229">https://youtu.be/zNrCp2768QQ?t=5229</a></p>
<ul>
<li><a href="https://datatracker.ietf.org/doc/draft-toutain-core-sid-encoding/">https://datatracker.ietf.org/doc/draft-toutain-core-sid-encoding/</a></li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-sid-in-dns-00">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-sid-in-dns-00</a></p>
<p><abbr title="Laurent Toutain">LT</abbr> presenting remotely.</p>
<p><abbr title="Laurent Toutain">LT</abbr> (p1): How can we put SIDs into DNS? When you receive CORECONF data,<br>
you want to understand the received data and find out what the SIDs<br>
actually mean.<br>
<abbr title="Laurent Toutain">LT</abbr>: Why on DNS? It exists, it is queryable, and it is already used for<br>
this kind of mapping.<br>
<abbr title="Laurent Toutain">LT</abbr>: YT is short for "YANG Tracker" (and French island). We ultimately<br>
want a domain like .sid.iana<br>
<abbr title="Laurent Toutain">LT</abbr>: On megaranges. (In particular, SNMP users have PENs that are usable<br>
with SIDs).<br>
<abbr title="Laurent Toutain">LT</abbr>: Example of querying DNS to get a pointer to a SID file. The<br>
serialization may be result of multiple YANG models.<br>
<abbr title="Laurent Toutain">LT</abbr>: Proposal on ranges. PENs are better for internal use, but things can<br>
move between companies.<br>
<abbr title="Laurent Toutain">LT</abbr>: Registrars can maintain integrity.<br>
<abbr title="Laurent Toutain">LT</abbr> (p8): Open questions.</p>
<p><abbr title="Christian Amsüss">CA</abbr>: Considerations from dereferenceable identifiers apply; in<br>
particular, "hey someone opened my file, because they hit my DNS".<br>
<abbr title="Christian Amsüss">CA</abbr> (note to self): tie in in<br>
<a href="https://christian.amsuess.com/idea-incubator/media-types/">https://christian.amsuess.com/idea-incubator/media-types/</a></p>
<p><abbr title="Jaime Jimenez">JJ</abbr> (on chat): Is SID+DNS intended for local/private networks (DNS-SD,<br>
mDNS) or Internet-wide too? I would assume DNS folks may complain of<br>
this use.</p>
<p><abbr title="Maria Matějka">MM</abbr>: I have many questions. What happens when a company/server goes down?<br>
The document needs IANA actions: complete the procedure on how to<br>
register DNS sets for every PEN, and another to check if the contact<br>
information is accurate. I could go on. Did you think of these problems?</p>
<p><abbr title="Laurent Toutain">LT</abbr>: If a company goes down, the SID cannot be allocated anymore but the<br>
YANG data model exists. So, a registrar could maintain this allocation,<br>
I need to study this case. on the IANA actions, yes, we need to see that<br>
too.</p>
<p><abbr title="Vojtěch Vilímek">VV</abbr>: <a href="/doc/rfc9595/">RFC 9595</a> already talks about how the registry should look like, if<br>
there are requests for megaranges. Is this needed? What is the<br>
relationship?<br>
<abbr title="Laurent Toutain">LT</abbr>: Good point. We have a link to the SID-file that is not "secure". One<br>
mapping can be between a number and a namespace, then there is a query<br>
for the data model.</p>
<p><abbr title="Christian Amsüss">CA</abbr>: Especially when considering delegation, this may cause a privacy<br>
situation. Opening a file can be revealed through dereferencing (here<br>
contacting a DNS server). See Carsten Bormann's and my document<br>
<a href="https://datatracker.ietf.org/doc/draft-bormann-t2trg-deref-id/">deref-id</a>; it might have more questions than answers though.</p>
<p><abbr title="Vojtěch Vilímek">VV</abbr>: For the delegation, the registrar would need to be paid. No one will<br>
pay if the company goes bankrupt. It could be about some old product<br>
sold long ago. I do not see that delegation will work. Maybe we can<br>
mandate devices to carry their own SID file inside them.<br>
<abbr title="Laurent Toutain">LT</abbr>: That means sending SID files when you send information. With respect<br>
to the business model, it needs study. It will be different from DNS<br>
names (where you lose the name).</p>
<p><abbr title="Alexander Pelov">AP</abbr>: The SID RFC talks about registries, it does not speak of an<br>
interface. We could have an HTTP/HTTPS/any interface. This provides DNS<br>
interface to that. The problem around paying is there for anyone. At<br>
that time, we asked IANA, and they said that they will do it for IETF<br>
RFCs.</p>
<p><abbr title="Sandoche Balakrichenan">SB</abbr>: I appreciate the questions from Maria Matějka. Have you seen such<br>
use cases before with RFID and IEEE identifiers? As a registry we feel<br>
it is economic.</p>
<p><abbr title="Esko Dijk">ED</abbr>: I agree with Alexander and Maria. The IETF could host this for their<br>
registered modules/SIDs. A megarange could just even have things on<br>
paper and not public, and only used internally. So, no general solution.<br>
For IETF standardized ones, it works. We do not require companies to<br>
publish or expose anything. So, the solution would only cover part of<br>
the SID space and, without 100% coverage, it might not catch on. The use<br>
case is not clear from the presentation, but I should read the draft.<br>
<abbr title="Laurent Toutain">LT</abbr>: The goal is that you need to understand all SIDs in the information<br>
you got, and those may come from different spaces.<br>
<abbr title="Esko Dijk">ED</abbr>: Could it be already built into the software?<br>
<abbr title="Laurent Toutain">LT</abbr>: I had a demo during the Hackathon. We can discuss more.</p>
<p><abbr title="Maria Matějka">MM</abbr> (on chat): thinking through the SID-DNS over and over again, i'm<br>
still convinced that as soon as a device is sold to a customer, it<br>
should be self-contained enough to allow querying its own yang module<br>
and sid file directly. i know that it needs some bytes but consider that<br>
both files can be pre-compressed, and generally the scale of the code is<br>
at best linear with the size of the YANG model and SID file. all in all,<br>
i don't expect the inclusion of the sidfile and yang module to eat a<br>
significant amount of rom/nvram/flash compared to the necessary<br>
parser/encoder code<br>
<abbr title="Laurent Toutain">LT</abbr> (on chat): Yes the device, but the one that receives the message from<br>
the device ... does it have to be configured with all the SID files to<br>
understand the message<br>
<abbr title="Maria Matějka">MM</abbr> (on chat): if it receives a message from a device, it should be able<br>
to query the same device for the sid file and yang module<br>
<abbr title="Laurent Toutain">LT</abbr> (on chat): a SID file can be very big and in a constrained<br>
environment it may be difficult to get.<br>
<abbr title="Maria Matějka">MM</abbr> (on chat): there is no reason to have a SID file unproportionally big<br>
to the constrained environment size → if you are able to process a<br>
complicated YANG, you are obviously able to store a similarly<br>
complicated YANG file and SID file. If you have a monolithic YANG file<br>
and SID file for lots of different machines, and each one is producing<br>
only a small portion of these, then you did a bad modeling job, and you<br>
should have split the modules and cleaned them up so that they contain<br>
only necessary things. People lose files, services go dead, even a<br>
simple static YANG+SID HTTP endpoint will go 410 eventually, and you are<br>
stranded with a device communicating just by weird numbered structures<br>
with no keys to the numbers</p>
<h2 id="coap-extensions-for-task-resources-linzhe-li-10">CoAP Extensions for Task Resources (Linzhe Li) (10)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=6413">https://youtu.be/zNrCp2768QQ?t=6413</a></p>
<ul>
<li><a href="https://datatracker.ietf.org/doc/draft-li-coap-task-resources/">https://datatracker.ietf.org/doc/draft-li-coap-task-resources/</a></li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-coap-extensions-for-asynchronous-task-resources-01">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-coap-extensions-for-asynchronous-task-resources-01</a></p>
<p><abbr title="Linzhe Li">LL</abbr> presenting.</p>
<p><abbr title="Linzhe Li">LL</abbr>: The goal is to provide a way to control/monitor long-running tasks<br>
on a server.<br>
<abbr title="Linzhe Li">LL</abbr>: The pattern is common, but the implementation is<br>
application-specific.<br>
<abbr title="Linzhe Li">LL</abbr>: Monitoring the task allowed us to identify a fault more quickly.<br>
<abbr title="Linzhe Li">LL</abbr>: Showing task life cycle and states.<br>
<abbr title="Linzhe Li">LL</abbr>: Details on interaction with tasks, new Content-Format used.<br>
<abbr title="Linzhe Li">LL</abbr>: Open issues. Useful abstraction? Aligning with other solutions?</p>
<p><abbr title="Christian Amsüss">CA</abbr>:</p>
<ul>
<li>The pattern looks familiar.</li>
<li>At what level are you describing the tasks? Some look familiar from<br>
  uploading firmware items (spawning a process). Introspection would be<br>
  about getting a backtrace for that execution.</li>
<li>Is it to the level of uploading binary code? Or getting a percentage<br>
  of completion?</li>
<li>Introspection: comparison to remote debugging (thread backtrace), and<br>
  upload of virtual machines? (p8 indicates from percentage that this is<br>
  planned for high-level operations, but is this continuous from low- to<br>
  high-level?)<br>
  <abbr title="Linzhe Li">LL</abbr>: It is for lifecycle. Maybe you can suggest use cases to generalize<br>
  this.</li>
</ul>
<p><abbr title="Carsten Bormann">CB</abbr>: This draft is in version -01 now. We could see the first version -00<br>
last week. We had a lot of comments, all taken into account here in<br>
version -01, so very good.<br>
<abbr title="Carsten Bormann">CB</abbr>: The classical case was the CoAP coffee machine.</p>
<p><abbr title="Marco Tiloca">MT</abbr>: The draft considers access control already (pointing to the ACE<br>
framework, <a href="/doc/rfc9200/">RFC 9200</a>), separating the permission for the application<br>
resource from the permissions for the task resource. Looking at AIF (RFC<br>
9237) may be a good way to enforce access control in this spirit.</p>
<p><abbr title="Esko Dijk">ED</abbr> (on chat): I just <a href="https://mailarchive.ietf.org/arch/msg/core/QmSyO6JOuy7aXoxw7NBEGIN1RkA/">mailed the list</a> - seeing some similarity<br>
between the 'task' lifecycle and PubSub<br>
<a href="https://datatracker.ietf.org/doc/html/draft-ietf-core-coap-pubsub-21#name-topic-lifecycle">https://datatracker.ietf.org/doc/html/draft-ietf-core-coap-pubsub-21#name-topic-lifecycle</a><br>
(even though different)<br>
<abbr title="Christian Amsüss">CA</abbr> (on chat): It's different but there is the similarity that beyond the<br>
CRUD pattern, it has a pair of resources that, in Linzhe's case, might<br>
be "instructions" and "state" and "outcome"<br>
<abbr title="Jaime Jimenez">JJ</abbr> (on chat): We also had that pattern (create a resource for async<br>
check the state of an operation) in lwm2m long ago if i remember right.<br>
it is a common pattern<br>
<abbr title="Jaime Jimenez">JJ</abbr> (on chat): coap has the beauty of observe + query parameters to also<br>
be notified instead of polling. Very neat!</p>
<h2 id="coap-message-diagnostic-notation-jaime-jimenez-carsten-bormann-5">CoAP Message Diagnostic Notation (Jaime Jiménez / Carsten Bormann) (5)</h2>
<p>Video: <a href="https://youtu.be/zNrCp2768QQ?t=7021">https://youtu.be/zNrCp2768QQ?t=7021</a></p>
<ul>
<li><a href="https://datatracker.ietf.org/doc/draft-jimenez-core-coap-diag/">https://datatracker.ietf.org/doc/draft-jimenez-core-coap-diag/</a></li>
</ul>
<p>Presented slides:<br>
<a href="https://datatracker.ietf.org/meeting/126/materials/slides-126-core-coap-diagnostic-message-notation-00">https://datatracker.ietf.org/meeting/126/materials/slides-126-core-coap-diagnostic-message-notation-00</a></p>
<p><abbr title="Carsten Bormann">CB</abbr> presenting.</p>
<p><abbr title="Carsten Bormann">CB</abbr>: Also in the informational space. We are now into 15 years of writing<br>
up CoAP interactions in 1000 different ways.<br>
<abbr title="Carsten Bormann">CB</abbr>: The problem is the varying notation used, with no clear convention<br>
and no CI.<br>
<abbr title="Carsten Bormann">CB</abbr>: Let's fix the 80%. Showing proposed notation and examples.<br>
<abbr title="Carsten Bormann">CB</abbr>: Open questions. Try to apply it to your draft examples. We will<br>
eventually integrate this into the draft toolchain.<br>
(many nods in the room)</p>
<p><abbr title="Mikolai Gütschow">MG</abbr>: Good idea to formalize. It may also be useful for diagnostics (with<br>
Wireshark). On non-traditional responses, how to handle this?<br>
<abbr title="Carsten Bormann">CB</abbr>: Good question. We can already distinguish a request from a response<br>
using the Code field. The easy answer is to just write down multiple<br>
responses.</p>
<p><abbr title="Christian Amsüss">CA</abbr>: It makes sense for CLI clients.</p>
<p><abbr title="Martine Lenders">ML</abbr>: I will have a look. Does it support multiple formats for the<br>
payload? Like hexadecimal and human-readable?<br>
<abbr title="Carsten Bormann">CB</abbr>: Good comment. <a href="https://datatracker.ietf.org/doc/draft-ietf-cbor-edn-literals/">CDN</a> is learning to do that.</p>
<p><abbr title="Marco Tiloca">MT</abbr>: Please review.<br>
<abbr title="Carsten Bormann">CB</abbr>: ... and apply the notation to the examples in your drafts.</p>
<p>Σ 120<br>
Video: <a href="https://youtu.be/zNrCp2768QQ?t=7541">https://youtu.be/zNrCp2768QQ?t=7541</a></p>
<hr>
    <script>(function(){function c(){var b=a.contentDocument||(a.contentWindow&&a.contentWindow.document);if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'a21a8b54d8cc3438',t:'MTc4NTE0Mzc3NQ=='};var a=document.createElement('script');a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>