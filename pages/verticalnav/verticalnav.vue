<template>
	<view>
		<!-- <view class='cu-custom'>
			<view class="cu-bar fixed bg-shadeTop" style="height:{{CustomBar}}px;padding-top:{{StatusBar}}px;">
				<navigator class='action' open-type="navigateBack" delta="1" hover-class="none">
					<text class='icon-back'></text> 返回
				</navigator>
				<view class='content' style='top:{{StatusBar}}px;'>Tab索引</view>
			</view>
		</view> -->
		<swiper class="screen-swiper round-dot" indicator-dots="true" circular="true" autoplay="true" interval="5000"
		 duration="500">
			<swiper-item v-for="(item,index) in 4" :key='index'>
				<image :src="'https://image.weilanwl.com/img/4x3-'+(index+1)+'.jpg'" mode='aspectFill'></image>
			</swiper-item>
		</swiper>
		<view class="VerticalBox">
			<scroll-view class="VerticalNav nav" scroll-y scroll-with-animation :scroll-top="VerticalNavTop" style="height:calc(100vh - 375rpx)">
				<view class="cu-item" :class="[index==TabCur?'text-green cur':'']" v-for="(item,index) in 20" :key='index'  @tap='tabSelect' :data-id="index">
					Tab{{index +1}}
				</view>
			</scroll-view>
			<scroll-view class="VerticalMain" scroll-y scroll-with-animation style="height:calc(100vh - 375rpx)"
			 :scroll-into-view="'main-id-'+TabCur" :scroll="VerticalMain">
				<view class="padding-top padding-lr" v-for="(item,index) in 20" :key='index' :id="'main-id-'+index">
					<view class='cu-bar solid-bottom bg-white'>
						<view class='action'>
							<text class='icon-title text-green'></text> Tab{{index +1}}</view>
					</view>
					<view class="cu-list menu menu-avatar">
						<view class="cu-item">
							<view class="cu-avatar round lg" style="background-image:url(https://image.weilanwl.com/img/square-1.jpg);"></view>
							<view class='content'>
								<view class='text-grey'>文晓港</view>
								<view class='text-gray text-sm'>
									<text class='icon-infofill text-red'></text> 消息未送达</view>
							</view>
							<view class='action'>
								<view class='text-grey text-xs'>22:20</view>
								<view class="cu-tag round bg-grey sm">5</view>
							</view>
						</view>
						<view class="cu-item">
							<view class="cu-avatar round lg" style="background-image:url(https://image.weilanwl.com/img/square-2.jpg);">
								<view class="cu-tag badge">99+</view>
							</view>
							<view class='content'>
								<view class='text-grey'>文晓港
									<view class="cu-tag round bg-orange sm">SVIP</view>
								</view>
								<view class='text-gray text-sm'>
									<text class='icon-redpacket_fill text-red'></text> 收到红包</view>
							</view>
							<view class='action'>
								<view class='text-grey text-xs'>22:20</view>
								<view class='icon-notice_forbid_fill text-gray'></view>
							</view>
						</view>
						<view class="cu-item ">
							<view class="cu-avatar radius lg" style="background-image:url(https://image.weilanwl.com/img/square-3.jpg);"></view>
							<view class='content'>
								<view>喵星人互动群</view>
								<view class='text-gray text-sm'>
									喵星酱：喵喵喵！</view>
							</view>
							<view class='action'>
								<view class='text-grey text-xs'>22:20</view>
								<view class="cu-tag round bg-red sm">5</view>
							</view>
						</view>
						<view class="cu-item grayscale">
							<view class="cu-avatar radius lg" style="background-image:url(https://image.weilanwl.com/img/square-3.jpg);"></view>
							<view class='content'>
								<view>喵星人互动群</view>
								<view class='text-gray text-sm'>
									喵星酱：喵喵喵！</view>
							</view>
							<view class='action'>
								<view class='text-grey text-xs'>22:20</view>
								<view class="cu-tag round bg-red sm">5</view>
							</view>
						</view>
					</view>
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				TabCur: 0,
				VerticalNavTop: 0
			};
		},
		methods: {
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id,
					this.VerticalNavTop = (e.currentTarget.dataset.id - 1) * 50
			},
			VerticalMain(e) {
				console.log(e.detail);
			}
		}
	}
</script>

<style>
	.VerticalNav.nav {
		width: 200upx;
		white-space: initial;
	}

	.VerticalNav.nav .cu-item {
		width: 100%;
		text-align: center;
		background-color: #fff;
		margin: 0;
		border: none;
		height: 50px;
		position: relative;
	}

	.VerticalNav.nav .cu-item.cur {
		background-color: #f1f1f1;
	}

	.VerticalNav.nav .cu-item.cur::after {
		content: "";
		width: 8upx;
		height: 30upx;
		border-radius: 10upx 0 0 10upx;
		position: absolute;
		background-color: currentColor;
		top: 0;
		right: 0upx;
		bottom: 0;
		margin: auto;
	}

	.VerticalBox {
		display: flex;
	}

	.VerticalMain {
		background-color: #f1f1f1;
	}
</style>
