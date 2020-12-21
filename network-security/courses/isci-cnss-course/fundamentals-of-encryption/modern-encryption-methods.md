# Modern Encryption Methods

### Symmetric Encryption

Symmetric encryption refers to the methods where the same key is used to encrypt and decrypt the plaintext.

### Binary Operations

**XORing** has an interesting property in that it is reversible. Binary encryption using the XOR operation opens the door for some rather simple encryption. Take any message and convert it to binary numbers and then XOR that with some key. Converting a message to a binary number is a simple two-step process. First, convert a message to its ASCII code, and then convert those codes to binary numbers. 

Each letter/number will generate an eight-bit binary number. You can then use a random string of binary numbers of any given length as the key. Simply XOR your message with the key to get the encrypted text, and then XOR it with the key again to retrieve the original message.

This method is easy to use and great for computer science students; however, it does not work well for truly secure communications because the underlying letter and word frequency remains. This exposes valuable clues that even an amateur cryptographer can use to decrypt the message. Yet, it does provide a valuable introduction to the concept of single-key encryption. 

Although simply XORing the text is not the method typically employed, single-key encryption methods are widely used today.

### Data Encryption Standard

DES uses a symmetric key system, which means the same key is used to encrypt and to decrypt the message. DES uses short keys and relies on complex procedures to protect its information. The actual DES algorithm is quite complex. The basic concept, however, is as follows:

1. The data is divided into 64-bit blocks, and those blocks are then reordered.

2. Reordered data are then manipulated by 16 separate rounds of encryption, involving substitutions, bit-shifting, and logical operations using a 56-bit key.

3. Finally, the data are reordered one last time.

DES uses a 56-bit cipher key applied to a 64-bit block. There is actually a 64-bit key, but one bit of every byte is actually used for error detection, leaving just 56 bits for actual key operations. The problem with DES is the same problem that all symmetric key algorithms have: How do you transmit the key without it becoming compromised? This issue led to the development of public key encryption.

### Blowfish

Blowfish is a symmetric block cipher. This means that it uses a single key to both encrypt and decrypt the message and works on “blocks” of the message at a time. It uses a variable-length key ranging from 32 to 448 bits. This flexibility in key size allows you to use it in various situations. Blowfish was designed in 1993 by Bruce Schneier. It has been analysed extensively by the cryptography community and has gained wide acceptance. It is also a non-commercial \(that is, free of charge\) product, thus making it attractive to budget-conscious organisations.

### **AES \(Advanced Encryption Standard\)**

Advanced Encryption Standard \(AES\) uses the Rijndael algorithm. ****AES specifies three key sizes: 128, 192, and 256 bits. By comparison, DES keys are 56 bits long, and Blowfish allows varying lengths up to 448 bits. AES uses a block cipher. This algorithm is widely used, considered very secure, and therefore a good choice for many encryption scenarios.

### Public Key Encryption

With any public key encryption algorithm, one key is used to encrypt a message \(called the public key\) and another is used to decrypt the message \(the private key\). You can freely distribute your public key so that anyone can encrypt a message to send to you, but only you have the private key and only you can decrypt the message.

#### RSA

One significant advantage of RSA is that it is a public key encryption method. That means there are no concerns with distributing the keys for the encryption. However, RSA is much slower than symmetric ciphers. In fact, in general, asymmetric ciphers are slower than symmetric ciphers.

The steps to create the key are as follow:

**1**. Generate two large random primes, **p** and **q**, of approximately equal size.

**2**. Pick two numbers so that when they are multiplied together the product will be the size you want \(that is, 2048 bits, 4096 bits, etc.\).

**3**. Now multiply **p** and **q** to get **n**.

**4**. Let **n = pq**.

**5**. Multiply Euler’s totient for each of these primes. If you are not familiar with this concept, the Euler’s Totient is the total number of co-prime numbers. Two numbers are considered co-prime if they have no common factors. 

For example, if the original number is 7, then 5 and 7 would be co-prime. It just so happens that for prime numbers, this is always the number minus 1. For example, 7 has 6 numbers that are co-prime to it \(if you think about this a bit you will see that 1, 2, 3, 4, 5, 6 are all co-prime with 7\).

**6**. Let **m = \(p – 1\)\(q – 1\).**

**7**. Select another number; call this number **e**. You want to pick **e** so that it is co-prime to **m**.

**8**. Find a number **d** that when multiplied by **e** and modulo **m** would yield 1. \(Note: Modulo means to divide two numbers and return the remainder. For example, 8 modulo 3 would be 2.\)

**9**. Find **d**, such that **de mod m ≡ 1**.

Now you publish **e** and **n** as the public key and keep **d** and **n** as the secret key. To encrypt you simply take your message raised to the **e** power and modulo **n** **= Me % n**

To decrypt you take the ciphertext, and raise it to the **d** power modulo **n**:

