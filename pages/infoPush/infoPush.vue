<template>
	<view class="content">
		<uni-section title="消息" type="line"></uni-section>
		<view class="example-body">
			<uni-grid :column="2" :show-border="false" :square="false" @change="change2">
				<uni-grid-item v-if="index < 2" v-for="(item ,index) in infoList" :index="index" :key="index">
					<view class="grid-item-box">
						<image class="image2" :src="item.url" mode="aspectFill" />
						<text class="text2">{{item.text}}</text>
						<!-- <view v-if="item.badge" class="grid-dot">
							<uni-badge :text="item.badge" :type="item.type" />
						</view> -->
					</view>
				</uni-grid-item>
			</uni-grid>
		</view>
		<uni-section title="常用应用" type="line"></uni-section>
		<view class="example-body">
			<uni-grid :column="3" :show-border="false" :square="false" @change="change3">
				<uni-grid-item v-if="index < 5" v-for="(item ,index) in gridList" :index="index" :key="index">
					<view class="grid-item-box">
						<image class="image2" :src="item.url" mode="aspectFill" />
						<text class="text2">{{item.text}}</text>
						<!-- <view v-if="item.badge" class="grid-dot">
							<uni-badge :text="item.badge" :type="item.type" />
						</view> -->
					</view>
				</uni-grid-item>
			</uni-grid>
		</view>
	</view>
	
</template>

<script>
	import uniSection from '@/components/uni-section/uni-section.vue'
	import uniSwiperDot from '@/components/uni-swiper-dot/uni-swiper-dot.vue'
	import uniGrid from '@/components/uni-grid/uni-grid.vue'
	import uniGridItem from '@/components/uni-grid-item/uni-grid-item.vue'
	import uniBadge from '@/components/uni-badge/uni-badge.vue'
	export default {
		components: {
			uniSection,
			uniSwiperDot,
			uniGrid,
			uniGridItem,
			uniBadge
		},
		data() {
			return {
				
				modeIndex: -1,
				styleIndex: -1,
				current: 0,
				mode: 'default',
				dotsStyles: {},
				dynamicList: [],
				infoList: [{
						url: '/static/tese.png',
						text: '家长消息',
						badge: '1',
						type: "primary"
					},
					{
						url: '/static/jzxx.png',
						text: '园长消息',
						badge: '1',
						type: "success"
					}
				],
				gridList: [{
						url: '/static/tese.png',
						text: '聊天',
						badge: '1',
						type: "primary"
					},
					{
						url: '/static/jzxx.png',
						text: '家长通讯录',
						badge: '1',
						type: "success"
					},
					{
						url: '/static/tskc.png',
						text: '回复园长',
						badge: '99',
						type: "warning"
					},
					{
						url: '/static/zxdt.png',
						text: '发布记录',
						badge: '2',
						type: "error"
					},
					{
						url: '/static/jzxx.png',
						text: '发布消息'
					} 
				]
			}
		},
		onLoad() {},
		methods: {
			change(e) {
				this.current = e.detail.current
			},
			selectStyle(index) {
				this.dotsStyles = this.dotStyle[index]
				this.styleIndex = index
			},
			selectMode(mode, index) {
				this.mode = mode
				this.modeIndex = index
				this.styleIndex = -1
				this.dotsStyles = this.dotStyle[0]
			},
			clickCard() {
				uni.showToast({
					title: '点击卡片',
					icon: 'none'
				})
			},
			change2(e) {
				let {
					index
				} = e.detail
				this.infoList[index].badge && this.infoList[index].badge++
				
				uni.showToast({
					title: `点击第${index+1}个宫格`,
					icon: 'none'
				})
				//家长聊天页面indexed-list
				if(index == 0){
					uni.navigateTo({
					    url: 'childCahtList/childCahtList'
					});
				}
			
				
			},
			change3(e) {
				let {
					index
				} = e.detail
				this.gridList[index].badge && this.gridList[index].badge++
			
				uni.showToast({
					title: `点击第${index+1}个宫格`,
					icon: 'none'
				})
			},
			add() {
				if (this.dynamicList.length < 9) {
					this.dynamicList.push({
						url: `/static/c${this.dynamicList.length+1}.png`,
						text: `Grid ${this.dynamicList.length+1}`,
						color: this.dynamicList.length % 2 === 0 ? '#f5f5f5' : "#fff"
					})
				} else {
					uni.showToast({
						title: '最多添加9个',
						icon: 'none'
					});
				}
			},
			del() {
				this.dynamicList.splice(this.dynamicList.length - 1, 1)
			}
			
		}
	}
