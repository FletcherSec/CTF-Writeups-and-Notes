#forensics 
![[Pasted image 20250610101428.png]]

---

This is a file recovery challenge

Immediately we unzip the .zip file to get a .raw.001 file:
![[Pasted image 20250610101510.png]]

with some junk along with a .txt file that says:

`=== 18-May-2025 Staff Sync ===
- Agenda: ClippyGPT post-deployment triage
- Action: Investigate why ClippyGPT replaced CEO password with "password123"
- Reminder: ProjectNextBigThing.docx was “encrypted” during cleanup.
  Password stored in passwords.xlsx, Sheet2, row 4.


 (\_/)
 (•‿•)  <-- 'Everything's fine' meme bunny
 /   \


=== 18-May-2025 Ad-hoc ===
- Determine if AI deleting files actually improves productivity...
`

Presumably we need to recover deleted files and can locate a password in a xlsx file at sheet 2 row 4

I used [[photorec]] to recover files in kali as a FAT16 partition:
`└─$ file future_of_swe.raw.001
`future_of_swe.raw.001: DOS/MBR boot sector, code offset 0x3c+2, OEM-ID "MSDOS5.0", sectors/cluster 4, reserved sectors 8, root entries 512, Media descriptor 0xf8, sectors/FAT 256, sectors/track 63, heads 255, hidden sectors 12390400, sectors 262144 (volumes > 32 MB), serial number 0xfa653f79, unlabeled, FAT (16 bit)`
┌──(fletcher㉿fletcher)-[~/…/CyberGames2025/Forensics/Future of SWE/recup_dir.1]
└─$ ls
`f0000680.xlsx  f0000700.doc  recovered.doc  report.xml`

We can open the .xlsx sheet:
![[Pasted image 20250610102237.png]]
We see some passwords,
we can navigate sheets with `Sheet -> Navigate -> Go to Sheet`
![[Pasted image 20250610102350.png]]
Here on Sheet 2 we have mor passwords, including password123 which is in row 4 of sheet 2 as aforementioned
![[Pasted image 20250610102453.png]]
And page 3 has seemingly useless information 
![[Pasted image 20250610102528.png]]

our .doc is encrypted and needs a password to open:

```
└─$ msoffcrypto-tool  f0000700.doc --test -v                                                       
Version: 5.4.2
OOXMLFile.type: agile
f0000700.doc: encrypted
```
``
After some research this is most easily performed with [[msoffcrypto-tool]]
where presumably
this command would net the decrypted file:
![[Pasted image 20250610102939.png]]

However, this is not the case:
![[Pasted image 20250610103003.png]]

Also trying to open the .doc in libreoffice and entering `password123`
I began trying every password in page 1 and 2 with no avail:
-`1234`
-`password123`
-`ilovecoffee`
-`h@rdPa$$1!`
-`CorrectHorseBatteryStaple`

Until I eventually hit:
-`clippyisawesome` and the new page opened
![[Pasted image 20250610103429.png]]

I spent **HOURS** going down incorrect rabbit holes thinking the password was `CorrectHorseBatteryStaple` or `password123` because I didn't realize that the xlsx spreadsheet has separate "sheets".

Flag: `SVUSCG{th3_futur3_is_look1n_br1ght}`

