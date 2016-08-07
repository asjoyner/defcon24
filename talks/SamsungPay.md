# Samsung Pay: Tokenized Numbers, Flaws and Issues

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Mendoza)

## Summary
The presenter unpacked the ~40 local databases the Samsung Pay client uses, rummaged through them and picked apart how the client stores transactions.  He discovered that "unused" transactions remain valid for a long period of time (I think it was indefinite?) and that the generated token be captured by a remote listener, and replayed into another machine far away.  He wrote two tools for doing this, jamming the receiving station and capturing the token, and another for replaying the token, both of which were released with the talk.  He played demo videos of himself capturing a token in advance elsewhere, then replaying it to a vending machine on the strip in Vegas and it dispensing a coke.

## Notes
I was busy typing up notes to the [Side-channel attacks on high-security electronic safe locks](https://github.com/asjoyner/defcon24/blob/master/Side-Channel-Locks.md) talk while this one was going on, so I didn't transcribe any notes in real time.
