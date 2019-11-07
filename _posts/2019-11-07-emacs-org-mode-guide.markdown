---
layout: post
title:  "emacs org-mode guide!"
date:   2019-11-07 10:12:19 +0800
categories: orgmode
---
* org guide
** Document Structure
*** Motion
    C-c C-n 下一个标题。
    C-c C-p 上一个标题。
    C-c C-f 下一个标题相同的级别。
    C-c C-b 前一个标题相同级别。

    C-c C-u 向后移至较高级别的标题。
*** Sparse trees
 C-c /
 C-c C-c
*** Plain lists
   1. Unordered list items start with '-', '+', or '*' as bullets.
   2. Ordered list items start with '1.' or '1)'.
   3. Description list use ' :: ' to separate the term from the description.

   TAB   折叠项目
   M-RET 在当前级别插入新项目
   M-S-RET 插入一个带有复选框的新项目
   M-S-up/down 上/下移动包含子项目的项目
   M-left/M-right 升降项级 不带子项
   M-S-left/right 升降项级
   C-c C-c 切换该复选框的状态
   C-c - Cycle the entire list level through the different itemize/enumerate bullets ('-', '+', '*', '1.', '1)').
*** Footnotes
C-c C-x f 当光标位于脚注参考上时，跳至定义。在定义时，跳至（第一个）参考。否则，请创建一个新的脚注。当使用前缀参数调用此命令时，将提供包括重编号在内的其他选项菜单。
C-c C-c 在定义和参考之间切换
** Tables
C-c |                   创建
|Name|Phone|Age C-c RET 快速创建
C-c C-c                 重新对齐表格
TAB                     重新对齐表格，移至下一个字段。如有必要，创建一个新行。
S-TAB                   重新对齐，移至上一个字段。
RET                     重新对齐表格并向下移动到下一行。如有必要，创建一个新行。
M-S-up                  杀死当前行或水平线。
M-S-down                在当前行上方插入新行。使用前缀参数，将在当前行下方创建该行。
C-c -                   在当前行下方插入一条水平线。使用前缀参数，将在当前行上方创建该行。
C-c RET                 在当前行下方插入一条水平线，然后将光标移到该行下方的行中。
C-c ^                   对区域中的表格行进行排序。点的位置表示要用于排序的列，行的范围是最近的水平分隔线或整个表格之间的范围。
** Hyperlinks 超链接:上下文中的注释
*** Link format:	  	How links in Org are formatted
    [[link][description]] or [[link]]
*** Internal links:	  	Links to other places in the current file
    [[My Target]] [[My Target][Find my target]]
*** External links:	  	URL-like links to the world
支持指向文件，网站，Usenet和电子邮件，BBDB数据库条目的链接，以及指向IRC对话及其日志的链接。
外部链接是类似URL的定位器。它们以简短的识别字符串开头，后跟冒号。冒号后面不能有空格
http://www.astro.uva.nl/~dominik          on the web
file:/home/dominik/images/jupiter.jpg     file, absolute path
/home/dominik/images/jupiter.jpg          same as above
file:papers/last.pdf                      file, relative path
file:projects.org                         another Org file
docview:papers/last.pdf::NNN              open file in doc-view mode at page NNN
id:B7423F4D-2E8A-471B-8810-C40F074717E9   Link to heading by ID
news:comp.emacs                           Usenet link
mailto:adent@galaxy.net                   Mail link
vm:folder                                 VM folder link
vm:folder#id                              VM message link
wl:folder#id                              WANDERLUST message link
mhe:folder#id                             MH-E message link
rmail:folder#id                           RMAIL message link
gnus:group#id                             Gnus article link
bbdb:R.*Stallman                          BBDB link (with regexp)
irc:/irc.com/#emacs/bob                   IRC link
info:org:External%20links                 Info node link (with encoded space)
*** Handling links:	  	Creating, inserting and following
    C-c l                  Store a link to the current location
    C-c C-l                Insert a link
    C-c C-l (with cursor on existing link) 编辑不可见链接内容
    C-c C-o                Open link at point.
    C-c &                  返回
