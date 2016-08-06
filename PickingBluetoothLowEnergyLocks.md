# Picking Bluetooth Low Energy Locks from a Quarter Mile Away

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Rose)

## Summary
The major locks weren't particularly broken, but the smaller vendors make a lot of bone-headed mistakes.  The apps universally sit awaiting to send the password to anyone who asks, possibly encrypted, but likely usable against the lock either by remotely requesting the nonce in a distant-mitm attack, or in some cases by predicting the nonce value.

## Notes
The speaker's first talk at DEFCON, and first *time* at DEFCON.  

Smart locks, made by dumb people.  Manufacturers chose user convenience over security.

Background in EE, collaborated with CS PhD.

### Goals

* Vulnerabilities in Bluetooth Locks.  Let the vendors know... but they don't care.  Only 1 responded, they acknowledge the problem, but refused to fix it.  Then notify consumers so they can decide for themselves.
* Release proof of concept exploits

### What is BTLE
Designed for low data rate, low energy, 2.4GHz, but short range because of limited battery size (<100m).  Wanted to take advantage of this, so with an improved antenna you can communicate at a much greater distance.

GATT (Generic Attribute Profile) is how they communicate.  Client sends requests to GATT server, servers tores attributes.

Advertisement channels, 37 38 and 39, would need 3 Ubertooth (Uberteeth?) to listen on all 3 at a time.

### Why should you care

Widely used and gaining populatiry.
* SEcurying homes and valuables.
* Currently BLE "security" products:
   * Deadbolts
   * Bike locks
   * Lockers
   * Gun Cases
   * Safes
   * ATMs
   * Airbnb

Small companies didn't have funding to do security

*What do you need?*
* Ubertooth One $100  affordable bluetooth monitoring, all passive, BLE receive only capability (with current firmware)
* Bluetooth Smart USB donel $15
* Raspberry Pi, allows you to set it up and leave it unattended and not care
* High gain directional antenna $50, 15db Yagi

Uncracked locks
* Noke Padlock
* August Doorlock - hard-coded key
* Master Padlock
* Kwikset Kevo Doorlock

### Exploits

#### Clear text passwords
There were about 4 or 5 locks vulnerable in this way, most commonly available was the Quicklock.  It uses a clear text password, in the format of opcode + old password + new password.  You can change the opcode from 0 to 1, and the second copy of the password is accepted as the new password.  Resetting the lock password requires removing the battery... but the password change locks the user out of pulling the battery, because the battery is protected by a little shield when the door is locked.  Whoops.

ScaPy has a socket library, useful for sending arbitrary data to the locks

#### Replay attacks
AES256 encryption! ...  with no replay protection.  Vulnerable locks include:
* Ceomate Bluetooth Smartlock
* Elecycle Smart Padlock
* Vians Bluetooth Smart Doorlock
* Lagute Sciener Smart Doorlock

#### Fuzzing
Okidokey Smart Doorlock

sniff, notice that key is not that unique
fuzzed and immediately found that if the 3rd byte is 0x00, it enters an error state, opens, sends up an error message in the app saying hte key is out of sync...

Contacted the vendor to let them know... and they turned off their website.

#### Decompiling APKs
Danalock

Reveals encryption method and hard coded password: "thisisthesecret"
XOR(password, thisisthesecret)

#### Rogue device
Can trick a users' phone into going to the lock providers' web backend, get a token and give it to you.

Possible due to a predictable nonce.

### Takeaways
* Vendors prioritized physical robustness over wirless security
* 12/16 locks had insufficient BLE security
* Recommendation: disable phone's bluetooth when not in use

6. Future Work
* Extract pattern of life using history logs
* Dynamic profiles for rogue device
* Extend python functionality
* Evaluate bluetooth ATM locks

Frightening information available from history logs, eg. when each of the members of the house are home.

