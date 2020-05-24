# Buffer Overflow Attacks

A buffer overflow attack is designed to put more data in a buffer than the buffer was designed to hold. Any program that communicates with the Internet or a private network must receive some data. This data is stored, at least temporarily, in a space in memory called a buffer. If the programmer who wrote the application was careful, the buffer will truncate or reject any information that exceeds the buffer limit.

For example, if the buffer can hold 1024 bytes of data and you try to fill it with 2048 bytes, the extra 1024 bytes is then simply loaded into memory.

If the extra data is actually a malicious program, then it has just been loaded into memory and is running on the target system. Or perhaps the perpetrator simply wants to flood the target machine’s memory, thus overwriting other items that are currently in memory and causing them to crash. 

