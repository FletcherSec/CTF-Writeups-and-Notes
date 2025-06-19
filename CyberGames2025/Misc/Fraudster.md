#misc #pcapanalysis
![[Pasted image 20250611134356.png]]

---
We are provided with a .pcap capture of 1000 GET flag requests.
![[Pasted image 20250611134447.png]]Upon following each stream you could see a different flag
![[Pasted image 20250611134515.png]]
The first thing I did was use chatgpt to help me gather all the HTTP/JSON packets containing the flag data and clean them into a list containing just the flag format.
![[Pasted image 20250611134625.png]]
I then threw this list into chatGPT and tried to have it identify any outliers from the list.  This however did not work and I quickly discovered that all flag formats were the same.  

The next rabbit hole I went down was using [[tshark]] to analyze my capture for different properties (I tried just about every property chatGPT could recommend me) just to be met with all the information matching.  Though this was not the solution, I did learn quite a bit about the utility of tshark and will consider using it for future pcap comparison analysis.  

I eventually decided to go back to square 1 and just start opening all the statistic tabs I could find in [[Wireshark]].  It was when I was scrolling through the conversations statistics tabs I saw something interesting about a quarter way down:
![[Pasted image 20250611135250.png]]
One of the packets had a rate of bits transferred where none of the others did.  Using this I noted the source Port A of the unique packet as: `50596`
![[Pasted image 20250611135358.png]]

And went back to the packet capture and filtered for it
![[Pasted image 20250611135434.png]]
Which produces this when you follow the TCP stream:
![[Pasted image 20250611135454.png]]

Surely enough, I entered this flag: `SVUSCG{26fddccb785b5cf3}` and it was correct.