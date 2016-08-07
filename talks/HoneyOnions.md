# Honey Onions
Exposing Snooping Tor HSDir Relays

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Noubir)

## Summary
HSDir relays are probably snooping on you.

## Notes

How many Tor relays are misbehaving?  Mostly affecting hidden services.

Amusingly, he asked how many people use tor?  run a relay?  are running a hidden service on tor?

He gave a brief overview of Tor, its uses, and hidden services.

Trying to find out how many relays misbehave, trying to get a feel of how many hidden services exist, by having modified the Tor code to log what's happening, etc.  Specifically not concerned with other vulnerabilities, eg. exit-relays which are snooping.

Tor authors are working on detecting and exposing this behavior, but their techniques are different.  Four questions to address.

1. How many hosts are misbehaving?
2. Which relays snoop?
3. What else do they do?
4. Who are they?

## Process
Create a Honey Onion (HOnion), and don't tell anyone about the associated hidden service URL.  Run a Hidden Service, serving a white page.  The only people with that URL at the 6 HSDir relays.  Rotate three buckets at daily, weekly, monthly, interavals with 1500 hidden services for each.  Wait to see who visits the services, and as you rotate through you can statistically tell which bad HSDir relay logged and visited your HOnion.  Bipartite graph, math, NP complete, but can approximate smallest set of bad HSDirs, MatLab ILP solver.

## Results
Ran from Feb, 12 2016 to April 24, 2016.
25% are exit nodes, 70% are on cloud uproviders.
Behavior was changed to delay visit from daily or weekly, to weekly or monthly delay.

Who are they?  It's hard to know, might try to figure that out in later research.
