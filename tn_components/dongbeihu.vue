<template>
	<view>
		<view class="wrap">
			<!-- <view class="u-tabs-box">
				<u-tabs-swiper activeColor="#0081ff" ref="tabs" :list="list" :current="current" @change="change" :is-scroll="false"
				 swiperWidth="750"></u-tabs-swiper>
			</view> -->
			
			<swiper class="swiper-box" :current="swiperCurrent" @transition="transition" @animationfinish="animationfinish">
					<!-- <swiper-item class="swiper-item" v-for="(item,index) in animals_data" :key="index">
						<scroll-view scroll-y style="height: 100%;width: 100%;">
							<image :src='item.icon' class="bg-set"></image>
							<view class="text-xl nav-btn-name shadow">
								{{item.name}}
							</view>
							<view @click="enterFile(item.key)" class="action">
								<view class="nav-btn shadow text-df">进入</view>
							</view>
							<view class="nav-btn-underline shadow">____</view>
						</scroll-view>
					</swiper-item> -->
					<!-- 第一页 -->
					<swiper-item class="swiper-item">
						<scroll-view scroll-y style="height: 100%;width: 100%;">
							<image src='@/static/animal_icon/dongbeihu.jpg' class="bg-set" mode="top left"></image>
							<!-- 图片展示 -->
							<view class="grid col-1" style="margin-left: 15%;margin-top: 10%;">
								<view class="padding-xs text-sl text-blue">
									对话
								</view>
								<view class="text-df">__________________________</view>
							</view>
							<view class="grid col-2">
								<view class="padding-xl"></view>
								<view class="padding-xl"></view>								
								<view class="bg-img padding-bottom-xl" style="background-color: transparent;background-image: url('../static/dongbeihu/dongbeihu-1-1.jpg'); background-size:80% 80%;height: 250upx;"></view>
								<view class="bg-img padding-top-xl flex align-end" style="background-color: transparent;background-image: url('../static/dongbeihu/dongbeihu-1-2.jpg'); background-size:80% 80%;height: 250upx;"></view>
								<view class="padding-xl"></view>
								<view class="padding-xl"></view>								
								<view class="bg-img padding-bottom-xl" style="background-color: transparent;background-image: url('../static/dongbeihu/dongbeihu-1-3.jpg'); background-size:80% 80%;height: 250upx;"></view>
								<view class="bg-img padding-top-xl flex align-end" style="background-color: transparent;background-image: url('../static/dongbeihu/dongbeihu-1-4.jpg'); background-size:80% 80%;height: 250upx;"></view>
								<view class="padding-xl"></view>
								<view class="padding-xl"></view>								
								<view class="bg-img padding-bottom-xl" style="background-color: transparent;background-image: url('../static/dongbeihu/dongbeihu-1-5.jpg'); background-size:80% 80%;height: 250upx;"></view>
								<view class="bg-img padding-top-xl flex align-end" style="background-color: transparent;background-image: url('../static/dongbeihu/dongbeihu-1-6.jpg'); background-size:80% 80%;height: 250upx;"></view>
							</view>
						</scroll-view>
						
					</swiper-item>
					<swiper-item class="swiper-item">
						<scroll-view scroll-y style="height: 100%;width: 100%;">
							<image src='@/static/animal_icon/dongbeihu.jpg' class="bg-set" mode="top"></image>
							<!-- 物种属性 -->
							
							<view class="grid col-1" style="margin-left: 15%;margin-top: 10%;">
								<view class="padding-xs text-sl text-blue">
									东北虎
								</view>
								<view class="text-df">__________________________</view>
								<view class="padding-xs text-df text-black">
									保护状况
								</view>
								<view class="padding-xs text-sl text-black">
									濒危
								</view>
								<view class="text-df">__________________________</view>
								<view class="padding-xs text-df text-black">
									野生总数
								</view>
								<view class="padding-xs text-sl text-black">
									500左右
								</view>
								<view class="text-df">__________________________</view>
								<view class="padding-xs text-df text-black">
									栖息地
								</view>
								<view class="padding-xs text-sl text-black">
									俄罗斯远东地区、中国长白山地区、朝鲜
								</view>
								<view class="text-df">__________________________</view>
								<view class="padding-xs text-df text-black">
									体重（千克）
								</view>
								<view class="padding-xs text-sl text-black">
									170-250
								</view>
								<view class="text-df">__________________________</view>
								<view class="padding-xs text-df text-black">
									体长（米）
								</view>
								<view class="padding-xs text-sl text-black">
									2.0-2.3
								</view>
								<view class="text-df">__________________________</view>
							</view>
							
						</scroll-view>
					</swiper-item>
					<swiper-item class="swiper-item">
						<scroll-view scroll-y style="height: 100%;width: 100%;">
							<image src='@/static/animal_icon/dongbeihu.jpg' class="bg-set" mode="top right"></image>
							<!-- 生存危机 -->
							<view class="grid col-1" style="margin-left: 15%;margin-top: 10%;">
								<view class="padding-xs text-sl text-blue">
									威胁
								</view>
								<view class="text-df">__________________________</view>
							</view>
							<swiper class="swiper-box" :current="swiperCurrent1" @transition="transition" @animationfinish="animationfinish1">
								<swiper-item class="swiper-item" style="width: 100%;height: 30%;">
									<view class="center text-xsl">
										<text class="cuIcon-back text-white"></text>
									</view>
								</swiper-item>
								<swiper-item class="swiper-item" style="width: 100%;height: 30%;">
									<view class="grid col-2 center" style="margin-right: 10%;">
										<view class="text-xxl center" style="color: rgb(129, 40, 49);">
											<view class="text-sl">
												<text class="cuIcon-homefill"></text>
											</view>
											<text>捕杀</text>
											<view class="text-xl text-black">______________</view>
										</view>
										<view class="flex align-end text-lg text-black center">
											东北虎的经济价值极高，肉和内脏可入药治疗多种慢性疾病，正因为这样，东北虎遭到无情的捕杀。
										</view>
									</view>
								</swiper-item>
							</swiper>
							<view class="padding-sm"></view>
							<view class="padding-sm"></view>	
							<swiper class="swiper-box" :current="swiperCurrent2" @transition="transition" @animationfinish="animationfinish2">
								<swiper-item class="swiper-item" style="width: 100%;height: 30%;">
									<view class="center text-xsl">
										<text class="cuIcon-back text-white"></text>
									</view>
								</swiper-item>
								<swiper-item class="swiper-item" style="width: 100%;height: 30%;">
									<view class="grid col-2 center" style="margin-right: 10%;">
										<view class="text-xxl center" style="color: rgb(129, 40, 49);">
											
											<view class="text-sl">
												<text class="cuIcon-group"></text>
											</view>
											<text>栖息地破坏</text>
											<view class="text-xl text-black">______________</view>
										</view>
										<view class="flex align-end text-lg text-black center">
											滥砍滥伐森林，乱捕乱杀野生动物，严重地破坏生态平衡，也是造成东北虎濒临灭绝的另一个重要原因。
										</view>
									</view>
								</swiper-item>
							</swiper>
							<view class="padding-sm"></view>
							<view class="padding-sm"></view>	
							<swiper class="swiper-box" :current="swiperCurrent3" @transition="transition" @animationfinish="animationfinish3">
								<swiper-item class="swiper-item" style="width: 100%;height: 30%;">
									<view class="center text-xsl">
										<text class="cuIcon-back text-white"></text>
									</view>
								</swiper-item>
								<swiper-item class="swiper-item" style="width: 100%;height: 30%;">
									<view class="grid col-2 center" style="margin-right: 10%;">
										<view class="text-xxl center" style="color: rgb(129, 40, 49);">
											
											<view class="text-sl">
												<text class="cuIcon-bad"></text>
											</view>
											<text>人类活动影响</text>
											<view class="text-xl text-black">______________</view>
										</view>
										<view class="flex align-end text-lg text-black center">
											随着人类社会的发展，人类对生态的干扰越来越激烈，不仅仅是破坏，同时也使得生态系统质量降低，使得很多的地区在现存的一些森林里面，东北虎没有足够的猎物。
										</view>
									</view>
								</swiper-item>
							</swiper>
						</scroll-view>
					</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				show: 1,
				list: [{
						name: 'UI设计'
					},
					{
						name: '小程序/App'
					},
					{
						name: '网站开发'
					}
				],
				current: 0,
				swiperCurrent: 0,
				current1: 0,
				swiperCurrent1: 0,
				current2: 0,
				swiperCurrent2: 0,
				current3: 0,
				swiperCurrent3: 0,
				dx: 0,
				MusicOn: "True"
			}
		},
		onLoad() {
	
		},
		onNavigationBarButtonTap(e) {
			var webView = this.$mp.page.$getAppWebview();
			console.log(this.MusicOn)
			if(this.MusicOn == "True") {
				this.MusicOn = "False";
				//titleNView.buttons[0].color == "rgb(144,147,153)";
				webView.setTitleNViewButtonStyle(0,{
					"fontSize": "20px",
					"fontSrc": "/static/fontsrc/iconfont.ttf",
					"text": "\ue657",
					"color": "#909399"
				});
				this.bgmMusic = getApp().globalData.bgmMusic;
				this.bgmMusic.pause();
				this.bgmMusic.onPause(()=>{
				console.log('背景音乐停止');
				});
				
			} else {
				this.MusicOn = "True";
				//titleNView.buttons[0].color == "rgb(0,129,255)";
				webView.setTitleNViewButtonStyle(0,{
					"fontSize": "20px",
					"fontSrc": "/static/fontsrc/iconfont.ttf",
					"text": "\ue657",
					"color": "#0081FF"
				});
				this.bgmMusic = getApp().globalData.bgmMusic;
				this.bgmMusic.play();
				this.bgmMusic.onPlay(()=>{
				console.log('背景音乐恢复播放');
				});
			}
		},
		methods: {
			enterFile(id) {
				uni.navigateTo({
					url: '../../tn_components/' + id
				});
			},
			// tab栏切换
			change(index) {
				this.swiperCurrent = index;
			},
			transition({
				detail: {
					dx
				}
			}) {
				// this.$refs.tabs.setDx(dx);
			},
			animationfinish({
				detail: {
					current
				}
			}) {
				
				this.swiperCurrent = current;
				this.current = current;
			},
			animationfinish1({
				detail: {
					current1
				}
			}) {
				
				this.swiperCurrent1 = current1;
				this.current1 = current1;
			},
			animationfinish2({
				detail: {
					current2
				}
			}) {
				
				this.swiperCurrent2 = current2;
				this.current2 = current2;
			},
			animationfinish3({
				detail: {
					current3
				}
			}) {
				
				this.swiperCurrent3 = current3;
				this.current3 = current3;
			}
		}
	}
