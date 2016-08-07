# Feds and 0Days

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Healey).

How many 0Days do the feds keep?  Less than hundreds, based on all available external evidence, but he knows we won't believe that.  :)  Rsearch has looked at gov involvement in 0day markets, vuln disclosure programs, usage in the wild, etc.  States his level of confidence clearly, and wants mostly to convince you that he's credibly researched it as thoroughly as is possible, rather than convince you of the accuracy of his answers.

Tension between users of vulns (DOD, NSA, CIA, Justice, FBI, DHS) and those who want them closed (Commerce, Treasury, Energy, DHS).  In the 90s, used to disclose but USG developed a policy of "tell the offensive side" of the branch of the armed service first, and let them decide to disclose or hoard in the "toolkit", eventually shared between branches of services in the late 90s.

White House got involved with NSPD-16 in 2002, confidential but clarified coordination between branches.  NSA developed internal cost/benefit (intel gain/loss) metric to decide what to do with vulns.  More likely to keep it if NOBUS ("No One But Us" is likely to use it).  Assuming CIA, Justisce had similar policies, but can't prove.

Things get interesting in 2010, formal process discovered by EFF, process for notification, decision-making, and appeals, established NSA/Inforumation Assurance Directorate (defensive side of NSA, good!) as Executive Secretariat.  Was the process until 2014... except it seems it wasn't fully implemented.  NSA still ran their own process.

Stuxnet's 5 0days probably was the trigger for the White House to reinvigorate this process.  Post Snowden, review group recommends strenghthening, Obama accepts, policy is to disclose by default.  Centralize decision power in the White House, rather than at the NSA, enacted in January 2014.  About as strong as it gets inside the beltway... but carveouts for national security and law enforcement, big enough to drive a truck through.  3 breakthroughs helped clarify

1. Bloomberg writse story that NSA knew about Heartbleed.  NSA publicly denies knowledge, unprecidented to do so, he believes them.  NSC cyber coordinator outlines White House [decision criteria](https://www.whitehouse.gov/blog/2014/04/28/heartbleed-understanding-when-we-disclose-cyber-vulnerabilities).  Policy wonk speaker was pleased with that breakdown.
2. EFF Core VEP documents
3. NSA infographic says 91% of vulns discovered between 2010 to 2015 were disclosed, of the 9% remainder some were discovered by the vendor before they could be disclosed.

How can we know the Government is telling the truth about that 91%?
Several testomonities from IAD and NSA, consistent, but would have to get info from vendors from to try to confirm.

## FBI v Apple
Policy implies they should disclose, supposedly only bought access to the tool, seems to contradict policy. Will be interesting to see if they 

## How many retained?
Not hundreds, but probably dozens.  Only moderate confidence, based on 2010 data.
* NSA has budget of 25.1 million for purchases of software vulnerabilities.  His number breakdown from that budget leads him to dozens.  His moderate confidence seems about right to me.

Based on 2015 data, higher confidene that it's single digits.  Press reported reviewed about 100, kept about 2.  Insiders have referenced that press response, strenghtening his confidence in it, other quotes are comparable with 2-3 per year.

Supported by the fact that No one's complaining / leaking that the agencies are going around the process: no disenting voices.  Comparable to known number of 0days, which is ~50/year.
Slightly undermined by the fact that the government discloses ~1,500 per year, 91% of that is about 135, so slightly over the dozens estimate, but might include before policy.
Redacted book of capabilities implies about 50 capabilities, aligning with estimates.
Drake-equation style limiting indicates that we're very unlikely to have a large arsenal stockpiled, as they have a limited shelf life, both if used or unused.
