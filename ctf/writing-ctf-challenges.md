# Writing CTF Challenges

Here are some ways to create challenges:

#### XOR a string or file with a key in Python \([link](https://opentechnotes.blogspot.com/2014/08/xor-string-with-key-in-python.html)\)

```python
import os, sys
from itertools import cycle

if len(sys.argv) != 3:
 print "usage: %s <filename> <key>" % sys.argv[0]
 sys.exit()

if os.path.exists(sys.argv[1]):
 data = open(sys.argv[1]).read()
 xored = [chr(ord(a) ^ ord(b)) for a,b in zip(data, cycle(sys.argv[2]))]
 
 open(sys.argv[1], 'w').write(''.join(xored))

 print "file xored"
 
else:
 print "%s: file not found" % sys.argv[1]
```



#### Special Morse using \([https://github.com/sotojuan/morse](https://github.com/sotojuan/morse)\)

```text
$ echo "Hey there! I hope you like dogs. Here is a flag. No wait. Here it is: flag{itis_m0r53_0f_c0ur53}. There you go. I hope you had fun!" | morse | sed -e 's/-/bark/g; s/./woof/g;s/{/growl/g;s/}/growl/g;s/\///g;s//whine/g'
woofwoofwoofwoof woof barkwoofbarkbark  bark woofwoofwoofwoof woof woofbarkwoof woof !  woofwoof  woofwoofwoofwoof barkbarkbark woofbarkbarkwoof woof  barkwoofbarkbark barkbarkbark woofwoofbark  woofbarkwoofwoof woofwoof barkwoofbark woof  barkwoofwoof barkbarkbark barkbarkwoof woofwoofwoof woofbarkwoofbarkwoofbark  woofwoofwoofwoof woof woofbarkwoof woof  woofwoof woofwoofwoof  woofbark  woofwoofbarkwoof woofbarkwoofwoof woofbark barkbarkwoof woofbarkwoofbarkwoofbark  barkwoof barkbarkbark  woofbarkbark woofbark woofwoof bark woofbarkwoofbarkwoofbark  woofwoofwoofwoof woof woofbarkwoof woof  woofwoof bark  woofwoof woofwoofwoof barkbarkbarkwoofwoofwoof  woofwoofbarkwoof woofbarkwoofwoof woofbark barkbarkwoof growl woofwoof bark whine woofwoof woofwoofwoof whine barkbark barkbarkbarkbarkbark woofbarkwoof woofwoofwoofwoofwoof woofwoofwoofbarkbark whine barkbarkbarkbarkbark woofwoofbarkwoof whine barkwoofbarkwoof barkbarkbarkbarkbark woofwoofbark woofbarkwoof woofwoofwoofwoofwoof woofwoofwoofbarkbark growl woofbarkwoofbarkwoofbark  bark woofwoofwoofwoof woof woofbarkwoof woof  barkwoofbarkbark barkbarkbark woofwoofbark  barkbarkwoof barkbarkbark woofbarkwoofbarkwoofbark  woofwoof  woofwoofwoofwoof barkbarkbark woofbarkbarkwoof woof  barkwoofbarkbark barkbarkbark woofwoofbark  woofwoofwoofwoof woofbark barkwoofwoof  woofwoofbarkwoof woofwoofbark barkwoof !
```



