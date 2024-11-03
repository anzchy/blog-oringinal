---
title: 每个人都应该有自己的英文发音练习计划
date: 2024-10-26 15:08:02
categories:
- 英语
- 编程
- 自学
tags:
- 成长
- 人生系统
---



今年进行英语阅读训练已经大半年了，我在一个叫做 `Enjoy` 的英语阅读软件中进行跟读练习，评估自己发音的准确程度。对于发音不准确的单词大部分都有记录，至今累计记录了 600+个单词（去重后）。

今天突发奇想，对于已经记录的单词，用`数据分析`的手段辅助自己更加有效率的训练。具体来说分为两个步骤：一是针对单词，输出每个单词的美式英语发音；二是将美式英语发音拆分成元音和辅音，并且统计各个元音、辅音出现的词频。

在ChatGPT的帮助下，写了两个 Python 脚本（见附录），英语词典离线文件来源于 Github 上网友已经整理好的 [json 字典](https://github.com/anzchy/macbook_computer_code/blob/main/cam_dict.refined.json)。

经过分析，有 500 个单词的英文发音，有100 个左右英文单词没有查询到。但是没关系，这 500 个单词也足以指导我接下来的训练。之前我隐约感觉英文 L 和 n 的发音需要注意，现在我有了更为量化的分析了。

具体来说，词频比较高的元音和辅音，之后要花更多精力练习。

也因此，我觉得市面上的英文单词书、英文发音练习计划其实并不适用于所有人，每个人应该有自己个性化、更有效率的英文发音练习计划，而大模型的出现让我们 DIY 英文发音练习计划成为可能。

```
元音频率统计:
ɪ: 246
ə: 216
e: 146
i: 101
æ: 72
ɑː: 63
eɪ: 54
iː: 49
ʊ: 47
ɚ: 45
ʌ: 35
aɪ: 30
oʊ: 26
u: 25
uː: 22
ɝː: 19
aʊ: 14
ɔː: 12
ɔːr: 12
er: 8
ɑːr: 6
ɪr: 5
ʊr: 4
ɔɪ: 3
aʊr: 1

辅音频率统计:
l: 214
t: 182
n: 172
s: 141
d: 128
r: 117
k: 109
p: 68
m: 64
f: 58
b: 51
v: 41
ŋ: 37
ʃ: 33
w: 30
ʒ: 28
t̬: 28
z: 25
dʒ: 24
h: 22
j: 18
tʃ: 17
tr: 14
θ: 13
ð: 11
dr: 5
```



附录：

```
# 导入excel，批量输出美式英语发音，并写回csv文件

import json
import pandas as pd

# Function to extract US pronunciation for a given word
def extract_us_pronunciation(word):
    with open('/Users/xxx/desktop/cam_dict.refined.json', 'r') as f:
        for line in f:
            try:
                # Load each line as JSON
                entry = json.loads(line)

                # Check if the word matches
                if entry.get('word') == word:
                    # Get the pronunciations list from the first pos_item
                    pos_items = entry.get('pos_items', [])

                    # Check if pos_items exists and is not empty
                    if pos_items:
                        pronunciations = pos_items[0].get('pronunciations', [])

                        # Iterate through the pronunciations
                        for pronunciation in pronunciations:
                            region = pronunciation.get('region')
                            ipa = pronunciation.get('pronunciation')

                            # Only return US pronunciation
                            if region == 'us':
                                return ipa
            except json.JSONDecodeError:
                # Continue to next line if there is a JSON parsing error
                continue

    # If no pronunciation is found, return None
    return None

# Load the CSV file into a DataFrame
csv_file_path = '/Users/xx/Desktop/hard_pronunciation_word_list.csv'
df = pd.read_csv(csv_file_path)

# Ensure the CSV has a column named 'word'
if 'word' not in df.columns:
    raise ValueError("CSV file must contain a 'word' column.")

# Add a new column to store US pronunciations if it doesn't already exist
if 'us_pronunciation' not in df.columns:
    df['us_pronunciation'] = None

# Iterate over each row in the DataFrame, extract pronunciation and update the DataFrame
for index, row in df.iterrows():
    word = row['word']

    # Skip rows that already have pronunciations
    if pd.notna(row['us_pronunciation']):
        continue

    us_pronunciation = extract_us_pronunciation(word)
    if us_pronunciation:
        print(f"Extracted US pronunciation for '{word}': {us_pronunciation}")  # Debugging output
    else:
        print(f"No US pronunciation found for '{word}'")  # Debugging output

    # Update the DataFrame
    df.at[index, 'us_pronunciation'] = us_pronunciation

# Save the updated DataFrame back to the CSV file
df.to_csv(csv_file_path, index=False)

print("Pronunciations have been successfully extracted and saved to the CSV file.")


```

其中CSV 应该是类似这样的格式：

```
word,us_pronunciation
access,
Adobe,
twelve,
25th,
absent,
achieve,
actually,
added,
addict,
admin,
admit,
adversarial,
again,
agile,
AJAX,
alias,
align,
also,
```

统计元音和辅音词频的Python 脚本：

```
# 统计csv文件中单词发音的元音、辅音出现的频率

import pandas as pd
import re
from collections import Counter

# 元音和辅音列表
vowels = [
    "ə", "ɚ", "ɝː", "ʌ", "ɑː", "ɑːr", "e", "ɛ", "æ", "er", "ɪ", "iː", "i", "ɪr",
    "ɔː", "ɔːr", "ʊ", "u", "uː", "ʊr", "aɪ", "aɪr", "eɪ", "ɔɪ", "aʊ", "aʊr", "oʊ"
]
consonants = [
    "p", "b", "t", "t̬", "d", "k", "g", "f", "v", "s", "z", "θ", "ð", "ʃ", "ʒ",
    "tʃ", "dʒ", "tr", "dr", "ts", "dz", "m", "n", "ŋ", "l", "r", "w", "j", "h"
]

# 加载 CSV 文件
csv_file_path = '/Users/xx/Desktop/hard_pronunciation_word_list.csv'
df = pd.read_csv(csv_file_path)

# 确保有 'us_pronunciation' 列
if 'us_pronunciation' not in df.columns:
    raise ValueError("CSV file must contain a 'us_pronunciation' column.")

# 初始化计数器
vowel_counter = Counter()
consonant_counter = Counter()

# 遍历每个发音并统计元音和辅音的频率
for pronunciation in df['us_pronunciation']:
    if pd.isna(pronunciation):  # 跳过没有发音的行
        continue

    # 统计元音频率
    for vowel in vowels:
        occurrences = len(re.findall(re.escape(vowel), pronunciation))
        if occurrences > 0:
            vowel_counter[vowel] += occurrences

    # 统计辅音频率
    for consonant in consonants:
        occurrences = len(re.findall(re.escape(consonant), pronunciation))
        if occurrences > 0:
            consonant_counter[consonant] += occurrences

# 打印统计结果
print("元音频率统计:")
for vowel, count in vowel_counter.most_common():
    print(f"{vowel}: {count}")

print("\n辅音频率统计:")
for consonant, count in consonant_counter.most_common():
    print(f"{consonant}: {count}")

```

