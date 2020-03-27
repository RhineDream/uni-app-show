<template>
	<view>
		<page-head title="登录"></page-head>
		<view class="uni-padding-wrap uni-common-mt">
			<form @submit="formSubmit" @reset="formReset">
				<view class="uni-form-item uni-column">
					<!-- <view class="title">账号</view> -->
					<input class="uni-input" name="nickname" placeholder="请输入账号" />
				</view>
				<view class="uni-form-item uni-column">
				    <!-- <view class="title"><text class="uni-form-item__title">可查看密码的输入框</text></view> -->
				    <view class="uni-input-wrapper">
				        <input class="uni-input" placeholder="请输入密码" :password="showPassword" />
				        <text class="uni-icon" :class="[!showPassword ? 'uni-eye-active' : '']" @click="changePassword">&#xe568;</text>
				    </view>
				</view>
				
				<view class="uni-btn-v">
					<button form-type="submit">登录</button>
					<button type="default" form-type="reset">重置</button>
				</view>
			</form>
		</view>
	</view>
</template>
<script>
	var  graceChecker = require("../../../common/graceChecker.js");
	export default {
		data() {
			return {
				showPassword: true,
			}
		},
		methods: {
			formSubmit: function(e) {
				console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
                //定义表单规则
                var rule = [
                    {name:"nickname", checkType : "string", checkRule:"1,3",  errorMsg:"姓名应为1-3个字符"},
                    {name:"gender", checkType : "in", checkRule:"男,女",  errorMsg:"请选择性别"},
                    {name:"loves", checkType : "notnull", checkRule:"",  errorMsg:"请选择爱好"}
                ];
                //进行表单检查
                var formData = e.detail.value;
                var checkRes = graceChecker.check(formData, rule);
                if(checkRes){
                    uni.showToast({title:"验证通过!", icon:"none"});
                }else{
                    uni.showToast({ title: graceChecker.error, icon: "none" });
                }
			},
			formReset: function(e) {
				console.log('清空数据')
			},
			changePassword: function() {
			    this.showPassword = !this.showPassword;
			},
		}
	}
</script>

<style>
	.uni-form-item .title {
		padding: 20rpx 0;
	}
	.uni-eye-active {
	    color: #007AFF;
	}
	.uni-icon {
	    font-family: uniicons;
	    font-size: 24px;
	    font-weight: normal;
	    font-style: normal;
	    width: 24px;
	    height: 28px;
	    line-height: 40px;
	    color: #999999;
		padding: 0px 10px 0px;
	}
	.uni-input-wrapper {
	    /* #ifndef APP-NVUE */
	    display: flex;
	    /* #endif */
	    /* padding: 8px 13px; */
	    flex-direction: row;
	    flex-wrap: nowrap;
	    background-color: #FFFFFF;
	}
	
</style>
