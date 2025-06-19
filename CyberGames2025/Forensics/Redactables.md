#forensics #passwordcracking
![[Pasted image 20250610154044.png]]

---

#### This is a classic CTF problem
You are provided with redactable.pdf which is password locked.
These can be brute forced with a wordlist by getting their internal hash with [[pdf2john]] and running a sufficient wordlist against the hash.

And that's what I did, after attempting some pdf cracking shortcuts like [qpdf] with no success.

```
┌──(fletcher㉿fletcher)-[~/Downloads/CyberGames2025/Forensics/Redactable]
└─$ pdf2john redactable.pdf > redact.hash 
                                                                                                          
┌──(fletcher㉿fletcher)-[~/Downloads/CyberGames2025/Forensics/Redactable]
└─$ ls
redactable.pdf  redact.hash
```

With I decided to first try `rockyou.txt` wordlist, as it contains many of the most common passwords and is frequently used in CTFs.

```
┌──(fletcher㉿fletcher)-[~/Downloads/CyberGames2025/Forensics/Redactable]
└─$ john --wordlist=/usr/share/wordlists/rockyou.txt redact.hash

Using default input encoding: UTF-8
Loaded 1 password hash (PDF [MD5 SHA2 RC4/AES 32/64])
Cost 1 (revision) is 6 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
friends4eva      (redactable.pdf)     
1g 0:00:00:02 DONE (2025-06-10 15:39) 0.4807g/s 4307p/s 4307c/s 4307C/s fucklife..147896
Use the "--show --format=PDF" options to display all of the cracked passwords reliably
Session completed.
```

So we get our pdf password: `friends4eva`
We see the pdf is redacted, hence the name:
![[Pasted image 20250610154905.png]]

I right clicked the redacted image and saved as a separate image: `redactedimg.png` and opened the saved image separately: ![[Pasted image 20250610155303.png]]

This is still pretty difficult to read so I opened it in GIMP and messed with the whirl and pinch settings:
![[Pasted image 20250610155534.png]]
![[Pasted image 20250610155552.png]]

Flag: `SVUSCG{oops_i_did_it_again_i_didnt_redact}`