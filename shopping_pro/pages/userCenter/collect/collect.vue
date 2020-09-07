<template>
	<view>
		<view class="nav_tab">
			<view class="nav_item {{}}" v-for="(item,index) in navList" :key="index">
				{{item}}
			</view>
			<view class="">
				
			</view>
		</view>
		<view class="nav_list">
			<view class="list_item">
				<view class="item_left">
					<image src="../../../static/img/category/list/9.jpg" mode="aspectFit"></image>
				</view>
				<view class="item_right">
					<view class="item_right_top">
						<text></text>
					</view>
					<view class="item_right_bottom">
						<view class="item_collect">
							
						</view>
						<view class="item_price">
							
						</view>
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
				navList:['商品','店铺']
			};
		}
	}
</script>

<style lang="scss">
	page{position: relative;background-color: #f2f2f2;}
	
	.nav_tab {
		width: 95vw;
		height: 100upx;
		position: fixed;
		z-index: 100;
		background-color: #007AFF;
		left: 2.5vw;
		display: flex;
		flex-direction: row;
		justify-content: center;
		.nav_item{
			width: 50%;
			display: flex;
			flex-direction: row;
			justify-content: center;
			line-height: 100upx;
		}
		
		
	}
</style>
