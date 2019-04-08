# 目录
* js效果
	* [轮播图（带分页器）](#轮播图带分页器)
	* [轮播图（带前进后退按钮）](#轮播图带前进后退按钮)
	* [栏目切换](#栏目切换)
	* [滚屏](#滚屏)
* 模板设参
	* [首页基本设参](#首页基本设参)
	* [文章页设参](#文章页设参)
# 轮播图（带分页器）
## html
```html   
	<link rel="stylesheet" href="images/swiper.min.css">
	<script type="text/javascript" src="http://libs.baidu.com/jquery/1.9.1/jquery.min.js"></script>
	<div class="swiper-container my-swiper">
		<ul class="swiper-wrapper">
			<li class="swiper-slide swiper-item"><a href="#"><img src="images/shouye_pic_1.png" alt=""><span>第一张图的简要</span></a></li>
			<li class="swiper-slide swiper-item"><a href="#"><img src="images/shouye_pic_2.png" alt=""><span>第二张图的简要</span></a></li>
		</ul>
		<!-- 如果需要分页器 -->
		<div class="swiper-pagination my-pagination"></div>
	</div>
	<script src="images/swiper.min.js"></script>
```
## css
```css
	.my-swiper {
		width: 400px;
		height: 200px;
		margin: 20px auto;
	}
	.my-swiper ul {
		padding: 0;
		margin: 0;
	}
	.swiper-item a {
		display: inline-block;
		width: 100%;
		height: 100%;
		overflow: hidden;
		position: relative;
	}
	.swiper-item a img {
		width: 100%;
		height: 100%;
	}
	.swiper-item a span {
		box-sizing: border-box;
		position: absolute;
		bottom: 0;
		left: 0;
		display: inline-block;
		width: 100%;
		height: 50px;
		line-height: 50px;
		color: #fff;
		font-size: 13px;
		padding-left: 20px;
		background: #000; 
		opacity: 0.5;
	}
	.my-pagination {
		box-sizing: border-box;
		text-align: right;
		padding-right: 13px;
		bottom: 13px !important;
	}
	.my-pagination .swiper-pagination-bullet {
		width: 22px;
		height: 22px;
		line-height: 22px;
		text-align: center;
		margin-right: 4px;
		font-size: 13px;
		color: #fff;
		background: #7f7969;
		opacity: 1;
	}
	.my-pagination .swiper-pagination-bullet-active {
			background: #fa8d00;
	}
```
## javascript
```javascript
	$(document).ready(function() {
		var mySwiper = new Swiper(".my-swiper", {
			autoplay: { // 是否自动切换
				disableOnInteraction: false, // 操作swiper后自动切换不会停止，每次都会重新启动swiper，操作包括触碰、拖动、点击pagination等。
			},
			speed: 300, // 切换速度
			loop: true, // 循环切换
				
			// 分页器
			pagination: {
				el: ".my-pagination",
				clickable: true,
				renderBullet: function (index, className) {
					return "<span class='" + className + "'>" + (index + 1) + "</span>";
				},
			},
		});
		// 鼠标移上停止切换
		mySwiper.el.onmouseover = function () {
			mySwiper.autoplay.stop();
		}
		// 鼠标移开开始切换
		mySwiper.el.onmouseleave = function () {
			mySwiper.autoplay.start();
		}
	});
```
效果：  
![轮播图带分页](/images/effectDiagram_1.png)
# 轮播图（带前进后退按钮）
## html
```html
	<link rel="stylesheet" type="text/css" href="images/swiper.min.css" />
	<div class="content">
		<div class="swiper-container my-swiper">
			<ul class="swiper-wrapper">
				<li class="swiper-slide swiper-item"><a href="#"><img alt="" src="images/shouye_pic_2.png" /></a></li>
				<li class="swiper-slide swiper-item"><a href="#"><img alt="" src="images/shouye_pic_3.png" /></a></li>
				<li class="swiper-slide swiper-item"><a href="#"><img alt="" src="images/shouye_pic_4.png" /></a></li>
				<li class="swiper-slide swiper-item"><a href="#"><img alt="" src="images/shouye_pic_5.png" /></a></li>
			</ul>
		</div>
		<!-- 如果需要导航按钮 -->
		<div class="swiper-button-prev swiper-btn"></div>
		<div class="swiper-button-next swiper-btn"></div>
	</div>
	<script type="text/javascript" src="images/swiper.min.js"></script>
```
## css
```css
	.content {
		position: relative;
		width: 1110px;
		height: 67px;
		padding: 0 32px;
		box-sizing: border-box;
		margin: 20px auto;
	}
	.my-swiper {
		height: 100%;
		margin-left: 12px;
	}
	.my-swiper ul {
		margin: 0;
		padding: 0;
		list-style: none;
	}
	.swiper-item {
		width: 241px;
		margin-right: 16px;
	}
	.swiper-item a {
		display: inline-block;
		width:100%;
		height: 100%;
		overflow: hidden;
	}
	.swiper-item a img {
		width: 100%;
		height: 100%;
	}
	.swiper-btn {
		top: 0;
		margin-top: 0;
		width: 32px;
		height: 67px;
	}
	.content .swiper-button-prev {
		left: 0;
		background: #9d9d9d url(images/shouye_bg_0.png) no-repeat 7px 17px;
	}
	.content .swiper-button-next {
		right: 0;
		background: #9d9d9d url(images/shouye_bg_1.png) no-repeat 7px 17px;
	}
```
## javascript
```javascript
	$(document).ready(function() {
		var mySwiper = new Swiper(".my-swiper", {
			autoplay: { // 是否自动切换
				disableOnInteraction: false, // 操作swiper后自动切换不会停止，每次都会重新启动swiper，操作包括触碰、拖动、点击pagination等。
			},
			speed: 300, // 切换速度
			loop: true, // 循环切换
			slidesPerView: "auto", // 设置slider容器能够同时显示的slides数量.可以设置为数字（可为小数，小数不可loop），或者 'auto'则自动根据slides的宽度来设定数量。
			navigation: {
				nextEl: '.swiper-button-next',
				prevEl: '.swiper-button-prev',
			},
		});
	});
```
效果：  
![轮播图带前进后退按钮](images/effectDiagram_0.png)
# 栏目切换
## html
```html
	<div class="news-container">
		<ul class="cf list-head">
			<li class="fl news-item item-active"><a href="#">政务要闻</a></li>
			<li class="fl news-item"><a href="#">各镇动态</a></li>
			<li class="fl news-item"><a href="#">部门信息</a></li>
			<li class="fl news-item"><a href="#">媒体聚焦</a></li>
			<li class="fl news-item"><a href="#">视频新闻</a></li>
		</ul>
		<ul class="news-list">
			<li><a href="#">我县召开扶贫对象动态调整和建档立卡信息采集工.. </a><span>11-16</span></li>
		</ul>
		<ul class="hide news-list">
			<li><a href="#">我县召开扶贫对象动态调整和建档立卡信息采集工1.. </a><span>11-16</span></li>
		</ul>
		<ul class="hide news-list">
			<li><a href="#">我县召开扶贫对象动态调整和建档立卡信息采集工2.. </a><span>11-16</span></li>
		</ul>
		<ul class="hide news-list">
			<li><a href="#">我县召开扶贫对象动态调整和建档立卡信息采集工3.. </a><span>11-16</span></li>
		</ul>
		<ul class="hide news-list">
			<li><a href="#">我县召开扶贫对象动态调整和建档立卡信息采集工4.. </a><span>11-16</span></li>
		</ul>
	</div>
```
## css
```css
	.cf:after {
		display: block;
		content: "";
		height: 0;
		visibility: hidden;
		clear: both;
	}
	.cf {
		zoom: 1;
	}
	.fl {
		float: left;
	}
	.hide {
		display: none;
	}
	ul {
		padding: 0;
		margin: 0;
	}
	a {
		text-decoration: none; 
	}
	.news-container {
		width: 500px;
		height: 340px;
		overflow: hidden;
		border: 1px solid #ccc;
		margin: 20px auto;
	}
	.list-head {
		box-sizing: border-box;
		border-bottom: 1px solid #ccc;
		list-style: none;
		height: 35px;
	}
	.news-item {
		box-sizing: border-box;
		padding: 0 10px;
		height: 35px;
		line-height: 35px;
		font-size: 17px;
		color: #333;
		width: 20%;
		text-align: center;
	}
	.item-active {
		border-bottom: 1px solid #125aae;
		color: #1a5fb0;
	}
	.news-item a {
		display: inline-block;
		width: 100%;
		height: 100%;
		color: inherit;
	}
	.news-list li {
		height: 43px;
		line-height:43px;
		border-bottom: 1px solid #bfbfbf;
		padding-left: 30px;
		background: url(shouye_icon_2.png) no-repeat 14px 20px;
		font-size: 15px;
		color: #333;
		list-style: none;
	}
	.news-list li a {
		color: inherit;
	}
	.news-list li span {
		float: right;
		font-size: 13px;
		color: #999;
	}
```
```javascript
	$(document).ready(function() {
		switchNav(".news-item", "item-active", "news-list");
	});
	/**
	* 栏目导航切换
	* @param item // 鼠标滑过的项
	* @param active // 当前的项
	* @param list // 要显示的项
	*/
	function switchNav(item, active, list) {
		$(item).mouseover(function() {
			$(this).addClass(active).siblings(item).removeClass(active);
			var index = $(this).index(item);
			$(list).eq(index).removeClass("hide").siblings(list).addClass("hide");
		});
	}
```
# 滚屏
## html
```html
	<div class="page_0"></div>
	<div class="page_1"></div>
	<div class="page_2"></div>
	<div class="page_3"></div>
```
```css
	html, body { height: 100%; }
	body { margin: 0; }
	div { height: 100%; }
	.page_0 { background: #fee; }
	.page_1 { background: #efe; }
	.page_2 { background: #eef; }
	.page_3 { background: red; }
```
```javascript
	document.addEventListener("DOMContentLoaded", function() {
		var body = document.body;
		var html = document.documentElement;
		var itv;
		var height = document.body.offsetHeight;
		var page = scrollTop() / height | 0;
		// 窗口大小改变事件
		addEventListener("resize", onresize, false);
		onresize();
		// 滚轮事件
		document.body.addEventListener("onwheel" in document ? "wheel" : "mousewheel", function(e) {
			// console.log(e);
			clearTimeout(itv);
			itv = setTimeout(function() {
				var delta = e.wheelDelta / 120 || -e.deltaY / 3;
				page -= delta;
				var max = (document.body.scrollHeight / height | 0) - 1;
				if (page < 0) return page = 0;
				if (page > max) return page = max; 
				move();
			}, 100);
			e.preventDefault();
		});
		// 平滑滚动
		function move() {
			var value = height * page;
			var diff = scrollTop() - value;
			(function callee() {
				diff = diff / 1.2 | 0;
				scrollTop(value + diff);
				if (diff) itv = setTimeout(callee, 16);
			})();
		}
		// resize事件
		function onresize() {
			height = body.offsetHeight;
			move();
		};
		// 获取或设置scrollTop
		function scrollTop(v) {
			if (v == null) return Math.max(body.scrollTop, html.scrollTop);
			else body.scrollTop = html.scrollTop = v;
		}
	});
```
# 首页基本设参
```html
	<!-- 大标题 -->
	<!--subfor-->
	<h1 class="s1-title"><a href='<!--articleurl-->' title='<!--articletitle-->' target='_blank'><!--articletitleshort--></a></h1>
	<p class="s1-p">[<!--articlebrief-->]</p>
	<!--/subfor-->

	<!-- 图片新闻 -->
	<!--subfor-->
	<li class="swiper-slide"><a href="<!--articleurl-->"><img src="<!--articleimage-->"  alt=""><span><!--articletitleshort--></span></a></li>
	<!--/subfor-->

	<!-- 栏目（带链接） -->
	<!--for--><a href="<!--columnurl-->"><!--columnname--></a><!--/for-->

	<!-- 新闻列表 -->
	<!--subfor-->
	<li><a href="<!--articleurl-->" title='<!--articletitle-->' target='_blank'><!--articletitleshort--></a><span><!--month2-->-<!--day2--></span></li>
	<!--/subfor-->
```
# 文章页设参
```html
	<script language="javascript">function doZoom(size){document.getElementById('zoom').style.fontSize=size+'px';}</script>
	<!--subfor-->
	<h2 class="s2-title"><!--articlehtmltitle--></h2>
	<p class="s2-date"><span>发布日期：<!--year4-->-<!--month2-->-<!--day2--></span><span class="ml20">浏览次数：<!--articlehits-->次</span><span class="ml20">字体：【<a href='javascript:doZoom(16)'>大</a> <a href='javascript:doZoom(14)'>中</a> <a href='javascript:doZoom(12)'>小</a>】</span></p>
	<div class="s2-p" id="zoom"><!--articlecontent--></div>
	<!--if--><!--articleauthor--><p class="s2-edit">（编辑：<!--articleauthor-->）</p><!--/if-->
	<!--if--><!--articlesource--><p class="s2-edit">信息来源：<!--articlesource--></p><!--/if-->
	<div class="cf s2-share">分享到：
		<div class="bshare-custom icon-medium" style="display: inline-block;">
			<a class=bshare-qzone title=分享到QQ空间></a>
			<a class=bshare-sinaminiblog title=分享到新浪微博></a>
			<a class=bshare-renren title=分享到人人网></a>
			<a class=bshare-qqmb title=分享到腾讯微博></a>
			<a class=bshare-neteasemb title=分享到网易微博></a>
			<a class="bshare-more bshare-more-icon more-style-addthis" title=更多平台></a>
			<span class="BSHARE_COUNT bshare-share-count">0</span>
		</div>
		<script charset=utf-8 src="http://static.bshare.cn/b/buttonLite.js#style=-1&uuid=&pophcol=2&lang=zh"></script>
		<script charset=utf-8 src="http://static.bshare.cn/b/bshareC0.js"></script>
		<div class="fr s2-print">
			<a href="javascript:window.print()">【打印本页】</a>
			<a href="javascript:window.opener=null;window.open('','_self');window.close();">【关闭本页】</a>
		</div>
	</div>
	<!--if--><!--articleattach-->
	<p class="s2-download"><span class="down">[全文下载]</span><a href='<!--articleattach-->'>附件下载</a></p>
	<!--/if-->
	<p class="s2-prev"><!--articlepreviouslink--></p>
	<p class="s2-prev"><!--articlenextlink--></p>
	<!--/subfor-->
```


              
       
      
