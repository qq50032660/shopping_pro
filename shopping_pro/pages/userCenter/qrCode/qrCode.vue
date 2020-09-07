<template>
	<view class="container">
		<view class="white-view">
			
		</view>
		<view class="qrcode">
			<image src="../../../static/img/qr.png" mode=""></image>
		</view>
		<view class="qr-text">
			扫描二维码，加我好友
		</view>
		<view class="save" v-show ="isApp" @tap="printscreen">
			{{tips}}
		</view>
		<view class="qrcode-icon">
			<image src="../../../static/img/qrlogo.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tips:'保存到相册',
				isApp:false
			};
		},
		onLoad() {
			// #ifdef APP-PLUS
			this.isApp = true;
			// #endif
		},
		methods:{
			// 截图，调用webview、Bitmap方法
			printscreen(){
				this.tis = "正在保存"
				let ws=this.$mp.page.$getAppWebview();
				let bitmap = new plus.nativeObj.Bitmap();
				this.showBtn = false;
				this.$nextTick(function(){
					setTimeout(()=>{
						ws.draw(bitmap,(e)=>{
							this.showBtn = true;
							console.log('bitmap绘制图片成功');
							console.log("e: " + JSON.stringify(e));
							bitmap.save("_doc/Qr.jpg", {
								overwrite: true,
								quality: 100
							}, (i)=>{
								plus.gallery.save(i.target,(e)=>{
									uni.showToast({
										title:'保存成功'
									})
									this.tis = "保存到相册"
									bitmap.clear(); //销毁
								},(e)=>{
									bitmap.clear(); //销毁
								});
							},(e)=>{
								console.log('保存图片失败：' + JSON.stringify(e));
							});
						},(e)=>{
							console.log('bitmap绘制图片失败：'+JSON.stringify(e));
						});
					},200)
				})
			}
		}
	}
</script>

<style lang="scss">
	page{background-color: #f06c7a;}
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.white-view {
		height: 30vh;
		background-color: #fff;
		width: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
		
	}
	
	.qrcode {
		margin-top: -20vh;
		
		image {
			height: 60vw;
			width: 60vw;
		}
	}
	.qr-text {
		position: relative;
		
	}
	
	.qrcode-icon {
		position: absolute;
		bottom: 20upx;
		image{
			height: 15vw;
			width: 80vw;
		}
	}
	
</style>
