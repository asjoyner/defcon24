# Bypassing Captive Portals and Limited Networks

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Bugher)

## Summary
Nothing particularly new, but a very nice overview of the available options, and tooling recommendations.  I should really bother to setup an Iodine end point, and script up the "watch for a working MAC to stop being used" suggestion.

## Notes
Submitted as a DEFCON 101 talk, but they stuck him in Track 1 because rightly they knew it would be popular, and indeed it filled the room.

Captive Portals aren't real security, just reliant on "obient" network clients.  Typically MAC filtering on the gateway with iptables rules.

Typically, everything's just Chilispot, requires webserver and RADIUS.

Even if it's not, it's basically still just the same idea, indistinguishable from the network.

#### Need to prepare
Have an endpoint to tunnel to.  Don't have to use a cleartet protocol, but need something on the other end.

Need a port or protocol that the captive portal isn't blocking.

Tpyically SSH on 22 or 3128
Iodine?

AppEngine uses Google IPs, so often allowed by captive portal proxies, Mirrorrr might be useful

#### Iodine
IP over DNS, the plausible choice.

#### Client setup
Have to setup the client in advance, as you won't have an internet connection when you want to start doing this.

* Iodine
* Wireshark or tcpdump
* nmap
* script up the sniffing of mac and waiting for one to stop being used?

#### Recon and proxy
1. Inspect the gateway and the subnet, look for TCP or DNS.  Random ports might be proxies.  Works surprisingly often.o
1. Try seting proxy to your appengine endpoint.
1. Try Iodine

#### If that fails...
1. Look for a MAC address that is used for a while, then isn't used.
1. Clone that MAC.
1. Profit.


