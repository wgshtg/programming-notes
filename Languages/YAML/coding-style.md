# YAML 編寫風格

- 縮排使用**兩個空白**，不能使用跳格字元
- 清單使用 `[, ]`
- 偏好使用**單引號**
- 包含很多複雜脫序字元應該使用**雙引號**
- 字串不一定要用雙引號標示
- 多列文字區塊要使用**雙引號**
- 參考標記 `*`，錨點標記 `&`，雜湊合併 `<<`
- 在單一字詞可以省略引號

```yaml
name: 123
# 下面兩個 book 效果相同
book:
  - title: title
  - author: author
book: [apple, banana]
itmes:
  # 第一個和第二個效果相同
  - {name: Joe, descrip: JJJ}
  - name: Joe
    descrip: JJJ
  - name: May
    descrip: MMM

# There once was a tall man from Ealing\nWho got on a bus to Darjeeling\n    It said on the door
content: >
  There once was a tall man from Ealing
  Who got on a bus to Darjeeling
      It said on the door

# Wrapped text\nwill be folded\n\nBlank lines denote
context: |
  Wrapped text
  will be folded

  Blank lines denote

school:
  # {
  #   "class": {
  #     "prop1": 1
  #   }
  # },
  # {
  #   "class": {
  #     "prop1": 1
  #   }
  # },
  # {
  #   "class": {
  #     "prop1": 100
  #   }
  # },
  # {
  #   "class": {
  #     "prop1": 1,
  #     "prop3": 3
  #   }
  # }
  - class:  &id001
      prop1: 1
  - class: *id001
  - class:
      <<: *id001
      prop1: 100
  - class:
      <<: *id001
      prop3: 3
```
