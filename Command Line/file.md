# FILE

In the previous lesson, we learned about `touch`. Did you notice that the filename didn't have to conform to standard naming conventions, like you've probably seen with other operating systems such as Windows? Normally, you would expect a file called `banana.jpeg` to be a JPEG picture file.

In Linux, **filenames aren't required to represent the contents of the file**. You can create a file called `funny.gif` that isn't actually a GIF.

To find out what kind of file a file is, you can use the file command. It will show you a description of the file's contents.

```bash
file banana.jpg
banana.jpg: JPEG image data
```
## Why File Extensions Are Not Enough

Linux tools usually do not require a file extension to decide what a file is. A shell script can be named `backup`, a text file can be named `README`, and an image can have the wrong extension. The `file` command inspects the file's contents and metadata to make a better guess.

```bash
file README
README: ASCII text
file /bin/ls
/bin/ls: ELF 64-bit LSB executable
```

## Checking Multiple Files

```bash
file notes.txt image.png archive.tar.gz
notes.txt: ASCII text
image.png: PNG image data
archive.tar.gz: gzip compressed data
```

Wildcards also work:

```bash
file *
```

## Showing MIME Types

The `-i` option prints MIME-style information, which is useful when working with web files or scripts.

```bash
file -i index.html
index.html: text/html; charset=us-ascii
```

## Common file Options

| Option | Description |
| --- | --- |
| `-i` | Show MIME type information. |
| `-b` | Brief mode, omit the filename in output. |
| `-L` | Follow symbolic links. |
| `-z` | Try to inspect compressed files. |

## Common Questions
1. **Does file rely only on extensions?** No. It primarily inspects file contents and known signatures.
2. **Can file be wrong? Yes.** It makes an educated guess, especially for unusual or damaged files.
3. **Why does file say "data"?** The file does not match a more specific known type, or it may be binary data without a recognizable signature.
