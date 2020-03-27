<template>
	<view class="content">
		<uni-swiper-dot :info="info" :current="current" :mode="mode" :dots-styles="dotsStyles" field="content">
			<swiper class="swiper-box" @change="change">
				<swiper-item v-for="(item, index) in info" :key="index">
					<view :class="item.colorClass" class="swiper-item">
						<image class="image" :src="item.url" mode="aspectFill" />
					</view>
				</swiper-item>
			</swiper>
		</uni-swiper-dot>
		<view class="example-body">
			<uni-grid :column="4" :show-border="false" :square="false" @change="change2">
				<uni-grid-item v-if="index < 4" v-for="(item ,index) in gridList" :index="index" :key="index">
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
		<uni-section title="幼儿园简介" type="line"></uni-section>
		<view class="example-box">
			<uni-card :is-shadow="true" title="uni-app 框架" mode="style" thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg" extra="DCloud 2019-05-20 12:32:19" note="" @click="clickCard">
				<text class="content-box-text">uni-app 是一个使用 Vue.js 开发所有前端应用的框架</text>
			</uni-card>
		</view>
		<uni-section title="办园目标" type="line"></uni-section>
		
		<text class="example-info">
			管理科学规范，保教优质一流 
			环境健康宜教，家园携手共育
			使园所成为社会认可的一级一类幼儿园
		</text>
		<!-- <text class="content-p">&nbsp;&nbsp;&nbsp;&nbsp;管理科学规范，保教优质一流</text>
		<text class="content-p">&nbsp;&nbsp;&nbsp;&nbsp;环境健康宜教，家园携手共育</text>
		<text class="content-p">&nbsp;&nbsp;&nbsp;&nbsp;使园所成为社会认可的一级一类幼儿园</text> -->

		<uni-section title="教育理念" type="line"></uni-section>
		<text class="example-info">
			以陶行知“生活即教育”的教育思想为引领
			环境健康宜教，家园携手共育
			开展素质教育，让幼儿在生活实践中快乐学习
		</text>
		<!-- <text class="content-p">&nbsp;&nbsp;&nbsp;&nbsp;以陶行知“生活即教育”的教育思想为引领</text>
		<text class="content-p">&nbsp;&nbsp;&nbsp;&nbsp;环境健康宜教，家园携手共育 </text>
		<text class="content-p">&nbsp;&nbsp;&nbsp;&nbsp;开展素质教育，让幼儿在生活实践中快乐学习</text> -->

		<uni-section title="人物风采" type="line"></uni-section>
		<view class="example-box">
			<uni-card :is-shadow="true" title="优秀教师一" mode="style" thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg" 
			extra="" note="" @click="clickCard">
			</uni-card>
			<uni-card :is-shadow="true" title="优秀教师二" mode="style" thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg" 
			extra="" note="" @click="clickCard">
			</uni-card>
			<uni-card :is-shadow="true" title="优秀班级" mode="style" thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg" 
			extra="" note="" @click="clickCard">
			</uni-card>
			<uni-card :is-shadow="true" title="优秀领导团队" mode="style" thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg"
			extra="" note="" @click="clickCard">
			</uni-card>
			<uni-card :is-shadow="true" title="全体教师" mode="style" thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg"
			extra="" note="" @click="clickCard"> 
			</uni-card>
		</view>
		
		
		<uni-section title="幼儿园食谱" type="line"></uni-section>
		<text class="example-info">卡片组件通用来显示完整独立的一段信息，同时让用户理解他的作用。例如一篇文章的预览图、作者信息、时间等，卡片通常是更复杂和更详细信息的入口点。</text>
		<uni-section title="基础卡片" type="line"></uni-section>
		<view class="example-body">
			<view v-for="item in list" :key="item.id" class="example-box">
				<uni-card :title="item.title" :is-shadow="item.shadow" :note="item.note" :extra="item.extra" :thumbnail="item.thumbnail" @click="clickCard"><text class="content-box-text">{{ item.content }}</text></uni-card>
			</view>
		</view>
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
				list: [{
						id: 2,
						title: '周一',
						content: '早餐:开花奶馒头(早) 素什锦 鸡蛋炒虾皮 鲜牛奶 红富士苹果\n加餐:奶酪棒\n午餐:葡萄干米饭 清炒油麦菜 红焖狮子头 什锦鲜蔬汤\n午点:香蕉\n晚餐:咖喱鸡盖饭 虾皮小白菜汤',
						shadow: true,
						note: 'Tips',
						extra: '额外信息',
						thumbnail: ''
					}, {
						id: 3,
						title: '周二',
						content: '早餐:果仁卷 卤鸡肝 卤鸡蛋 鲜牛奶 哈密瓜\n加餐:奶酪棒\n午餐:三鲜包子 山药粥\n午点:桔子\n晚餐:米饭 宫爆肉丁 西湖牛肉羹',
						shadow: true,
						note: 'Tips',
						extra: '额外信息',
						thumbnail: ''
					},{
						id: 4,
						title: '周三',
						content: '早餐:枣荷叶饼 炸鸡柳 煮鸡蛋 鲜牛奶 香梨\n加餐:奶酪棒\n午餐:芝麻紫菜米饭 蛋烩小肉丸 一品豆腐 西红柿鸡蛋汤\n午点:哈密瓜\n晚餐:什锦炒饭(豌豆) 馄饨',
						shadow: true,
						note: 'Tips',
						extra: '额外信息',
						thumbnail: ''
					},{
						id: 5,
						title: '周四',
						content: '早餐:水果馒头 五香豆腐干 葱花炒鸡蛋 鲜牛奶 香蕉(早餐)\n加餐:奶酪棒\n午餐:紫薯双色花卷 红烧排骨 素炒圆白菜 鲜蘑豆腐汤 炒青菜\n午点:红心火龙果\n晚餐:金银米饭 炒木须肉 黄瓜紫菜柳叶汤',
						shadow: true,
						note: 'Tips',
						extra: '额外信息',
						thumbnail: ''
					},{
						id: 6,
						title: '周五',
						content: '早餐:小枣窝头 素鸡腿 五香鸡蛋 鲜牛奶 桔子\n加餐:奶酪棒\n午餐:紫米饭 西红柿炒鸡蛋 可乐鸡翅 海带豆腐菜汤\n午点:酥梨\n晚餐:肉丝茄丁卤面 菠菜粉丝汤',
						shadow: true,
						note: 'Tips',
						extra: '额外信息',
						thumbnail: '' 
					}],
					Tips: ['喜欢', '评论', '分享'],
				info: [{
						colorClass: 'uni-bg-red',
						url: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg',
						content: '内容 A'
					},
					{
						colorClass: 'uni-bg-green',
						url: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg',
						content: '内容 B'
					},
					{
						colorClass: 'uni-bg-blue',
						url: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/cbd.jpg',
						content: '内容 C'
					}
				],
				dotStyle: [{
						backgroundColor: 'rgba(0, 0, 0, .3)',
						border: '1px rgba(0, 0, 0, .3) solid',
						color: '#fff',
						selectedBackgroundColor: 'rgba(0, 0, 0, .9)',
						selectedBorder: '1px rgba(0, 0, 0, .9) solid'
					},
					{
						backgroundColor: 'rgba(255, 90, 95,0.3)',
						border: '1px rgba(255, 90, 95,0.3) solid',
						color: '#fff',
						selectedBackgroundColor: 'rgba(255, 90, 95,0.9)',
						selectedBorder: '1px rgba(255, 90, 95,0.9) solid'
					},
					{
						backgroundColor: 'rgba(83, 200, 249,0.3)',
						border: '1px rgba(83, 200, 249,0.3) solid',
						color: '#fff',
						selectedBackgroundColor: 'rgba(83, 200, 249,0.9)',
						selectedBorder: '1px rgba(83, 200, 249,0.9) solid'
					}
				],
				modeIndex: -1,
				styleIndex: -1,
				current: 0,
				mode: 'default',
				dotsStyles: {},
				dynamicList: [],
				gridList: [{
						url: '/static/tese.png',
						text: '校园特色',
						badge: '1',
						type: "primary"
					},
					{
						url: '/static/jzxx.png',
						text: '家长学校',
						badge: '1',
						type: "success"
					},
					{
						url: '/static/tskc.png',
						text: '特色课程',
						badge: '99',
						type: "warning"
					},
					{
						url: '/static/zxdt.png',
						text: '最新动态',
						badge: '2',
						type: "error"
					},
					{
						url: '/static/c5.png',
						text: 'Grid 5'
					},
					{
						url: '/static/c6.png',
						text: 'Grid 6'
					},
					{
						url: '/static/c7.png',
						text: 'Grid 7'
					},
					{
						url: '/static/c8.png',
						text: 'Grid 8'
					},
					{
						url: '/static/c9.png',
						text: 'Grid 9'
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
				this.list[index].badge && this.list[index].badge++
			
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