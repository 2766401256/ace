# 一个做好的ACE Editor在线代码测试器
***
现在支持功能有：
+ 语法高亮
+ 语法提示功能
+ 更换主题
+ 在线运行
#### 多用于学习中的在线代码测试
详细请看[CeceBlog](www.baidu.com)

## 使用引导：
##### 1、引入

var ace = require("lib/ace");
##### 2、设置主题

editor.setTheme("ace/theme/twilight");
##### 3、设置程序语言模式

editor.getSession().setMode("ace/mode/javascript");
##### 4、一般常用操作
设置、获取内容:

editor.setValue("the new text here"); // or session.setValue
editor.getValue(); // or session.getValue
获取选择内容:

editor.session.getTextRange(editor.getSelectionRange());
在光标处插入:

editor.insert("Something cool");
获取光标所在行或列:

editor.selection.getCursor();
跳转到行:

editor.gotoLine(lineNumber);
获取总行数:

editor.session.getLength();
设置默认制表符的大小:

editor.getSession().setTabSize(4);
使用软标签:

editor.getSession().setUseSoftTabs(true);
设置字体大小，这个其实不算API:

document.getElementById('editor').style.fontSize='12px';
设置代码折叠:

editor.getSession().setUseWrapMode(true);
设置高亮:

editor.setHighlightActiveLine(false);
设置打印边距可见度:

editor.setShowPrintMargin(false);
设置编辑器只读:

editor.setReadOnly(true); // false to make it editable
##### 5、触发尺寸缩放
编辑器默认自适应大小，如果要程序控制resize，使用如下方法:

editor.resize();
##### 6、搜索

editor.find('needle',{
backwards: false,
wrap: false,
caseSensitive: false,
wholeWord: false,
regExp: false
});
editor.findNext();
editor.findPrevious();
下列选项可用于您的搜索参数:
needle: 要查找的字符串或正则表达式
backwards: 是否反向搜索，默认为false
wrap: 搜索到文档底部是否回到顶端，默认为false
caseSensitive: 是否匹配大小写搜索，默认为false
wholeWord: 是否匹配整个单词搜素，默认为false
range: 搜索范围，要搜素整个文档则设置为空
regExp: 搜索内容是否是正则表达式，默认为false
start: 搜索起始位置
skipCurrent: 是否不搜索当前行，默认为false
替换单个字符:

editor.find('foo');
editor.replace('bar');
替换多个字符:

editor.replaceAll('bar');
editor.replaceAll使用前需要先调用editor.find('needle', ...)
##### 7、事件监听
监听改变事件:

editor.getSession().on('change', function(e) {
// e.type, etc
});
监听选择事件:

editor.getSession().selection.on('changeSelection', function(e) {
});
监听光标移动:

editor.getSession().selection.on('changeCursor', function(e) {
});
##### 8、添加新命令、绑定按键
要指定键绑定到一个自定义函数:

editor.commands.addCommand({
name: 'myCommand',
bindKey: {win: 'Ctrl-M', mac: 'Command-M'},
exec: function(editor) {
//...
},
readOnly: true // 如果不需要使用只读模式，这里设置false
});
