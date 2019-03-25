# 目录
* [轮播图（带分页器）](#轮播图带分页器)
* [轮播图（带前进后退按钮）](#轮播图带前进后退按钮)
# 轮播图（带分页器）
## html
```html   
	<link rel="stylesheet" href="images/swiper.min.css">
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
	      width: 300px;
	      height: 400px;
	      margin: 20px auto;
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
	.my-paginetion {
	      text-align: right;
	      padding-right: 52px;
	      bottom: 13px !important;
	}
	.my-pagination .swiper-pagination-bullet {
	      width: 26px;
	      height: 6px;
	      boder-radius: 0;
	      background: #fff;
	      opacity: 1;
	}
	.my-pagination .swiper-pagination-bullet-active {
	      background: #fa8d00;
	}
```
## javascript
```javascript
    $(document).ready(function() {
        var mySwiper = new Swiper("my-swiper", {
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
				       return "<span class='" + className + "'>" + (index + 1) + "</span>"
            },
        )};
   )};
```
# 轮播图（带前进后退按钮）
## html
```html
	<div class="content">
		<div class="swiper-container my-swiper">
			<ul class="swiper-wrapper">
				<li class="swiper-slide swiper-item"><a href="#"><img alt="" src="images/shouye_pic_0.png" /></a></li>
				<li class="swiper-slide swiper-item"><a href="#"><img alt="" src="images/shouye_pic_0.png" /></a></li>
			</ul>
		</div>
		<!-- 如果需要导航按钮 -->
		<div class="swiper-button-prev swiper-btn"></div>
		<div class="swiper-button-next swiper-btn"></div>
	</div>
```
## css
```css
	.content {
		position: relative;
		height: 67px;
		padding: 0 32px;
	}
	.my-swiper {
		height: 100%;
		margin-left: 12px;
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
		width: 32xp;
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
			slidePreView: "auto", // 设置slider容器能够同时显示的slides数量.可以设置为数字（可为小数，小数不可loop），或者 'auto'则自动根据slides的宽度来设定数量。
			navigation: {
				nextEl: '.swiper-button-next',
				prexEl: '.swiper-button-prec',
			},
		});
	});
```

              
       
      
