# sky tree nest xmasð¼
ã¹ã«ã¤ããªã¼ã®ã¨ã¬ãã¼ã¿ã¼ã§ä¸ã«ç»ã£ããã¨ã¯ããããï¼ãã­ãã­ãããã­ãããä¸åããã®ãã­ãã­ãä½é¨ãããã¦ããããªãã®ãä½ã£ã¦ã¿ããã ãã©ãã©ãããªï¼

### Solution
ãã¹ã¯ã¼ãã§ä¿è­·ããã7zipãã¡ã¤ã«ã¨ãã¹ã¯ã¼ããæ¸ããããã­ã¹ããã¡ã¤ã«ãæ¸¡ããã

è©¦ãã«ãæ¸¡ããããã­ã¹ããã¡ã¤ã«ããã¨ã«è§£åããã¨æ¬¡ã®7zipãã¡ã¤ã«ã¨ãã­ã¹ããã¡ã¤ã«ãæ¸¡ããã

ãªã®ã§ããã¹ããã¦ããzipãã¡ã¤ã«ãç¶ãã¨è§£åããããã«ä»¥ä¸ãæ¸ãã

```python
import py7zr

password = ""
with open("pass.txt") as f:
    password = f.read().replace('\n','')
with py7zr.SevenZipFile(f'skytree.7z', mode='r', password=password) as z:
    z.extractall()

for i in range(1000):
    with open(f"pass{i+2}.txt") as f:
        p = f.read().replace('\n','')
        # ãã¹ã¯ã¼ãã¯ããä»¥åã¾ã§ã®ãã¹ã¯ã¼ãã¨ä»ã®ãã¹ã¯ã¼ããé£çµããã ã
        password += p
        print(password)
    with py7zr.SevenZipFile(f'skytree{i+2}.7z', mode='r', password=password) as z:
        z.extractall()
```

å®è¡ããã¨ã`skytree634.7z`ã¾ã§è§£åãããä¸­ã«ä»¥ä¸ã®ãããªç»åããã

![](./files/skytree-xmass.webp)

ããããã¤ããªã¨ãã£ã¿ã§éãã¨ä¸ã®æ¹ã«flagããã

`imctf{xmas_colored_skytree_is_bright}`