### 数据处理方案

```
    // 去除标点符号
    df_textonly['headline'] = df_textonly['headline'].str.replace(r'[.,:;()\'"?+!&]', '',regex=True)
    // 去除多余“-”符号
    df_textonly['headline'] = df_textonly['headline'].str.replace(r'-+', ' ', regex=True)
    // 去除多余斜杠
    df_textonly['headline'] = df_textonly['headline'].str.replace(r'/', ' ', regex=True)
```
符号处理
1. unicode转成字母ASCII字符
2. \* 待特殊处理
3. 敏感词恢复
```
# 定义一个敏感词的字典，键为正则表达式，值为要替换成的完整单词
sensitive_words = {
    r'f\**k': 'fuck',
    r's\**t': 'shit',
    r'p\**y': 'pussy',
}

# 遍历字典，替换DataFrame中的敏感词
for pattern, replacement in sensitive_words.items():
    df_textonly['headline'] = df_textonly['headline'].str.replace(pattern, replacement, regex=True)

```



### 词向量方案

### 模型方案

### 评估方案

### 问题