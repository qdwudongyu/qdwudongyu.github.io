---
title: HTML5新特性及移动端设计思路
date: 2018-08-29 11:58:34
tags: HTML5
---

# 移动端设计思路
- Device Pixel Ratio（dpr）：设备像素比（倍率）
  - 苹果以普通屏为基准，给Retina屏定义了一个2倍的倍率（iphone6plus除外，它达到了3倍）
  - 实际像素除以倍率，得到逻辑像素尺寸，只要两个屏幕逻辑像素相同，显示效果相同
  - 真正决定显示效果的，时逻辑像素尺寸
- 视口设置
  - meta name="viewport" content="width=device-width,maximum-scale=1.0,minimum-scale=1.0,initial-scale=1.0,user-scalable=no"
  1.  viewport 代表可视区域的大小
  2.  width=device-width 视口宽度等于设备宽度（设备尺寸即逻辑尺寸）
  3.  禁止缩放
- 单位
  - em： 描述相对于应用在当前元素的字体尺寸，所以也是相对长度的单位，一般浏览器字体大小默认为16px，则2em==32px；（相对于父元素的倍数）
  - rem： 根元素（html）的font-size
  - vw： viewpoint widht，视窗宽度，1vw=视窗宽度的1%
  - vh： viewpoint height，视窗高度，1vh=视窗高度的1%
  - vmin： vw和vh中较小的那个
  - vmax： vw和vh中较大的那个。如果宽度大于高度，则1vmax=宽度的1%
