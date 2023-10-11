# Cybersecurity_Projects

Cybersecurity is my passion, and I've channelled that passion into a collection of practical projects that highlight my dedication to honing my skills. Each project here represents a step forward in my journey to understand and address the evolving challenges in cybersecurity. Dive into this repository to explore a diverse array of cybersecurity projects, each presenting its unique set of challenges and solutions. Whether you're a fellow enthusiast seeking inspiration, a beginner looking for hands-on learning opportunities, or a prospective employer curious about my approach, there's something here for you.

## PROJECT1: Malware Analysis Techniques - Dylan Barker
<details>
<summary><h3>Chapter 2 - Static Analysis - Techniques and Tooling</h3></summary>

### Hashing_Algorithms

Hashing algorithms are cryptographic techniques used to transform data (usually of variable sizes) into a fixed-length string of characters, which is typically a hexadecimal number. These algorithms are designed to be fast to compute but difficult to reverse, making them suitable for various security and data integrity purposes. They are known as one-way functions, and they are extremely difficult to reverse engineer.

Here's a rundown of some commonly used hashing algorithms:

- **MD5 (Message Digest 5):**
  - Output Length: 128 bits (16 bytes)
  - Vulnerabilities: Vulnerable to collision attacks, unsuitable for security-critical applications.

- **SHA-1 (Secure Hash Algorithm 1):**
  - Output Length: 160 bits (20 bytes)
  - Vulnerabilities: Vulnerable to collision attacks, deprecated for security purposes.

- **SHA-256 and SHA-3 (Secure Hash Algorithm 256 and 3):**
  - Output Length: 256 bits (32 bytes)
  - SHA-256 is widely used for data integrity and security.
  - SHA-3 is the latest member of the Secure Hash Algorithm family, designed to provide resistance to specific attacks.

- **SHA-512:**
  - Output Length: 512 bits (64 bytes)
  - A variant of SHA-2, which is more secure and suitable for security-critical applications.

- **bcrypt:**
  - Output Length: Variable (based on the algorithm configuration)
  - Designed for securely hashing passwords. Incorporates a work factor (cost) to make brute-force attacks more challenging.

- **scrypt:**
  - Output Length: Variable (based on the algorithm configuration)
  - Similar to bcrypt, designed for secure password hashing with resistance to hardware-based attacks.

- **Argon2:**
  - Output Length: Variable (based on the algorithm configuration)
  - Winner of the Password Hashing Competition (PHC). Designed to be memory-hard and resistant to GPU and ASIC attacks.

- **Whirlpool:**
  - Output Length: 512 bits (64 bytes)
  - A cryptographic hash function designed for increased security.

- **RIPEMD-160 (RACE Integrity Primitives Evaluation Message Digest 160):**
  - Output Length: 160 bits (20 bytes)
  - A cryptographic hash function used in various security applications.

- **CRC32 (Cyclic Redundancy Check):**
  - Output Length: 32 bits (4 bytes)
  - Commonly used for error-checking in data transmission but not suitable for cryptographic security.

- **BLAKE2:**
  - Output Length: Variable (up to 512 bits)
  - A cryptographic hash function is known for its high performance and security.

- **XXHash:**
  - Output Length: Variable (32 or 64 bits)
  - Designed for fast hashing and checksumming.

There are many choices for hashing data, though it is important you choose a hashing algorithm to suit your specific needs. For cryptographic security, newer and more secure algorithms like SHA-256, SHA-512, bcrypt, scrypt, Argon2, and BLAKE2 are recommended. MD5 and SHA-1 have both exhibited collision vulnerabilities and are also prone to attacks that undermine the one-way property of secure hash functions. MD5 and SHA-1 should be avoided in security-critical applications due to being considered broken.  

In the following section, you will find an image illustrating how the MD5 algorithm is vulnerable to collision attacks. Additionally, you will see how simply rehashing the data with a stronger algorithm, such as SHA-256, allows us to confirm the file's uniqueness.

### Obtaining_file_hashes

<a href="https://imgur.com/bm9VWdm"><img src="https://i.imgur.com/bm9VWdm.png" title="source: imgur.com" /></a>

