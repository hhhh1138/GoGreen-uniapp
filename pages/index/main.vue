<!-- 导航页 -->
<template>
	<view class="u-wrap">
		<!-- top background -->
		<view style="margin-top:-50rpx;height: 156rpx; position: relative;margin-bottom: 80rpx;">
			<image src='https://zhoukaiwen.com/img/wccQQP.png' mode='widthFix' class='png' style='width:100%;height:156rpx'></image>
		</view>
		<view class="u-menu-wrap">
			<scroll-view scroll-y scroll-with-animation class="u-tab-view menu-scroll-view" :scroll-top="scrollTop">
				<view v-for="(item,index) in tabbar" :key="index" class="u-tab-item" :class="[current==index ? 'u-tab-item-active' : '']"
				 :data-current="index" @tap.stop="swichMenu(index)">
					<text class="u-line-1">{{item.name}}</text>
				</view>
			</scroll-view>
			<block v-for="(item,index) in tabbar" :key="index">
				<scroll-view scroll-y class="right-box" v-if="current==index">
					<view class="page-view">
						<view class="class-item">
							<!-- <view class="item-title text-center">
								<text>{{item.name}}</text>
							</view> -->
							<view class="item-container">
								<!-- <view class='nav-list margin-top'> -->
<!-- 									<navigator open-type="navigate" hover-class='none' :url="'/tn_components/' + item.title"
										:class="'nav-li bg-kuxuan' + (index+1)" v-for="(item, index) in kuxuan" :key="index">
										<view class="nav-name">{{item.name}}</view>
									</navigator> -->
									<navigator open-type="navigate" hover-class='none' :url="'/tn_components/' + item1.key"
										class="thumb-box" v-for="(item1, index1) in item.foods" :key="index1">
										<image class="item-menu-image" :src="item1.icon" mode=""></image>
										<view class="item-menu-name margin-top-sm">{{item1.name}}</view>
									</navigator>
								<!-- </view> -->
								
<!-- 								<view class="thumb-box" v-for="(item1, index1) in item.foods" :key="index1">
									<image class="item-menu-image" :src="item1.icon" mode=""></image>
									<view class="item-menu-name margin-top-sm">{{item1.name}}</view>
								</view> -->
								
							</view>
						</view>
					</view>
				</scroll-view>
			</block>
		</view>
	</view>
</template>

