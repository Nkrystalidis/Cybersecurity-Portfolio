# Linux Security Investigation: Data Decryption & Cryptography

## Scenario
As a security analyst, I investigated a simulated ransomware/data encryption event. The objective was to navigate the file system to locate hidden decryption instructions, decipher a basic cryptographic algorithm, and use enterprise command-line tools to recover the encrypted data.

## Task
Utilize Linux command-line tools (Bash) to uncover hidden files, manipulate text strings using pipes, and execute symmetric decryption commands.

## Action
- Explored the directory structure and utilized `ls -a` to discover a hidden file (`.leftShift3`) containing encrypted recovery instructions.
- Utilized the `tr` command and piping (`|`) to translate and decode a substitution cipher, extracting the necessary AES encryption key and command syntax.
- Executed the `openssl aes-256-cbc` command with the extracted key (`ettubrute`) to successfully decrypt the target file (`Q1.encrypted`).

## Outcome
Successfully recovered the encrypted data. This project demonstrates practical proficiency in Linux file system navigation, command-line text manipulation, and applied cryptography using OpenSSL.
