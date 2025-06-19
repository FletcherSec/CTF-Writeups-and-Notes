#misc #OSINT
![[Pasted image 20250610225710.png]]

![[lol-osint.png]]

---
We are provided with nothing but a flag format and this picture of a suitcase with no apparent Personally Identifiable Information on it.

*We need to find the flight number, departure IATA, and destination IATA*

First I checked for metadata in the image seeing if I could get GPS coordinates or a date, but all was stripped.

I then noticed the two barcodes on the luggage tag along with the delta Silver Medallion card.

Using an online barcode reading site called [inlite](https://online-barcode-reader.inliteresearch.com/): I found the barcodes resolved to `6006015722`
![[Pasted image 20250610230119.png]]

I then looked up what this code meant and found that it followed a standard IATA format:
`[1-digit tag type][3-digit airline code][6-digit bag serial]`

While this is good to know I still needed to tie this luggage number to a flight or person.  I first went to American Airlines bag tracker since its the first one I saw that took a baggage number:
![[Pasted image 20250610230553.png]]
This required me to input a last name, which I was able to easily get from clicking on the profile of the challenges creator `@tsuto`
![[Pasted image 20250610230640.png]]
Which redirected me to a github with what I presume is his real name
![[Pasted image 20250610230701.png]]

I entered Elliot as the last name and the code as the baggage code (under the search by feature) but it didn't work.

At this point I remembered that the Delta card was also in the original image and I sought out their baggage tracker.  Upon finding it, I entered the same information and hit `Check Bag Status`
![[Pasted image 20250610230847.png]]

This provided me with extensive information about his flight:
![[Pasted image 20250610230920.png]]
Departure from Cancun, Destination to Atlanta, on June 6th, flight DL2013.

Using this information I constructed the flag and passed the challenge
Flag: `SVUSCG{DL2013-CUN-ATL}`