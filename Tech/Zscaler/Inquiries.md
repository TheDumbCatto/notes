# Connectivity service
- As Z-tunnel 2.0 already forwards all traffic to ZCC at network level, what use is the optional included proxy settings?
> Is it to configure proxy-aware traffic that needs to bypass ZCC?

- Difference between Enforce Proxy mode vs Tunnel with Local Proxy?
> *In **Enforce Proxy** mode, Zscaler Client Connector enforces system proxy settings as specified, without tunneling any traffic.*
> -> Does this mean the proxy configured on the local system will point directly to the Zscaler cloud, and not to ZCC?