# Cybersecurity_Projects

Cybersecurity is my passion, and I've channelled that passion into a collection of practical projects that highlight my dedication to honing my skills. Each project here represents a step forward in my journey to understand and address the evolving challenges in cybersecurity. Dive into this repository to explore a diverse array of cybersecurity projects, each presenting its unique set of challenges and solutions. Whether you're a fellow enthusiast seeking inspiration, a beginner looking for hands-on learning opportunities, or a prospective employer curious about my approach, there's something here for you.

## Malware Analysis Techniques - Dylan Barker
<details>
<summary><h3>Chapter 2 - Static Analysis - Techniques and Tooling</h3></summary>

#### Hashing_Algorithms

Hashing algorithms are cryptographic techniques used to transform data (usually of variable sizes) into a fixed-length string of characters, which is typically a hexadecimal number. These algorithms are designed to be fast to compute but difficult to reverse, making them suitable for various security and data integrity purposes. They are known as one-way functions. Very easy to compute in one direction, however, they are extremely difficult to reverse engineer.

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

There are many choices for hashing data, though it is important you choose a hashing algorithm to suit your specific needs. For cryptographic security, newer and more secure algorithms like SHA-256, SHA-512, bcrypt, scrypt, Argon2, and BLAKE2 are recommended. MD5 and SHA-1 should be avoided in security-critical applications due to their vulnerabilities which are considered broken. MD5 and SHA-1 have both exhibited collision vulnerabilities and are also prone to attacks that undermine the one-way property of secure hash functions.  



##### Obtaining_file_hashes

##### Leveraging_VirusTotal

VirusTotal stands as a formidable tool for static malware analysis, offering assistance in the identification and attribution of malicious software through its extensive repo of publicly accessible data. It is widely used by analysts all over the world and assists us in making sure we don't continuously find ourselves rediscovering the wheel.  


#### Getting_Fuzzy (ssdeep.exe)








#### Picking_Up_The_Pieces

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



#### Malware_Stereotyping

#### Collecting_Strings

#### Further_Reading

#### Challenge 1

###### **What is the SHA256 hash of the sample?**



*Hash*:
B6D7E579A24EFC09C2DBA13CA90622790866E017A3311C1809C5041E91B7A930
*Algorithm*:
SHA256
###### **What is the ssdeep hash of the sample?**



*ssdeep.exe "fuzzy" hash*:
3072:C5OLkQW8JS0k0wcBalDIs3hlAp5+hQQE89X3Qo+PgaE3:CsWnGYlAp5+hR9sYaE

*format*:
chunksize:chunk:double_chunk

###### **Can you attribute this sample to a particular malware family?**


##### Attribution
*Malware Family*: **Trojan Malware**

#### Challenge 2

###### Utilising the second sample, can you correctly identify the kill-switch domain?


First, I obtained a strings dump of the malware sample. This can be done using the `strings.exe `command, or similar tools like ``objdump`` or `IDAPython` can be utilised for more complex analysis.




Secondly, I had to think about the question. The question points to a kill-switch domain and although I am familiar with what a domain is, it took some further research to understand what a kill-switch domain is. After some googling and some reading, it seems as though this domain which 

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
