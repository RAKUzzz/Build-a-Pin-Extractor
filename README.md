# 📌 pin_extractor

A simple utility that generates a **secret code** from multiple poems using word positions and lengths.  
Useful for puzzles, challenges, text manipulation, and creative encoding.

---

## 🔍 How It Works

For each poem:

1. Split the poem into **lines**.
2. For each line (using `line_index`):
   - Split the line into **words**.
   - If the number of words is greater than `line_index`,  
     take the **length of the word at index `line_index`**.
   - Otherwise, append `"0"`.
3. Combine all digits to form a secret code.
4. Repeat for every poem in the input list.

---

## 🧩 Function Code

```python
def pin_extractor(poems):
    secret_codes = []
    for poem in poems:
        secret_code = ''
        lines = poem.split('\n')
        for line_index, line in enumerate(lines):
            words = line.split()
            if len(words) > line_index:
                secret_code += str(len(words[line_index]))
            else:
                secret_code += '0'
        secret_codes.append(secret_code)
    return secret_codes

```
## 📘 Example Usage

```python
poem = """Stars and the moon
shine in the sky
white and
until the end of the night"""

poem2 = 'The grass is green\nhere and there\nhoping for rain\nbefore it turns yellow'
poem3 = 'There\nonce\nwas\na\ndragon'

print(pin_extractor([poem, poem2, poem3]))

```

## 📤 Example Output

```python
['54150', '43350', '15510']

```

## ✔ Notes
- Works with any number of poems.
- Core logic:Use the word at position = line number. If not available → use 0.