*** Targeted links:	  	Point at a location in a file
    [[file:~/code/main.c::255]]                 Find line 255
    [[file:~/xx.org::My Target]]                Find ‘<<My Target>>’
    [[file:~/xx.org::#my-custom-id]]            Find entry with custom id
** TODO Items 每个树枝都可以是TODO项目
不需要TODO列表位于单独的文档中。相反，TODO项目是注释文件的一部分，因为TODO项目通常在记录笔记时出现！
只需将树中的任何条目标记为TODO项。这样，信息就不会重复，而且TODO项目仍保留在它们出现的上下文中。
*** Using TODO states:	  	Setting and switching states
C-c C-t 选择
S-right/left 快速切换
C-c / t 在稀疏树中查看TODO项目,即在整个文件中高亮显示TODO项目，C-c C-c取消高显。
C-c a t
S-M-RET
*** Multi-state workflows:	  	More than just on/off
#+TODO: TODO(t) | DONE(d)
#+TODO: REPORT(r) BUG(b) KNOWNCAUSE(k) | FIXED(f)
#+TODO: | CANCELED(c)
*** Progress logging:	  	Dates and notes for progress
进度记录
更改TODO项目的状态时都可以自动记录时间戳
**** Closing items:	  	When was this entry marked DONE?
（setq org-log-done'time）
（setq org-log-done'note）
**** Tracking TODO state changes:	  	When did the status change?
记录将作为详细列表插入到标题后面
*** Priorities:	  	Some things are more important than others
    *** TODO [#A] Write letter to Sam Fortune
    C-c , A B C 设置当前标题的优先级
    S-up/dwn 增加/减少当前标题的优先级
*** Breaking down tasks:	  	Splitting a task into manageable pieces
    [/]
    [%]
    C-c C-c 状态改变时用

    * Organize Party [33%]
    ** TODO Call people [1/2]
    *** TODO Peter
    *** DONE Sarah
    ** TODO Buy food
    ** DONE Talk to neighbor
*** Checkboxes:	  	Tick-off lists
   [ ]

   * TODO Organize party [1/2]
     - [-] call people [1/2]
       - [ ] Peter
       - [X] Sarah
     - [X] order food

   C-c C-c 切换
   M-S-RET 插入
** Tags 标记标题和匹配的标记集
每个标题都可以包含标签列表；它们出现在标题末尾。
标签是包含字母，数字，'_'和'@'。标记之前必须加上一个冒号
*** Tag inheritance:	  	Tags use the tree structure of the outline
如果标题具有特定标签，则所有子标题也将继承该标签
    * Meeting with the French group      :work:
    ** Summary by Frank                  :boss:notes:
    *** TODO Prepare slides for him      :action:

    #+ FILETAGS：：Peter：Boss：Secret：
*** Setting tags:	  	How to assign tags to a headline
M-TAB   插入标签
C-c C-q 输入当前标题的新标签
C-c C-c 当光标位于标题中时，同上
C-u C-c C-q 对齐所有标签

#+TAGS: @work(w)  @home(h)  @tennisclub(t)  laptop(l)  pc(p)
(setq org-tag-alist '(("@work" . ?w) ("@home" . ?h) ("laptop" . ?l)))
*** Tag groups:	  	Use one tag to search for several tags
搜索组标签时，它将返回该组中所有成员的匹配项。
在议程agenda视图中，按组标签过滤将显示带有至少一个组成员标签的标题。
这使标签搜索和过滤器更加灵活。
#+TAGS: { @read : @read_book  @read_ebook }
C-c C-x q
org-toggle-tags-groups
*** Tag searches:	  	Searching for combinations of tags
设置标签系统后，就可以将其收集到特殊列表中。
C-c \
C-c / m 创建一个稀疏树，其中所有标题都与标签搜索匹配。使用 C-u前缀参数，请忽略不是TODO行的标题。
C-c a m 从所有议程agenda文件中创建标记匹配的全局列表
C-c a M 从所有议程agenda文件创建一个全局标签匹配列表，但仅检查TODO项目并强制检查子项目

这些命令都提示输入匹配字符串，该字符串允许使用基本的布尔逻辑
    +boss+urgent-project1
    Kathy|Sally
** Properties
- 每个属性都在一行中指定，首先带有键（由冒号包围），然后是键值
   * CD collection
   ** Classic
   *** Goldberg Variations
       :PROPERTIES:
       :Title:     Goldberg Variations
       :Composer:  J.S. Bach
       :Publisher: Deutsche Grammophon
       :NDisks:    1
       :END:
- org-global-properties
  #+PROPERTY: NDisks_ALL 1 2 3 4
- 
C-c C-x p 设置一个属性。这提示输入属性名称和值。
C-c C-c d 从当前条目中删除一个属性。

要基于属性选择创建稀疏树和特殊列表，将使用与标记搜索相同的命令
** Dates and Times 使项目对计划有用
为了帮助项目规划，可以用日期和/或时间标记TODO项目
*** Timestamps:	  	Assigning a time to a tree entry
时间戳是采用特殊格式的日期（可能带有时间或时间范围）的规范
- 普通时间戳；事件; 约会
  一个简单的时间戳只是为项目分配日期/时间。这就像在纸质议程agenda中写下约会或事件一样。
  * 在电影中与彼得见面
  <2006-11-01 Wed 19:15> 
- 具有中继器间隔
  在N天（d），周（w），月（m）或年（y）的一定间隔后一次又一次地应用
  * 在学校接萨姆
  <2007-05-16周三12:30 + 1w>
- 日记样式的sexp条目
  对于更复杂的日期规范,使用Emacs日历/日记包中实现的特殊sexp日记条目
  * 每个月的第二个星期四的书呆子会议
  <%%(diary-float t 4 2)>
- 时间/日期范围
  **在阿姆斯特丹开会
   <2004-08-23星期一>-<2004-08-26星期四>
- 无效时间戳
  这些时间戳是不活动的，因为它们 不会触发条目显示在议程agenda中
  * Gillian第五次迟到
  [2006-11-01 Wed]
*** Creating timestamps:	  	Commands which insert timestamps
- C-c .         
  提示输入日期并插入相应的时间戳 
  当光标位于缓冲区中的现有时间戳上时，该命令将用于修改此时间戳
  连续使用两次时，将插入一个时间范围
- C-c ! 插入无效时间戳记
- S-left/right 将光标处的日期更改一天。
- S-up/down 在时间戳中更改光标下方的项目。光标可以位于年，月，日，小时或分钟
*** Deadlines and scheduling:	  	Planning your work
时间戳记之前可以带有特殊关键字以方便进行计划
- DEADLINE  任务（很可能是TODO项目，尽管不一定）应该在该日期完成
  C-c C-d

  *** TODO为该指南撰写有关地球的文章
    负责编辑是[[bbdb：Ford Prefect]] 
    DEADLINE: <2004-02-29 Sun>
- SCHEDULED 你打算开始工作在指定的日期是任务
  C-c C-s

  将出现一个提醒，提示已过去预定日期，直到该条目标记为DONE

  *** TODO在新年前夜给Trillian打电话。
    SCHEDULED: <2004-12-25周六>

  ** TODO支付租金
   DEADLINE: <2005-10-01周六+ 1m>
*** Clocking work time:	  	Tracking how long you spend on a task
- C-c C-x C-i
  启动当前项目的时钟（时钟输入）。这会将CLOCK关键字与时间戳一起插入。
  使用C-u前缀参数调用时，请从最近计时的任务列表中选择任务。
- C-c C-x C-o
  停止时钟（超时）。这样会在上次启动时钟的同一位置插入另一个时间戳。
  它还会直接计算结果时间，并将其插入时间范围后的时间范围为'=> HH：MM'。
- C-c C-x C-e
  更新当前时钟任务的工作量估计。
- C-c C-x C-q
  取消当前时钟。如果时钟是错误启动的，或者您结束了其他工作，则此功能很有用。
- C-c C-x C-j
  跳转到包含当前运行时钟的条目。
  使用 C-u前缀arg，从最近计时的任务列表中选择目标任务。
- C-c C-x C-r
  将包含时钟报告的动态块作为组织模式表插入当前文件中。
  当光标位于现有时钟表上时，只需对其进行更新即可。
  #+BEGIN: clocktable :maxlevel 2 :emphasize nil :scope file
  #+END: clocktable
- C-c C-c
  更新动态块。光标需要#+BEGIN在动态块的 行中。
** Capture - Refile - Archive 项目的来龙去脉
系统的重要组成部分是能够快速捕获新的想法和任务，并将参考资料与之关联的能力
需要移动任务和项目。将完成的项目树移动到归档文件可保持系统的紧凑和快速。

*** Capture:	  	Capturing new stuff
让您快速存储笔记，而不会中断您的工作流程
**** Setting up a capture location:	  	Where notes will be stored
- 为笔记设置了默认的目标文件，
  (setq org-default-notes-file (concat org-directory "/notes.org"))
- 捕获新内容
  'org-capture
**** Using capture:	  	Commands to invoke and terminate capture
- C-c c
  开始捕获过程，将您置于狭窄的间接缓冲区中进行编辑。
- C-c C-c
  在将信息输入到捕获缓冲区中后， C-c C-c将使您返回到窗口配置，然后再进行捕获，这样您就可以继续工作而不会分心。
- C-c C-w
  通过将条目移到重新归档位置来完成。
- C-c C-k
  中止捕获过程并返回到先前的状态。
**** Capture templates:	  	Define the outline of different note types
- 模板
(setq org-capture-templates
 '(("t" "Todo" entry (file+headline "~/org/gtd.org" "Tasks")
        "* TODO %?\n  %i\n  %a")
   ("j" "Journal" entry (file+datetree "~/org/journal.org")
        "* %?\nEntered on %U\n  %i\n  %a")))
- M-x org-capture
  * TODO 
  [[文件：链接到发起捕获时的位置 ]]
*** Refile and copy:	  	Moving a tree from one place to another
- C-c M-w
  复制输入项或区域。该命令的行为类似于 org-refile，只是原始注释不会被删除。
- C-c C-w
  重新归档该点的输入或区域。此命令提供了可能的位置来刷新该条目，并让您选择一个完整的位置。
  该项目（或该区域中的所有项目）作为子项目归档在目标标题下方。
  默认情况下，当前缓冲区中的所有1级标题都被视为目标，但是您可以在多个文件中使用更复杂的定义。
- C-u C-c C-w
  使用refile界面跳转到标题。
- C-u C-u C-c C-w
  跳转到org-refile最后将树移到的位置。
*** Archiving:	  	What to do with finished projects
存档对于保持工作文件的紧凑性和快速进行全局搜索（例如快速构建议程视图）非常重要。最常见的归档操作是将项目树移动到另一个文件，即归档文件。
- C-c C-x C-a
  使用归档当前条目org-archive-default-command。
- C-c C-x C-s or short  C-c $
  从光标位置开始将子树存档到所给定的位置org-archive-location。

_archive
org-archive-location
#+ARCHIVE: %s_done::
** Agenda Views 将信息收集到视图中
*** Agenda files:	  	Files being searched for agenda information
org-agenda-files
- C-c [
  将当前文件添加到议程文件列表。该文件将添加到列表的最前面。如果已在列表中，则将其移到最前面。使用前缀参数，文件被添加/移动到末尾。
- C-c ]
  从议程文件列表中删除当前文件。
- C-,
  循环浏览议程文件列表，依次访问另一个文件。
*** Agenda dispatcher:	  	Keyboard access to agenda views
该分派器应绑定到全局键，例如C-c a需要以下另一个字母来执行命令
- a
  类似于日历的议程（请参阅每周/每日议程）。
- t / T
  所有TODO项目的列表（请参阅“ 全局TODO列表”）。
- m / M
  匹配TAGS表达式的标题列表（请参阅匹配标签和属性）。
- s
  由关键字和/或正则表达式的布尔表达式选择的条目列表，这些条目必须或不能出现在条目中。
*** Built-in agenda views:	  	What is available out of the box?
**** Weekly/daily agenda:	  	The calendar page with current tasks
- C-c a a  org-agenda-to-appt
  从组织文件列表中编译当前一周的议程。议程显示了每天的条目。
**** Global TODO list:	  	All unfinished action items
- C-c a t
  显示全局TODO列表。这会将所有议程文件（请参阅议程视图）中的TODO项目收集到一个缓冲区中。
- C-c a T
  与上述类似，但允许选择特定的TODO关键字。
**** Matching tags and properties:	  	Structured information with fine-tuned search
- C-c a m
  产生与给定标签集匹配的所有标题的列表。
  该命令会提示您输入选择条件，这是带有标签的布尔逻辑表达式，例如'+工作+紧急负责人' 要么 '工作|家'（请参见标签）。
- C-c a M
  类似于C-c a m，但仅选择也是TODO项的标题。
- 匹配语法
  & | + -
**** Search view:	  	Find entries by searching for text
C-c a s
这是一种特殊的搜索，它使您可以通过使用布尔逻辑匹配子字符串或特定单词来选择条目。
*** Agenda commands:	  	Remote editing of Org trees
**** Motion
- n
  下一行（与up和相同C-p）。
- p
  前一行（与down和相同C-n）。
**** View/Go to Org file
- mouse-3
  SPC
  在另一个窗口中显示项目的原始位置。使用前缀arg，请确保整个条目（不仅是标题）在轮廓中可见。
- TAB
  在另一个窗口中转到项目的原始位置。在Emacs 22下，mouse-1也将为此工作。
- RET
  转到项目的原始位置，然后删除其他窗口。
**** Change display
- o
  删除其他窗口。
- d / w
  切换到日/周视图。
- f and b
  及时前进/后退以显示接下来的 org-agenda-current-span日子。例如，如果显示涵盖一周，请切换到下一个/上一个星期。
- .
  今天去。
- j
  提示日期，然后去那里。
- v l  or short  l
  切换日志模式。
  在日志模式下，日志记录打开时（变量org-log-done）标记为DONE的条目将显示在议程中，而当天已计时的条目也会显示在议程中。
  用C-u 前缀调用时，显示所有可能的日志条目，包括状态更改。
- r or g
  重新创建议程缓冲区，以反映所做的更改。
- s
  将所有Org缓冲区以及当前ID的位置保存在当前Emacs会话中。
**** Secondary filtering and query editing
- /
  根据标签过滤当前的议程视图。提示您输入字母以选择标签。按 '--'首先针对标签进行选择。
- \
  通过其他条件使当前议程过滤器变窄。
**** Remote editing (see the manual for many more commands)
- 0--9
  数字参数。
- t
  在议程和组织文件中更改项目的TODO状态。
- C-k
  在原始Org文件中删除当前议程项目以及属于它的整个子树。
- C-c C-w
  重新归档该点的条目。
- C-c C-x C-a  or short  a
  使用中设置的默认归档命令，将与该点对应的条目的子树归档org-archive-default-command。
- C-c C-x C-s  or short  $
  存档与当前标题相对应的子树。
- C-c C-s
  计划此项目，使用前缀arg删除计划时间戳记
- C-c C-d
  设置此项目的最后期限，使用前缀arg删除该最后期限。
- S-right and S-left
  将与当前行关联的时间戳更改一天。
- I
  在当前项目上启动时钟。
- O / X
  停止/取消先前启动的时钟。
- J
  跳到另一个窗口中的运行时钟。
*** Custom agenda views:	  	Defining special searches and views
- org-agenda-custom-commands
(setq org-agenda-custom-commands
      '(("w" todo "WAITING")
        ("u" tags "+boss-urgent")
        ("v" tags-todo "+boss-urgent")))
- C-c a w
  作为全局搜索“等候'作为TODO关键字
- C-c a u
  作为全局标签，搜索标记为“：老板：' 但不是 '：紧急：'
- C-c a v
  与的搜索相同C-c a u，但将搜索限制为标题也是TODO项
** Markup 准备文本以进行丰富的导出
由于诸如HTML，LaTeX或DocBook之类的导出目标允许更丰富的格式，因此组织模式对如何准备文本以进行丰富的导出制定了规则。
*** Structural markup elements:	  	The basic structure as seen by the exporter
**** Document title:	  	Where the title is taken from
     #+TITLE: This is the title of the document
**** Headings and sections:	  	The document structure as seen by the exporter
标题和章节
org-export-headline-levels
#+OPTIONS: H:4
**** Table of contents:	  	The if and where of the table of contents
目录通常直接插入文件的第一个标题之前。

#+OPTIONS：toc：2（仅限TOC中的两个级别）
#+OPTIONS：toc：nil（根本没有TOC）
**** Paragraphs:	  	Paragraphs
段落，换行符和引号

- 段落之间至少用一个空行分隔。如果您需要在段落中强制换行，请使用“\\在行尾
- 为了使换行符保持在某个区域中，但要使用正常的格式设置，可以使用此结构，该结构也可以用于格式化诗歌。
  #+BEGIN_VERSE
   Great clouds overhead
   Tiny black birds rise and fall
   Snow covers Emacs

     -- AlexSchroeder
  #+END_VERSE
- 当引用另一个文档的段落时，习惯上将其格式化为在左右两边都缩进的段落。您可以像这样在组织模式文档中包含引号：
  #+BEGIN_QUOTE
   Everything should be made as simple as possible,
   but not any simpler -- Albert Einstein
  #+END_QUOTE
- 如果您想将某些文本居中，请按照以下步骤操作：
  #+BEGIN_CENTER
   Everything should be made as simple as possible, \\
   but not any simpler
  #+END_CENTER
**** Emphasis and monospace:	  	Bold, italic, etc.
强调与等宽
 *bold*, /italic/, _underlined_, =verbatim= and ~code~, +strike-through+
**** Comment lines:	  	What will *not* be exported
#+BEGIN_COMMENT  ... #+END_COMMENT
C-c ;
在条目的开头切换COMMENT关键字。
*** Images and tables:	  	Images, tables and caption mechanism
*** Literal examples:	  	Source code examples with special formatting
- 您可以包括不应该进行标记的文字示例。此类示例将在等宽字体中排版，因此非常适合源代码和类似示例。
  #+BEGIN_EXAMPLE
   Some example from a text file.
  #+END_EXAMPLE
- 为简化起见，在使用小示例时，您还可以在示例行中以冒号开头，后跟一个空格。冒号之前可能还会有其他空格：
  Here is an example
   : Some example from a text file.
- 对于来自编程语言的源代码，或在Emacs中可以通过字体锁定标记的任何其他文本，您可以要求它看起来像字体化的Emacs缓冲区
  #+BEGIN_SRC emacs-lisp
   (defun org-xor (a b)
     "Exclusive or."
     (if a (not b) b))
  #+END_SRC
- 要在支持该语言的特殊缓冲区中编辑示例，请使用 C-c '进入和退出编辑缓冲区
*** Include files:	  Include additional files into a document
#+INCLUDE: "~/.emacs" src emacs-lisp
#+INCLUDE: "./otherfile.org::#my_custom_id" :only-contents t
C-c ' 将访问包含的文件
*** Embedded LaTeX:	  	LaTeX can be freely used inside Org documents
Angles are written as Greek letters \alpha, \beta and \gamma.  The mass of
the sun is M_sun = 1.989 x 10^30 kg.  The radius of the sun is R_{sun} =
6.96 x 10^8 m.  If $a^2=b$ and $b=2$, then the solution must be either
$a=+\sqrt{2}$ or $a=-\sqrt{2}$.

\begin{equation}
x=\sqrt{b}
\end{equation}
** Exporting 共享和发布笔记
*** Export options:	  	Per-file export settings
- C-c C-e #
  插入带有导出选项的模板，请参见下面的示例。

  #+TITLE:       the title to be shown
  #+AUTHOR:      the author (default taken from user-full-name)
  #+DATE:        a date, fixed, or an Org timestamp
  #+EMAIL:       his/her email address (default from user-mail-address)
  #+LANGUAGE:    language, e.g. ‘en’ (org-export-default-language)
  #+OPTIONS:     H:2 num:t toc:t \n:nil ::t |:t ^:t f:t tex:t ...
*** The export dispatcher:	  	How to access exporter commands
C-c C-e 用于导出和发布命令的分派器
*** ASCII/Latin-1/UTF-8 export:	  	Exporting to flat files with encoding
- C-c C-e t a   and   C-c C-e t A
  导出为ASCII文件或临时缓冲区。
- C-c C-e t n   and   C-c C-e t N
  类似于上述命令，但使用Latin-1编码。
- C-c C-e t u   and   C-c C-e t U
  类似于上述命令，但使用UTF-8编码。
*** HTML export:	  	Exporting to HTML
- C-c C-e h h
  导出为HTML文件 myfile.html。
- C-c C-e h o
  导出为HTML文件，并立即使用浏览器将其打开。

#+HTML: Literal HTML code for export

#+BEGIN_EXPORT html
All lines between these markers are exported literally
#+END_HTML
*** LaTeX and PDF export:	  	Exporting to LaTeX, and processing to PDF
- C-c C-e l l
  导出为LaTeX文件 myfile.tex。
- C-c C-e l p
  导出为LaTeX，然后处理为PDF。
- C-c C-e l o
  导出为LaTeX，然后处理为PDF，然后打开生成的PDF文件。
*** iCalendar export:	  	Exporting to iCalendar
- C-c C-e c f
  在目录中为当前文件创建iCalendar条目 .ics 文件。
- C-c C-e c c
  从其中的所有文件创建一个大的iCalendar文件， org-agenda-files然后将其写入给出的文件中 org-icalendar-combined-agenda-file。
** Publishing 出版
- C-c C-e P x
  提示一个特定的项目，并发布属于该项目的所有文件。
- C-c C-e P p
  发布包含当前文件的项目。
- C-c C-e P f
  仅发布当前文件。
- C-c C-e P a
  发布每个项目。
** Working With Source Code 使用源代码
- 代码块的结构
  #+NAME: <name>
  #+BEGIN_SRC <language> <switches> <header arguments>
    <body>
  #+END_SRC
- 编辑源代码
  C-c ' 进入和退出编辑
- 评估代码块
  使用C-c C-c以评估当前代码块，并插入其在组织模式缓冲区的结果

  #+BEGIN_SRC emacs-lisp
    (+ 1 2 3 4)
  #+END_SRC

  #+RESULTS:
  : 10
- 提取源代码
  C-c C-v t
  org-babel-expand-src-block
  :tangle
- 巴别图书馆
  用于C-c C-v l将代码块从组织模式文件加载到 Babel库
  然后可以从任何组织模式缓冲区中评估这些块
- 标头参数
:var
  报头参数用于将参数传递给代码块。传递给参数的值可以是文字值，组织模式表和文字示例块中的值或其他命名代码块的结果。
:results
  报头参数控制集合， 类型，和处理的码块的结果。
  output或的值 value（默认值）指定如何从代码块的评估中收集结果。
  的值vector，scalar file raw html latex并code指定代码块，其指示他们将如何被并入组织模式缓冲区的结果的类型。
  的值silent， replace，prepend，和append指定的代码块的结果的处理，特别是如果和如何结果应插入到组织模式缓冲区。
:session
  标头参数将使代码块在Emacs中的持久交互劣等过程中进行评估。这样可以在代码块评估之间保持状态不变，并可以手动检查评估结果。
:exports
  代码或块结果的任何组合都可以保留在导出时，这可以通过将:resultsheader参数设置为code results none或指定both。
:tangle
  标头参数of :tangle yes将导致代码块的内容与以Org-mode缓冲区的文件名命名的文件纠缠在一起。可以使用指定备用文件名:tangle filename。
:cache
  标头参数of :cache yes将导致将扩展的代码块的哈希值与结果相关联，以确保仅在代码块的输入已更改时才重新运行代码块。
:noweb
  标头参数:noweb yes将在评估和纠结时扩展“ noweb”样式引用。
:file
  将结果输出到文件（例如，图形，图表和图形）的代码块可以接受:file filename标头参数，
  在这种情况下，结果将保存到命名文件中，并且指向该文件的链接会插入到组织模式缓冲区中。