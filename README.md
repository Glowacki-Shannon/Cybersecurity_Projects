# Cybersecurity_Projects

Cybersecurity is my passion, and I've channelled that passion into a collection of practical projects that highlight my dedication to honing my skills. Each project here represents a step forward in my journey to understand and address the evolving challenges in cybersecurity. Dive into this repository to explore a diverse array of cybersecurity projects, each presenting its unique set of challenges and solutions. Whether you're a fellow enthusiast seeking inspiration, a beginner looking for hands-on learning opportunities, or a prospective employer curious about my approach, there's something here for you.

## Malware Analysis Techniques - Dylan Barker

### *Chapter 2 - Static Analysis - Techniques and Tooling*

##### Hashing_Algorithms



##### Obtaining_file_hashes

##### Leveraging_VirusTotal

![[VirusTotal.png]]

VirusTotal is a great utility for static malware analysis, and it can assist in the detection of malware with its huge database of reliable publicly available.

Simply input a suspicious file, generated hash or even a URL of a website you may be questioning to access the database for the returned results of the analysis. 

![[VirusTotal_Detail.png]]

##### Getting_Fuzzy (ssdeep.exe)

![[ssdeep_fuzzy.png]]



![[ssdeep_Hash.png]]


##### Picking_Up_The_Pieces

###### *A table of common file headers related to malware*

|Header | File type|
|-------|-----------|
|MZ     |Windows PE (.exe, .dll)|
|PK..   |ZIP file formats (.zip, .docx, .apk, .jar)|
|Rar!.. |WinRAR archives|
|.ELF   |Linux ELF executable|
|X.S.BB |Mac disk image file|
|%PDF-  |PDF document|
|MSCF   |Microsoft cabinet files (.cab)|



##### Malware_Stereotyping

##### Collecting_Strings

##### Further_Reading

#### Challenge 1

###### **What is the SHA256 hash of the sample?**

![[Challenge1_Q1.png]]

*Hash*:
B6D7E579A24EFC09C2DBA13CA90622790866E017A3311C1809C5041E91B7A930
*Algorithm*:
SHA256
###### **What is the ssdeep hash of the sample?**

![[Challenge1_Q2.png]]

*ssdeep.exe "fuzzy" hash*:
3072:C5OLkQW8JS0k0wcBalDIs3hlAp5+hQQE89X3Qo+PgaE3:CsWnGYlAp5+hR9sYaE

*format*:
chunksize:chunk:double_chunk

###### **Can you attribute this sample to a particular malware family?**

![[Challenge1_Q3.png]]
##### Attribution
*Malware Family*: **Trojan Malware**

#### Challenge 2

###### Utilising the second sample, can you correctly identify the kill-switch domain?

![[Challenge2_txt.png]]
First, I obtained a strings dump of the malware sample. This can be done using the `strings.exe `command, or similar tools like ``objdump`` or `IDAPython` can be utilised for more complex analysis.



![[Challenge2.png]]
Secondly, I had to think about the question. The question points to a kill-switch domain and although I am familiar with what a domain is, it took some further research to understand what a kill-switch domain is. After some googling and some reading, it seems as though this domain which 
