<template>
	<view>
		<view class="container">
			<view class="list">
				<view class="row">
					<view class="title">
						头像
					</view>
					<view class="right">
						<view class="des">
							<image src="/static/img/face.jpg" mode=""></image>
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
				<view class="row">
					<view class="title">
						昵称
					</view>
					<view class="right">
						<view class="des">
							大黑哥
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
				<view class="row">
					<view class="title">
						个性签名
					</view>
					<view class="right">
						<view class="des">
							这人太懒了，什么都不想写呀～
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
				<view class="row">
					<view class="title">
						收货地址
					</view>
					<view class="right">
						<view class="des">
							
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
				<view class="row">
					<view class="title">
						账户安全
					</view>
					<view class="right">
						<view class="des">
							
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
			</view>
			<view class="list">
				<view class="row">
					<view class="title">
						通知提醒
					</view>
					<view class="right">
						<view class="des">
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
				<view class="row">
					<view class="title">
						支付设置
					</view>
					<view class="right">
						<view class="des">
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
				<view class="row">
					<view class="title">
						通用
					</view>
					<view class="right">
						<view class="des">
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
			</view>
			<view class="list">
				<view class="row">
					<view class="title">
						版本升级
					</view>
					<view class="right">
						<view class="des">
							v1.0.0
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
				<view class="row">
					<view class="title">
						清除缓存
					</view>
					<view class="right">
						<view class="des">
							
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
				<view class="row">
					<view class="title">
						问题反馈
					</view>
					<view class="right">
						<view class="des">
							
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
				<view class="row">
					<view class="title">
						关于商城
					</view>
					<view class="right">
						<view class="des">
							
						</view>
						<view class="iconfont xiangyou"></view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
	page{background-color: #f0f0f0;}
	.container {
		padding-bottom: 20upx;
		
		.list {
			margin-bottom: 10upx;
			background-color: #fff;
			padding: 0upx 20upx;
			.row{
				background-color: #fff;
				border-bottom: 1upx;
				border-color: #3B4144;
				display: flex;
				flex-direction: row;
				justify-content: space-between;
				align-items: center;
				min-height: 100upx;
				border-bottom: solid 1upx #f3f3f3;
				.right {
					display: flex;
					flex-direction: row;
					align-items: center;
					
					.des {
						font-size: 30upx;
						color: #555555;
						line-height: 40upx;
						margin: 20upx 0;
						// height: 40upx;
						image {
							border-radius: 100%;
							width: 100upx;
							height: 100upx;
						}
					}
					.iconfont {
						font-size: 30upx;
						color: #666666;
					}
				}
			}
		}
	}
</style>