- 注意事项
  1.  Chrome浏览器最小字号12px，如果需要更小字号，可以对装载文本的盒子设置transform：scale（.8）
  2.  背景图片一定要设置background-size
  3.  边框太细在某些小屏手机不显示
  4.  js获取的长度单位是px？rem？
  5.  img{vertical-align:top;}
  6.  **zepto.js**(Zepto是一个轻量级的针对现代高级浏览器的JavaScript库， 它与jquery有着类似的api。 如果你会用jquery，那么你也会用zepto。减少移动断不需要的组件等，压缩体积)
    
      [zepto中文文档](http://www.css88.com/doc/zeptojs_api/#$())
# HTML5新结构标签
- 推出的理由及目标
  - 把目前WEB上存在的各种问题一并解决掉
    - WEB浏览器之间兼容性很低
    - 文档结构不够明确
    - Web应用程序的功能受到了限制
  - 世界知名浏览器厂商对HTML5的支持
    - 微软（IE9，EDGE）Google（chrome）Opera Mozilla（FireFox）
- HTML5的优势
  - 移动端Android browser与IOS Safari都对HTML5有非常好的支持，移动端现在大热，依靠Android与IOS、Windows开发成本巨大，WEBAPP页面必然越来越弱
  - HTML5的CANVAS元素能够很好的制作特效动画，取代FLASH
  - 视频的播放功能的提升
  - 新增的语义标签让HTML页面内容更清晰，便于搜索引擎搜索
- HTML5语法的改变
  - 内容类型（扩展名和内容类型保持不变）：HTML5的文件扩展符与内容类型保持不变。也就是说，扩展符仍然为".html"或".htm"，内容类型（ContentType）仍然为"text/html"
  - DOCTYPE声明：在HTML5中，刻意不使用版本声明，一份文档将会适用于所有版本的HTML。HTML5中的DOCTYPE声明方法（不区分大小写）
  - 指定字符编码：从HTML5开始，对于文件的字符编码推荐使用UTF-8
  - 可以省略标记的元素
  - 具有boolean值的属性：对于具有boolean值的属性，例如disabled与readonly等，当只写属性而不指定属性值时，表示属性值为true；如果想要将属性值设为flase，可以不使用该属性。另外要想将属性值设为true时，也可以将属性命名设定为属性值，或将空字符串设定为属性值
  - 省略引号:在之前的HTML版本中，指定属性值的时候，属性值两边既可以用双引号，也可以用单引号。HTML5在此基础上做了一些改进，当属性值不包括空字符串、"<"、">"、"="、单引号、双引号、等字符时，属性值两边的引号可以省略
  - 可以省略标记的元素
- HTML5页面独特予以标签
  - HTML5引入了新的HTML元素，通过使用这些元素，开发者可以更细致的描述文档结构，让文档更加易读，搜索引擎也能更好的理解页面中各部分间的关系，我们也可以搜索到更快，更准确的信息
- 新增的元素
  - 新增的结构元素
    - section、article、aside、header、hgroup、footer、nav、figure、figcaption、
  - 新增的其他元素
    - video、audio、canvas、embed、mark、progress、meter、time、ruby、rt、rp、wbr、command、details、datalist、datalist、datagrid、keygen、output、source、menu
  - 新增的input元素的类型
    - email、url、number、range、DatePickers、color
  - 废除的元素
    - 能使用css替代的元素：basefont、big、center、font、s、tt、u等
    - 不再使用frame框架
    - 只有部分浏览器支持的元素
    - 其他被废除的元素
  - 新增的结构标签
    1.  header：页眉
    2.  footer：页脚
    3.  nav：导航
    4.  article：文章
    5.  section：文档中的区段
    6.  aside：侧边栏
    7.  hgroup：标题
    8.  figure：一组媒体对象以及文字
    9.  figcaption：定义figure的标题
  - 使用HTML5新标签的网站：
    - 苹果 -  太享设计 
- header标签
  - header元素是一种具有引导和导航作用的结构元素，通常用来放置整个页面或页面内的一个内容快的标题，但是也可以包含其他内容
- footer标签
  - footer元素定义文档或章节的末尾部分，通常包含一些章节的基本信息，如作则信息、相关链接即版信息。在footer标签里，还可以用nav、ul、div标签
- nav标签
  - nav元素是一个可以用作页面导航的链接组，其中的导航元素链接到其他页面或当前页面的其他部分。并不是所有的链接组都要被放进nav元素，只需要将主要的、基本的链接组放进nav元素即可
  - nav元素的应用场景
    - 传统导航条
    - 侧边栏导航
    - 页内导航
    - 翻页操作
- article标签
  - article元素代表文档、页面或应用程序中独立的、完整的、可以独自被外部引用的内容。他可以是一篇博客或则报刊中的文章，一篇论坛帖子、一段用户评论或独立的插件，或则其他任何独立的内容。article元素可以嵌套使用
- section标签
  - section元素用于对网站或应用程序中页面上的内容进行分块。一个section元素通常由内容及其标题组成。但section元素并非一个普通的容器元素；当一个容器需要直接定义样式或通过脚本定义行为时，推荐使用div而非section元素
  - 注意
    - 不要将section元素作为设置样式的页面容器
    - 如果article元素、aside元素、nav元素更符合使用条件，那不要使用section元素
    - 没有标题内容，不要使用section元素
- aside标签
  - aside元素用来表示当前页面或文章的附属信息部分，他可以包含与当前页面或主要内容相关的引用、侧边栏、广告、导航条、以及其他类似的有区别于主要内容的部分。
  - aside往往用于侧边栏的使用，特别是2分栏，3分栏的侧边栏的使用
- hgroup标签
  - 定义网页栏目或则模块之间的导航
- figure标签、figcaption标签
  - 标签定义独立的的流内容（图像、图标、照片等等）
- 低版本IE如何支持HTML5标签
  - **html5shiv.js通过JavaScript来创建HTML5元素（如main，header，footer等）**通过引用htmlshiv即可使低版本的IE支持HTML5标签（注释）
- ico百科
  - Favicon原本是windows中存储单个图案的一种图标文件格式，现在可以用作软件、文件夹以及网站等的缩略标志，显示在用户的资源管理器，浏览器的地址栏、标题栏和多页面浏览器的标签栏上。图标文件一般尺寸较小，常见的是16x16， 32x32和48x48.图标是部分透明的，可以直接打开浏览
  - 关于favicon.ico
    - favicon.ico图标是网站的缩略标志，可以显示在浏览器标签、地址栏左边和收藏夹，是展示网站个性的缩略logo标志，也可以说是网站的头像，如果要让网站看起来更专业、更美、更有个性，favicon.ico是必不可少的
    - 在线ico制作工具说明
      - 原始图片必须是jpg、jpeg、gif、png格式之一
      - 原始图片文件大小《300k
      - 建议原图的长和宽相同，以避免转换后生成的ico图标因缩放而失真
    - 使用
      - 将生成的图标文件改名为favicon.ico，上传到网站根目录
      - 在网站首页的源文件head标签之间插入下面的斜体部分代码head> ……link rel="shortcut icon" href="favicon.ico"</head
      - 动态ico图标的实现方法，先把做好的gif动态图标命名为favico.gif在head之间加上link rel=icom href=favicon.gif type=image/gif
- base64编码
  - 减少不必要的http请求
  - 图片小，又不适合做成精灵图，在页面中使用的又多
  - 步骤
    -  base64编码/解码的网站：[编码/解码网站](http://tool.css-js.com/base64.html)
    -  Base64目前主要用于HTML5、移动开发等不考虑ie6的场景
    -  Base64在css中使用(支持img和背景图)
- webp图片格式
  - webp格式，谷歌开发的一种旨在加快图片加载速度的图片格式。图片压缩体积大约只有jpeg的2/3，并能节省大量的服务器带宽资源和数据空间。Facebook ebay等知名网站已经开始测试并使用webp格式
  - 当你webp是一种有损压缩。相较编码jpeg文件，编码同样质量的webp文件需要占用更多的计算资源
    - 下载软件：xnconvert并安装
    - 把jpg图片防砸itu文件夹
    - 打开软件，选择文件夹tu，切换到输出--》选择输出后文件夹，选择格式webp
    - 单击转换
# 本地存储
- 客户端存储数据的方法
  - cookie
  - localStorage
    - localStorage方法存储的数据没有时间限制，**不能跨浏览器读取数据**
    - 保存数据：localStorage.setItem(key,value); 
	          localStorage.key = value;
    - 读取数据：localStorage.getItem(key); 
	          localStorage.key
    - 删除单个数据：localStorage.removeItem(key); 
    - 删除所有数据：localStorage.clear(); 
  - sessionStorage
    - 针对session进行数据存储，当用户关闭浏览器窗口后，数据会被删除
    - 保存数据：sessionStorage.setItem(key,value); 
	          sessionStorage.key = value;
    - 读取数据：sessionStorage.getItem(key); 
	           sessionStorage.key
    - 删除单个数据： sessionStorage.removeItem(key); 
    - 删除所有数据：sessionStorage.clear()
  - 共同点：都是保存在浏览器端，且同源的。
    - 区别：
      1. 与服务器的数据交换方式不同。 cookie数据始终在同源的http请求中携带（**即使不需要**），即cookie在浏览器和服务器间来回传递。而sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。
      2. 存储大小限制也不同，cookie数据不能超过4k，同时因为每次http请求都会携带cookie，所以cookie只适合保存很小的数据，如会话标识。sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。
      3. 数据有效期不同，sessionStorage：仅在当前浏览器窗口关闭前有效，自然也就不可能持久保持；localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭。
      4. 作用域不同，sessionStorage、localStorage不在不同的浏览器窗口中共享，即使是同一个页面；cookie也是在所有同源窗口中都是共享的。
# 离线存储之Application Cache
- 应用缓存
  - HTML5引入了应用缓存（又叫离线缓存），这意味着web应用可进行缓存，并可在没有网络连接时进行访问
- 应用缓存的优势
  - 离线浏览-用户可以在离线状态下浏览网站内容
  - 速度-因为数据被存储在本地，所以速度会更快
  - 减少服务器负载-浏览器只会下载在服务器上发生改变的资源
- 应用
  - php（web服务器环境）
  - 创建html文件
  - 创建xxx.appcache文件
    - CACHE MANIFEST（头部必不可少）
    - #version 1.3（#注释 通过改变加载更新缓存）
    - CACHE:（需要缓存的文件 只能是文件名）
    - XXX
    - XXX
    - NETWORK:（不需要缓存的文件 通常为*-》通配所有）
    - *
    - FALLBACK：(指定后备页面，当第一个资源无法访问时，浏览器使用该页面)（该段落的每条记录都列出两个URI-第一个表示资源，第二个表示后备页面。两个URI都必须使用相对路径并且与清单文件同源可以使用通配符）
    - 在html文件中html标签中设置关联（html lang="en" manifest="demo.appcache">（添加manifest=“appcache文件的路径”）
- 注意事项
  - 站点离线存储的容量限制是5m
  - 如果manifest文件，或则内部列举的某个文件不能正常下载，整个更新过程将视为失败，浏览器继续全部使用老的缓存
  - 引用的appcache必须与html文件同源，在同一个域下
  - FALLBACK中的资源必须和manifest文件同源
  - 当一个资源被缓存后，该浏览器直接请求这个绝对路径也会范文缓存中的资源
  - 站点中的其他页面即使没有设置manifest属性，请求的资源如果在缓存中也从缓存中访问
  - 当manifest文件发生改变时，资源请求本身也会触发更新
# 检测设备是否在线
- navigator.online(判断其值是否为真)
# HTML5Geolocation（地理定位）
- HTML5 Geolocation API用于获得用户的地理位置
- 支持情况
  - Internet Explorer 9+，Firefox，Chrome，Safari和Opera支持Geolocation（地理定位）
  - 注意：Geolocation（地理定位）对于拥有 GPS的设备，比如iphone，地理定位更加精确
- getCurrentPosition（）
  - 使用getCurrentPosition（）方法来获取用户的位置
  - 该方法属于navigator.geolocation.getCurrentPosition()
  - 同时该方法有三个参数，一个是成功是运行的函数，一个是失败时返回的函数，还有一个是可选参数。navigator.geolocation.getCurrentPosition(success,error,{enableHightAccuracy:true,timeout:5000,maximumAge:3000})(enableHighAccuracy:true只是浏览器获取高精度的位置，默认为false-/-指定获取地理位置的超时时间，默认不限时，单位为毫秒-/-最长有效期，在重复获取地理位置时，此参数多次再次获取位置)
- 错误代码
  - code1：Permission denied - 用户不允许地理定位
  - code2：Position unavailable - 无法获取当前位置
  - code3：Timeout - 操作超时
- getCurrentPosition（）
- getCurrentPosition() 方法 - 返回数据
  - 属性	                           描述
  - coords.latitude	              十进制数的纬度
  - coords.longitude	十进制数的经度
  - coords.accuracy	              位置精度
  - coords.altitude	              海拔，海平面以上以米计
  - coords.altitudeAccuracy	位置的海拔精度
  - coords.heading	              方向，从正北开始以度计
  - coords.speed	              速度，以米/每秒计
  - timestamp	              响应的日期/时间
- Geolocation对象-其它方法
  - HTML5 watchPosition 监听地理位置变化- 返回用户的当前位置，并继续返回用户移动时的更新位置（就像汽车上的 GPS）。
  - clearWatch() - 停止 watchPosition() 方法
# 视频、音频
- HTML5的视频标签
  - video width="320" height="240" controls="controls"> 
      - source src="movie.ogg" type="video/ogg"> 
      - source src="movie.mp4" type="video/mp4"> 
      您的浏览器不支持video标签 
  - /video> 
- video标签的属性
  - autoplay：视频在就绪后马上播放
  - controls：向用户显示控件，比如播放按钮
  - height：设置视频播放器的高度
  - loop：当媒介文件完成播放后再次开始播放
  - preload：视频在页面加载时进行加载，并预备播放。如果使用autoplay，则忽略该属性
  - src：要播放视频的URL
  - widht：设置视频播放器的宽度
  - poster：指定一张图片，在当前视频数据无效时显示（预览图）
- HTML5的音频标签
  - HTML5支持的音频格式
    - .wav .mp3
  - audio音频标签的属性
    - autoplay：音频就绪后马上播放
    - controls：向用户显示控件，比如播放按钮
    - loop：当音频结束后重新开始播放
    - preload：音频在页面加载时进行加载，并预备播放，如果使用autoplay，则忽略该属性
    - src：要播放的音频的URL
- 自定播放控件相关api
  - video.webkitRequestFullScreen()全屏
  - video.paused:布尔值，是否暂停
  - video.play()播放
  - video.pause();暂停
  - 事件:timeupdate 当前播放位置发生改变时触发该事件
  - video.currentTime 当前播放的事件，单位秒
  - video.duration 返回总时间，单位秒
  - video.muted 布尔值，是否静音
  - video.volume 设置音量
- 更多API参考  
  - 方法
    - play（）播放
    - pause（）暂停
    - load（）加载
    - canPlayType可以播放的文件类型
  - 属性
    - currentSrch获取当前视频的URL
    - currentTimef返回当前位置（进度条位置）
    - videoWidth获取播放器的宽度
    - videoHeight获取播放器高度
  - 事件
    - play开始播放时触发
    - pause
    - progressl浏览器正在下载时触发
    - errors视频加载发生错误时
  - 全屏
    - Webkit（Safari5.1/Chrome15）
      - element.webkitRequestFullScreen();
      - document.webkitCancelFullScreen(); 
    - Firefox (works in nightly)
      - element.mozRequestFullScreen();
      - document.mozCancelFullScreen(); 
    - W3C 提议
      - element.requestFullscreen();
      - document.exitFullscreen();
- Video的API属性
  - audioTracks：返回可用的音轨列表
  - autoplay：媒体加载后自动播放
  - buffered：返回缓冲部件的事件范围
  - controller：返回当前的媒体控制器
  - controls：显示播控控件
  - crossOrigin：CORS设置
  - currentSrc：返回当前媒体的URL
  - currentTime：当前播放的时间，单位秒（快进 快退10s）
  - defaultMuted：缺省是否静音
  - defaultPlaybackRate：播控的缺省倍速
  - duration：返回媒体的播放总时长，单位秒
  - ended：返回当前播放是否结束标志
  - error：返回当前播放的错误状态
  - initialTime：返回初始播放的位置
  - loop：是否循环播放
  - mediaGroup：当前音视频所属的媒体组（用来链接多个音视频标签）
  - muted：是否静音
  - networkState:返回当前的网路状态
  - paused：是否暂停
  - playbackRate：播放的倍速（加速、减速播放）
  - played：当前播放部件已经播放的时间范围
  - preload：页面加载时是否同时加载音视频
  - readyState返回当前的准备状态
  - seekable：返回当前可跳转部件的时间范围
  - seeking：返回用户是否做了跳转操作
  - src：当前音视频源的URL
  - startOffsetTime：返回当前的时间偏移
  - textTracks：返回可用的文本轨迹
  - videoTracks：返回可用的视频轨迹
  - volume：音量值
- video的时间
  - abort：当音视频加载被异常终止时产生该事件
  - canplay：当浏览器可以播放该音视频时触发
  - canplaythrough：当浏览器可以开始播放该音视频到结束而无需因缓冲而停止时触发
  - durationchange：当媒体的总时长改变时触发
  - emptied：当播放列表为空时触发
  - ended：当播放列表结束时触发
  - error：当加载媒体发生错误时触发
  - loadeddata：当加载媒体数据时触发
  - loadedmetadata：当收到总时长、分辨率和字轨等metadata时产生该事件
  - loadstart：开始查找媒体数据时产生该事件
  - pause：当媒体暂停时触发
  - play：播放时触发
  - playing：从因缓冲而引起的暂停和停止恢复到播放时产生该事件
  - progress：获取到媒体数据时
  - ratechange：播放倍数改变时
  - seeked：完成跳转时
  - seeking：正在执行跳转时
  - stalled：试图获取媒体数据，但数据还不可用时
  - suspend：获取不到数据时
  - timeupdate：播放位置发生改变时产生该事件
  - volumechange：当音量发生改变时产生
  - waiting：因缓冲下一帧而停止时
# SVG
- SVG基于XML描述的矢量图形格式
- SVG优势
  - SVG可被非常多的工具读取和修改（比如记事本）
  - SVG与JPEG和GIF图像比起来，尺寸更小，且可压缩性更强
  - SVG时可伸缩的
  - SVG图像可在任何的分辨率下被高质量的打印
  - SVG可在图像质量不下降的情况下被放大
  - SVG图像中的文本是可选的，同时也是可搜索的（很适合制作地图）
  - SVG是开放的标准
  - SVG文件是纯粹的XML
- 浏览器支持
  -  IE 9+
  -  Chrome 33.0+
  -  Firefox 28.0+
  -  Safari 7.0+
- **应用**
  1. 直接设置到img的src属性中使用
  2. svg标签
  3. css背景图 
# HTML5的canvas标签
- canvas标签定义图形，比如图表和其他图像
- canvas标签只是图形容器，必须使用脚本来绘制图形
- 这个 HTML 元素是为了客户端矢量图形而设计的。它自己没有行为，但却把   
    一个绘图 API 展现给客户端 JavaScript 以使脚本能够把想绘制的东西都绘制到一块画布上。
- Canvas绘图API定义在通过画布的getContext（）方法获得一个绘图环境对象上
##  使用方法
- var canvas=document.getElementById(id);
- var context=canvas.getContext("2d");
- 默认尺寸：300*150
- [参考网址](http://www.cnblogs.com/tim-li/archive/2012/08/06/2580252.html)
##  基本姿势
- 绘制图像的两种方法
  - context.fill()  填充
  - context.stroke() 绘制边框
- style绘图样式
  - context.fillStyle  //填充的样式
  - context.strokeStyle  //边框的样式
  - context.lineWidth   //边框宽度
- 绘制矩形
  - context.fillRect(x,y,width,height)  起点坐标   宽高
  - strokeRect(x,y,width,height)
- 清除矩形区域 
  - context.clearRect(x,y,width,height)
-  圆弧
  -  context.arc(x, y, radius, starAngle,endAngle, anticlockwise) //圆心，半径，开始角度，结束角度，是否逆时针（true-逆时针）
- 路径  
  - context.beginPath()    
  - context.closePath()
- 绘制线段 
  - context.moveTo(x,y)起点  
  - context.lineTo(x,y)终点
  - 每次画线都从moveTo的点到lineTo的点，

    如果没有moveTo那么第一次lineTo的效果和moveTo一样，

    每次lineTo后如果没有moveTo，那么下次lineTo的开始点为前一次lineTo的结束点
- **需要服务器环境**
- ctx.drawImg->将图片绘制在canvas上
- canvas.toDataURL->将画布上的图像转成Base64格式（可压缩图片）（默认为image/png）（只能为image/jpeg或则image/webp文件压缩-》默认压缩比列为.92）
# FileReader读取文件-（实现上传文件的预览功能）
- **方法**
  - readAsArrayBuffer（file）
    - 按字节读取文件内容，结果用ArrayBuffer对象表示
  - readAsBinaryString（file）
    - 按字节读取文件内容，结果为文件的二进制串
  - **readAsDataURL（file）**
    - 读取文件内容，结果用data：url的字符串形式显示（转换成Base64格式）
  - readAsText（file，encoding）
    - 按字符读取文件内容，结果用字符串形式表示
  - abort()
    - 终止文件读取操作
- **事件**
  - onabort()
    - 当读取操作被终止时调用
  - onerror()
    - 当读取操作发生错误时调用
  - onload()
    - 当读取操作成功完成时调用
  - onloadend()
    - 当读取操作完成时调用，无论成功或失败
  - onloadstart()
    - 当读取操作开始时调用
  - onprogress()
    - 在读取数据过程中周期性调用
- input-type="file"(选择文件)
- input.onchange-(当选中文件即，发生改变时)-获取其**files[0]（当选择一个文件时，其中存储的为文件的属性，files[0]就是文件对象）**
- 生成FileReader的实例（var reader=new FileReader（））
- 当文件被选中，即触发change事件时，当文件存在时，调用FileReader.readAsDataURL(file)-(将其中的文件对象转换成Base64格式)-该方法无返回值-只能在其onload事件之后输出xx.result(结果为传入文件对象的Base64结果)
- 然后直接将其设置到img标签的src属性，即可在网页中显示（由于Base64格式的特性，可直接在写在src中正常显示）
- **实现上传文件的预览功能**
  1.  依靠input的file类型（选择文件上传）
  2.  input.files[0]，单个选中文件的文件对象（其中存放着对应选中文件的信息）（由于input.value中存放的不是图片的完整路径，所有不能直接通过该方法直接设置） 
  3.  通过生成FileReader的实例，通过其readAsDataURL将传入的文件对象转换成Base64模式，再将其设置到img的src中，再与页面中显示即可
-  **选中文件的压缩，可以通过与canvas结合实现**
-  通过canvas的drawImg方法可以将选中文件的需要部分打印到canvas上，实现文件的而裁剪
-  **img.naturalWidht**(获取图片的原始尺寸)
