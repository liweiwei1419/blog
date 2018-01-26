---
layout: post                        ## 文章使用的模板
title:  "Pandas 学习笔记（1）-Hello World"    ## 文章的标题
subtitle: ""
date:   2017-12-01          ## 发布时间
author: "李威威"                 ## 作者
categories: pandas                  ## 文章所属的目录
tag: pandas
background: '/img/posts/06.jpg'
---

# Pandas 学习笔记（1）-Hello World

+ Series 上 `[]` 这个操作符是对索引操作，里面可以填 index 的名称，也可以填序号（这里要注意，写两行代码比较一下就清楚了，注意是否包含后面的那个索引）。
+ DataFrame 直接上 `[]` 这个操作符，就是对列操作。

```python
# 增加列
df_obj2['G'] = df_obj2['D'] + 4

# 删除列
del(df_obj2['G'] )
```

## Series 和 DataFrame 的索引

+ 索引对象是不可变对象

### Series 的索引

+ 直接设置 Series 的索引对象

```python
ser_obj = pd.Series(range(5), index = ['a', 'b', 'c', 'd', 'e'])
# 使用 ser_obj.head() 查看
```

+ 索引的切片使用 `:`。
+ 不连续的索引，要使用二维数据来索引。
例如：
```python
ser_obj[[0, 2, 4]]
ser_obj[['a', 'e']]
```
+ 掌握使用遮罩进行索引的技巧，`[]` 里面是一个布尔数组：
例如：
```python
ser_obj[ser_obj > 2]
```

### DataFrame 的索引

+ 默认添加的索引是 0，1，2，3
```python
df_obj = pd.DataFrame(np.random.randn(5,4), columns = ['a', 'b', 'c', 'd'])
```
上面的 df_obj['a'] 返回的是 Series 类型。
+ loc 是按标签索引，**包含索引末尾位置**
```python
df_obj.loc[0:2,'b']
```
+ 可以根据索引和值排序，注意轴的方向。
```python
df_obj.sort_index(axis=0)
df_obj.sort_index(axis=1)
df4.sort_values(by=1,axis=0)
```
+ 判断数据是否为 NaN
```python
df_data.isnull()
```
+ 丢弃 NaN 的数据
```python
df_data.dropna(axis=0)
```
+ 填充 NaN 的数据
```python
df_data.fillna(-100.)
```
