# 在GitHub上搭建个人主页
最近因为项目组统一要求，在[GitHub](https://so.csdn.net/so/search?q=GitHub&spm=1001.2101.3001.7020)上搭建了一个个人主页，也就是个人简历页面。过程中遇到了一些问题，特记录下来与大家分享。  
首先大家需要在 GitHub 上注册一个账号，注册账号过程就不在此赘述了，注册好账号后并登入将进入如下页面：

![](https://img-blog.csdnimg.cn/20181218142807819.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

选择 “Start a [project](https://so.csdn.net/so/search?q=project&spm=1001.2101.3001.7020)” 或者 “New repository” 创建一个新的仓库，输入 Repository name，其格式是 “[username.github.io](http://username.github.io/)” 或者 “[username.github.com](http://username.github.com/)”，username 就是大家注册账号时的 username，Description 处可以写上对仓库的描述。

![](https://img-blog.csdnimg.cn/20181218144438464.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

然后点击 “Create repository” 完成仓库的创建。之后，就可以往仓库中上传代码了，我们的目的是建一个个人主页，通常简单的 html 代码就能满足。更令人激动的是，GitHub 为我们提供了一系列的主题模板。点击 “Setting” 按钮进入 Setting 页面。

![](https://img-blog.csdnimg.cn/20181218151602162.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

找到 “GitHub Pages”，点击 “Choose a theme”。

![](https://img-blog.csdnimg.cn/20181218152043334.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

我选择了第一个 “Cayman theme”，大家可以根据自己的爱好选择。

![](https://img-blog.csdnimg.cn/20181218152645408.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

确定主题后，GitHub 将帮助我们自动完成主题的创建，生成两个文件，“\_config.yml” 和 “[index.md](http://index.md/)”，其中 “[index.md](http://index.md/)” 是包含我们主页内容的 markdown 格式文本，“\_config.yml” 是对 “[index.md](http://index.md/)” 进行渲染的配置文件。按照我的理解是，GitHub 后台采用 Jekyll 根据 “\_config.yml” 配置将 “[index.md](http://index.md/)” 渲染成对应的 “index.html” 文件，完成展示。

![](https://img-blog.csdnimg.cn/2018121815365049.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

对 “[index.md](http://index.md/)” 文件进行编辑，生成个人主页的内容和格式。“[index.md](http://index.md/)” 采用 markdown 格式书写，markdown 是一种标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式。就像写论文一样，我们首先要确定个人主页要展示的主要内容，我选择展示以下信息：“个人信息、最新消息、研究方向、荣誉奖励、项目研究”。

![](https://img-blog.csdnimg.cn/20181218155111555.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

“### 内容” 是 markdown 标题格式，一个 “#” 代表一级标题，依此类推，“###” 表示三级标题。确定好标题后，往各个类目中填入内容即可完成个人主页的编辑。

![](https://img-blog.csdnimg.cn/20181218161955108.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

然后点击 “Commit changes” 即可完成提交，可以看到现在我们的个人主页内容和格式如下：

![](https://img-blog.csdnimg.cn/20181218162425745.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

此时，我们就已经完成了一个简单的个人主页的搭建，通过[https://bdhehohai.github.io 就能访问到我们的个人主页。“bdhehohai” 对应大家的 username。](https://bdhehohai.github.io就能访问到我们的个人主页。“bdhehohai”对应大家的username。)

![](https://img-blog.csdnimg.cn/20181218173610201.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

上面的个人主页也未免太过简单，通常在制作个人简历时，我们会将个人主要信息以及个人生活照 / 证件照放在最顶端，因此下面开始我们的改造完善工作。markdown 中插入图片的语法如下：

```
![图片描述](图片链接)
![证件照](/zhengjianzhao.jpg)

```

首先，我们需要将个人照片上传到项目仓库中，在项目主页点击 “Upload files” 从本地上传一张照片，与 “[index.md](http://index.md/)” 放在同一级目录。

![](https://img-blog.csdnimg.cn/201812181749581.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

接着对 “[index.md](http://index.md/)” 文件进行编辑，我们希望将个人主要信息，如：姓名、地址、邮箱等主要信息和个人照片并排显示。但是这种格式在 markdown 语法中并不支持，庆幸的是，我们可以在 md 文件中编写 html 代码。这个该怎么实现呢？我们可以插入一个一行两列的表格，左边填入个人信息等文本数据，右边插入照片。具体代码如下：

```
<table border="0">
  <tr>
    <td width="75%">
      <h1>张三</h1>
      <p><b>硕士研究生</b></p>
      <p><b>××大学××学院</b></p>
      <p><b>邮箱：1234567789@qq.com</b></p>
      <p><b>地址：××市××区××路××号××大学，××楼，邮编×××</b></p>
    </td>
    <td width="25%">
      <img src="/zhengjianzhao.jpg" width="100%">      % 插入证件照代码
    </td>
  </tr>
</table>

```

这里有一个坑需要大家注意一下，所有 html 标签都要写成闭标签的形式，如：`<p></p>`的形式，本人开始没有写`</p>`标签，导致渲染出来的页面出现了乱码情况，花了很大时间排查。闭合标签也是一个良好的编码习惯。  
效果如下所示：

![](https://img-blog.csdnimg.cn/20181218181402253.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

除了中文主页外，我们也会建立英文主页，并且提供相互[链接](https://so.csdn.net/so/search?q=%E9%93%BE%E6%8E%A5&spm=1001.2101.3001.7020)，在 “[index.md](http://index.md/)” 也可以很方便的插入链接。在 markdown 中插入链接的语法如下：

```
[链接描述](url)
[英文版](index-en.md)

```

首先，我们需要建立英文版主页文件 “[index-en.md](http://index-en.md/)”，创建方法与上面编辑 “[index.md](http://index.md/)” 类似。然后，我们将英文版链接放在个人主要信息的下面，即表格中，因此此时插入链接要采用 html 的语法格式

```
<a href="/index-en.html">英文版</a>

```

注意，此处我写的英文版链接是 “/index-en.html”，可能大家会疑问明明没有 “index-en.html” 这个，这样写能链接到指定的英文主页吗？我的个人理解是 “[index-en.md](http://index-en.md/)” 最终也是渲染成 html 文件了，所以能够通过. html 访问到。至于为什么不写成 “/index-en.md”，我也这么尝试过，但是访问到是 md 文本文件。最终的个人主页如下图所示：

![](https://img-blog.csdnimg.cn/20181218183853275.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

GitHub 自带的主题毕竟有限，如果想设计更加丰富炫酷的主页，还是需要用 html 代表编写。在这里提供一个将 markdown 文件转化成 html 文件的网站，[http://mahua.jser.me/](http://mahua.jser.me/)。将转好的 html 页面上传项目仓库，我们可以访问自己主题的个人主页。

![](https://img-blog.csdnimg.cn/20181218185235627.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hvaGFpeng=,size_16,color_FFFFFF,t_70)

本文简单记录了 GitHub 上个人主页搭建流程，以及可能遇到的坑，关于整个项目的内容，大家可以[在 GitHub 上进行 fork](https://github.com/bdhehohai/bdhehohai.github.io)。 
 [https://blog.csdn.net/hohaizx/article/details/85066248](https://blog.csdn.net/hohaizx/article/details/85066248)

 [https://blog.csdn.net/hohaizx/article/details/85066248](https://blog.csdn.net/hohaizx/article/details/85066248)
