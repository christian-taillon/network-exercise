# Network Exercise: TrickBot
This is a simple walk through of a file extraction excersise that may be performed in Network Forensics to enable File Forensics. The excersise is simple / no decryption neccessary and guides you through identifying a HTTP steam from a malicious host and recreating a file downloaded in the stream.

1. Search for the host `dchristjan.com`
```
http.host contains "ww.dchristjan.com"
```
2. Follow the HTTP Stream
3. Review. Note that the GET requests a zip: `/dd05ce3a-a9c9-4018-8252-d579eed1e670.zip`
4. Look at the file header for the file (aka first characters) to confirm. Review Zip file [magic number](https://en.wikipedia.org/wiki/ZIP_(file_format)).
5. File > Export objects > HTTP
6. Save the application/zip `dd05ce3a-a9c9-4018-8252-d579eed1e670.zip` file.
7. Unzip the file and get the SHA256 value.
```
unzip dd05ce3a-a9c9-4018-8252-d579eed1e670.zip
shasum -a 256 InvoiceAndStatement.lnk
```
![terminal](https://github.com/christian-taillon/network-exercise/blob/main/network-exercise.png?raw=true)


8. Run the file against a Sandbox, YaraRule set for TrickBot or take the Hash to a signature database like [VirusTotal](https://www.virustotal.com/gui/file/387682995c339dd34e1b7943d7bcb84a7c1a3b538ffa10cf5a1555361a40a0fd/detection).
