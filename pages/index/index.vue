<!-- 首页 -->
<template>
	<view>
		<view class="wrap">
			<view class="u-tabs-box">
				<u-tabs-swiper activeColor="#0081ff" ref="tabs" :list="list" :current="current" @change="change"
					:is-scroll="false" swiperWidth="750"></u-tabs-swiper>
			</view>

			<swiper class="swiper-box" :current="swiperCurrent" @transition="transition"
				@animationfinish="animationfinish">
				<swiper-item class="swiper-item" v-for="(item,index) in animals_data" :key="index">
					<scroll-view scroll-y style="height: 100%;width: 100%;">
						<image :src='item.icon' class="bg-set"></image>
						<view class="grid col-1">
							<view class="text-sl padding-xs shadow center text-white"
								style="margin-top: 70%; margin-bottom: 40%;margin-left:30%; margin-right:30%; border: solid; border-color: white; border-radius: 0; border-width: 8rpx;">
								{{item.name}}
							</view>
							<view @click="enterFile(item.key)" class="action">
								<view class="nav-btn shadow text-df center" style="margin-top:-33%;">进入</view>
							</view>
							<view class="nav-btn-underline shadow center" style="margin-top:-31%;">____</view>
						</view>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import classifyData from "@/common/item_classify_data.js";

	export default {
		data() {
			return {
				animals_data: classifyData,
				show: 1,
				current: 0,
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
				swiperCurrent: 0,
				dx: 0
			}
		},
		onLoad() {

		},
		methods: {
			enterFile(id) {
				uni.navigateTo({
					url: '../../tn_components/' + id,
					animationType: 'zoom-fade-out',
					animationDuration: 300
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
				//this.$refs.tabs.setDx(dx);
			},
			animationfinish({
				detail: {
					current
				}
			}) {
				//this.$refs.tabs.setFinishCurrent(current);
				this.swiperCurrent = current;
				this.current = current;
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

<style lang="scss" scoped>
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
		height: 100rpx;

	}
</style>
