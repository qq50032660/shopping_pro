<template>
	<view class="container">
		<view class="login-icon"><image src="../../static/img/log.png" mode="aspectFit"></image></view>
		<view class="login-content">
			<view class="loign-input">
				<view class="login-input-i">
					<input id="account" type="number" @input="inputChanged" v-model="account" placeholder="请输入手机号" placeholder-class="input-placeholder" />
					<view class="login-input-c">
						<view class="" style="color: #fff;">
							|
						</view>
						<view class="get-code" :style="{'color':getCodeBtnColor}" @click.stop="getCodeEvent()">
							{{getCodeText}}
						</view>
					</view>
				</view>
				<view class="login-input-item"><input id="code" type="number" @input="inputChanged" v-model="code" placeholder="请输入验证码" placeholder-class="input-placeholder" /></view>
				<view class="login-input-item"><input id="psw" type="text" @input="inputChanged" v-model="psw" value="" placeholder="请输入密码" placeholder-class="input-placeholder" /></view>
			</view>
			<view class="login-certain"><view @tap="resetPswEvent">重置密码</view></view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			account:'',
			psw:'',
			code:'',
			codeBtnIsClick:false,
			getCodeBtnColor:"#ffffff",
			getCodeText:'获取验证码'
		};
	},
	methods:{
		getCodeEvent(){
			if(this.codeBtnIsClick){
				return ;
			}
			if(!(/^1(3|4|5|6|7|8|9)\d{9}$/.test(this.account))){ 
				uni.showToast({title: '请填写正确手机号码',icon:"none"});
				return false; 
			} 
			this.getCodeText = "发送中..."
			this.getCodeisWaiting = true;
			this.getCodeBtnColor = "rgba(255,255,255,0.5)"
			//示例用定时器模拟请求效果
			setTimeout(()=>{
				uni.showToast({title: '验证码已发送',icon:"none"});
				//示例默认1234，生产中请删除这一句。
				this.code=1234;
				this.setTimer();
			},1000)
		},
		// Timer(){},
		setTimer(){
			var time = 60;
			this.getCodeText = '重新获取(60)'
			this.Timer = setInterval(()=>{
				if(time<=0){
					this.getCodeisWaiting = false;
					this.getCodeBtnColor = "#ffffff";
					this.getCodeText = "获取验证码"
					clearInterval(this.Timer);
					return;
				}
				this.getCodeText="重新获取("+time+")"
				time--;
			},1000)
		},
		resetPswEvent(){
			uni.hideKeyboard()
			//模板示例部分验证规则
			if(!(/^1(3|4|5|6|7|8|9)\d{9}$/.test(this.account))){ 
				uni.showToast({title: '请填写正确手机号码',icon:"none"});
				return false; 
			} 
			//示例验证码，实际使用中应为请求服务器比对验证码是否正确。
			if(!this.code){ 
				uni.showToast({title: '验证码不正确',icon:"none"});
				return false; 
			}
			uni.showLoading({
				title: '提交中...'
			})
			setTimeout(()=>{
				uni.navigateBack({
					delta:1
				})
			},1000)
		},
		backEvent(){
			wx.navigateBack();
		}
		
	}
};
</script>

<style lang="scss">
page {
	background-color: #f06c7a;
}

.container {
	background-color: #f06c7a;
	display: flex;
	flex-direction: column;
	align-items: center;

	.login-icon {
		margin-top: 70upx;
		image {
			border-radius: 75upx;
			width: 150upx;
			height: 150upx;
		}
	}

	.login-content {
		margin-top: 70upx;
		width: 88%;

		.loign-input {
		}
		.login-input-i {
			display: flex;
			flex-direction: row;
			line-height: 90upx;
			height: 90upx;
			background-color: rgba($color: #f06c7a, $alpha: 0.3);
			margin-bottom: 20upx;
			justify-content: space-between;
			
			input {
				color: #ffffff;
				padding-left: 20upx;
				height: 100%;
			}
			.input-placeholder {
				color: #fff;
			}
			
			.login-input-c {
				display: flex;
				flex-direction: row;
				
				.get-code {
					margin-left: 20upx;
					// color: #FFFFFF;
				}
			}
			
		}
		.login-input-item {
			
			line-height: 90upx;
			height: 90upx;
			background-color: rgba($color: #f06c7a, $alpha: 0.3);
			margin-bottom: 20upx;

			input {
				color: #ffffff;
				padding-left: 20upx;
				height: 100%;
			}
			.input-placeholder {
				color: #fff;
			}
		}

		.login-certain {
			line-height: 90upx;
			height: 90upx;
			background-color: #fff;
			color: #f06c7a;
			text-align: center;
			border-radius: 45upx;
			margin-bottom: 20upx;
		}

		.login-jump {

			.login {
				color: #ffffff;
				font-size: 32upx;
				text-align: center;
			}
			
		}
	}
}
</style>
