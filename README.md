CanYouSee

Category: Forensics
Author: regexp
Flag Format: academy{...}

Challenge Description:

How about some hide and seek?
Download this file here.
Hints
1
How can you view the information about the picture?
2
If something isn't in the expected form, maybe it deserves attention?

Flag:

academy{ME74D47A_HIDD3N_aebe8c0f}

Unzipping the file

I used ⇒ unzip unknown.zip ⇒ to unzip the given file (unknown.zip).

In Terminal:
$ unzip unknown.zip
Archive:  unknown.zip
  inflating: ukn_reality.jpg

$ ls -la
-rw-r--r-- 1 khyati khyati 2263748 Sep 23 05:17 ukn_reality.jpg
-rw-r--r-- 1 khyati khyati 2252242 Sep 26 16:08 unknown.zip

This gave us me one file: ukn_reality.jpg

It looked like a normal looking photo.

Hence, with not much to go by from looking at the photo, I decided to take a look at the file type.

Checking File Type:

I typed ⇒ file ukn_reality.jpg ⇒ in Terminal


In Terminal:

$ file ukn_reality.jpg
ukn_reality.jpg: JPEG image data, JFIF standard 1.01,
resolution (DPI), density 72x72, segment length 16,
baseline, precision 8, 4308x2875, components 3
This confirms that it is a real JPEG. Hence, the file is real, and not fake. Hence, it can be inferred that any hidden data which is there should be inside the file structure and data instead.

Using “strings” to look for clues that could just be hidden in the plain text:

$ strings ukn_reality.jpg | grep -i flag

Nothing showed up when I wrote this. Hence, I inferred that there must be no flag/clue hiding in the plain text here.

Checking the metadata:

In terminal:

$ exiftool ukn_reality.jpg
File Type                       : JPEG
JFIF Version                    : 1.01
XMP Toolkit                     : Image::ExifTool 12.76
Attribution URL                 : YWNhZGVteXtNRTc0RDQ3QV9ISUREM05fYWViZThjMGZ9Cg==
Image Width                     : 4308
Image Height                    : 2875
Encoding Process                : Baseline DCT, Huffman coding
Megapixels                      : 12.4

Here, the “attribution URL” part caught my attention, since it had a “==” at the end of its text string. Normally, an “==” is put at the end of a Base64 text. Hence, I opened Dcode.fr, and decoded the string.

By this, I got the Flag: academy{ME74D47A_HIDD3N_aebe8c0f}
