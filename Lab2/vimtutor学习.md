# vimtutor学习
## 配置asciinema

- 安装asciinema  
```
sudo apt-add-repository ppa:zanchey/asciinema
sudo apt-get update
sudo apt-get install asciinema
```
- 关联asciiname  
```
assiinema auth
```

## 学习vimtutor

- [Lesson1](https://asciinema.org/a/0P1kDODIR11bbccvAZBymVVBW)  
- [Lesson2](https://asciinema.org/a/ZgvlmXOGmL3P75oKwY5NQlvdC)  
- [Lesson3](https://asciinema.org/a/EwACPYL5dzDejsFY8rGQuzRai)
- [Lesson4](https://asciinema.org/a/BRlYb4fpVt2CsIRIjtvHh9Rvr)
- [Lesson5](https://asciinema.org/a/iAPsulp8xq5VWWbCY8AuQsuAv)
- [Lesson6](https://asciinema.org/a/ljw2nbA63U5QJ0fJZYQMqUD8e)
- [Lesson7](https://asciinema.org/a/PXsuhGr2OT38WCRoKzXgJ5suV)

## 自查清单

- 你了解vim有哪几种工作模式？
  - 正常模式(normal-mode) 
  - 命令模式(command-mode) 
  - 插入模式(insert-mode)
  - 可视模式(visual-mode)

- Normal模式下，从当前行开始，一次向下移动光标10行的操作方法？如何快速移动到文件开始行和结束行？如何快速跳转到文件中的第N行？
  - 向下移动光标10行：10j
  - 移动到开始行：gg
  - 移动到结束行：G
  - 移动到文件中的第N行：NG
  
- Normal模式下，如何删除单个字符、单个单词、从当前光标位置一直删除到行尾、单行、当前行开始向下数N行？
  - 删除单个字符：x
  - 删除单个单词：dw
  - 从光标位置删除到行尾：d$
  - 删除单行：dd
  - 删除当前行开始向下的N行：Ndd

- 如何在vim中快速插入N个空行？如何在vim中快速输入80个-？
  - 插入N个空行：No
  - 输入80个-：80i-ESC
  
- 如何撤销最近一次编辑操作？如何重做最近一次被撤销的操作？
  - 撤销最近一次编辑操作：u
  - 重做最近一次被撤销的操作：Ctrl+R
  
- vim中如何实现剪切粘贴单个字符？单个单词？单行？如何实现相似的复制粘贴操作呢？
  - 剪切粘贴
    - 字符：d p
    - 单词：dw p
    - 单行：dd p
  - 复制粘贴
    - 字符：y p
    - 单词：yw p
    - 单行：yy p
 
- 为了编辑一段文本你能想到哪几种操作方式（按键序列）？
  - i 切换到插入模式，在当前光标位置之前插入。
  - I 光标移动到当前行的开头进入插入模式。
  - a 在光标之后进入插入模式
  - A 行尾进入插入模式
  - R 进入插入模式替换当然文档的字符
  - o 当前行的下方打开新行
  - O 当前行的上方打开新行
 
- 查看当前正在编辑的文件名的方法？查看当前光标所在行的行号的方法？
  - Ctrl+G
 
- 在文件中进行关键词搜索你会哪些方法？如何设置忽略大小写的情况下进行匹配搜索？如何将匹配的搜索结果进行高亮显示？如何对匹配到的关键词进行批量替换？
  - 关键词搜索 
    - / 后接搜索内容
    - ？ 后接搜索内容
  - 忽略大小写：:ser 
  - 设置高亮：:set hls is
  - 批量替换：:s/old/new/g

- 在文件中最近编辑过的位置来回快速跳转的方法？
  - Ctrl+i  Ctrl+o

- 如何把光标定位到各种括号的匹配项？例如：找到(, [, or {对应匹配的),], or }
  - %

- 在不退出vim的情况下执行一个外部程序的方法？
  - :!+命令

- 如何使用vim的内置帮助系统来查询一个内置默认快捷键的使用方法？如何在两个不同的分屏窗口中移动光标？
  - :help
  - Ctrl+w
