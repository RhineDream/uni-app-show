<template>
	<view class="content">
		<uni-section title="环境创设" type="line"></uni-section>
		<view hidden>
			<block v-for="(a,b) in imgList">
				<block v-for="(item,index) in a">
					<image @load="imageLoad" :data-src="item.src" :src="item.src" mode="widthFix"></image>
				</block>
			</block>
		</view>
		<view>
			<block v-for="(item,index) in imgList1">
				<image :src="item.src" mode="widthFix" :style="`left: ${item.left}upx;top: ${item.top}upx;`"></image>
			</block>
		</view>
	</view>
</template>

<script>
	import uniSection from '@/components/uni-section/uni-section.vue'
	
	var colCount //定义列数
	var colHeightArry = [] //定义列高度数组
	var imgWidth = 375 //单张图片的宽度，可通过调整宽度显示不同列数

	colCount = parseInt(750 / imgWidth) //计算出列数，这里是两列

	for (var i = 0; i < colCount; i++) {
		colHeightArry[i] = 0
	}

	export default {
		commenuniSectionts:{
			uniSection
		},
		data() {
			return {
				title: 'Hello',
				imgList: [
					[{
						src: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg"
					}, {
						src: "https://img.cdn.aliyun.dcloud.net.cn/stream/plugin_screens/ee6f23d0-4961-11e9-af60-4f55eb065ac7_0.jpg?v=1554362136"
					}, {
						src: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg"
					}, {
						src: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg"
					}, {
						src: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg"
					}, {
						src: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg"
					}, {
						src: "https://img.cdn.aliyun.dcloud.net.cn/stream/plugin_screens/ee6f23d0-4961-11e9-af60-4f55eb065ac7_0.jpg?v=1554362136"
					}, {
						src: "https://img.cdn.aliyun.dcloud.net.cn/stream/plugin_screens/ee6f23d0-4961-11e9-af60-4f55eb065ac7_0.jpg?v=1554362136"
					}]
				],
				imgList1: []
			}
		},
		onLoad() {

		},
		onReachBottom() {
			var imgList = [{
						src: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg"
					}, {
						src: "https://img.cdn.aliyun.dcloud.net.cn/stream/plugin_screens/ee6f23d0-4961-11e9-af60-4f55eb065ac7_0.jpg?v=1554362136"
					}, {
						src: "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg"
					}]
			this.imgList.push(imgList)
		},
		methods: {
			imageLoad(e) {
				var src = e.currentTarget.dataset.src //图片地址
				var width = e.detail.width //图片宽度
				var height = e.detail.height //图片高度
				height = imgWidth * height / width //在设备上实际显示的高度
				var minValue = colHeightArry[0] //定义最小的高度
				var minIndex = 0 //定义最小高度的下标
				for (var i = 0; i < colCount; i++) {
					if (colHeightArry[i] < minValue) { //如果最小高度组数中的值小于最小值
						minValue = colHeightArry[i] //那么认为最小高度数组中的值是真正的最小值
						minIndex = i //最小下标为当前下标
					}
				}
				this.imgList1.push({
					src: src,
					left: minIndex * imgWidth,
					top: minValue
				})
				colHeightArry[minIndex] += height
			}
		}
	}
</script>

<style>
	image {
		position: absolute;
		width: 355upx;
		margin: 10upx;
	}
</style>