<script>
	import classifyData from "@/common/animals_classify_data.js";
	export default {
		data() {
			return {
				tabbar: classifyData,
				scrollTop: 0, //tab标题的滚动条位置
				current: 0, // 预设当前项的值
				menuHeight: 0, // 左边菜单的高度
				menuItemHeight: 0, // 左边菜单item的高度
			}
		},
		onLoad() {

		},
		methods: {
			getImg() {
				return Math.floor(Math.random() * 35);
			},
			// 点击左边的栏目切换
			async swichMenu(index) {
				if(index == this.current) return ;
				this.current = index;
				// 如果为0，意味着尚未初始化
				if(this.menuHeight == 0 || this.menuItemHeight == 0) {
					await this.getElRect('menu-scroll-view', 'menuHeight');
					await this.getElRect('u-tab-item', 'menuItemHeight');
				}
				// 将菜单菜单活动item垂直居中
				this.scrollTop = index * this.menuItemHeight + this.menuItemHeight / 2 - this.menuHeight / 2;
			},
			// 获取一个目标元素的高度
			getElRect(elClass, dataVal) {
				new Promise((resolve, reject) => {
					const query = uni.createSelectorQuery().in(this);
					query.select('.' + elClass).fields({size: true},res => {
						// 如果节点尚未生成，res值为null，循环调用执行
						if(!res) {
							setTimeout(() => {
								this.getElRect(elClass);
							}, 10);
							return ;
						}
						this[dataVal] = res.height;
					}).exec();
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.card-swiper {
		  height: 550upx !important;
		}
		
		.card-swiper swiper-item {
		  width: 260upx !important;
		  left: 245upx;	
		  box-sizing: border-box;
		  padding: 0upx 15upx 50upx 15upx;
		  overflow: initial;
		  /* margin: 100rpx 0; */
		}
		
		.card-swiper swiper-item .swiper-item {
		  width: 100%;
		  display: block;
		  height: 100%;
		  border-radius: 10upx;
		  transform: scale(0.7);
		  transition: all 0.2s ease-in 0s;
		  overflow: hidden;
		}
		
		.card-swiper swiper-item.cur .swiper-item {
		  transform: none;
		  transition: all 0.2s ease-in 0s;
		}
		.bg-top-blue {
			background-image: linear-gradient(135deg, #52B5FC, #746BFE);
			color: #fff;
		}
	
		.nav-list {
			display: flex;
			flex-wrap: wrap;
			padding: 0px 40upx 0px;
			justify-content: space-between;
		}
	
		.nav-li {
			padding: 30upx;
			border-radius: 12upx;
			width: 45%;
			margin: 0 2.5% 40upx;
			background-image: url(https://s1.ax1x.com/2020/06/27/NyU04x.png);
			background-size: cover;
			background-position: center;
			position: relative;
			z-index: 1;
		}
	
		.nav-li::after {
			content: "";
			position: absolute;
			z-index: -1;
			background-color: inherit;
			width: 100%;
			height: 100%;
			left: 0;
			bottom: -10%;
			border-radius: 10upx;
			opacity: 0.2;
			transform: scale(0.9, 0.9);
		}
	
		.nav-li.cur {
			color: #fff;
			background: rgb(94, 185, 94);
			box-shadow: 4upx 4upx 6upx rgba(94, 185, 94, 0.4);
		}
	
		.nav-title {
			font-size: 32upx;
			font-weight: 300;
		}
	
		.nav-title::first-letter {
			font-size: 40upx;
			margin-right: 4upx;
		}
	
		.nav-name {
			font-size: 28upx;
			text-transform: Capitalize;
			margin-top: 20upx;
			position: relative;
		}
	
		.nav-name::before {
			content: "";
			position: absolute;
			display: block;
			width: 40upx;
			height: 6upx;
			background: #fff;
			bottom: 0;
			right: 0;
			opacity: 0.5;
		}
	
		.nav-name::after {
			content: "";
			position: absolute;
			display: block;
			width: 100upx;
			height: 1px;
			background: #fff;
			bottom: 0;
			right: 40upx;
			opacity: 0.3;
		}
	
		.nav-name::first-letter {
			font-weight: bold;
			font-size: 36upx;
			margin-right: 1px;
		}
	
		.nav-li text {
			position: absolute;
			right: 30upx;
			top: 30upx;
			font-size: 52upx;
			width: 60upx;
			height: 60upx;
			text-align: center;
			line-height: 60upx;
		}
	
		.text-light {
			font-weight: 300;
		}
	
		@keyframes show {
			0% {
				transform: translateY(-50px);
			}
	
			60% {
				transform: translateY(40upx);
			}
	
			100% {
				transform: translateY(0px);
			}
		}
	
		@-webkit-keyframes show {
			0% {
				transform: translateY(-50px);
			}
	
			60% {
				transform: translateY(40upx);
			}
	
			100% {
				transform: translateY(0px);
			}
		}
	
		/* 
	2f9bfe 主色蓝
	189eff 配色蓝
	
	0081ff--0070FF 蓝
	CCE6FF--E5F1FF 淡蓝
	39B54A--7FD02B 绿
	D7F0DB--EAF8F5 淡绿
	FBBD08--FFD627 黄
	f37b1d--F39902 橙
	FEF2CE--FEF6E9 淡橙
	1CBBB4--19CF8A 青
	E03997--FF4F94 粉
	8dc63f--9ddb47 橄榄绿
	e54d42--ff3434 红
	a5673f--7F2D00 棕
	6739b6--6F68DF 蓝紫
	*/
		.banner-index {
			width: 100%;
			padding: 0 0rpx;
			height: 220rpx;
		}
	
		.title-header {
			display: flex;
			height: 120rpx;
			font-size: 40rpx;
			align-items: center;
			justify-content: center;
			/* padding: 40rpx 0 0 0; */
			font-weight: bold;
			background-image: url(https://s1.ax1x.com/2020/09/16/wccswF.png);
			background-size: cover;
		}
	
		.radius-index {
			overflow: hidden;
			border-radius: 10rpx;
		}
	
		.bg-top {
			background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0));
			color: #fff;
		}
	
		.tn-btn {
			height: 100%;
			width: 110%;
			line-height: 30rpx;
			background: transparent;
		}
	
		.tn-btn::after {
			border-color: transparent;
		}
	
		.tn-bg {
			position: fixed;
			width: 100%;
			z-index: -1
		}
	
		.tn-bg-cart {
			/* position: fixed; */
			width: 100%;
			z-index: -1
		}
	
		.bg-gradual-index {
			/* background-image: linear-gradient(45deg, #ff9700, #ed1c24); */
			background-image: linear-gradient(45deg, #1CA5FF, #1B6CFF);
			color: #fff;
		}
	
		.tn-align {
			text-align: justify;
		}
	
		.opacity-a {
			opacity: 0.4
		}
	
		.strip-bottom {
			/* background: #F2F3F9; */
			width: 100%;
			border-bottom: 20rpx solid rgba(241, 241, 241, 0.8);
		}
	
		.name-title-a {
			-webkit-line-clamp: 1;
			display: -webkit-box;
			-webkit-box-orient: vertical;
			text-overflow: ellipsis;
			overflow: hidden;
		}
	
		.name-title-b {
			-webkit-line-clamp: 2;
			display: -webkit-box;
			-webkit-box-orient: vertical;
			text-overflow: ellipsis;
			overflow: hidden;
		}
	
		.tn-footerfixed {
			position: fixed;
			width: 100%;
			bottom: 0;
			z-index: 1024;
			box-shadow: 0 1rpx 6rpx rgba(0, 0, 0, 0.35);
		}
	
		.tn-border {
			border-top: solid #F3F3F3 20rpx;
		}
	
		.tn-bg-color {
			background-color: #F3F3F3;
		}
	
		.text-shop-active {
			/* color: #ff8b00 */
			/* background-image: -webkit-linear-gradient(45deg, #ff7612, #ff571c); */
			background-image: -webkit-linear-gradient(180deg, #ff3434, #ff8a34);
			-webkit-background-clip: text;
			-webkit-text-fill-color: transparent;
		}
	
		.title-text {
			background-image: -webkit-linear-gradient(0deg, #ff8a34, #FBBD12);
			-webkit-background-clip: text;
			-webkit-text-fill-color: transparent;
			/* border:10px solid #ddd;
	    border-image: -webkit-linear-gradient(red,yellow);
	   	border-image: -moz-linear-gradient(red,yellow);
	    border-image: linear-gradient(red,yellow);  */
		}
	
		.title-index {
			background-image: -webkit-linear-gradient(0deg, #000, #FBBD12);
			-webkit-background-clip: text;
			-webkit-text-fill-color: transparent;
		}
	
		.text-shop-no {
			color: #aaaaaa
		}
	
		.search-round {
			border-radius: 5000rpx;
			/* border-top-right-radius: 20rpx; */
			border-bottom-left-radius: 20rpx
		}
	
		.shadowimport {
			box-shadow: 0 1rpx 6rpx rgba(0, 0, 0, 0.1) !important;
		}
	
		/* 标签 */
	
		.bg-label1.light {
			color: #ff3434;
			background: #fadbd9;
		}
	
		.bg-label2.light {
			color: #7fd02b;
			background: #eaf8f5;
		}
	
		.bg-label3.light {
			color: #0070ff;
			background: #e5f1ff;
		}
	
		.bg-label4.light {
			color: #9ddb47;
			background: #e8f4d9;
		}
	
		.bg-label5.light {
			color: #f39902;
			background: #fde6d2;
		}
	
		.bg-label6.light {
			color: #7f2d00;
			background: #ede1d9;
		}
	
		.bg-label7.light {
			color: #ff4f94;
			background: #f9d7ea;
		}
	
		.bg-label8.light {
			color: #6f68df;
			background: #e1d7f0;
		}
	
		.bg-label9.light {
			color: #9c26b0;
			background: #ebd4ef;
		}
	
		.bg-label10.light {
			color: #19cf8a;
			background: #d2f1f0;
		}
	
		.bg-label11.light {
			color: #8799a3;
			background: #e7ebed;
		}
	
	
		.bg-index1 {
			background-color: #F33F5A;
			color: #fff;
		}
	
		.bg-index2 {
			background-color: #954FF6;
			color: #fff;
		}
	
		.bg-index3 {
			background-color: #5177EE;
			color: #fff;
		}
	
		.bg-index4 {
			background-color: #FFC32E;
			color: #fff;
		}
	
		.bg-index5 {
			background-color: #FF4F94;
			color: #fff;
		}
	
		.bg-index6 {
			background-color: #0acffe;
			color: #fff;
		}
	
		/*  */
		.bg-exper1 {
			background-color: #FF4F94;
			color: #fff;
		}
	
		.bg-exper2 {
			background-color: #006FFF;
			color: #fff;
		}
	
		.bg-exper3 {
			background-color: #19D08B;
			color: #fff;
		}
	
		.bg-exper4 {
			background-color: #F49A02;
			color: #fff;
		}
	
		.bg-exper5 {
			background-color: #1cbbb4;
			color: #fff;
		}
		.bg-exper6 {
			background-color: #9c26b0;
			color: #fff;
		}
		.bg-exper7 {
			background-color: #8799a3;
			color: #fff;
		}
		.bg-exper8 {
			background-color: #00c4fb;
			color: #fff;
		}
		.bg-exper9 {
			color: #fff;
			background-color: #FFC32E;
		}
		.bg-exper10 {
			color: #fff;
			background-color: #a5673f;
		}
		.bg-exper11 {
			background-color: #BC78EC;
			color: #fff;
		}
		.bg-exper12 {
			background-color: #8DC63F;
			color: #fff;
		}
		.bg-exper13 {
			color: #fff;
			background-color: #ff3434;
		}
		.bg-exper14 {
			color: #fff;
			background-color: #FF4F94;
		}
	
		/*  */
		.bg-kuxuan1 {
			background-color: #FF5656;
			color: #fff;
		}
	
		.bg-kuxuan2 {
			background-color: #6F68DF;
			color: #fff;
		}
	
		.bg-kuxuan3 {
			background-color: #9c26b0;
			color: #fff;
		}
	
		.bg-kuxuan4 {
			background-color: #0070FF;
			color: #fff;
		}
	
		.bg-kuxuan5 {
			background-color: #1cbbb4;
			color: #fff;
		}
	
		.bg-kuxuan6 {
			background-color: #BC78EC;
			color: #fff;
		}
	
		.bg-kuxuan7 {
			background-color: #f39902;
			color: #fff;
		}
	
		.bg-kuxuan8 {
			color: #fff;
			background-color: #19CF8A;
		}
	
		.bg-kuxuan9 {
			color: #fff;
			background-color: #8799a3;
		}
	
		.bg-kuxuan10 {
			color: #fff;
			background-color: #0396FF;
		}
	
		.bg-kuxuan11 {
			color: #fff;
			background-color: #00c4fb;
		}
	
		.bg-kuxuan12 {
			color: #fff;
			background-color: #FFC32E;
		}
	
		.bg-kuxuan13 {
			color: #fff;
			background-color: #a5673f;
		}
		.bg-kuxuan14 {
			color: #fff;
			background-color: #FF4F94;
		}
		.bg-kuxuan15 {
			color: #fff;
			background-color: #8DC63F;
		}
	.u-wrap {
		height: calc(100vh);
		/* #ifdef H5 */
		height: calc(100vh - var(--window-top));
		/* #endif */
		display: flex;
		flex-direction: column;
	}
	
	.u-search-box {
		padding: 18rpx 30rpx;
	}
	
	.u-menu-wrap {
		flex: 1;
		display: flex;
		overflow: hidden;
	}
	
	.u-search-inner {
		background-color: rgb(234, 234, 234);
		border-radius: 100rpx;
		display: flex;
		align-items: center;
		padding: 10rpx 16rpx;
	}
	
	.u-search-text {
		font-size: 26rpx;
		color: $u-tips-color;
		margin-left: 10rpx;
	}
	
	.u-tab-view {
		width: 200rpx;
		height: 100%;
	}
	
	.u-tab-item {
		height: 110rpx;
		background: #f6f6f6;
		box-sizing: border-box;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 26rpx;
		color: #444;
		font-weight: 400;
		line-height: 1;
	}
	
	.u-tab-item-active {
		position: relative;
		color: #000;
		font-size: 30rpx;
		font-weight: 600;
		background: #fff;
	}
	
	.u-tab-item-active::before {
		content: "";
		position: absolute;
		border-left: 4px solid $u-type-primary;
		height: 32rpx;
		left: 0;
		top: 39rpx;
	}
	
	.u-tab-view {
		height: 100%;
	}
	
	.right-box {
		background-color: rgb(250, 250, 250);
	}
	
	.page-view {
		padding: 16rpx;
	}
	
	.class-item {
		margin-bottom: 30rpx;
		background-color: #fff;
		padding: 16rpx;
		border-radius: 8rpx;
	}
	
	.item-title {
		font-size: 30rpx;
		color: $u-main-color;
		font-weight: bold;
		margin: 10rpx 0;
	}
	
	.item-menu-name {
		font-weight: normal;
		font-size: 24rpx;
		color: $u-main-color;
	}
	
	.item-container {
		display: flex;
		flex-wrap: wrap;
	}
	
	.thumb-box {
		width: 33.333333%;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		margin-top: 20rpx;
		margin-bottom: 10rpx;
	}
	
	.item-menu-image {
		width: 120rpx;
		height: 120rpx;
		border-radius: 100rpx;
	}
</style>
