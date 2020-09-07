<template>
	<view class="container">
		<view v-if="showHeader" class="status" :style="{position:headerPosition,top:statusTop}"></view>
		<view v-if="showHeader" class="header" :style="{position:headerPosition,top:headerTop}">
			<view class="addr"></view>
			<view class="input-box">
				
			</view>
			<view class="icon-btn">
				<view class="iconfont tongzhi" @tap="jumpToMsg()"></view>
				<view class="iconfont setting" @tap="jumpToInfo()"></view>
			</view>
		</view>
		<!-- 占位 -->
		<view v-if="showHeader" class="place"></view>
		<!-- header -->
		<view class="header-bg">
			<view class="header-bg-view">
				<view class="header-top">
					<view class="top-left">
						<image class="header-pic" :src="user.face" @tap="jumpToInfo()"></image>
						<view class="user-info">
							<view class="user-name">
								游客12313
							</view>
							<view class="user-desc" @tap="jumpToLoginEvent">
								点我可以跳转登录哟
							</view>
						</view>
					</view>
					<view class="iconfont qr" @tap = "jumpTpQrCode"></view>
				</view>
				<view class="header-center">
					<view class="center-left">
						<view class="icon-doudoule"></view>
						<text>开通vip会员</text>
					</view>
					<view class="center-right">
						<text>会员特权</text>
					</view>
				</view>
			</view>
		</view>
		<view class="order-view">
			<view class="order-top">
				<view class="order-top-item" v-for="(item,index) in orderList" :key="index" @tap="jumpToOrderList(index)">
					<view class="order-img">
						<view class="iconfont" :class="item.icon"></view>
					</view>
					<view class="order-text">{{item.text}}</view>
				</view>
			</view>
			<view class="order-bottom">
				<view class="left">
					<view class="box">
						<view class="num">{{user.integral}}</view>
						<view class="text">积分</view>
					</view>
					<view class="box">
						<view class="num">{{user.envelope}}</view>
						<view class="text">佣金</view>
					</view>
					<view class="box">
						<view class="num">{{user.balance}}</view>
						<view class="text">余额</view>
					</view>
				</view>
				<view class="right">
					<view class="box" @tap="jumpToDeposit">
						<view class="img">
							<view class="iconfont chongzhi"></view>
						</view>
						<view class="text">充值</view>
					</view>
				</view>
			</view>
		</view>
		<view class="tool-view">
			<view class="tool-title">
				我的工具栏
			</view>
			<view class="tool-list-view">
				<view class="tool-item" v-for="(item,index) in mytoolbarList" :key="index" @tap= "jumpToToolsRoute(index)">
					<view class="img">
						<image :src="item.img"></image>
					</view>
					<view class="text">
						{{item.text}}
					</view>
				</view>
			</view>
		</view>
		<!-- 占位 -->
		<view class="place-bottom"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isfirst:true,
				headerPosition:"fixed",
				headerTop:null,
				statusTop:null,
				showHeader:true,
				//个人信息,
				user:{
					username:'游客1002',
					face:'/static/img/face.jpg',
					signature:'点击昵称跳转登录/注册页',
					integral:100,
					balance:0,
					envelope:1000
				},
				// 订单类型
				orderList:[
					{text:'待付款',icon:"fukuan"},
					{text:'待发货',icon:"fahuo"},
					{text:'待收货',icon:"shouhuo"},
					{text:'待评价',icon:"pingjia"},
					{text:'退换货',icon:"tuihuo"}
				],
				// 工具栏列表
				mytoolbarList:[
					{url:'../../user/keep/keep',text:'我的收藏',img:'/static/img/user/point.png'},
					{url:'../../user/coupon/coupon',text:'优惠券',img:'/static/img/user/quan.png'}, 
					{url:'',text:'新客豪礼',img:'/static/img/user/renw.png'},
					{url:'',text:'领红包',img:'/static/img/user/momey.png'},
					
					{url:'../../user/address/address',text:'收货地址',img:'/static/img/user/addr.png'},
					{url:'',text:'账户安全',img:'/static/img/user/security.png'},
					{url:'',text:'银行卡',img:'/static/img/user/bank.png'},
					{url:'',text:'抽奖',img:'/static/img/user/choujiang.png'},
					// {text:'客服',img:'/static/img/user/kefu.png'},
					// {text:'签到',img:'/static/img/user/mingxi.png'}
					
				]
			};
		},
		onPullDownRefresh() {
		    setTimeout(function () {
		        uni.stopPullDownRefresh();
		    }, 1000);
		},
		onPageScroll(e){
			//兼容iOS端下拉时顶部漂移
			this.headerPosition = e.scrollTop>=0?"fixed":"absolute";
			this.headerTop = e.scrollTop>=0?null:0;
			this.statusTop = e.scrollTop>=0?null:-this.statusHeight+'px';
		},
		onLoad() {
			this.statusHeight = 0;
			// #ifdef APP-PLUS
			this.showHeader = false;
			this.statusHeight = plus.navigator.getStatusbarHeight();
			// #endif
		},
		methods:{
			 
			jumpToOrderList(index){
				
			},
			
			jumpToDeposit(){
				
			},
			jumpToInfo(){
				uni.navigateTo({
					url:'userInfo/userInfo'
				})
			},
			jumpTpQrCode(){
				uni.navigateTo({
					url:'qrCode/qrCode'
				})
			},
				
			jumpToMsg(){
				uni.navigateTo({
					url:'msg/msg'
				})
			},
			
			jumpToLoginEvent(){
				uni.navigateTo({
					url:'../login/login'
				})
			}
			
		}
	}
