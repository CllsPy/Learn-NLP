

# **Python `re` Module Cheat Sheet**

### **Importing `re`**
```python
import re
```

### **Basic Functions in `re`**
- **`re.match(pattern, string)`**: Tries to match the pattern at the beginning of the string.
- **`re.search(pattern, string)`**: Searches the entire string for the first match.
- **`re.findall(pattern, string)`**: Returns a list of all non-overlapping matches in the string.
- **`re.finditer(pattern, string)`**: Returns an iterator yielding match objects for all non-overlapping matches.
- **`re.sub(pattern, repl, string)`**: Replaces all occurrences of the pattern in the string with the replacement string (`repl`).
- **`re.split(pattern, string)`**: Splits the string by the occurrences of the pattern.

---

### **Regular Expression Syntax**

#### **Special Characters**
- **`.`**: Matches any single character except newline.
  ```python
  re.match("a.b", "acb")  # Match, as '.' matches 'c'
  ```
- **`^`**: Matches the start of the string.
  ```python
  re.match("^abc", "abc")  # Match, as string starts with 'abc'
  ```
- **`$`**: Matches the end of the string.
  ```python
  re.match("abc$", "abc")  # Match, as string ends with 'abc'
  ```
- **`[]`**: A character class. Matches any one of the characters inside the brackets.
  ```python
  re.match("[aeiou]", "a")  # Match, as 'a' is a vowel
  re.match("[0-9]", "5")  # Match, as '5' is a digit
  ```
- **`|`**: OR operator. Matches either the pattern on the left or the one on the right.
  ```python
  re.match("cat|dog", "dog")  # Match, as the string is 'dog'
  ```

#### **Quantifiers**
- **`*`**: Matches 0 or more repetitions of the preceding pattern.
  ```python
  re.match("a*b", "aaab")  # Match, as 'aaa' is followed by 'b'
  ```
- **`+`**: Matches 1 or more repetitions of the preceding pattern.
  ```python
  re.match("a+b", "aaab")  # Match, as 'aaa' is followed by 'b'
  ```
- **`?`**: Matches 0 or 1 repetition of the preceding pattern.
  ```python
  re.match("a?b", "b")  # Match, as 'b' can match 'a?b'
  ```
- **`{n}`**: Matches exactly n occurrences of the preceding pattern.
  ```python
  re.match("a{3}", "aaa")  # Match, as the string is exactly 'aaa'
  ```
- **`{n,}`**: Matches n or more occurrences.
  ```python
  re.match("a{2,}", "aaa")  # Match, as there are more than 2 'a's
  ```
- **`{n,m}`**: Matches between n and m occurrences.
  ```python
  re.match("a{2,3}", "aaa")  # Match, as there are between 2 and 3 'a's
  ```

#### **Character Classes**
- **`\d`**: Matches any digit (0-9).
  ```python
  re.match("\d", "5")  # Match, as '5' is a digit
  ```
- **`\D`**: Matches any non-digit.
  ```python
  re.match("\D", "a")  # Match, as 'a' is not a digit
  ```
- **`\w`**: Matches any alphanumeric character (letters, digits, and underscore).
  ```python
  re.match("\w", "a")  # Match, as 'a' is alphanumeric
  ```
- **`\W`**: Matches any non-alphanumeric character.
  ```python
  re.match("\W", "#")  # Match, as '#' is not alphanumeric
  ```
- **`\s`**: Matches any whitespace character (spaces, tabs, newlines).
  ```python
  re.match("\s", " ")  # Match, as space is a whitespace character
  ```
- **`\S`**: Matches any non-whitespace character.
  ```python
  re.match("\S", "a")  # Match, as 'a' is not a whitespace character
  ```

#### **Grouping and Capturing**
- **`()`**: Creates a capturing group.
  ```python
  re.match("(abc)", "abc")  # Match, as 'abc' is captured
  ```
- **`(?:...)`**: Creates a non-capturing group.
  ```python
  re.match("(?:abc)", "abc")  # Match, but does not capture
  ```

#### **Escape Sequences**
- **`\.`**: Matches a literal dot `.` (because dot is a special character in regex).
  ```python
  re.match(r"abc\.", "abc.")  # Match, as the literal dot is part of the string
  ```
- **`\(`, `\)`**: Matches literal parentheses.
  ```python
  re.match(r"\(abc\)", "(abc)")  # Match, as literal parentheses are in the string
  ```

---

### **Examples**

#### **Example 1: Matching an Email Address**
```python
import re

email_pattern = r"[\w\.-]+@[\w\.-]+\.\w+"
text = "Please contact us at support@example.com."

matches = re.findall(email_pattern, text)
print(matches)  # Output: ['support@example.com']
```

#### **Example 2: Removing Extra Spaces**
```python
import re

text = "This   is   an    example  text."
clean_text = re.sub(r'\s+', ' ', text)
print(clean_text)  # Output: 'This is an example text.'
```

#### **Example 3: Replacing Punctuation**
```python
import re

text = "Hello!!! How are you???"
cleaned_text = re.sub(r'[!?.]+', '!', text)
print(cleaned_text)  # Output: 'Hello! How are you!'
```

#### **Example 4: Validating a Phone Number**
```python
import re

phone_pattern = r"^\(\d{2}\) \d{4,5}-\d{4}$"
phone = "(11) 98765-4321"

match = re.match(phone_pattern, phone)
if match:
    print("Valid phone number")
else:
    print("Invalid phone number")
```

---

### **Useful `re` Functions and Methods**
- **`re.match(pattern, string)`**: Checks if the pattern matches at the beginning of the string.
- **`re.search(pattern, string)`**: Searches for the pattern throughout the string.
- **`re.findall(pattern, string)`**: Finds all matches and returns them as a list.
- **`re.sub(pattern, repl, string)`**: Substitutes all occurrences of the pattern in the string with `repl`.
- **`re.split(pattern, string)`**: Splits the string by the pattern.
- **`re.finditer(pattern, string)`**: Returns an iterator yielding match objects for all matches.

---

### **Quick Tips**
- Use raw strings (`r"..."`) to avoid having to escape backslashes (e.g., `r"\d"`).
- Regular expressions can be difficult to read, so consider adding comments and using verbose mode (`re.VERBOSE`) for complex patterns.
  
---

This cheat sheet covers the most common operations and patterns in Python's `re` module. As you work with regular expressions, you'll find yourself getting more comfortable with different patterns and their applications!