Obtaining file hashes in various OS environments from the command line interface (CLI).

Windows PowerShell (see above)

`Get-FileHash -Algorithm MD5 -Path C:\example\file.txt`

MacOS/Linux Terminal

`hash_algorithm path/to/file.ext`


### Leveraging_VirusTotal

VirusTotal stands as a formidable tool for static malware analysis, offering assistance in the identification and attribution of malicious software through its extensive repo of publicly accessible data. It is widely used by analysts all over the world and assists us in making sure we don't continuously find ourselves rediscovering the wheel.

<a href="https://imgur.com/YaUEj3E"><img src="https://i.imgur.com/YaUEj3E.png" title="source: imgur.com" /></a>

In the upcoming image, we'll observe how inputting a hash value into VirusTotal and clicking 'search' produces results. This is made possible by the collective efforts of thousands of analysts who have previously submitted this file.

<a href="https://imgur.com/ofovMqm"><img src="https://i.imgur.com/ofovMqm.png" title="source: imgur.com" /></a>

### Getting_Fuzzy (ssdeep.exe)

A common technique implemented by authors of malware - *hashbusting*

Hashbusting ensures each malware sample has a unique static hash, and has become a popular technique among threat actors and advanced malware authors, such as the actor behind the EMOTET threat. It is worth your time researching implementations of hashbusting as they vary. 

"In the constant arms race of malware authoring and Digital Forensics and Incident Response (DFIR) analysts attempting to find solutions to common obfuscation techniques, hashbusting has also been addressed in the form of fuzzy hashing." - Dylan Barker

In the following screenshot, I use a fuzzy hashing algorithm that adopts a similarity digest, which is a process of compact representation (digest) of data that captures its essential features while allowing for the detection of near-duplicates or similar data. Plainly, fuzzy hashing is a technique used to spot datasets that are similar but not necessarily identical. The 'ssdeep' algorithm breaks the data up into smaller chunks and then proceeds to hash those chunks, which is useful for identifying near-duplicates when modifications have been made by the author in order to obfuscate. So even if modifications have been made to mask the data from being discovered as malicious, the chunks can be compared, and if similarities are detected, then the likelihood of the data being the same is affirmed.

<a href="https://imgur.com/HSN7Z93"><img src="https://i.imgur.com/HSN7Z93.png" title="source: imgur.com" /></a>

**fromat**: chunksize:chunk:double_chunk

### Picking_Up_The_Pieces

##### *A table of common file headers related to malware*

|Header | File type|
|-------|-----------|
|MZ     |Windows PE (.exe, .dll)|
|PK..   |ZIP file formats (.zip, .docx, .apk, .jar)|
|Rar!.. |WinRAR archives|
|.ELF   |Linux ELF executable|
|X.S.BB |Mac disk image file|
|%PDF-  |PDF document|
|MSCF   |Microsoft cabinet files (.cab)|

In the screenshot provided, we encounter a .png file. The question is this: how as analysts, do we make certain that it is what it truly claims to be? To investigate further, we should acknowledge that a file can disclose more details about itself without the need for execution. Attackers frequently employ a handful of conventional strategies aimed at slowing down our malware analysis efforts. 

In the next section, I explored one such strategy.

<a href="https://imgur.com/gE0ro53"><img src="https://i.imgur.com/gE0ro53.png" title="source: imgur.com" /></a>

### Malware_Stereotyping

When I tried to open the sample 888888.png, I observed that it exhibited behaviour typical of corrupted files. I learned, upon further reading, that sometimes adversaries change the extension of files, and sometimes they omit them altogether, even creating double extensions, such as dontlooktwice.doc.exe. They do this in order to attempt to obfuscate their true intent, bypass EDR (Endpoint Detection and Response) or use social engineering to lure their victim into executing their payload.

This is but an aesthetic change in most circumstances. In the computing world, all files have a header that indicates to the OS a way of interpreting the file. This header can be used to 'type' a file, akin to a crime forensic analyst typing blood samples.

I used a Windows OS tool not native to Windows, but helpful nonetheless. The tool I used is called `filetype.exe` and whilst it serves as a great tool for discerning the file's true nature, in this case, an executable file (.exe); another way to ascertain this information is to use a hexadecimal editor, such as 010 Editor - with this we can also inspect the file's header. 