</script>

<style lang="scss">
	
	page{position: relative;background-color: #fff;}
	
	.status {
		width: 100%;
		height: 0;
		position: fixed;
		z-index: 10;
		background-color: #f06c7a;
		top: 0;
		/*  #ifdef  APP-PLUS  */
		height: var(--status-bar-height);//覆盖样式
		/*  #endif  */
		
	}
	
	.header{
		width: 92%;
		padding: 0 4%;
		height: 100upx;
		display: flex;
		justify-content: flex-end;
		align-items: center;
		position: fixed;
		top: 0;
		z-index: 10;
		background-color: #f06c7a;
		/*  #ifdef  APP-PLUS  */
		top: var(--status-bar-height);
		/*  #endif  */
		.icon-btn{
			width: 120upx;
			height: 60upx;
			flex-shrink: 0;
			display: flex;
			.iconfont{
				color: #fff;
				width: 60upx;
				height: 60upx;
				display: flex;
				justify-content: flex-end;
				align-items: center;
				font-size: 42upx;
			}
		}
	}
	.place{
		background-color: #f06c7a;
		height: 100upx;
		/*  #ifdef  APP-PLUS  */
		margin-top: var(--status-bar-height);
		/*  #endif  */
	}
	.place-bottom{
		height: 300upx;
	}
	
	.container{
		
	}
	.header-bg {
		height: auto;
		width: 100%;
		background-color: #f06c7a;
		background-size: 750rpx 100rpx;

		display: flex;
		flex-direction: column;
	}
	.header-bg-view {
		display: flex;
		flex-direction: column;
		margin: 20rpx;
		.header-top {
			display: flex;
			flex-direction: row;
			align-items: center;
			justify-content: space-between;
			.top-left {
				display: flex;
				flex-direction: row;
				.header-pic {
					width: 120rpx;
					height: 120rpx;
					border-radius: 100%;
				}
				.user-info {
					display: flex;
					flex-direction: column;
					margin-left: 20rpx;
				}
			}
			
			.qrcode {
				width: 70rpx;
				height: 70rpx;
			}	
			
		}
		.header-center {
			margin-top: 60rpx;
			margin-bottom: 40rpx;
			background: linear-gradient(to left, #dea96d 0%,#f6d59b 100%);
			box-shadow: 0upx 0upx 25upx rgba(0,0,0,0.2);			height: 100rpx;
			display: flex;
			flex-direction: row;
			align-items: center;
			justify-content: space-between;
			padding: 0 30rpx;
			border-radius: 10rpx;
			.center-left{
				
			}
		}
		
	}
	.order-view {
		margin: 20rpx;
		padding: 20rpx 40rpx;
		background-color: #fff;
		width: 84%;
		box-shadow: 0rpx 0rpx 25rpx rgba(0,0,0,0.1);
		border-radius: 15rpx;
		.order-top{
			
			display: flex;
			flex-direction: row;
			align-items: center;
			justify-content: space-between;
			padding-bottom: 10rpx;
			border-bottom: solid 1upx #17e6a1;
			margin: 0rpx 10rpx;
			.order-top-item {
				display: flex;
				flex-direction: column;
				align-items: center;
				.order-text {
					font-size: 26rpx;
					margin-top: 10rpx;
				}
			}
			
		}
		.order-bottom {
			margin-top: 10rpx;
			margin-left: 10rpx;
			margin-right: 10rpx;
			display: flex;
			flex-direction: row;
			align-items: center;
			.left {
				display: flex;
				flex-direction: row;
				justify-content: space-between;
				align-items: center;
				width: 70%;
				
				
				.box {
					display: flex;
					flex-direction: column;
					align-items: center;
					justify-content: space-around;
					height: 80rpx;
					
					
				}
			}
			
			.right {
				width: 30%;
				display: flex;
				flex-direction: row;
				justify-content: flex-end;
				align-items: center;
				height: 120rpx;
			
				.box {
					margin-top: 0rpx;
					
					.img {
						display: flex;
						flex-direction: column;
						justify-content: flex-start;
						align-items: center;
						margin-top: 0rpx;
						.iconfont{
							font-size: 45rpx;
							color: #e78901;
						}
					}
				}
				
			}
		}
	}
	.tool-view {
		margin: 20rpx;
		padding: 20rpx 30rpx;
		display: flex;
		flex-direction: column;
		box-shadow: 0rpx 0rpx 25rpx rgba(0,0,0,0.1);
		border-radius:15rpx;
		.tool-title{
			
		}
		.tool-list-view {
			// padding: 10rpx;
			display: flex;
			flex-wrap: wrap;
			.tool-item {
				display: flex;
				flex-direction: column;
				justify-content: space-between;
				align-items: center;
				width: 25%;
				margin: 30rpx 0rpx;
				.img{
					height: 10.5vw;
					display: flex;
					justify-content: center;
					
					image{
						width: 9vw;
						height: 9vw;
					}
				}
				.text{
					width: 100%;
					display: flex;
					justify-content: center;
					font-size: 26upx;
					color: #3d3d3d;
				}
			}
		}
	}
	
</style>
