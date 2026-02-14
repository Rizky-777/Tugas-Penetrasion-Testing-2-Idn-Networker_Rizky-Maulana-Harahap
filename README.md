# 🔐 Tugas Penetration Testing 2 - IDN Networker
### Rizky Maulana Harahap

![OverTheWire Banner](https://img.shields.io/badge/OverTheWire-Bandit-orange?style=for-the-badge)
![Linux](https://img.shields.io/badge/Linux-CLI-blue?style=for-the-badge&logo=linux)
![Security](https://img.shields.io/badge/CyberSecurity-Penetration%20Testing-red?style=for-the-badge)

## 📋 Deskripsi
Repository ini berisi write-up lengkap dan solusi langkah-demi-langkah untuk tantangan **OverTheWire: Bandit Wargame** dari Level 0 hingga Level 33. Proyek ini bertujuan untuk melatih dan meningkatkan keterampilan dalam:
- Linux Command Line Interface (CLI)
- Keamanan Siber (Cybersecurity)
- Penetration Testing Dasar
- Problem Solving dalam Environment Linux

## 🎯 Tujuan Pembelajaran
- Memahami konsep dasar keamanan sistem Linux
- Menguasai command-line tools untuk security testing
- Mengembangkan logical thinking dalam mencari celah keamanan
- Mempelajari teknik-teknik dasar penetration testing

## 📚 Daftar Isi
- [Level 0 → Level 1](#level-0--level-1)
- [Level 1 → Level 2](#level-1--level-2)
- [Level 2 → Level 3](#level-2--level-3)
- ... (hingga Level 33)
- [Commands Learned](#-commands-learned)
- [Kesimpulan](#-kesimpulan)

---

## 🚀 Quick Start

### Prerequisites
- Terminal/Command Line Interface
- SSH Client
- Koneksi Internet

### Cara Mengakses Bandit
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Password untuk Level 0: `bandit0`

---

## 📖 Write-Up Solutions

### Level 0 → Level 1
**Tujuan:** Login ke game menggunakan SSH dan temukan password untuk level berikutnya.

**Solusi:**
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
```

**Password untuk Level 1:** `[masukkan password di sini]`

---

### Level 1 → Level 2
**Tujuan:** Password tersimpan dalam file bernama "-"

**Solusi:**
```bash
cat ./-
# atau
cat < -
```

**Konsep:** Handling special characters dalam filename

**Password untuk Level 2:** `[masukkan password di sini]`

---

### Level 2 → Level 3
**Tujuan:** Password tersimpan dalam file dengan spasi di namanya

**Solusi:**
```bash
cat "spaces in this filename"
# atau
cat spaces\ in\ this\ filename
```

**Password untuk Level 3:** `[masukkan password di sini]`

---

### Level 3 → Level 4
**Tujuan:** Password tersimpan dalam hidden file

**Solusi:**
```bash
cd inhere
ls -la
cat .hidden
```

**Password untuk Level 4:** `[masukkan password di sini]`

---

### Level 4 → Level 5
**Tujuan:** Password tersimpan dalam satu-satunya file human-readable

**Solusi:**
```bash
cd inhere
file ./-file*
cat ./-file07
```

**Password untuk Level 5:** `[masukkan password di sini]`

---

### Level 5 → Level 6
**Tujuan:** Find file dengan properti: human-readable, 1033 bytes, non-executable

**Solusi:**
```bash
find . -type f -size 1033c ! -executable -exec file {} + | grep text
cat ./maybehere07/.file2
```

**Password untuk Level 6:** `[masukkan password di sini]`

---

### Level 6 → Level 7
**Tujuan:** Find file di server dengan: owned by user bandit7, group bandit6, 33 bytes

**Solusi:**
```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```

**Password untuk Level 7:** `[masukkan password di sini]`

---

### Level 7 → Level 8
**Tujuan:** Password ada di data.txt next to word "millionth"

**Solusi:**
```bash
grep millionth data.txt
```

**Password untuk Level 8:** `[masukkan password di sini]`

---

### Level 8 → Level 9
**Tujuan:** Password adalah satu-satunya baris yang hanya muncul sekali

**Solusi:**
```bash
sort data.txt | uniq -u
```

**Password untuk Level 9:** `[masukkan password di sini]`

---

### Level 9 → Level 10
**Tujuan:** Password dalam data.txt dalam format human-readable dengan beberapa "="

**Solusi:**
```bash
strings data.txt | grep "===="
```

**Password untuk Level 10:** `[masukkan password di sini]`

---

### Level 10 → Level 11
**Tujuan:** Password di-encode dengan base64

**Solusi:**
```bash
base64 -d data.txt
```

**Password untuk Level 11:** `[masukkan password di sini]`

---

### Level 11 → Level 12
**Tujuan:** Password ter-rotasi 13 posisi (ROT13)

**Solusi:**
```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

**Password untuk Level 12:** `[masukkan password di sini]`

---

### Level 12 → Level 13
**Tujuan:** Hexdump yang telah dikompres berulang kali

**Solusi:**
```bash
mkdir /tmp/mywork
cp data.txt /tmp/mywork
cd /tmp/mywork
xxd -r data.txt > data
file data
# Lakukan decompress berulang menggunakan gzip, bzip2, tar
mv data data.gz
gzip -d data.gz
# Ulangi hingga mendapat file ASCII text
```

**Password untuk Level 13:** `[masukkan password di sini]`

---

### Level 13 → Level 14
**Tujuan:** Gunakan SSH private key untuk login ke bandit14

**Solusi:**
```bash
ssh -i sshkey.private bandit14@localhost -p 2220
```

**Password untuk Level 14:** `[baca dari /etc/bandit_pass/bandit14]`

---

### Level 14 → Level 15
**Tujuan:** Submit password level saat ini ke port 30000

**Solusi:**
```bash
cat /etc/bandit_pass/bandit14 | nc localhost 30000
```

**Password untuk Level 15:** `[masukkan password di sini]`

---

### Level 15 → Level 16
**Tujuan:** Submit password menggunakan SSL encryption ke port 30001

**Solusi:**
```bash
cat /etc/bandit_pass/bandit15 | openssl s_client -connect localhost:30001 -ign_eof
```

**Password untuk Level 16:** `[masukkan password di sini]`

---

### Level 16 → Level 17
**Tujuan:** Find port yang listening antara 31000-32000 dan gunakan SSL

**Solusi:**
```bash
nmap -p 31000-32000 localhost
openssl s_client -connect localhost:31790
# Paste password bandit16
# Save SSH key yang didapat
```

**Password untuk Level 17:** `[gunakan SSH key]`

---

### Level 17 → Level 18
**Tujuan:** Password ada di passwords.new, temukan perbedaan dengan passwords.old

**Solusi:**
```bash
diff passwords.old passwords.new
```

**Password untuk Level 18:** `[masukkan password di sini]`

---

### Level 18 → Level 19
**Tujuan:** Password di readme, tapi .bashrc logout otomatis

**Solusi:**
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```

**Password untuk Level 19:** `[masukkan password di sini]`

---

### Level 19 → Level 20
**Tujuan:** Gunakan setuid binary untuk akses password bandit20

**Solusi:**
```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

**Password untuk Level 20:** `[masukkan password di sini]`

---

### Level 20 → Level 21
**Tujuan:** Program yang connect ke localhost dan kirim password

**Solusi:**
```bash
# Terminal 1:
echo "GbKksEFF4yrVs6il55v6gwY5aVje5f0j" | nc -l -p 6000

# Terminal 2:
./suconnect 6000
```

**Password untuk Level 21:** `[masukkan password di sini]`

---

### Level 21 → Level 22
**Tujuan:** Cari password di cron job

**Solusi:**
```bash
cd /etc/cron.d
cat cronjob_bandit22
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

**Password untuk Level 22:** `[masukkan password di sini]`

---

### Level 22 → Level 23
**Tujuan:** Analisis script cron yang menggunakan md5hash

**Solusi:**
```bash
cat /etc/cron.d/cronjob_bandit23
cat /usr/bin/cronjob_bandit23.sh
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
cat /tmp/[hasil_hash]
```

**Password untuk Level 23:** `[masukkan password di sini]`

---

### Level 23 → Level 24
**Tujuan:** Script yang execute dan delete script di direktori

**Solusi:**
```bash
mkdir /tmp/mywork23
cd /tmp/mywork23
nano script.sh
# Script: cat /etc/bandit_pass/bandit24 > /tmp/mywork23/password
chmod 777 script.sh
chmod 777 /tmp/mywork23
cp script.sh /var/spool/bandit24/foo
# Tunggu 1 menit
cat password
```

**Password untuk Level 24:** `[masukkan password di sini]`

---

### Level 24 → Level 25
**Tujuan:** Brute force 4-digit PIN code

**Solusi:**
```bash
mkdir /tmp/mywork24
cd /tmp/mywork24
nano bruteforce.sh
# Script untuk generate 0000-9999
chmod +x bruteforce.sh
./bruteforce.sh | nc localhost 30002
```

**Password untuk Level 25:** `[masukkan password di sini]`

---

### Level 25 → Level 26
**Tujuan:** Exploit shell yang menggunakan `more`

**Solusi:**
```bash
# Resize terminal menjadi sangat kecil
ssh -i bandit26.sshkey bandit26@localhost -p 2220
# Saat di more, tekan 'v' untuk vim
# :set shell=/bin/bash
# :shell
```

**Password untuk Level 26:** `[masukkan password di sini]`

---

### Level 26 → Level 27
**Tujuan:** Gunakan setuid binary dari bandit26 shell

**Solusi:**
```bash
# Dari vim shell level sebelumnya
./bandit27-do cat /etc/bandit_pass/bandit27
```

**Password untuk Level 27:** `[masukkan password di sini]`

---

### Level 27 → Level 28
**Tujuan:** Clone git repository

**Solusi:**
```bash
mkdir /tmp/mywork27
cd /tmp/mywork27
git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
cd repo
cat README
```

**Password untuk Level 28:** `[masukkan password di sini]`

---

### Level 28 → Level 29
**Tujuan:** Password di git commit history

**Solusi:**
```bash
mkdir /tmp/mywork28
cd /tmp/mywork28
git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
cd repo
git log
git show [commit_hash]
```

**Password untuk Level 29:** `[masukkan password di sini]`

---

### Level 29 → Level 30
**Tujuan:** Password di branch lain

**Solusi:**
```bash
mkdir /tmp/mywork29
cd /tmp/mywork29
git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
cd repo
git branch -a
git checkout dev
cat README.md
```

**Password untuk Level 30:** `[masukkan password di sini]`

---

### Level 30 → Level 31
**Tujuan:** Password di git tag

**Solusi:**
```bash
mkdir /tmp/mywork30
cd /tmp/mywork30
git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
cd repo
git tag
git show secret
```

**Password untuk Level 31:** `[masukkan password di sini]`

---

### Level 31 → Level 32
**Tujuan:** Push file ke remote repository

**Solusi:**
```bash
mkdir /tmp/mywork31
cd /tmp/mywork31
git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
cd repo
echo "May I come in?" > key.txt
git add -f key.txt
git commit -m "Add key.txt"
git push origin master
```

**Password untuk Level 32:** `[masukkan password di sini]`

---

### Level 32 → Level 33
**Tujuan:** Escape dari uppercase shell

**Solusi:**
```bash
$0
cat /etc/bandit_pass/bandit33
```

**Password untuk Level 33:** `[masukkan password di sini]`

---

## 🛠️ Commands Learned

Berikut adalah daftar command Linux yang dipelajari dan digunakan selama menyelesaikan Bandit Wargame:

### 🔐 SSH & Network
| Command | Deskripsi | Penggunaan dalam Challenge |
|---------|-----------|---------------------------|
| `ssh` | Secure Shell untuk remote login | Digunakan di setiap level untuk connect ke server Bandit |
| `ssh -i` | SSH dengan private key | Level 13→14: Login menggunakan SSH private key |
| `nc` (netcat) | Network utility untuk read/write data | Level 14→15, 20→21: Mengirim data ke port tertentu |
| `openssl s_client` | SSL/TLS client | Level 15→16, 16→17: Komunikasi terenkripsi ke port |
| `nmap` | Network scanner | Level 16→17: Scan port yang listening di range tertentu |

### 📁 File Operations
| Command | Deskripsi | Penggunaan dalam Challenge |
|---------|-----------|---------------------------|
| `cat` | Membaca dan menampilkan isi file | Hampir semua level untuk membaca password file |
| `ls` | List directory contents | Level dasar untuk melihat file di directory |
| `ls -la` | List all files termasuk hidden | Level 3→4: Menemukan hidden file |
| `file` | Determine file type | Level 4→5, 12→13: Identifikasi tipe file |
| `find` | Search for files | Level 5→6, 6→7: Mencari file dengan kriteria spesifik |

### 🔍 Text Processing
| Command | Deskripsi | Penggunaan dalam Challenge |
|---------|-----------|---------------------------|
| `grep` | Search text patterns | Level 7→8: Mencari kata "millionth" di file besar |
| `sort` | Sort lines of text | Level 8→9: Mengurutkan data sebelum filter |
| `uniq` | Remove duplicate lines | Level 8→9: Menemukan baris yang unik |
| `strings` | Extract printable strings | Level 9→10: Ekstrak human-readable text dari binary |
| `tr` | Translate characters | Level 11→12: Decode ROT13 cipher |
| `diff` | Compare files | Level 17→18: Membandingkan dua file password |

### 🗜️ Compression & Encoding
| Command | Deskripsi | Penggunaan dalam Challenge |
|---------|-----------|---------------------------|
| `base64 -d` | Decode base64 | Level 10→11: Decode password yang ter-encode base64 |
| `gzip -d` | Decompress gzip file | Level 12→13: Ekstrak file yang dikompres gzip |
| `bzip2 -d` | Decompress bzip2 file | Level 12→13: Ekstrak file yang dikompres bzip2 |
| `tar -xvf` | Extract tar archive | Level 12→13: Ekstrak multiple compressed archives |
| `xxd -r` | Reverse hexdump | Level 12→13: Convert hexdump kembali ke binary |

### 🔧 System & Permissions
| Command | Deskripsi | Penggunaan dalam Challenge |
|---------|-----------|---------------------------|
| `chmod` | Change file permissions | Level 23→24: Memberikan permission execute pada script |
| `setuid binary` | Execute with different user privileges | Level 19→20, 26→27: Eksekusi command sebagai user lain |
| `./` | Execute binary file | Berbagai level untuk menjalankan program setuid |

### ⏰ Cron & Scheduling
| Command | Deskripsi | Penggunaan dalam Challenge |
|---------|-----------|---------------------------|
| `cron` | Time-based job scheduler | Level 21→22, 22→23, 23→24: Memahami scheduled tasks |
| `cat /etc/cron.d/` | View cron jobs | Level 21→24: Analisis cronjob untuk menemukan password |
| `/var/spool/` | Cron spool directory | Level 23→24: Direktori untuk execute script via cron |

### 🌿 Git Commands
| Command | Deskripsi | Penggunaan dalam Challenge |
|---------|-----------|---------------------------|
| `git clone` | Clone repository | Level 27→28, 28→29, 29→30, 30→31: Download git repo |
| `git log` | View commit history | Level 28→29: Menemukan password di commit history |
| `git show` | Show commit details | Level 28→29, 30→31: Melihat detail commit dan tag |
| `git branch -a` | List all branches | Level 29→30: Menemukan branch development |
| `git checkout` | Switch branches | Level 29→30: Pindah ke branch lain untuk menemukan password |
| `git tag` | List tags | Level 30→31: Menemukan secret tag |
| `git add -f` | Force add file | Level 31→32: Bypass gitignore |
| `git commit` | Commit changes | Level 31→32: Commit file ke repository |
| `git push` | Push to remote | Level 31→32: Upload changes ke remote server |

### 🎯 Advanced Techniques
| Command | Deskripsi | Penggunaan dalam Challenge |
|---------|-----------|---------------------------|
| `2>/dev/null` | Redirect error messages | Level 6→7: Suppres error messages saat find di root |
| `\| grep` | Pipe output ke grep | Berbagai level untuk filter output |
| `vim` | Text editor (escape tool) | Level 25→26: Exploit more untuk akses shell |
| `$0` | Shell variable | Level 32→33: Escape dari uppercase shell |
| `md5sum` | Calculate MD5 hash | Level 22→23: Memahami hash untuk prediksi filename |

### 💡 Tips & Tricks
- **Handling special filenames**: Gunakan `./`, quotes, atau backslash untuk file dengan karakter spesial
- **Redirection**: `2>/dev/null` sangat berguna untuk membersihkan error messages
- **Pipes**: Kombinasi command dengan `|` sangat powerful (contoh: `sort | uniq -u`)
- **Man pages**: Gunakan `man [command]` untuk dokumentasi lengkap
- **Tab completion**: Gunakan tab untuk autocomplete path dan filename

---

## 📊 Statistik Penyelesaian
- **Total Level Diselesaikan:** 34 level (0-33)
- **Command yang Dipelajari:** 50+ Linux commands
- **Waktu Penyelesaian:** 60 Menit
- **Tingkat Kesulitan:** ⭐⭐⭐⭐☆

---

## 💡 Key Takeaways

### Technical Skills
1. **Linux CLI Mastery**: Menguasai fundamental dan advanced Linux commands
2. **File System Navigation**: Memahami struktur direktori Linux dan permissions
3. **Text Processing**: Mahir dalam manipulasi dan analisis text files
4. **Encoding & Compression**: Familiar dengan berbagai format encoding dan compression
5. **Git Version Control**: Memahami git workflow dan version control concepts
6. **Network Security**: Basic understanding of SSL/TLS, port scanning, dan network communication

### Security Concepts
- **Privilege Escalation**: Memahami setuid binaries dan permission exploitation
- **Information Disclosure**: Mencari informasi sensitive di berbagai tempat
- **Encryption & Encoding**: Berbagai metode untuk menyembunyikan data
- **Git Security**: Bahaya menyimpan credentials di version control
- **Cron Security**: Analisis scheduled tasks untuk security assessment

---

## 🎓 Kesimpulan

OverTheWire Bandit adalah starting point yang sangat baik untuk belajar:
- **Linux command-line fundamentals**
- **Basic security concepts**
- **Problem-solving skills**
- **Logical thinking dalam cybersecurity context**

Setelah menyelesaikan semua level, saya memiliki foundation yang kuat untuk melanjutkan ke wargame yang lebih advanced seperti:
- Natas (Web security)
- Leviathan (Binary exploitation)
- Krypton (Cryptography)

---

## 🔗 Resources

- [OverTheWire Bandit](https://overthewire.org/wargames/bandit/)
- [Linux Command Line Basics](https://ubuntu.com/tutorials/command-line-for-beginners)
- [Git Documentation](https://git-scm.com/doc)
- [Bash Scripting Tutorial](https://www.shellscript.sh/)

---

## 📝 Notes
Repository ini dibuat sebagai bagian dari Tugas Penetration Testing 2 - IDN Networker. Semua solusi ditemukan secara independent dengan referensi ke dokumentasi resmi dan man pages.

---

## 👤 Author
**Rizky Maulana Harahap**
- GitHub: [@Rizky-777](https://github.com/Rizky-777)
- Program: IDN Networker - Penetration Testing

---

## 📜 License
Educational purposes only. Please solve the challenges yourself before referring to solutions.

---

## ⚠️ Disclaimer
Konten dalam repository ini adalah untuk tujuan edukasi. Gunakan pengetahuan ini secara bertanggung jawab dan etis. Jangan gunakan untuk aktivitas ilegal atau merugikan pihak lain.

---

**Happy Hacking! 🚀**
