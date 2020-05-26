<template>
	<view class="content" :style="picWidth">
		<image src="../../static/bg.png" :style="picHeight" class="image"></image>
		<view class="download">
			<view class="download-body">
				<image src="../../static/logo.jpg" class="download-image"></image>
				<view class="download-text">
					<text class="download-title">Ears</text>
					<text>一分钟，找到你</text>
				</view>
				<view style="flex-grow: 1;"></view>
				<button class="download-btn" @click="toDownlaod()">下载有礼</button>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			title: 'Hello',
			picWidth: 'width:320px',
			picHeight: 'height:640px'
		};
	},
	created() {
		var w = document.documentElement.clientWidth || document.body.clientWidth;
		var h = document.documentElement.clientHeight || document.body.clientHeight;
		this.picWidth = 'width:' + w + 'px';
		this.picHeight = 'height:' + h + 'px';
		console.log(w);
	},
	onLoad() {
		var music = null;
		music = uni.createInnerAudioContext(); //创建播放器对象
		music.src = 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/audio/music.mp3'; //选择播放的音频
		music.autoplay = true;
		music.loop = true;
		music.play(); //执行播放
		console.log('4444');
		document.addEventListener(
			'WeixinJSBridgeReady',
			function() {
				music.play();
			},
			false
		);
	},
	methods: {
		toDownlaod() {
			window.open('http://www.yunshenglive.com/');
		}
	}
};
</script>

<style>
.content {
	display: flex;
}
.download-image {
	border-radius: 15rpx;
	width: 80rpx;
	height: 80rpx;
	margin-left: 20rpx;
}
.download-text {
	margin-left: 20rpx;
	display: flex;
	flex-direction: column;
	font-size: 20rpx;
	color: white;
}
.download-title {
	color: #e66465;
	font-size: 40rpx;
}
.download-body {
	background-color: #333333;
	display: flex;
	height: 100%;
	padding-top: 20rpx;
}
.download {
	z-index: 100;
	position: fixed;
	width: 100%;
	bottom: 0%;
	background-color: #fff;
	height: 120rpx;
}
.image {
	width: 100%;
}
.download-btn {
	margin-top: 20rpx;
	flex-grow: 0;
	margin-right: 20rpx;
	height: 100%;
	text-align: center;
	height: 60rpx;
	background-image: linear-gradient(#e66465, #9198e5);
	color: #ffffff;
	width: 180rpx;
	font-size: 25rpx;
	border-radius: 90rpx;
}
</style>
