#forensics #windows
![[Pasted image 20250611100442.png]]

---
This challenge took me much longer than it should have as I kept going too deep trying to follow suspicious files whenever something seemed out of place.

You are initially given a zip file of a windows machine snapshot with some hives and user folders.
![[Pasted image 20250611100701.png]]

From here I opened [[FTK Imager]] and exported the software and system hives to investigate for suspicious processes which "run when a user logs in".  After exporting the hives I opened them in [[Registry Explorer]]; A helpful tool for navigating exported hives.  

At this point I spent an extensive amount of time looking at anything that could be out of place in the `SYSTEM` and `SOFTWARE` hives, getting caught up in red herrings like:
![[Pasted image 20250611101012.png]]
services: `123` and `1234` that run `wget.exe` with data like `flag4 flag` and `sampleflag flag`
![[Pasted image 20250611101100.png]]

However, even though I spent quite a bit of time poking at these processes, I knew they couldn't be right as the Start value is `0x03` indicating a **Manual** service start as opposed to the **Automatic** start we are searching for
![[Pasted image 20250611101248.png]]

I also spent time investigating potential startup paths in the `SOFTWARE` hive, finding only benign things like vmware tools:
![[Pasted image 20250611101600.png]]

After much more time sleuthing around, I began to move on the NTUSER.dat files that were present for some of the users in the `Users` folder, investigating primarily their `.../Windows/CurrentVersion/Run` folder directories (amongst some other paths in the CurrentVersion and WindowsNT directories).  ![[Pasted image 20250611101928.png]]

Most of these Run folders were empty and I continued investigating until upon investigating the last NTUSER.dat that I exported (the NTUSER.dat associated with usgcadmin), I found:

![[Pasted image 20250611102113.png]]

Flag: `SVUSCG{uf0undme}`

Overall, this challenge took me much longer than it likely did for others as I went down many investigative rabbit holes that were unrelated to this specific flag but I gained a significant amount of experience using, and comfortably navigating, [[FTK Imager]] and [[Registry Explorer]] in a forensic setting.
