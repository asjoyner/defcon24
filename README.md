# Realtime Bluetooth Device Detection
Couldn't get into the DEFCON 101 room on day 1.  Small room, only one thing going on, several tens of thousands of attendees... thus an endless line.

# Cyber Grand Challenge
Very interesting pre-roll video, lots of quotes from people involved.  Amuzing airgap with a machine that burns a CD with the data for visulization, and a robot that picks it up and drops it over the airgap wall.  :)  Lots of discussion about the visualizations, how the scoring works, how the rounds of the competition works, etc.

# Scoring
Scores are awarded on 3 axes:
   1 availability:  you have to keep your service up, and it has to do what it's supposed to do (eg. serve mail).
   2 security: other teams are attempting to send you "proof of vulnerability" packets; you have to keep those probes from succeeding, presumably by fixing the vulnerability before the other team successfully exploits it against you.
   3 evaluation: when you find a vulnerability, you can send a ping against another team to prove the vulnerability.  You can gain up to 6 "pie pieces" in the visualization, for successfully demonstrating a vulnerability in each service run by each of the other teams.

score == availability * (sec + eval)

Thus, availability is critical.

Lots and lots of video, and commentary explaining the contest.  Amusing pauses, dead air, as the physicist host and hacker co-hosts stumble through using teleprompters and following their script.

The game is played in 100 Rounds.  The first one they show is the results of Round 3, then Round 7,, then 11, etc.. which is at first confusing.  This is driven by the time allowed to do static analysis, optionally patch, before the rules of the challenge allow sending proof of vulnerability packets to other competitors.
   0 get code
   1 analyze code
   2 patch and send pov probes
... 