**P = Cd % n**

RSA has become a popular encryption method. It is considered quite secure and is often used in situations where a high level of security is needed.

#### Elliptic Curve

The security of Elliptic Curve cryptography is based on the fact that finding the discrete logarithm of a random elliptic curve element with respect to a publicly known base point is difficult to the point of being impractical to do.

The size of the elliptic curve determines the difficulty of finding the algorithm, and thus the security of the implementation. The level of security afforded by an RSA-based system with a large modulus can be achieved with a much smaller elliptic curve group. There are actually several ECC algorithms. There is an ECC version of Diffie-Hellman, an ECC version of DSA, and many others.

The U.S. National Security Agency has endorsed ECC \(Elliptic Curve Cryptography\) by including schemes based on it in its Suite B set of recommended algorithms and allows their use for protecting information classified up to top secret with 384-bit keys.

### Digital Signatures and Certificates

A digital signature is not used to ensure the confidentiality of a message, but rather to guarantee who sent the message. This is referred to as non-repudiation. Essentially, a digital signature proves who the sender is. Digital signatures are actually rather simple, but clever. They simply reverse the asymmetric encryption process. 

Recall that in asymmetric encryption, the public key \(which anyone can have access to\) is used to encrypt a message to the recipient, and the private key \(which is kept secure, and private\) can decrypt it. With a digital signature, the sender encrypts something with his or her private key. If the recipient is able to decrypt that with the sender’s public key, then it must have been sent by the person purported to have sent the message.

#### Digital Certificates



Public keys are widely distributed and that getting someone’s public key is fairly easy to do and are also needed to verify a digital signature. As to how public keys are distributed, probably the most common way is through digital certificates. The digital certificate contains a public key and some means to verify whose public key it is.

X.509 is an international standard for the format and information contained in a digital certificate. X.509 is the most used type of digital certificate in the world. It is a digital document that contains a public key signed by a trusted third party, which is known as a certificate authority \(CA\). The contents of an X.509 certificate are:

* Version
* Certificate holder’s public key
* Serial number
* Certificate holder’s distinguished name
* Certificate’s validity period
* Unique name of certificate issuer
* Digital signature of issuer
* Signature algorithm identifier

A certificate authority issues digital certificates. The primary role of the CA is to digitally sign and publish the public key bound to a given user. It is an entity trusted by one or more users to manage certificates.

A registration authority \(RA\) is used to take the burden off, of a CA by handling verification prior to certificates being issued. RAs act as a proxy between users and CAs. RAs receive a request, authenticate it, and forward it to the CA.

A public key infrastructure \(PKI\) distributes digital certificates. This network of trusted CA servers serves as the infrastructure for distributing digital certificates that contain public keys. A PKI is an arrangement that binds public keys with respective user identities by means of a CA.

What if a certificate is expired, or revoked? A certificate revocation list \(CRL\) is a list of certificates that have been revoked for one reason or another. Certificate authorities publish their own certificate revocation lists. A newer method for verifying certificates is Online Certificate Status Protocol \(OCSP\), a real-time protocol for verifying certificates.

There are several different types of X.509 certificates. They each have at least the elements listed at the beginning of this section, but are for different purposes. The most common certificate types are listed below:

* Domain validation certificates are among the most common. These are used to secure communication with a specific domain. This is a low-cost certificate that website administrators use to provide TLS for a given domain.
* Wildcard certificates, as the name suggests, can be used more widely, usually with multiple sub-domains of a given domain. So rather than have a different X.509 certificate for each sub-domain, you would use a wildcard certificate for all sub-domains.
* Code-signing certificates are X.509 certificates used to digitally sign some type of computer code. These usually require more validation of the person requesting the certificate, before they can be issued.
* Machine/computer certificates are X.509 certificates assigned to a specific machine. These are often used in authentication protocols. For example, in order for the machine to sign into the network, it must authenticate using its machine certificate.
* User certificates are used for individual users. Like machine/computer certificates, these are often used for authentication. The user must present his or her certificate to authenticate prior to accessing some resource.
* E-mail certificates are used for securing e-mail. Secure Multipurpose Internet Mail Extensions \(S/MIME\) uses X.509 certificates to secure e-mail communications. 
* A Subject Alternative Name \(SAN\) is not so much a type of certificate as a special field in X.509. It allows you to specify additional items to be protected by this single certificate. These could be additional domains or IP addresses.
* Root certificates are used for root authorities. These are usually self-signed by that authority.

#### PGP Certificates

Pretty Good Privacy \(PGP\) is not a specific encryption algorithm, but rather a system. It offers digital signatures, asymmetric encryption, and symmetric encryption. It is often found in e-mail clients. PGP was introduced in the early 1990s, and it’s considered to be a very good system.

PGP uses its own certificate format. The main difference, however, is that PGP certificates are self-generated. They are not generated by any certificate authority.