</script>

<style lang="scss" scoped>
	/* #ifndef H5 */
	page {
		height: 100%;
		background-color: #f2f2f2;
	}

	/* #endif */
</style>

<style lang='scss'>
	.center {
		height: 100%;
		flex: auto;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
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
	.bg-set-1 {
		position: fixed;
		width: 100%;
		height: 100%;
		background-position: 40% auto cover;
		z-index: -1;
	}
	.bg-set-2 {
		position: fixed;
		width: 100%;
		height: 100%;
		background-size: 40% auto cover;
		z-index: -1;
	}
	.bg-set {
		position: fixed;
		width: 100%;
		height: 100%;
		top: 0;
		left: 0;
		z-index: -1;
	}
	.nav-btn {
		width: 200rpx;
		height: 60rpx;
		margin: 8rpx auto;
		text-align: center;
		line-height: 1000rpx;
		border-radius: 10rpx;
		color: white;
		//text-decoration: underline;
	}
	.nav-btn-underline {
		width: 200rpx;
		height: 60rpx;
		margin: 8rpx auto;
		text-align: center;
		line-height: 880rpx;
		border-radius: 10rpx;
		color: white;
		font-size: 25rpx;
		text-decoration: underline;
	}
	.nav-btn-name {
		// display: block;
		// text-align: center;
		// border-style: solid;
		// border-color: white;
		// border-width: 10rpx;
		// border-radius: 0;
		
		// width: 40%;
		// padding: 7rpx;
		width: 200rpx;
		height: 60rpx;
		margin: 8rpx auto;
		text-align: center;
		line-height: 1000rpx;
		border-radius: 10rpx;
		color: white;		
	}
	.cu-timeline .cu-time {
		width: 100%;
		text-align: left;
		padding: 20rpx 0 20rpx 37rpx;
		font-size: 26rpx;
		color: #888;
		display: block;
	}
	
	.text-red,
	.line-red,
	.lines-red {
		color: #FF3434;
	}
	
	.margin-avatar {
		margin-left: -15rpx;
	}
	
	.margin-avatar-bottom {
		margin-bottom: 150rpx;
	}
	
	.line-blue-tuniao::after {
		border-color: #0070ff !important;
		color: #0070ff;
	}
	
	.resume {
		/* background: #f1f1f1; */
		padding-top: 10rpx;
		border-radius: 6rpx;
		display: block;
		color: #666;
		line-height: 1.6;
	}
	
	.resume+.resume {
		margin-top: 20rpx;
	}
	
	.resume2 {
		padding-top: 10rpx;
		border-radius: 6rpx;
		display: block;
		color: #666;
		line-height: 1.6;
	}
	
	.edit {
		position: fixed;
		width: 100rpx;
		height: 100rpx;
		bottom: 250rpx;
		right: 30rpx;
		z-index: 1;
		opacity: 0.8;
		border: 1px solid #189eff;
		border-radius: 100rpx;
		box-shadow: 0rpx 0rpx 6rpx rgba(24, 158, 255, 1);
		padding: 20rpx;
	}
	
	.love {
		position: fixed;
		width: 100rpx;
		height: 100rpx;
		bottom: 550rpx;
		right: 30rpx;
		z-index: 1024;
		opacity: 0.8;
		border: 1px solid #189eff;
		border-radius: 100rpx;
		box-shadow: 0rpx 0rpx 6rpx rgba(24, 158, 255, 1);
		padding: 20rpx;
	}
	
	.bg-img-cont {
		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;
		height: 350rpx;
	}
	
	.share-png {
		width: 100rpx;
		height: 100rpx;
		margin: 0 auto;
	}
	
	.share-wechat {
		width: 35rpx;
		height: 35rpx;
		margin: 0 10rpx -4rpx 0;
		opacity: 0.5;
	}
	
	.button-no::after {
		border: none;
	}
	
	.title-pyq {
		background-image: -webkit-linear-gradient(0deg, #1b6cff, #1ca5ff);
		/*1B6CFF 1B42FF*/
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		opacity: 0.5;
	}
	
	.edit-fixed {
		position: fixed;
		width: 100%;
		bottom: 0;
		z-index: 1024;
		box-shadow: 0 1rpx 6rpx rgba(0, 0, 0, 0.1);
	}
	
	.button-no {
		border: none;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0);
	}
	
	.centre {
		text-align: center;
		margin: 200rpx auto;
		font-size: 32rpx;
	
		image {
			width: 300rpx;
			border-radius: 50%;
			margin: 0 auto;
		}
	
		.tips {
			font-size: 24rpx;
			color: #999999;
			margin-top: 20rpx;
		}
	
		.btn {
			margin: 80rpx auto;
			width: 200rpx;
			border-radius: 32rpx;
			line-height: 64rpx;
			color: #ffffff;
			font-size: 26rpx;
			background: linear-gradient(270deg, #1cbbb4 0%, #0081ff 100%);
		}
	}
	
	.wrap {
		display: flex;
		flex-direction: column;
		height: calc(100vh - var(--window-top));
		width: 100%;
	}
	
	.swiper-box {
		flex: 1;
	}
	
	.swiper-item {
		height: 100%;
	}
</style>