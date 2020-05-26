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



