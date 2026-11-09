# SecLists - Curated

A curated, lightweight collection of wordlists from [SecLists (danielmiessler/SecLists)](https://github.com/danielmiessler/SecLists), specifically optimized for web application security assessments, bug bounty recon, and endpoint fuzzing without downloading gigabytes of unused lists.

---

## 📂 Included Collections

### 1. Web Content Discovery (`Discovery/Web-Content`)
Targeted wordlists for endpoint enumeration, directory busting, and API discovery:

- **`common.txt`** — Essential fast dictionary for top web roots (~4.7k entries).
- **`DirBuster-2007_directory-list-2.3-medium.txt`** — Standard for broad directory brute-forcing (~220k entries).
- **`raft-medium-words.txt` & `raft-medium-directories.txt`** — High-yield RAFT wordlists for file and directory discovery.
- **`quickhits.txt`** — High-probability sensitive paths and endpoints (~2.5k entries).
- **`common-api-endpoints-mazen160.txt`** — Common REST and microservice API paths.
- **Technology-specific lists** — CMS, IIS, Apache, CGI, framework routes, and hidden backups.

### 2. Web Fuzzing Payloads (`Fuzzing/`)
Comprehensive dictionaries and polyglots for web vulnerability testing:

- **SQL Injection (`Fuzzing/Databases/SQLi/`)**
  - `Generic-SQLi.txt`, `SQLi-Polyglots.txt`, `quick-SQLi.txt`, `NoSQL.txt`, `MySQL.fuzzdb.txt`, `MSSQL.fuzzdb.txt`.
- **Cross-Site Scripting (`Fuzzing/XSS/`)**
  - PortSwigger Cheat Sheet, Polyglots (`XSS-Polyglot-Ultimate-0xsobky.txt`), BruteLogic, and filter-bypass strings.
- **Local File Inclusion / Path Traversal (`Fuzzing/LFI/`)**
  - `LFI-Jhaddix.txt`, Linux and Windows LFI wordlists, package file lists.
- **Additional Payloads**
  - `403/` bypass headers and paths.
  - `JSON.Fuzzing.txt` for REST/JSON API parser testing.
  - `User-Agents/` for header rotation and evasion.
  - `LDAP.Fuzzing.txt` & `Unicode.txt` for encoding boundary tests.

---

## 🚀 Quick Usage

### Content Discovery with `ffuf`
```bash
ffuf -u https://TARGET.com/FUZZ -w Discovery/Web-Content/common.txt -mc 200,301,302,403
```

### Directory Enumeration with `gobuster`
```bash
gobuster dir -u https://TARGET.com -w Discovery/Web-Content/DirBuster-2007_directory-list-2.3-medium.txt -t 50
```

### LFI / Path Traversal Testing
```bash
ffuf -u https://TARGET.com/view?page=FUZZ -w Fuzzing/LFI/LFI-Jhaddix.txt -mr "root:"
```

### SQL Injection Parameter Fuzzing
```bash
ffuf -u https://TARGET.com/search?q=FUZZ -w Fuzzing/Databases/SQLi/quick-SQLi.txt -mc all -filter-mode and
```

---

## 📜 Credits & License

All lists originate from the upstream [danielmiessler/SecLists](https://github.com/danielmiessler/SecLists) project maintained by Daniel Miessler, Jason Haddix, Ignacio Portal, g0tmi1k, and the security community.

Distributed under the [MIT License](LICENSE).
