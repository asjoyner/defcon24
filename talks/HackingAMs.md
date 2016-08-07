# Hacking Next-Gen ATM's From Capture to Cashout

## Summary

He first did some research online, looking at how credit card selling sites will likely sell ATM data in the future.

He bought an ATM, built a banking backend, signed up with a credit card processing gateway, and started sending his "normal" transactions through the system to ensure he woudln't hit fraud limits.  He simulated his "bank" having 150k accounts and got to a stable simulation.

He then modeled how you would use a blockchain to coordinate using shimmers to attach your fraudulent transaction to live, active in-progress transactions against cards in a network of shimmers in the real world, and funnel the fradulent transaction to a "cash-out ATM", where it would dispense all the money in rapid order.

## Notes
Attacks on EMV standard (Europay, MasterCard, Visa), aka chip-and-pin cards.

He has a script to scrape card selling sites on the web and see if a lot of cards are for sale in a given region.

Considered what it would look like to buy EMV card data.  There are professionally-made shimmers, with serial numbers, etc.  Being able to sell an EMV transaction, you'll have to buy 
You're not buying static access any more, you're buying access to a network of shimmed devices that are connected to the ATMs.

Badguy picks hich minute he's going to be standing at the ATM, which timezonea nd one of the two passwords.  Pick out where that transaction is

Things sold on newer carder sites
* Static MAG Data track 1 2 3
* EMV (DDA Dyamic Authentication)
* EMV (CDA Combined Data Authentication)
* Some 13.56 RFID NFC (Non Token Based)

Rejects cards with flags not set for ATM
Aside from Card Pass Off bad guys will also get PIN Number and Assumed ATM Limit

Multiple Shimmed Devices passing off to a single Cashout ATM, via a backbone

Leased gear, Multes/STore Employees, and Independen/Small breaches feed into a Small Carder Site, which feeds up to a Main Carder Site
Can't be held as static data, needs to be used in real time to match some of the flags with how the transaction was initiated.

Intercept after a certain portion, run a separate transaction, which runs against a different limit (ATM limit vs. Point-of-Sale limit)

Found ways to disable foreign object detection on the ATMs

La-Cara: criminals automating cacheouts

2 arduinos, controlled by a raspberry pi, connected to an android device

Setup a banking backend, integrated his ATM with a gateway processor, so he could serve as both sides of the equation in an EMV validator.

OpenCV to aotumate reading of the pin
also RF reading of the pin based on magnetic dust on the pins and reading how each pin's RF signature changes?  He spoke very fast, hard to understand exactly what he was doing here.
