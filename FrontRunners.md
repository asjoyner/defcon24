Fontrunning the Frontrunners

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Vixie1)

## Summary

There's apparently no one using NXDOMAIN to detect what domains they should register.

## Notes
People are grabbing resources and holding them for ransom.  Used to be possible to do "domain tasting", within limits.  ICANN shut it down.

Wanted to introspect from their DNS data how common the reading of NXDOMAIN to decide what domains to buy.

Not concerned with Amaterus, who think of names in the shower, but the professionals who do it at scale are getting in the way.  If you can't get "yourname.com", you'll likely choose another name for your company.  DNS should be available for people who want to add value to the internet, not do expense at the .

Don't sell the NXDOMAIN feed to spammers or domainers, not just for ethical reasons, it's a practical concern.  200k cache-miss transactions, in order to retain access to that data for commercial uses, they don't allow people to have access to the data without very careful scrutiny and contracts with teeth.  Others have access to that stream, and nefarious actors may use it (eg. ISPs may sell it).

... low on time, went really fast through the slide deck...

### Conclusion
After pruning, only 181 crossovers, where negative before positive, in a 1 week dataset.  At the moment, we have no evidence that the bad guys are using NXDOMAIN to drive their operation.

Bot command-and-control are using dynamically generated names to lookup based on timestamp, so they only need to register one of the random .ru domains which the bot will try to lookup tomorow, but you can see that behavior in the NXDOMAIN as the clients have to lookup all of tomorrow's names.

Hope to continue using this technique for good, and out of the hands of the bad guys.  They provide access to this data for internet superheroes and people who are doing good, without charging a fee.
