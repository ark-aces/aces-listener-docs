
# Overview

```shell
curl 'http://aces-listener-bitcoin.domain.com' \
-X POST \
-d '{
   "callbackUrl": "http://consumer.domain.com/handler",
   "minConfirmations": 5
}'
```

```java
ApiClient apiClient = new ApiClient();
apiClient.setBasePath("http://aces-listener-bitcoin.domain.com");
AcesListenerApi api = new AcesListenerApi(apiClient);

SubscriptionRequest request = new SubscriptionRequest();
request.setCallbackUrl("http://consumer.domain.com/handler");
request.setMinConfirmations(5);

api.createSubscription(request);
```

> After subscribing, the ACES Listener will `POST` Bitcoin transaction data to the
 to `http://consumer.domain.com/handler`:
  
```json
{
  "id": "93598235283502398502398",
  "createdAt": "2017-11-01T00:00:00.000Z",
  "status": "new",
  "tries": 1,
  "data": {
    "hex": "01000000019a9aa57825106e72c92c0c771b88a9f7bbdd399d12e405e29757964f9a387ef0000000006b483045022100fdac2e51068717da7f564ae676d84f04aa6e5157b72c168301809518bc8e733902200b39ba9d0ee8cd0c5f0ed7a4d51ec2aaf5976252aeca6ffd5b9794076898c463012102892589b5b0e2751bd2500a71f06b2d851439678eb0e976be5b5a0cc8f3e49895ffffffff021caa3900000000001976a914ddaccd2403cfffad5936ca66c2c6a7c98146936888ac9b593001000000001976a91461752641b0bf1cecd08341224f83e690853abd0588ac00000000",
    "txid": "fdcd3564c09ddd33dafd9d1bd2f5dc583f8c818fff631397c7f6d0d12ecf17b4",
    "hash": "fdcd3564c09ddd33dafd9d1bd2f5dc583f8c818fff631397c7f6d0d12ecf17b4",
    "size": 226,
    "vsize": 226,
    ...
  }
}
```

Consumers must subscribe to an ACES Listener API instance to start receiving blockchain
events from the ACES Listener.

Once a consumer has been subscribed, the ACES Listener will start
sending `POST` requests to the registered endpoint for every new blockchain transaction
event.

If the consumer fails to respond to the `POST` with a `200` response (for example if there is
an error processing the event or the server times out), the ACES Listener will try to resend
the request as configured by the ACES Listener.

<img src="images/figures/aces-listener-seq-diagram.png" alt="ACES Listener Sequence Diagram" />

If the ACES Listener tries to post too many events to a consumer without success,
the ACES Listener can cancel the subscription and stop sending events to the consumer.

Consumers can also unsubscribe directly by sending a `POST` request to the Unsubscribe
endpoint.

Developers of ACES Listener APIs can view our sample
[ACES Listener Ark implementation](https://github.com/ark-aces/aces-listener-ark).