# csharp-dns-server

Fully functional DNS server written in C#.

The project was written to provide DNS services within a datacentre, specifically to remove the need for an expensive load-balancer device by providing round-robin DNS services, and retrying connectivity instead.

## Licence
This software is licenced under MIT terms that permits reuse within proprietary software provided all copies of the licensed software include a copy of the MIT License terms and the copyright notice.  See [licence.txt](./licence.txt)

## Features

As written, the server has a number of intrinsic features:

 - Pluggable Zone Resolver.  Host one or more zones locally, and run your code to resolve names in that zone.  Enables many complex scenarios such as:
 - round-robin load-balancing.  Distribute load and provide failover with a datacentre without expensive hardware.
 - health-checks.  While maintaining a list of machines in round-robin for a name, the code performs periodic healthchecks against the machines, if necessary removing machines that fail the health checks from rotation.
 - time-based constraints. Parental controls blockage of Facebook.
 - Delegates all other DNS lookup to host machines default DNS server(s)

The DNS server also has a builtin basic Web Server providing operational insight into the server behaviour.
- healthcheck for server status
- counters
- zone information

## Challenges

### Testing
Much time was spent using Netmon to capture real DNS challenges and verify that the C# DNS server responded appropriately.

### DNS-Sec
No effort made to handle or respond to DNS-Sec challenges.
