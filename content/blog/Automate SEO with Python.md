---
title: Automate SEO with Python
description: Compress images with few lines of Python to improve the SEO. Reduce images size 10 times. Automate multilingual processes with Aligner.
sidebar: false
ogImage: "https://www.aligner.io/images/Automate-with-Python.png" 
date: 2020-06-12
sidebarlogo: 
image: ../images/Automate-with-Python.png
---
#### How to optimize web page image size with python?

Large images are taking time to load. Usually people have a lot of images, illustrations. In order to improve the SEO and make page load fast we need to reduce the size of the image.

In this tutorial we will show how to do that with writing a couple lines of code in Python.

Our goal is to find all PNG files and convert them to JPEG. We will reduce approximately file size up to 10 times.

### Reduce image size 10 times, here's how:

[Open Jupyter notebook](https://jupyter.org/). We will use *glob* to find patterns, *PIL* (Python Imaging Libraries) to convert, and *os* to delete files we don’t need.

``` python 
from PIL import Image
import glob
import os
````

This is a code piece that we will use.

``` python 
for file in glob.glob("website/**/*.png", recursive=True):
    im = Image.open(file)
    rgb_im = im.convert('RGB')
    rgb_im.save(file.replace("png", "jpeg"), quality=95)
    print(file.title())
    os.remove(file)
```

Let’s break it down.


    for file in glob.glob(“website/**/*.png", recursive=True):

For loop is looking for patterns in all directories and subdirectories, where we want to find all .png files.

Next step, open the files and assign a variable.

    im = Image.open(file)

Then, convert.

    rgb_im = im.convert('RGB')  

Save the document with the right extension name and add a level of compression.

    rgb_im.save(file.replace("png", "jpeg"), quality=95)

Print image title, to see what files have been processed.
    print(file.title()) 


Delete the old file.

    os.remove(file)

Now, since we already had content connected to these images, it will ruin all of our blogs and pages. We need to fix it by updating the names in the files.

Here is the code that we will run. Since all of our files are in Markdown, we need to find patterns from all directories and subdirectories.

```python
for file in glob.glob(“website/content/blog/*.md",recursive=True):
    with open(file, 'r') as file_1:
        filedata = file_1.read()
    filedata = filedata.replace('png', 'jpeg')
    with open(file, 'w') as file_2:
        file_2.write(filedata)
    print(file.title())
```

Here we are looking for all patterns that will look after markdown.

    for file in glob.glob("website/content/blog/*.md",recursive=True):

Open the file

    with open(file, 'r') as file_1:
        filedata = file_1.read()

Replace png to jpeg

    filedata = filedata.replace('png', 'jpeg')

Write changes to the file

    with open(file, 'w') as file_2:
            file_2.write(filedata)  

##### Quality remains and the size of images is 10 times less.

3 crucial things for SEO (Check more parameters here)

- image size (to load pages faster)
- alt tag (so that machine could understand it)
- name (to come up in google images search)
___


### Automation is the key to success. The same logic we use in Aligner.

In Aligner editor you can update ALL LANGUAGES at once.

Here we have a document in 4 languages. **English**, **Belarusian**, **Arabic** and **Armenian**.


![aligner-parallel-view-editor](../alinger-python-editor.png)

### Styles and numbering are applied to all languages
![alinger-editor-numbering](../aligner-numbering-python.png)

### Invite collaborators or use selective machine translation to update other languages.

![alinger-selective-machine-translation](../selective-aligner-python.png)

[Read how companies use Aligner Daily](/case/)

[Go and check out Aligner app.](https://app.aligner.io)



