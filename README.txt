                          改造VIM变成Source Insight
首先你要确定你的linux里安装了ctags，在RHEL6.3.ios的Packages目录下有这个rpm包。

如果你在定制安装的时候选择了开发工具这一项就会默认的帮你安装这个软件。

然后就是重点了

taglist.vim: http://www.vim.org/scripts/script.php?script_id=273

这个是vim官网上长期下载和分数都为第一位的插件，是实现图中最左边功能框的插件


SrcExpl :    http://www.vim.org/scripts/script.php?script_id=2179   

这插件从作者的名字上看像是一个中国人(很是骄傲，希望能和这位大牛见上一面)，这是实现source insight的预览框的功能，就是图中最下面的功能框。


Trinity :       http://www.vim.org/scripts/script.php?script_id=2347

这个也是上面那个大牛写的，里面有含有NERD_tree这个插件。我直接用NERD_tree原插件替换过没有出现过问题。

NERD_tree是实现图中最右边的功能框。就是实现文件树这个功能，而这个Trinity的文件下有一个trinity.vim，是实现三个功能框快速开关的功能

把这三个文件解压后会有taglist.vim  srcexpl.vim  NERD_tree.vim  trinity.vim这四个插件，直接复制到vim安装目录下的plugin文件夹下，我的RHEL6.3的vim是安装在/urs/share/vim文件夹下。我把这四个插件复制到了/usr/share/vim/vimfiles/plugin。然后在修改/etc文件夹下的vimrc文件。在最后一行加上

" Open and close all the three plugins on the same time 
nmap <F8>   :TrinityToggleAll<CR> 

" Open and close the srcexpl.vim separately 
nmap <F9>   :TrinityToggleSourceExplorer<CR> 

" Open and close the taglist.vim separately 
nmap <F10>  :TrinityToggleTagList<CR> 

" Open and close the NERD_tree.vim separately 
nmap <F11>  :TrinityToggleNERDTree<CR> 

这个是Trinity中的使用介绍，也就是F8打开关闭所有的功能框，F9打开关闭SourceExplorer功能框，剩下的都是相关的键控制相关的功能框。可以自己定义功能键。F10另一个功能就是更新ctags的内容，如果更改了代码保存后按下F10更新ctags。

当然如果再加上set mouse=a  就可以再vim下使用鼠标了。

这时先在你的工程目录下执行ctags -R后用vim打开一个文件，按下F8(打开所有的功能框)，试一试是不是和source insight一样了。

要去到预览框中的文件直接在预览框中双击鼠标，要返回就按空格键。

现在在加上一个自动补全功能

AutoComplPop：http://www.vim.org/scripts/script.php?script_id=1879

和安装其他插件一样把解压后相应的文件夹下的内容复制到vim安装目录下的相应文件夹下，重新开启vim，开始写代码是不是就有代码补全功能了，用上下键选择，回车确定。

到此VIM已经和source insight一样强大了。当然还可以寻找更多的插件，来安装。VIM一定能变成史上最强IDE。顺便说一句在win下也可以实现以上功能，当然ctags 是.exe文件在http://www.vim.org/scripts/script.php?script_id=2288下载复到C:\WINDOWS\system32目录下，在DOS中在你的工程目录下执行ctags -R。其他的和在linux下一样的，就可以在win下改造vim了。


参考网站：
http://qiweiyou1982.blog.163.com/blog/static/14164218620132112548476/
