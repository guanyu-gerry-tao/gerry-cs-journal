# Regex 正则表达式

正则表达式（Regular Expression，简称 regex）是一种用于匹配文本模式的强大工具，主要用于字符串搜索、替换和解析。以下是正则表达式的基本使用方法：

---

### 1. **基本匹配**

- `.` ：匹配任意单个字符（除换行符外）。
- `[]`：匹配方括号内的任意一个字符，如 `[aeiou]` 匹配任意一个元音字母。
- `[^]`：匹配不在括号内的字符，如 `[^0-9]` 匹配非数字字符。
- `\`：用于转义特殊字符，如 `\.` 匹配 `.` 本身。

---

### 2. **重复匹配**

- `*` ：匹配前面的字符 0 次或多次，如 `ab*` 可匹配 `"a"`、`"ab"`、`"abb"` 等。
- `+` ：匹配前面的字符 1 次或多次，如 `ab+` 只能匹配 `"ab"`、`"abb"`，但不能匹配 `"a"`。
- `?` ：匹配前面的字符 0 次或 1 次，如 `colou?r` 可匹配 `"color"` 或 `"colour"`。
- `{n}`：匹配前面的字符恰好 n 次，如 `a{3}` 只能匹配 `"aaa"`。
- `{n,}`：匹配前面的字符至少 n 次，如 `a{2,}` 匹配 `"aa"`、`"aaa"`、`"aaaa"` 等。
- `{n,m}`：匹配前面的字符至少 n 次，至多 m 次，如 `a{2,4}` 只能匹配 `"aa"`、`"aaa"` 或 `"aaaa"`。

---

### 3. **分组和引用**

- `()`：分组，如 `(abc)+` 匹配 `"abc"`、`"abcabc"`。
- `\d`：匹配数字（等价于 `[0-9]`）。
- `\D`：匹配非数字字符（等价于 `[^0-9]`）。
- `\w`：匹配字母、数字或下划线（等价于 `[a-zA-Z0-9_]`）。
- `\W`：匹配非字母、非数字、非下划线字符（等价于 `[^a-zA-Z0-9_]`）。
- `\s`：匹配空白字符（空格、换行、制表符等）。
- `\S`：匹配非空白字符。
- `\b`：匹配单词边界，如 `\bword\b` 仅匹配完整的 `"word"`。
- `\B`：匹配非单词边界。

---

### 4. **逻辑运算**

- `|`：或运算，如 `apple|banana` 匹配 `"apple"` 或 `"banana"`。
- `(?:...)`：非捕获组，不保存匹配结果，如 `(?:ab)+` 仅匹配 `ab`，但不存储捕获组。

---

### 5. **锚点**

- `^`：匹配字符串的开头，如 `^hello` 只能匹配 `"hello world"` 中的 `"hello"`。
- `$`：匹配字符串的结尾，如 `world$` 只能匹配 `"hello world"` 中的 `"world"`。
- `(?=...)`：正向先行断言，如 `\d(?=px)` 仅匹配 `12px` 中的 `12`。
- `(?!...)`：负向先行断言，如 `\d(?!px)` 仅匹配不跟随 `px` 的数字。

---

### 6. **常见应用**

### （1）搜索和匹配

```python
import re
pattern = r"\d+"  # 匹配一个或多个数字
text = "There are 42 apples and 88 oranges."
matches = re.findall(pattern, text)  # 返回 ['42', '88']
```

### （2）替换字符串

```python
import re
pattern = r"\d+"
replacement = "#"
text = "Phone: 123-456-7890"
new_text = re.sub(pattern, replacement, text)  # 替换数字为 "#"
```

### （3）拆分字符串

```python
import re
pattern = r",\s*"  # 逗号后可带空格
text = "apple, banana, cherry, date"
split_list = re.split(pattern, text)  # 返回 ['apple', 'banana', 'cherry', 'date']
```

### （4）检查是否匹配

```python
import re
pattern = r"^\d{4}-\d{2}-\d{2}$"  # 匹配 YYYY-MM-DD 格式
date = "2025-03-09"
if re.match(pattern, date):
    print("Valid date format")
```