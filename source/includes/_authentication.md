
# Authentication

The ACES Listener API does not define any authentication method at this time.
This allows any consumer to subscribe to and receive listener blockchain event data. If an
ACES Listener provider needs more security around subscriptions, they can host
their instance on private network or implement `HTTP Basic Auth` for their web server and
require consumers to send an `Authorization` header with valid credentials.
