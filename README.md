
# Ultimate `colossus-words` Wordlist

## Overview
This project contains the file **`colossus-words.txt`**, which is a very large and powerful wordlist used to discover web paths and files during penetration testing and CTF challenges.

---

## How was the file created?

Three well-known and popular wordlist files in cybersecurity were combined:

1. **common.txt**  
   From the [SecLists](https://github.com/danielmiessler/SecLists) repository, it contains the most common paths used in web applications.

2. **directory-list-2.3-medium.txt**  
   Also from [SecLists](https://github.com/danielmiessler/SecLists), larger and more comprehensive than common.txt.

3. **raft-large-directories.txt**  
   From the same repository, it contains thousands of large and important paths to discover rare or hidden files and directories.

---

## Creation steps

- The three files were downloaded directly from the internet.  
- Their contents were merged into one file.  
- Duplicates were removed using the command `sort -u`.  
- The result is the file `colossus-words.txt` containing about 260,000 unique paths.

---

## How to use `colossus-words.txt`?

You can use this file with tools such as:

- [ffuf](https://github.com/ffuf/ffuf)  
- [gobuster](https://github.com/OJ/gobuster)  
- [dirsearch](https://github.com/maurosoria/dirsearch)

### Practical examples:

---

### 1. ffuf (Fast web fuzzer)

```bash
ffuf -u http://10.10.67.228/FUZZ -w colossus-words.txt -mc 200,301,302,403 -t 50 -e .php,.html,.bak
````

* `-u`: target URL with the keyword **FUZZ** as the placeholder for paths
* `-w`: wordlist file
* `-mc`: accepted status codes
* `-t`: number of threads to speed up scanning
* `-e`: file extensions to look for

---

### 2. gobuster (Go-based directory/file brute forcing tool)

```bash
gobuster dir -u http://10.10.67.228/ -w colossus-words.txt -t 50 -e -x php,html,bak -s 200,301,302,403
```

* `dir`: directory scanning mode
* `-u`: target URL
* `-w`: wordlist file
* `-t`: number of threads
* `-e`: show extensions
* `-x`: file extensions
* `-s`: accepted status codes

---

### 3. dirsearch (Python tool for directory scanning)

```bash
python3 dirsearch.py -u http://10.10.67.228/ -w colossus-words.txt -e php,html,bak -t 50 -x 404
```

* `-u`: target website
* `-w`: wordlist file
* `-e`: extensions
* `-t`: number of threads
* `-x`: ignore status codes (here 404)

---

## Additional tips

* You can modify the list of extensions or status codes according to your target.
* Due to the large file size, you might need to reduce the number of threads depending on your device resources.
* It is recommended to monitor performance and manage the scan to avoid getting blocked by the target server.

---

## Usage rights

The merged files are taken from publicly available open-source repositories (SecLists and others) for educational and professional security use only.

---

## Contact

For help or inquiries, contact me:
**mr\_piip-pro**
