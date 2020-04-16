Unsolicited responses
=====================

```
Req: GET /.well-known/core

Res: 2.05 Content
Payload: </firmware>,</food-preference>

Res: 2.05 Content
Response-For: GET /food-preference
Payload: vegan
```

----

Use cases
---------

* [draft-bormann-core-responses-00](https://tools.ietf.org/html/draft-bormann-core-responses-00): configured setups, triangles
* Block2 transfer with window size (reference lost)
* [DOTS](https://mailarchive.ietf.org/arch/msg/core/H4NM0doO_ZzaHdkm5Op9UukP3-4/): Observation for more than first block
* Cache prepopulation
* Multicast notifications

Usable tokens
-------------

* Prolonging a prior request's token usage time
* Agreeing on a token out-of-(message-layer)-band agreement
* Option that changes the rules

<!--
Prior art
---------

* Observation
* Multicast
* HTTP/2 push
-->

Dirctions
---------

* Take up
* Reject
