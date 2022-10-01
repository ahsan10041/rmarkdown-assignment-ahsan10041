R Markdown Homework Assignment
================
Ali Ahsan(Q4RUJI)

First, let’s display some system information:

    ## "Machine type: AMD64

    ## Node name: DESKTOP-OAD42SK

    ## OS name: Windows

    ## OS release: 10

    ## OS version: 10.0.19044

    ## User name: Sharam ker Ahsan

    ## Home directory: C:\Users\Sharam ker Ahsan

    ## Current directory: C:\Users\Sharam ker Ahsan\Desktop\rmarkdown-assignment-ahsan10041

    ## PATH: C:\Users\Sharam ker Ahsan\miniconda3\envs\rmarkdown;C:\Users\Sharam ker Ahsan\miniconda3\envs\rmarkdown\Library\mingw-w64\bin;C:\Users\Sharam ker Ahsan\miniconda3\envs\rmarkdown\Library\usr\bin;C:\Users\Sharam ker Ahsan\miniconda3\envs\rmarkdown\Library\bin;C:\Users\Sharam ker Ahsan\miniconda3\envs\rmarkdown\Scripts;C:\Users\Sharam ker Ahsan\miniconda3\envs\rmarkdown\bin;C:\Users\Sharam ker Ahsan\miniconda3\condabin;C:\Program Files\Common Files\Oracle\Java\javapath;C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0;C:\Windows\System32\OpenSSH;C:\Program Files\MATLAB\R2021b\bin;C:\Program Files\PuTTY;C:\Users\Sharam ker Ahsan\AppData\Local\Microsoft\WindowsApps;.;C:\Users\Sharam ker Ahsan\AppData\Local\Programs\Microsoft VS Code\bin

Let’s create a word cloud of the complete Sherlock Holmes Canon that is
available in plain text from
[here](https://sherlock-holm.es/stories/plain-text/cano.txt).

The word cloud can be generated with the
[word_cloud](https://github.com/amueller/word_cloud) package as follows:

``` python
from wordcloud import WordCloud, STOPWORDS
import urllib.request
from PIL import Image
import numpy as np

text = urllib.request.urlopen('https://sherlock-holm.es/stories/plain-text/cano.txt').read().decode('utf-8')

stopwords = set(STOPWORDS)
stopwords.add("said")

mask = np.array(Image.open('detectiveHat.png'))

wordcloud = WordCloud(stopwords=stopwords, collocations=False, mask=mask, margin=0, background_color='white').generate(text)
```

    ## Matplotlib is building the font cache; this may take a moment.

``` python
import matplotlib.pyplot as plt
plt.imshow(wordcloud, interpolation='bilinear')
plt.axis("off")
```

    ## (-0.5, 900.5, 485.5, -0.5)

``` python
plt.show()
```

![](wordcloud-1.png)<!-- -->

This document was generated on October 01, 2022 at 14:59:44.