</script>

<style>
	/* 头条小程序组件内不能引入字体 */
	/* #ifdef MP-TOUTIAO */
	@font-face {
		font-family: uniicons;
		font-weight: normal;
		font-style: normal;
		src: url('~@/static/uni.ttf') format('truetype');
	}

	/* #endif */

	/* #ifndef APP-NVUE */
	page {
		display: flex;
		flex-direction: column;
		box-sizing: border-box;
		background-color: #efeff4;
		min-height: 100%;
		height: auto;
	}

	view {
		font-size: 14px;
		line-height: inherit;
	}

	.example {
		padding: 0 15px 15px;
	}

	.example-info {
		padding: 15px;
		color: #3b4144;
		background: #ffffff;
	}

	.example-body {
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center;
		padding: 0;
		font-size: 14px;
		background-color: #ffffff;
	}

	/* #endif */
	.example {
		padding: 0 15px;
	}

	.example-info {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		padding: 15px;
		color: #3b4144;
		background-color: #ffffff;
		font-size: 14px;
		line-height: 20px;
	}

	.example-info-text {
		font-size: 14px;
		line-height: 20px;
		color: #3b4144;
	}


	.example-body {
		flex-direction: column;
		padding: 15px;
		background-color: #ffffff;
	}

	.word-btn-white {
		font-size: 18px;
		color: #FFFFFF;
	}

	.word-btn {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		align-items: center;
		justify-content: center;
		border-radius: 6px;
		height: 48px;
		margin: 15px;
		background-color: #007AFF;
	}

	.word-btn--hover {
		background-color: #4ca2ff;
	}


	.swiper-box {
		height: 200px;
	}

	.swiper-item {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background-color: #999;
		color: #fff;
	}

	.image {
		width: 750rpx;
	}

	.uni-bg-red {
		background-color: #ff5a5f;
	}

	.uni-bg-green {
		background-color: #09bb07;
	}

	.uni-bg-blue {
		background-color: #007aff;
	}

	.example-body {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		padding: 20rpx;
	}

	.example-body-item {

		flex-direction: row;
		justify-content: center;
		align-items: center;
		margin: 15rpx;
		padding: 15rpx;
		height: 60rpx;
		/* #ifndef APP-NVUE */
		display: flex;
		padding: 0 15rpx;
		/* #endif */
		flex: 1;
		border-color: #e5e5e5;
		border-style: solid;
		border-width: 1px;
		border-radius: 5px;
	}

	.example-body-item-text {
		font-size: 28rpx;
		color: #333;
	}

	.example-body-dots {
		width: 16rpx;
		height: 16rpx;
		border-radius: 50px;
		background-color: #333333;
		margin-left: 10rpx;
	}

	.active {
		border-style: solid;
		border-color: #007aff;
		border-width: 1px;
	}
	.example-body {
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center;
		padding: 0;
		font-size: 14px;
		background-color: #ffffff;
	}
	.example-body {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
		padding: 20rpx 0;
		padding-bottom: 0;
	}
	.example-body {
		flex-direction: column;
		padding: 15px;
		background-color: #ffffff;
	}
	.content-box-text {
		font-size: 12px;
		line-height: 20px;
	}
	.content-p {
		font-size: 14px;
		line-height: 20px;
	}
	.flex-item {
		width: 33.3%;
		height: 200rpx;
		text-align: center;
		line-height: 200rpx;
	}
	.example-body {
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center;
		padding: 0;
		font-size: 14px;
		background-color: #ffffff;
	}
	.example-body {
		flex-direction: column;
		padding: 15px;
		background-color: #ffffff;
	}
	.example-body {
		/* #ifndef APP-NVUE */
		display: block;
		/* #endif */
	}
	.grid-item-box {
		flex: 1;
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding: 15px 0;
	}
	.image2 {
		width: 50rpx;
		height: 50rpx;
	}
	.text2 {
		font-size: 26rpx;
		margin-top: 10rpx;
	}
	.grid-dot {
		position: absolute;
		top: 5px;
		right: 15px;
	}
</style>