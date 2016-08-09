# Use Their Machines Against Them: Loading Code with a Copier

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Mike)

## Summary
If the user can code, the system is not secure.  If the user has Excel, the user can code.  Hilarity ensues.

## Notes
Closed / locked down network, couldn't use the tools he wanted, couldn't load them without setting off alarm bells.  How to fix?

### Environment restrictions
* Windows/Office environment
* USB ports secure and monitored
* CD use secure and monitored
* end point security
* data stransfer entry points do not exist, etc.

### Tools available
1. Commercial Scanner / Multifunction copier device
1. Acrobat OCR
1. Locked down workstation, but with Excel...

### Phase 0
1. Put Excel into "attack mode", eg.  turn on developer checkbox.  Now have access to basically an IDE in Excel.
1. Write an arbitrary script elsewhere, at your convenience.
1. Print that script to paper.
    a. no indentation, the OCR won't cope well
    b. works down to about 8 point font
1. Scan that on the work copier, email it to yourself
1. OCR it with Acrobat.  common errors include:
    a. missing the leading single quote comment characters 
    b. ells as ones, and vice versa
1. Paste it into Excel
    a. fight syntax errors until it behaves as expected

### Phase 1
1. Use excel to implement a hex encoder/decoder
    a. hex is remarkably better at transcription
    b. base64 allows you to 
2. use checksums, 2 byte XOR

#### Real world problems
1. 1.1% error is still a lot of error
    a. b to 8, 1 to l, 5 to s
    b. D to 0 or O, 6 to G or g or b
2. Devise alternate characters for the problematic ones
    a. ? instead of D, # instead of 1
3. Down to 1 manual correction in 1210 lines of text, about 19 pages

#### Pros
* Reliable
* could be entered by hand

#### Cons
* low data density: ~3.6K per page
* PowerSploit: 935kb = 232 pages
* Mimikatz: 538kb = 150 pages

### Phase 2
* 2d bar codes!
    a. ~45K per page, but with error recovery data, ~25K data per page
* build your own!  He called it "Big Bar Code"
    a. create a grid of timing lines around the edge
    a. No built-in Error correction
    b. reed solomon encoding
    b. printed at 72dpi
    b. about 88 bytes across
    b. 85KB data per page
* turns out reed solomon is hard... so use a library
    a. forward erasure correction vs. forward error correction
    b. most of the libraries out there don't work!?!?
* forward erasure correction is for missing data
* forward error correction is for corrupted data

#### Results
Needed 45% error correction, meaning he got ~47KB per page of data
* PowerSploit in 18 pages 
* Mimikatz in 12 pages

### Future Work
* Reduce the size of BBC DLL from 19 pages
* Improve error rages
* *Get 2^16 Reed Solomon FED working*
   a. much slower, but would dramatically reduce the required parity
* Add color to BBC
* Restore the command prompt, it only requires flipping a bit on disk
