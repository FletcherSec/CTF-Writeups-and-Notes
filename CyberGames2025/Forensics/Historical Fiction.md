 #forensics
 ![[Pasted image 20250609144510.png]] 

---

I began this challenge by downloading the .7z file and extracting it.

It appeared to have a significant amount of browser information so I looked up the file path as the contents were quite overwhelming.  From there I learned that the History file is stored as a [[sqlite3]], a serverless database.  

I then enumerated the tables in History and chose to query the `urls` table in hopes to find information about the paperback book that was visited in the person's Chrome history.

![[Pasted image 20250609145212.png]]
![[Pasted image 20250609145247.png]]

investigating the links, I found the url that lead to a paperback (not an ebook) was

`https://www.amazon.com/Hack-Back-Techniques-Hackers-Their/dp/1032818530/ref=tmm_pap_swatch_0|The Hack Is Back: Varsalone, Jesse, Haller, Christopher: 9781032818535: Amazon.com: Books`

and I guessed the ISBN was either `1032818530` or `9781032818535`.
The first flag failed and the second was correct.

Flag: <mark style="background: #BBFABBA6;">`SVUSCG{9781032818535}`</mark>