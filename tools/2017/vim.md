### 安装
[spf13-vim](https://github.com/spf13/spf13-vim)

### 使用

#### 一.多文件编辑：缓冲区管理

**1.打开**

```bash
# 打开文件到缓存区
vim filename1 filename2
```

在vim内打开新的缓冲区：`:e filename` or `:new`

**2.切换缓冲区**

- 显示缓冲区列表: `ls`
- 切换到下一个缓冲区: `:bn` 或者 `Ctrl` `^`
- 切换到上一个缓冲区: `:bp`
- 切换到第一个缓冲区: `:bf`
- 切换到最后一个缓冲区: `:bl`
- 切换到索引或者表达式目标缓冲区: `:b {index, expression}`

**3.关闭缓冲区**

- 关闭: `bd`
- 强制关闭: `bd!`

#### 二. 分屏管理

**1.分屏启动**

```bash
# O 为大写字母,大小写表示分屏方向;
# n 为数字,表示分为几个屏
# 垂直分屏
vim -On file1,file2...
# 水平分屏
vim -on file1,file2...
```

**2.关闭分屏**

关闭当前: `Ctrl+W` `c` 或者 `:clo`

关闭当前,如果只剩下一个窗口则关闭vim: `Ctrl+W` `q`

**3.启动后分屏**

上下分割当前文件: `Ctrl+W` `s`

上下分割并打开新文件: `:sp filename`

左右分割当前文件: `Ctrl+W` `v`

左右分割并打开新文件: `:vsp filename`

水平分屏并打开buffer: `sb {number}`

垂直分屏并打开buffer: `verticle sb {number}`

**4.切换分屏**

左下上右切换分屏: `Ctrl+W` `h/j/k/l`

切换下一个分屏: `Ctrl+W` `w`

**5.移动分屏**

左下上右移动分屏: `Ctrl+W` `H/J/K/L`

**6.调整分屏尺寸**

所有分屏大小一样: `Ctrl+W` `=`

增加高度: `Ctrl+W` `+`

减小高度: `Ctrl+W` `-`

#### 三.键位映射Map

**1.映射种类**

- 用于普通模式: 输入命令时
- 用于可视模式: 可视区域高亮并输入命令
- 用于操作等待模式: 操作符等待中，如d,y,c
- 用于插入模式: 也用于替换模式
- 用于命令行模式: 输入: 或者 /

| Command<br/>命令|Normal<br/>常规模式|Visual<br/>可视模式|Operator Pending<br/>运算符模式|Insert Only<br/>插入模式|Command Line<br/>命令行模式|
|:---------:|:---------:|:--------:|:---------:|:-----------:|:---------:|
|:map|y|y|y|||
|:nmap|y|||||
|:vmap|||y|||
|:omap||||y||
|:map!||||y|y|
|:imap||||y||
|:cmap|||||y|


**2.键表对应**

|vim标识符|键盘对应|
|:-----:|:--------:|
|<k0>-<k9>|小键盘0-9|
|<S-...>|Shift + ...|
|<C-...>|Ctrl + ...|
|<M-...>或者<A-...>|Alt + ... 或者 Meta + ...|
|<Esc>|Escape|
|<Up>|光标上移键|
|<Space>|空格键|
|<Tab>|Tab键|
|<CR>|Enter键|

#### 四.常规快捷键

**1. 移动类**

> 相对屏幕移动

通过`c-f`向下翻页，`c-b`向上翻页；`c-e`逐行下滚，`c-y`逐行上滚。这在几乎所有Unix软件中都是好使的，比如`man`和`less`。 `H`可以移动到屏幕的首行，`L`到屏幕尾行，`M`到屏幕中间。

`zt`可以置顶当前行，通常用来查看完整的下文，比如函数、类的定义。 `zz`将当前行移到屏幕中部，`zb`移到底部。

**2. 选择类**

> 快速选择单词

- 光标移动目标单词，然后`Normal`模式下`viw`

> 快速全选

- 全选：`ggVG`
- 复制：`ggyG`



### 插件

#### NERDtree

`<leader>` + `e`

```bash
?: 快速帮助文档
o: 打开一个目录或者打开文件，创建的是buffer，也可以用来打开书签
go: 打开一个文件，但是光标仍然留在NERDTree，创建的是buffer
t: 打开一个文件，创建的是Tab，对书签同样生效
T: 打开一个文件，但是光标仍然留在NERDTree，创建的是Tab，对书签同样生效
i: 水平分割创建文件的窗口，创建的是buffer
gi: 水平分割创建文件的窗口，但是光标仍然留在NERDTree
s: 垂直分割创建文件的窗口，创建的是buffer
gs: 和gi，go类似
x: 收起当前打开的目录
X: 收起所有打开的目录
e: 以文件管理的方式打开选中的目录
D: 删除书签
P: 大写，跳转到当前根路径
p: 小写，跳转到光标所在的上一级路径
K: 跳转到第一个子路径
J: 跳转到最后一个子路径
<C-j>和<C-k>: 在同级目录和文件间移动，忽略子目录和子文件
C: 将根路径设置为光标所在的目录
u: 设置上级目录为根路径
U: 设置上级目录为跟路径，但是维持原来目录打开的状态
r: 刷新光标所在的目录
R: 刷新当前根路径
I: 显示或者不显示隐藏文件
f: 打开和关闭文件过滤器
q: 关闭NERDTree
A: 全屏显示NERDTree，或者关闭全屏
ma: 新建目录或者文件
```

#### ctrlP

`ctrl` + `f`: 模糊搜索最近打开的文件(MRU)

`ctrl` + `p`: 模糊搜索当前目录及其子目录下的所有文件

```zsh
ctrl + j/k 进行上下选择
ctrl + x 在当前窗口水平分屏打开文件
ctrl + v 同上, 垂直分屏
ctrl + t 在tab中打开
```

#### [vim-surround 说明](https://gist.github.com/wilon/ac1fc66f4a79e7b0c161c80877c75c94)

- 普通模式
--------
|    | 命令                   | 说明 + 示例                                                                          |
|---:|----------------------|:---------------------------------------------------------------------------------|
|    | ds                   | 删除括号                                                                             |
|  例 | `ds` `"`             | `"Hello world!"` =><br> `Hello world!`                                           |
|    | cs                   | 替换括号                                                                             |
|  例 | `cs` `"(`            | `"Hello world!"` =><br> `(Hello world!)`                                         |
|    | cS                   | 替换括号，括号内文本做新一行                                                                   |
|  例 | `cS` `"{`            | `"Hello world!"` =><br> `{` <br> &nbsp;&nbsp;&nbsp;&nbsp;`Hello world!` <br> `}` |
|    | ys                   | 添加括号(配合vim光标移动)                                                                  |
|  例 | `ys` `w` `[`         | `Hello world!` =><br> `[Hello] world!`                                           |
|  例 | `ys` `w` `<em` Enter | `Hello world!` =><br> `<em>Hello<em> world!`                                     |
|    | yS                   | 添加括号，括号内文本做新一行                                                                   |
|  例 | `yS` `w` `[`         | `Hello world!` =><br> `[` <br> &nbsp;&nbsp;&nbsp;&nbsp; `Hello` <br> `] world!`  |
|    | yss                  | 整行括起来                                                                            |
|  例 | `yss` `(`            | `Hello world!` =><br> `( Hello world! )`                                         |
|    | ySS                  | 整行括起来，括号内文本做新一行                                                                  |
|  例 | `ySS` `{`            | `Hello world!` =><br> `{` <br> &nbsp;&nbsp; `Hello world! ` <br> `}`             |
|  例 | `ySS` `<div` Enter   | `Hello world!` =><br> `<div>` <br> &nbsp;&nbsp; `Hello world! ` <br> `<div>`     |
|    | ySs                  | 与ySs功能相同                                                                         |


- 可视模式
--------
|    | 命令             | 说明 + 示例                                                           |
|---:|:---------------|:----------------------------------------------------------------------|
|    | S              | 选中的括起来                                                              |
|  例 | 选中world: `S(`  | `Hello world!` =><br> `Hello (world)!`                                |
|    | gS             | 选中的括起来，括号内文本做新一行                                             |
|  例 | 选中world: `gS{` | `Hello world!` =><br> `Hello {` <br> &nbsp;&nbsp; ` world` <br> `}! ` |


### 参考
- [酷壳](http://coolshell.cn/)
- [vim map自定义快捷键](http://blog.jasonding.top/2015/04/29/Developer%20Kits/%E3%80%90Vim%E3%80%91%E4%BD%BF%E7%94%A8map%E8%87%AA%E5%AE%9A%E4%B9%89%E5%BF%AB%E6%8D%B7%E9%94%AE/)
