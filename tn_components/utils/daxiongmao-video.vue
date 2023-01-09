<template>
	<view class="components-anloading">
		<view class="uni-padding-wrap uni-common-mt">
			<view>
				<video id="myVideo" src="@/static/daxiongmao/panda-video.mp4"
					@error="videoErrorCallback" controls @fullscreenchange="fullscreenchange"></video>
			</view>		
		</view>
	</view>
</template>

<script>
	export default {
	    data() {
	        return {
	            src: '',
	            // danmuList: [{
	            //         text: '第 1s 出现的弹幕',
	            //         color: '#ff0000',
	            //         time: 1
	            //     },
	            //     {
	            //         text: '第 3s 出现的弹幕',
	            //         color: '#ff00ff',
	            //         time: 3
	            //     }
	            // ],
	            danmuValue: '',
				Custom: this.Custom
	        }
	    },
	    onReady: function(res) {
	        // #ifndef MP-ALIPAY
	        this.videoContext = uni.createVideoContext('myVideo', this)
			this.videoContext.requestFullScreen();
	        // #endif
	    },
	    methods: {
			fullscreenchange (e){
			   if(!e.detail.fullScreen){
			      this.videoContext.stop()
				  uni.navigateBack()
			   }
			},
	        sendDanmu: function() {
	            this.videoContext.sendDanmu({
	                text: this.danmuValue,
	                color: this.getRandomColor()
	            });
	            this.danmuValue = '';
	        },
	        videoErrorCallback: function(e) {
	            uni.showModal({
	                content: e.target.errMsg,
	                showCancel: false
	            })
	        },
	        getRandomColor: function() {
	            const rgb = []
	            for (let i = 0; i < 3; ++i) {
	                let color = Math.floor(Math.random() * 256).toString(16)
	                color = color.length == 1 ? '0' + color : color
	                rgb.push(color)
	            }
	            return '#' + rgb.join('')
	        }
	    }
	}
</script>

<style lang='scss' scoped>
	.components-anloading {
	  margin: 0;
	  width: 100%;
	  height: 100vh;
	  color: #fff;
	  /* background: linear-gradient(45deg, #0fd850, #f9f047); */
	  background-color: #fff;
	}
</style>