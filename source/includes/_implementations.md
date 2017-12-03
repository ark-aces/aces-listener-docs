
# Implementations

The ACES Listener API defines a standard protocol to facilitate the consumption
of blockchain transaction events across numerous different blockchains. As such, it is a
high level abstraction on top of the different transaction types across blockchains and
needs to be implemented separately for each blockchain. 

The ACES Listener API specifies only the base necessary capabilities for consuming blockchain
transaction events in a generic way that can be supported across many different blockchains.
All implementations conforming to the ACES Listener API specification can be 
consumed using the common client libraries and processing logic, allowing different blockchains
to be easily plugged into an application, including ACES Services.

In the future we may add API Capability Interfaces that can define more advanced implementations
for subscribing to and consuming blockchain events such as searching or filtering on event
streams.
