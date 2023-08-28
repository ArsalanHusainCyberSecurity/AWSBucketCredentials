<h1>AWS S3 Bucket Credentials CTF </h1>

<h2>Description</h2>
I participated in a capture the flag for an AWS S3 Misconfiguration vulnerability which can occur on website using AWS buckets to store that data and resource.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Parrot</b> 
- <b>Powershell</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Linux (HTB VM)</b>

<h2>Program walk-through:</h2>

<p align="center">
I Started the CTF by logging into flaws.cloud: <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145768213234331738/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Based off the hunt we had to access the following link:  <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145770329214554153/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I looked up the bucket in aws cli and found the following: <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145770392535978096/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Used the sync command to download bucket contents to my machine :  <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145771676232065044/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
A huge red flag is the .git so we will try to exploit it:  <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145779324314722324/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Downloading contents of .git pathway:  <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145773184747065394/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
With all the information snyced we can now interact with the .git:  <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145780075342598264/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145773788466790410/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
When checking the git logs we were able to find two commits to the git:  <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145774072974823506/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Based on the logs there was vulnerable information in the first commit so we will check it out:  <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145774777097797734/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We found access keys.txt and are going to cat it:  <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145774854281371709/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We then configure an AWS profile to match the access and secret key:  <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145775410936811650/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After looking at the profile we were able to find the next level:  <br/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145775857848307722/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://cdn.discordapp.com/attachments/1145767870459031646/1145775896939208795/image.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>


