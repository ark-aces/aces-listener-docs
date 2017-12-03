
# Versions

ACES Listeners instances can upgrade to new backwards compatible versions without
breaking client integrations. ACES defines backwards compatible changes as any of the following:

- Adding new API endpoints
- Adding new optional request parameters
- Adding new response properties
- Changing length or format of String properties

If breaking changes to the ACES Listener must be made, the provider needs to launch a new
version in parallel at a different URL and have clients re-subscribe to the new version URL. 

