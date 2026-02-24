# 🏴‍☠️ John the Ripper: Hash Cracking Lab Writeup

Ok, so in this lab, I learned about **John the Ripper** (or simply John), which is a very powerful hash-cracking tool, and explored how it can be used to crack many different types of files and passwords.

## 🧠 Understanding Hashes
As we know, hashes are the best way to store passwords or secret data. They store them in a way where the input can be of any size, but the output will always be the same size. This creates a pigeonhole effect. 

However, an unhashing algorithm would be an **NP** (Non-deterministic Polynomial time) problem, meaning it cannot be computed or reversed in a reasonable amount of time using standard computers.

## 🛠️ How John the Ripper Works
Because we can't just "reverse" a hash, that's where tools like John the Ripper come in. John takes a massive library of words, converts them into hashes, and then matches them against the target hash. These large word libraries mostly consist of millions of common passwords used worldwide.



To do a dictionary attack with John, we need a wordlist. In my case, I used `rockyou.txt` from the famous rockyou.com database leak.

I also learned how to install John the Ripper and discovered there are different versions. The most famous one is **Jumbo John**, which comes packed with many interesting and extended features.

## 💻 Practical Applications & Commands

In short, I learned the applications of John, like using it to automatically crack hashes without specifying the hash type (although it's much faster and better if we do provide it). 

Example command:
```bash
john --format=raw-md5 --wordlist=rockyou.txt hash.txt
```

Before cracking, I also got familiar with a very helpful tool called hash-identifier,which is used to identify the hash type so we can feed the correct format to John. I performed several tasks where I first found the hash type using the identifier, and then cracked those hashes.

## 🪟 Windows vs. 🐧 Linux Hashes
### Windows Authentication Hashes
I learned how to crack Windows authentication hashes. Windows mostly uses NTLM, which is saved in the SAM file. These hashes can be spoofed/extracted using tools like Mimikatz, and then cracked by John the Ripper in the exact same way.

### Linux Shadow Files
Cracking Linux shadow files required some interesting extra steps. John needs to be able to identify the file it's reading, so I had to use a built-in tool in the John suite called unshadow. This combines both the /etc/passwd and /etc/shadow files into a single file that John can easily read and use to crack the info.

## 🎯 Single Crack Mode & Custom Rules
After the basics, I learned about Single Crack Mode. This mode uses provided information (like the username, GECOS fields, etc.) to smartly guess the passwords.

I also learned that we can set custom rules. You know how websites ask you to set your password with rules like "First letter must be capital, add a number"? We can give these exact types of rules to John to help it guess passwords that follow common human patterns.

📁 Cracking Archives & SSH Keys
Further into the lab, I learned how to crack password-protected .zip and .rar files. You can't feed a zip file directly to John, so you have to extract the hash first using:

```zip2john```

```rar2john```

Finally, I learned how to even crack SSH keys (like RSA files) using ssh2john and cracking the resulting hash.

## 🛡️ Conclusion
Overall, in this lab, I did practical exercises for every single task. Doing this hands-on allowed me to really think like an attacker, which is incredibly useful when you are on the other side defending your own system.
