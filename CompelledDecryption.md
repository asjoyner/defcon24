Cmopelled Decryption
State of the Art Doctrinal Perversions
Ladar Levinson

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Levison)

# Summary
The only thing safe from compelled decryption is your mind, and only if they can't specifically request a set of files and can prove that you have knowledge of how to decrypt them.  Don't admit to knowing the key, that it's your laptop, and don't print out recovery keys or other physical artifacts that can be searched for and used to subvert your encryption.  Vote, and support reforming the government, who is continously trying to undermine your privacy.

# Notes

Great slides (diploma from school of hard knocks, drinking from the firehose).

Government corrupted by people who derive gratification from corrupting the law to impinge our freedoms.

Government is coming to believe they're entitled to our data.  The plaintext, not the ciphertext.  DOJ blames infosec community as the problem, believes they can compel the courts to compel you or others to decrypt.  Has argued they can use existing statutes to seek assistance if not explicitly prohibited by congress.  All Writs Act as a blank check.  Only thing standing in the way is the court.

Want to enable to you have an informed conversation with your lawyer.  If you lawyer tells you to comply of to go jail, you should probably look for a different attourney.

### First Party
Government seeks to compel a subject to decrypt their own data.

### Third Party
Seeks to concrypt a company like Lavabit or Apple to assist them in accessing encrypted info w/o the users' assistance.

A common strategy is to convert first parties into third parties by granting them immunity.  If you believe Law Enforceent is idishonest, then no amount of immunity can protect you, as they'll use duplicate chains of evidence.

*No law on the books that allows law enforcement to cmopel decryption.*  We have no right to privacy, what we have is the 4th ammendment.  Protects our home from search and seizure without probable cause.  Gov. careful to distinguish that from a right to privacy.

No supreme court cases yet dealing with compelled decryption.  Only a handful of district court decisions, extrapolating from supreme court cases about physical security cases, establishing case law within those districts.  Affects other districts decisions.

### First, a digression.
The 5th amendment.  Fisher v. US, cited by all the modern district court cases, not violated by the fact alone that the papers might encriminate them, protects only against their own compelled testimony.  Because the documents were created voluntarily, they're note considered compelled evidence.  The bits on your hard drive were created voluntarily, they're subject to search and seizure.

Doe vs. US distinguishes the contents of your mind, vs. things elsewhere in the physical world.  

US vs. Hubbell: knowing the location of the information is testimonial.  If you can decrypt it, and the government can prove that, your 5th ammendment protections begin to fall away.  Keep that in mind when being questioned by law enforcement.

### The modern cases

#### In re Boucher (2007)
Agents found porn, and suspected child porn, lost access when they powered the laptop down.  Knew what was on the drive, only quesiton was Boucher's knowledge of the password was in fact testimonial.  "Resoanble particularity", if the gov. can prove you know how to accdss the info, and knows what it's seeking, it can force you to decrypt your hard drive.  Initial request was thrown out, later narrowed by the procecutor that only required an unencrypted copy of the drive based on foregone conclusion.  District court reversed the decision, don't need to know the specific contents, just demonstrate that they exist.  Investigator saw the filenames, can overcome the particularity and specificity requirements.  You may want to start encrypting the names of your files in addition to the files themselves.

# In re Decryption of a Seized Storage System (2013)
Raided home, seized laptop, he decrypted to show that it was personal files
ultimately, leave plausible deniability that the computer is yours

#### In re Grand Jury Subpoena Duces Tecum (11th circuit 2004)
Suspected of sharing child porn, laptop couldn't be decrypted, subpeona required decruption, doe claimed 5th ammendment right against self encryption.  Government gave him immunity to circumvent the claim, but circut court reversed the decision because they couldn't prove that the drive contained relevant content.  Requires some specificity in request.

#### No. 15-3537
Sisters says she saw child porn on defendant's laptop.  Forensic exam of laptop found underage boy in bathing suit.  Used pin to iPhone to find screenshot of recover key for mac drive.  Used that evidence to compel him to decrypt, etc.  Case still pending.

When you print or save a recovery key, subject to search if they can prove its recovery key or proximate location.

FBI is less concerned upon realizing that they can search for the printed recovery key.

Pin code isn't safe, as vendor can be compelled to modify it and be succeptible to a brute force attack.

### Third Party Case Law

#### Smith v. Maryland
pen register order without first receiving a warrant, supreme court said it was legal because the info was normally collected by the phone company, thus no expectation of privacy.  Congress decied to pass pen register trace statutes.  Passed in the day of physical pen register devices, could not have foreseen encryption, or backdoor of encryption, as what they were mandating.

EMail communication not considered to have an expectation of privacy, because receipient might leak the email to others.

Computers on the internet not considered to have an expectation of privacy in the circuit court of virginia, because they will eventually be hacked.  Queue laughs and groans from crowd.  Clearly, thus hacking is legal.

#### Lavabit case
Tried to compell him to give up his TLS key and source code, so they could MITM user connections to collect passwords, and then reverse the encryption of the storage of the user's data.

#### Apple iPhone case
Relying on a law from 1784 to compel apple to provided a signed IPSW to allow them to brute force the pin.

#### Snowden
Would be willing to return to face a jury of his peers, but didn't think he'd receive a fair trial.  Ladar agrees, because he'd face the same jury he did.  He was willing to insatll the device, but not to give up the TLS key.  Indicated he would retain a lawyer, and object in court, but then DOJ claimed they couldn't get in contact with him, went to another judge and sought an order to install the tap upstream w/ the service provider before I showed up in court.  Ladar had to sue to get that document.  They installed it 2 days later, well before he flew to DC.  When he arrived, they didn't inform the court they had already installed the device.  Continued, and insisted that he was not in compliance.

Ran out of time... skipped to close.