<a href="https://imgur.com/pzskSxo"><img src="https://i.imgur.com/pzskSxo.png" title="source: imgur.com" /></a>

### Collecting_Strings

<a href="https://imgur.com/HQE5RF6"><img src="https://i.imgur.com/HQE5RF6.png" title="source: imgur.com" /></a>

<a href="https://imgur.com/hqdaya8"><img src="https://i.imgur.com/hqdaya8.png" title="source: imgur.com" /></a>

### Further_Reading

[ssdeep advanced usage: click here!!!](https://ssdeep-project.github.io/ssdeep/usage.html)

### Challenge 1

#### **What is the SHA256 hash of the sample?**

<a href="https://imgur.com/CIwwTFX"><img src="https://i.imgur.com/CIwwTFX.png" title="source: imgur.com" /></a>

***Hash***:
B6D7E579A24EFC09C2DBA13CA90622790866E017A3311C1809C5041E91B7A930
***Algorithm***:
SHA256

#### **What is the ssdeep hash of the sample?**

<a href="https://imgur.com/UPYWqtV"><img src="https://i.imgur.com/UPYWqtV.png" title="source: imgur.com" /></a>

***ssdeep.exe "fuzzy" hash***:
3072:C5OLkQW8JS0k0wcBalDIs3hlAp5+hQQE89X3Qo+PgaE3:CsWnGYlAp5+hR9sYaE

***format***:
chunksize:chunk:double_chunk

#### **Can you attribute this sample to a particular malware family?**

<a href="https://imgur.com/bfWuSOT"><img src="https://i.imgur.com/bfWuSOT.png" title="source: imgur.com" /></a>

*Malware Family*: **Trojan Malware**

### Challenge 2

#### Utilising the second sample, can you correctly identify the kill-switch domain?


First, I obtained a strings dump of the malware sample. This can be done using the `strings.exe` command, or similar tools like `objdump` or `IDAPython` can be utilised for more complex analysis.

<a href="https://imgur.com/frfrqVY"><img src="https://i.imgur.com/frfrqVY.png" title="source: imgur.com" /></a>


Secondly, I had to consider the question. The question referred to a kill-switch domain, and while I am familiar with what a domain is, it required some additional research to understand the concept of a kill-switch domain. After some googling and some reading, it seems as though this domain, known as a "kill-switch domain," plays a critical role in cybersecurity and threat mitigation. This domain essentially functions as a safeguard against the spread and impact of malware, serving as the communication channel between the malware and its C2 (Command and Control) server. If we as security researchers can access this domain, it can assist us in gaining new insights and potentially disrupt or control the malware's communication with the C2 server. This domain is the very reason Marcus Hutchins was able to put a stop to the spread of the WannaCry Ransomware outbreak of May 2017.

So using this information and my Powershell knowledge, I was able to search the string dump for a pattern associated with domains - the obvious choice was the scheme: `http://|https://`

<a href="https://imgur.com/38yE0PZ"><img src="https://i.imgur.com/38yE0PZ.png" title="source: imgur.com" /></a>

Surely enough it returned the 'kill-switch' domain, without the noise.

</details>
<details>
  <summary><h3>Chapter 3: Dynamic Analysis - Techniques and Tooling</h3></summary>
</details>
<details>
  <summary><h3>Chapter 4: A Word on Automated Sandboxing</h3></summary>
</details>
<details>
  <summary><h3>Chapter 5: Advanced Static Analysis - Out of the White Noise</h3></summary>
</details>
<details>
  <summary><h3>Chapter 6: Advanced Dynamic Analysis - Looking at Explosions</h3></summary>
</details>
<details>
  <summary><h3>Chapter 7: Advanced Dynamic Analysis Part 2 - Refusing to Take the Blue Pill</h3></summary>
</details>
<details>
  <summary><h3>Chapter 8: De-Obfuscating Malicious Scripts: Putting the Toothpaste Back in the Tube</h3></summary>
</details>

## PROJECT2: Mr Robot (CTF) - VulnHub/Leon Johnson

<details>
  
</details>
