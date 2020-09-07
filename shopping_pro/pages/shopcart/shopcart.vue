<template>
	<view>
	        <scroll-view style="height: 300px;color: #007AFF;" scroll-y="true" refresher-enabled="true" :refresher-triggered="triggered"
	            :refresher-threshold="100"  @refresherpulling="onPulling"
	            @refresherrefresh="onRefresh" @refresherrestore="onRestore" @refresherabort="onAbort"></scroll-view>
	    </view>
	
</template>

<script>
	export default {
		data() {
			return {
				triggered: false,
				goodsList:[
					{id:1,img:'/static/img/goods/p1.jpg',name:'商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题',spec:'规格:S码',price:127.5,number:1,selected:false},
					{id:2,img:'/static/img/goods/p2.jpg',name:'商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题',spec:'规格:S码',price:127.5,number:1,selected:false},
					{id:3,img:'/static/img/goods/p3.jpg',name:'商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题',spec:'规格:S码',price:127.5,number:1,selected:false},
					{id:4,img:'/static/img/goods/p4.jpg',name:'商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题',spec:'规格:S码',price:127.5,number:1,selected:false},
					{id:5,img:'/static/img/goods/p5.jpg',name:'商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题商品标题',spec:'规格:S码',price:127.5,number:1,selected:false}
				],
			};
		},
		 onLoad() {
		            this._freshing = false;
		            setTimeout(() => {
		                this.triggered = true;
		            }, 1000)
		        },
		        methods: {
		            onPulling(e) {
		                console.log("onpulling", e);
		            },
		            onRefresh() {
		                if (this._freshing) return;
		                this._freshing = true;
		                setTimeout(() => {
		                    this.triggered = false;
		                    this._freshing = false;
		                }, 3000)
		            },
		            onRestore() {
		                this.triggered = 'restore'; // 需要重置
		                console.log("onRestore");
		            },
		            onAbort() {
		                console.log("onAbort");
		            }
					}
	}
</script>

<style lang="scss">

</style>
