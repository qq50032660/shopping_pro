<template>
	<view class="container">
		<view class="login-icon">
			<image src="../../static/img/log.png" mode="aspectFit"></image>
		</view>
		<view class="login-content">
			<view class="loign-input">
				<view class="login-input-item">
					<input id="account" type="number" @input="inputChanged" placeholder="请输入手机号" placeholder-class="input-placeholder" />
				</view>
				<view class="login-input-item">
					<input id="psw" type="text" @input="inputChanged" value="" placeholder="请输入密码" placeholder-class="input-placeholder"/>
				</view>
			</view>
			<view class="login-certain">
				<view @tap="loginEvent">登陆</view>
			</view>
			<view class="login-jump">
				<view class="register" @tap="registerEvent">
					用户注册
				</view>
				<view class="forgetPsw" @tap="forgetPswEvent">
					忘记密码
				</view>
			</view>
		</view>
		<view class="login-third">
			<view class="third">
				一 快速登陆 一
			</view>
			<view class="third-content">
				<view class="third-icon" @tap="jumpToWX">
					<image src="../../static/img/share/wx.png" mode=""></image>
				</view>
				<view class="third-icon" @tap="jumpToQQ">
					<image src="../../static/img/share/qq.png" mode=""></image>
				</view>
				<view class="third-icon" @tap="jumpToWB">
					<image src="../../static/img/share/wb.png" mode=""></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				psw:'',
				account:''
			};
		},
		
		methods:{
			jumpToWX(){
				
			},
			jumpToQQ(){
				
			},
			jumpToWB(){
				
			},
			registerEvent(){
				uni.navigateTo({
					url:'./register'
				})
			},
			forgetPswEvent(){
				uni.navigateTo({
					url:'./resetPsw'
				})
			},
			inputChanged:function(event){
				if(event.target.id == 'account'){
					this.account = event.target.value;
				}else{
					this.psw = event.target.value;
				}
			},
			loginEvent(){
				if(!this.account){
					uni.showToast({
						title:'请输入手机号'
					})
					return;
				}
				if(!this.psw){
					uni.showToast({
						title:'请输入密码'
					})
					return
				}
				if(!(/^1[3456789]\d{9}$/.test(this.account))){ 
				     uni.showToast({
				     	title:'手机号码有误'
				     }) 
				    return; 
				} 
				
				uni.navigateBack({
					delta:1
				})
			}
		}
	}
</script>

<style lang="scss">
	page{background-color: #f06c7a;}
	
	.container {
		background-color: #F06C7A;
		display: flex;
		flex-direction: column;
		align-items: center;
		
		.login-icon {
			margin-top: 70upx;
			image{
				border-radius: 75upx;
				width: 150upx;
				height: 150upx;
			}
		}
		
		.login-content {
			margin-top: 70upx;
			width: 88%;
			
			
			.loign-input{
				
			}
			
			.login-input-item {
				line-height: 90upx;
				height: 90upx;
				background-color: rgba($color: #F06C7A, $alpha: 0.3);
				margin-bottom: 20upx;
				
				input {
					color: #FFFFFF;
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
				color: #F06C7A;
				text-align: center;
				border-radius: 45upx;
				margin-bottom: 20upx;
			}
			
			.login-jump {
				display: flex;
				flex-direction: row;
				padding: 0 10upx;
				justify-content: space-between;
				
				.register {
					color: #FFFFFF;
					font-size: 32upx;
				}
				.forgetPsw {
					color: #FFFFFF;
					font-size: 32upx;
				}
			}
		}
		.login-third {
			position: absolute;
			bottom: 100upx;
			width: 50%;
			height: 150upx;
			
			.third {
				color: #fff;
				text-align: center;
			}
			
			.third-content {
				display: flex;
				flex-direction: row;
				margin: 20upx 0upx;
				
				.third-icon {
					
					margin: 0 20upx;
					
					image {
						width: 80upx;
						height: 80upx;
					}
				}
				
			}
			
		}
	}
</style>
