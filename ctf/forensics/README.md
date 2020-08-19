# Forensics

## File Categorization

### File Extension

There will be challenges that involve a file upload that checks the extension of the file based on some form of RegEx \(e.g. with some `substr()` , `strpos()` ,`preg_match()`\). 

* If the validator is just looking for the name to include `.pdf` then you can use double extensions, like `reverse_shell.pdf.php`. 
* You can use Burp Suite's Intruder on Sniper mode with a wordlist of extensions to check what extensions are allowed, e.g. `.php`, `.php2`, `.php3`, `.php4`, `.php5`,`.php6`, `.php7`,  `.phtm`, `.phtml`, `.phps`, `.php-s`, `.pht`, `.phar`.



### Media Type

Some servers will trust the `Content-Type` specified by the user, e.g.:

```php
<?php
$mime = $_SERVER["CONTENT_TYPE"];
if (strcasecmp($mime, "image/png") == 0){
    echo "photo"
} else {
    echo "not a photo"
}
```

```bash
$ curl 127.0.0.1:80/upload.php
not a photo%
$ curl 127.0.0.1:80/upload.php -H "Content-Type: image/png"
photo%
```

You can also change the `Content-Type` in Burp.

### Structure

![PNG Structure](../../.gitbook/assets/image%20%2815%29.png)

If the server is checking the structure of the file, consider Polyglot files \([link](https://medium.com/swlh/polyglot-files-a-hackers-best-friend-850bf812dd8a)\). Polyglots, in a security context, are files that are a valid form of multiple different file types. For example, a [GIFAR](https://en.wikipedia.org/wiki/Gifar) is both a GIF and a RAR file. There are also files out there that can be both GIF and JS, both PPT and JS, etc. Most famous one is PHAR-JPG \([link](https://github.com/kunte0/phar-jpg-polyglot)\).  


### Magic Bytes

File starting with specific leading bytes will usually be read as that type of file by utilities.

 A file might be corrupted. Use a hex editor `xd filename.png|head` and you may be able to guess the actual filetype from the contents \(e.g. `IDAT` means PNG\) and change the leading bytes to recover it.

{% embed url="https://en.wikipedia.org/wiki/List\_of\_file\_signatures" %}

### Known-plaintext attack \([link](https://en.wikipedia.org/wiki/Known-plaintext_attack)\)

If you have an encrypted file of a known type. If you XOR the encrypted file with the known magic bytes, you can potentially recover a key. Then, XOR the encrypted file with the key to decrypt and recover the image.

## Binwalk

```text
$ binwalk --dd='.*' <file to extract>
```

## Field Guide

{% embed url="https://trailofbits.github.io/ctf/forensics/" %}



