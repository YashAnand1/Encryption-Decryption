<div align = "center">

# Encryption-Decryption

</div>

# # Task 1: Symetric Encrypting

## Introduction
The task was to encrypt a file from user 1 and decrypt it in user 2. For this task, I heavilt utilised this [article by BaeldungLinux](https://www.baeldung.com/linux/encrypt-decrypt-files)


## Steps followed
Created 2 users using:
```
sudo adduser user001
sudo adduser user002
```

Then I created a new text file using the following steps:
```
nano file.txt
This is Yash's sample file.
ctrl+o
```

Then I proceeded to check the version of gpg (GNU Privacy Guard) on my system using the following steps:
```
gnupg --version
```

Once ensuring I had gnupg installed, I encrypted the created `file.txt` using the following command:
```
gpg --batch --output file.txt.gpg --passphrase a --symmetric file.txt
```

Doing so created a new encrypted version of the file.txt, which gave the following output upon running `cat file.txt.gpg` :
```
�       �}o������T��Uf22�h$8�)�����e� �2��m�
f�_�}*:���E^�TG�1e�ih��BJ��i�i�r�t��)ǿ?=�Ɗ
```

As a part of the task, I needed to send the encrypted file to the second user and to do so, I first added the both of the users to the sudoers file using `visudo` from my root account. Then from user001, I shared the file using:
```
sudo scp -r file.txt.gpg /home/user002
```

I ensured that the file had moved to the second user using `ls` inside the terminal tab where I was logged in as user002. In order to decrypt the file, I ran:
```
gpg --batch --output file.txt --passphrase a --decrypt file.txt.gpg
```

I then ran `cat file.txt` for displaying the contents of this file. The file had indeed been decrypted as I was able to view the content of this file successfuly:
```
This is Yash's sample file.
```

## Task 1: Asymetric Encrypting   
