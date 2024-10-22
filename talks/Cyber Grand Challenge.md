# Cyber Grand Challenge

The [Cyber Grand Challenge](https://www.cybergrandchallenge.com/) was DARPA's effort to advance the state of machine learning in security, by staging a competition for autonomous hacking and defense, in the style of DEFCON Capture The Flag (CTF) hacking competition.

## The Pregame Show
Very interesting pre-roll video, lots of quotes from people involved.  Amuzing airgap with a machine that burns a CD with the data for visulization, and a robot that picks it up and drops it over the airgap wall.  :)  Lots of discussion about the visualizations, how the scoring works, how the rounds of the competition works, etc.

## Scoring
Scores are awarded on 3 axes:

1. availability:  you have to keep your service up, and it has to do what it's supposed to do (eg. serve mail).
2. security: other teams are attempting to send you "proof of vulnerability" packets; you have to keep those probes from succeeding, presumably by fixing the vulnerability before the other team successfully exploits it against you.
3. evaluation: when you find a vulnerability, you can send a ping against another team to prove the vulnerability.  You can gain up to 6 "pie pieces" in the visualization, for successfully demonstrating a vulnerability in each service run by each of the other teams.

score == availability * (sec + eval)

Thus, availability is critical.

## Realtime commentary
Lots and lots of video, and commentary explaining the contest.  Amusing pauses, dead air, as the physicist host and hacker co-hosts stumble through using teleprompters and following their script.

The game is played in 100 Rounds.  The first one they show is the results of Round 3, then Round 7,, then 11, etc.. which is at first confusing.  This is driven by the time allowed to do static analysis, optionally patch, before the rules of the challenge allow sending proof of vulnerability packets to other competitors.  Note that Markdown doesn't seem to allow me to start a bulleted list with a zero, but the first round is actually zero.

0. get code
1. analyze code
2. patch and send pov probes

## Developments

An exciting development!  A team has discovered an unintended vulnerability in one of the challenges, exploited it against a second team, and the second team reacted to that intrustion and deployed a mitigation against it, all in less than 10 minutes of analysis end to end.

## Conclusions

It was presented as if the results were coming in "in real time", but as we started to better understand what was happening, it seemed that they were actually presenting the outcomes of rounds that had arleady been played.  In each round, each team's Cyber Reasoning System (CRS) is given 5 minutes of computation time before declaring what it will do in the next round.  For 100 rounds that's 500 minutes or >8 hours of pure computation time.  There were rumors of results being posted on twitter earlier in the day, though I couldn't find them in a quick search.  It seems likely that they actually started thecompettion earlier on Thursday; it would have been nice of them to communicate that more clearly.
