<script>
	export default {
		globalData() {
			bgmMusic:""
		},
		onLaunch: function() {
			console.log('App Launch')
			uni.getSystemInfo({
				success: function(e) {
					// #ifndef MP
					Vue.prototype.StatusBar = e.statusBarHeight;
					if (e.platform == 'android') {
						Vue.prototype.CustomBar = e.statusBarHeight + 50;
					} else {
						Vue.prototype.CustomBar = e.statusBarHeight + 45;
					};
					// #endif
			
					// #ifdef MP-WEIXIN
					Vue.prototype.StatusBar = e.statusBarHeight;
					let custom = wx.getMenuButtonBoundingClientRect();
					Vue.prototype.Custom = custom;
					Vue.prototype.CustomBar = custom.bottom + custom.top - e.statusBarHeight + 4;
					// #endif		
			
					// #ifdef MP-ALIPAY
					Vue.prototype.StatusBar = e.statusBarHeight;
					Vue.prototype.CustomBar = e.statusBarHeight + e.titleBarHeight;
					// #endif
				}
			});
			//const bgmMusic = uni.createInnerAudioContext();
			this.globalData.bgmMusic = uni.createInnerAudioContext();
			this.globalData.bgmMusic.autoplay = true;//自动播放
			this.globalData.bgmMusic.loop = true;//循环播放
			this.globalData.bgmMusic.src = '/static/bgm.mp3';//背景音乐地址
			this.globalData.bgmMusic.volume = 0.3;//音量
			this.globalData.bgmMusic.onPlay(function(){
				console.log('背景音乐播放中');
			});
			this.globalData.bgmMusic.onError((res) => {
			  console.log(res.errMsg);
			  console.log(res.errCode);
			});
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	/*每个页面公共css */
	/* #ifndef APP-PLUS-NVUE */
	@import "colorui/main.css";
	@import "colorui/icon.css";
	@import "uview-ui/theme.scss";
	@import "uview-ui/index.scss";
	/* #endif*/
</style>
