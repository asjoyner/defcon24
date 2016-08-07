# Hacking Hotel Keys and Point of Sale systems ...

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Hecker2)

## Summary
Hotel keys and POS systems use mag strips.  The encoding is often very simple, the "manager" or admin key numbers are very guessable (all zeros, all nines).  Magspoofer can write to the mag heads of a POS system without being "swiped", just being pretty close (eg. NFC distances).  Even more frightening, the mag spoofer can write arbitrary characters to readers which are often just HID devices, capable of sending arbitrary keystrokes, to do things like open a terminal, run arbitrary commands, load arbitrary code from the internet, etc. to the habitually-out-of-date OS on which the POS is likely being run.

## Notes
### Presenting about hotel hacking at a hotel
Ceasar's took him into the bowels of the hotel, discussed their own security, and he confirmed that because they tokenize their card numbers, they are not vulnerable.  Having seen Casino, this naturally made him a bit nervous.

### Hardware
Iron oxide on a white credit card mag strip makes a really beautiful picture, allowing you to visualize the binary data.

[Magspoofer](https://samy.pl/magspoof/) is awesome for hacking and talking to magnetic card readers.  It has risk of burning out if you write to it too fast.  His solution was to build a more fragile device, "big bertha", made of 6 magspoofers joined together, controlled with an arduino, and (presumably) used in a round-robin fashion.  He did some testing by writing to it at increasing pace, and reading the output, and checking for bit errors to tell when it started to overheat and thus determine a safe maximum write rate.  The modified "big bertha" magspoofer can inject 45 cards per minute.

It leverages MST (Magnetic Secure Transmission), which is also used by SamsungPay and the like to be able to "talk to" the magnetic readers from a phone, without having to upgrade the terminal.

[MSR605: Mag strip reader](https://smile.amazon.com/Deftun-MSR605-Magnetic-Stripe-Encoder/dp/B00DE8248Q)

PMS: Property Management Software

### The data on the card
Hotel cards contain simple encoded data of the following fields:
1. Folio Number
2. Room Number
3. Checkout Date

With some assumptions, that leads to a very small key space, subject to brute force search:
* Incremental folio numbers
* relatively few rooms in the property (~50)
* a checkout date in the next week

### How it is encoded
Hotel chains use Track 3, typically don't use the whole strip.

It is often easy to break the encoding, it's just base64 or similar, no fancy encryption here!

### Practical lessons learned
Can test at hotel or pool area, rather than at someone's door for 18 minutes...

Floor restrictions on elevators are typically only via reading the room number from the key.

Maid key, attach to back of the door, wait for it to go by.  I totally didn't understand how this worked from the talk?

After discovering the maid key contents, Weston felt foolish for brute forcing based on folio+roomnum+checkout, because when snoofing he discovered all zeros was the maid key, experiementing showed all 9s was the "service" key.  There is also a brewing push to standardize "firemen's keys" which are behind a small metal panel on the door to prevent you from swiping your card there.  Conveniently, Magspoofer can write to mag heads over a pretty good distance, through metal even...

Track 2 sometimes had the name, but fortunately the door wasn't validating it.  That was the only PII he found.

Magspoofer can inject illegal characters.  Fuzzing POS systems is still an area in need of research.

Some readers inject a return after the card is swipped.

To aid in breaking the encoding, have your own key issued twice, which gives you two samples to go off of.  You can use the automated checkin kiosk to get several keys without being suspicious.

### Pivoting to POS systems
He discovered that the card readers were often embedded in keyboards, or otherwise showed up as HID keybaords to the OS, and you can take any key input it can decode from the reader.  Anything you can type as a keyboard key, you can inject via the reader.

Injecting F8 to the reader opens the cash drawer.

Exiting out of the POS via win-R, open cmd, and call out to a memory-corruption bug to own the local OS.

By buying a couple POS systems at auction, he noticed the Managers keys worked between POS systems.

Giving your card to your waiter with malicious code on it proved more difficult than expected, due to limited payload size and character limitations.  This is also an area for future research.

Today, in casinos, people often leave their "players points" cards in high limit slots machines.  With a MagSpoofer you could squat players-rewards points by attaching a box to the slot machine which would write to the magstrip.

Rewards card point collecting into 10 different accounts at a grocery store or gas station.

The readers are triggered to turn on for a transaction, so he had to sniff for it turning on (it wasn't clear how).

Clock-in system using magstrip reader?  never be late for work again!

Can set bits on the mag strip to tell the reader that a card's chip'n'pin has pins which are damaged, and it should be allowed to fall back to using the mag strip, as a way to force a downgrade.  Samy Kamakar demo'd this, but neither he nor Weston included it in their code to avoid encouraging nefarious illegal uses.
