## About gpg for trusted signatures of software

gpg uses [public key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography) to allow one person to create a signature that another person can verify, if they have a trusted copy if the public key of the signer.

For easy distribution of a large file, the signer often creates a "checksum" file containing several different cryptographic hashes of the original file. They then sign 
the checksum file.

In distribution of software, the system is used as follows.

The signer:
* owns a secret, private key, and
* uses it to create a public key, which they can share with any recipients of messages.
* uses the private key to make a signature for a message.
The signature:
* can only be made using the private key and the original document and the private key.
* can be uniquely verified using the original document and the public key.
The receiver:
* must own and trust a copy of the private key of the sender
* must receive the original message and the signature made by the sender with their secret key. These two are sometimes combined in one file.
* can use 


## gnupg home directory

Windows/cygwin applications
use the standard ~/.gnupg path
of the linux/unixy versions)
Other Windows versions of gnupg keep their
data in
in %APPDATA%\gnupg, which usually expands to
C:\Users\<username>\AppData\Roaming\gnupg 
( for recent Windows versions, but different
before Windows Vista.)
