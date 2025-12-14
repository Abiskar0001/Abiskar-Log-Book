# Password Cracking Report

## 1. Introduction

This report documents the process used to crack passwords from the Phase 2 Booking System lab. Hashcat and dictionary attacks were used to recover passwords.

---

## 2. Cracked Passwords

Below are the cracked passwords, methods used, and screenshots (insert your own screenshots in VS Code).

### **1. Hash:** `827ccb0eea8a706c4c34a16891f84e7b`

* **Password:** 12345
* **Method:** Dictionary attack using *rockyou.txt*
* **Command Used:**

```
.\hashcat.exe -m 0 -a 0 "hashes.txt" "rockyou.txt"
```

* **Screenshot:** *![alt text](https://github.com/Abiskar0001/Abiskar-Log-Book/blob/main/BookingSystem-Phase1/Screenshot%202025-12-08%20233553-edit.png))*

---

### **2. Hash:** `fc5e038d38a57032085441e7fe7010b0`

* **Password:** helloworld
* **Method:** Dictionary attack
* **Screenshot:** *![alt text](https://github.com/Abiskar0001/Abiskar-Log-Book/blob/main/BookingSystem-Phase1/Screenshot%202025-12-08%20233553-edit.png)*

---

### **3. Hash:** `a0e8402fe185455606a2ae870dcbc4cd`

* **Password:** carrots123
* **Method:** Dictionary attack
* **Screenshot:** *![alt text](https://github.com/Abiskar0001/Abiskar-Log-Book/blob/main/BookingSystem-Phase1/Screenshot%202025-12-08%20233553-edit.png)*

---

### **4. Hash:** `d730fc82effd704296b5bbcff45f323e`

* **Password:** donuts4life
* **Method:** Dictionary attack
* **Screenshot:** *![alt text](https://github.com/Abiskar0001/Abiskar-Log-Book/blob/main/BookingSystem-Phase1/Screenshot%202025-12-08%20233553-edit.png)*

---

### **5. Hash:** `d57f21e6a273781dbf8b7657940f3b03`

* **Password:** aaaaaaaaaaa
* **Method:** Added the hash to hashes.txt and used dictionary attack
* **Screenshot:** *![alt text](https://github.com/Abiskar0001/Abiskar-Log-Book/blob/main/BookingSystem-Phase1/Screenshot%202025-12-08%20233553-edit.png)*

---

## 3. Questions & Answers

### **Q1: What is the main difference between Dictionary and Non‑Dictionary attacks?**

A **dictionary attack** uses a list of real passwords (like rockyou.txt) and checks each one to see if it matches the hash.  
A **non-dictionary attack** tries every possible combination of letters, numbers, and symbols (brute force) instead of using real words.

**Simple summary:**  
- **Dictionary = tries common passwords.**  
- **Non-dictionary = tries every possible password.

---

### **Q2: What advantage does an attacker gain by having access to the system's database that reveals users and password hashes?**

If an attacker gets the database, they can see all the usernames and the password hashes.  
They can try to crack the passwords **offline** without triggering alarms or rate limits.

**Simple summary:**  
- Crack passwords secretly.  
- Try millions of guesses quickly.  
- Target specific users.

---

### **Q3: What security benefits are achieved by using longer passwords?**

Longer passwords take much more time to crack because the number of possible combinations grows a lot with each extra character.

**Simple summary:**  
- Longer passwords = harder to brute-force.  
- Protect against fast cracking tools like Hashcat.  
- Even simple long passwords are stronger than short ones.

---

## 4. Conclusion

Five passwords were successfully cracked using dictionary and stdin-based hashcat techniques. The results demonstrate why weak or short passwords are insecure.
