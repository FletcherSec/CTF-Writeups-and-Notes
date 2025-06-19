#forensics
![[Pasted image 20250609145843.png]]

---

Downloading and catting the log file I find it to be quite long (613,000 lines):
![[Pasted image 20250609150314.png]]

I appended a grep search to the cat command and looked for 'PASS - 530 1326' and a word count command and kept getting incorrect answers for number of failed attempts.

![[Pasted image 20250609151105.png]]

after *lots* of guessing and tinkering *(and substantially tanking my accuracy)* I realized that the grep word count wasn't accurate due to it treating the results like binary.

I used the `-a` command on grep (which treats text as a string) and it found the right answer.  
![[Pasted image 20250609154857.png]]

Flag: <mark style="background: #FF5582A6;">SVUSCG{306737}</mark>
