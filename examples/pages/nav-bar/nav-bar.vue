<template>
	<view>
        <page-head :title="title"></page-head>
		<view>
			<view class="example-title">基本用法</view>
			<uni-nav-bar left-icon="back" @click-left="back" title="标题" fixed='true'></uni-nav-bar>
            <view class="example-title">左右显示文字</view>
            <uni-nav-bar left-icon="back" right-text="菜单" left-text="返回" @click-left="back" title="标题"></uni-nav-bar>
            <view class="example-title">插入slot</view>
            <uni-nav-bar color="#333333" background-color="#FFFFFF" fixed="false" right-icon="scan" @click-left="showCity"
            @click-right="scan">
            	<block slot="left">
            		<view class="city">
            			<text>{{city}}</text>
            			<uni-icon type="arrowdown" color="#333333" size="22"></uni-icon>
            		</view>
            	</block>
            	<view class="input-view">
            		<uni-icon type="search" size="22" color="#666666"></uni-icon>
            		<input confirm-type="search" @confirm="confirm" class="input" type="text" placeholder="输入搜索关键词" />
            	</view>
            </uni-nav-bar>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				city: '北京',
                title:'NavBar'
			}
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1
				})
			},
			showMenu() {
				uni.showToast({
					title: '菜单'
				})
			},
			clickLeft() {
				uni.showToast({
					title: '左侧按钮'
				})
			},
			search() {
				uni.showToast({
					title: '搜索'
				})
			},
			showCity() {
				uni.showToast({
					title: '选择城市'
				})
			},
			scan() {
				uni.showToast({
					title: '扫码'
				})
			},
			confirm() {
				uni.showToast({
					title: '搜索'
				})
			}
		},
		onPullDownRefresh() {
			console.log('onPullDownRefresh')
			setTimeout(function() {
				uni.stopPullDownRefresh()
				console.log('stopPullDownRefresh')
			}, 1000)
		}
	}
</script>

<style>
	.title {
		font-size: 15px;
		line-height: 20px;
		color: #333333;
		padding: 15px;
	}

	.city {
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
		width: 100%;
		margin-left:8px;
	}

	.input-view {
		width: 92%;
		display: flex;
		background-color: #e7e7e7;
		height: 30px;
		border-radius: 15px;
		padding: 0 4%;
		flex-wrap:nowrap;
		margin:7px 0;
		line-height:30px;
	}
	
	.input-view .uni-icon{
		line-height:30px !important;
	}

	.input-view .input {
		height:30px;
		line-height:30px;
		width:94%;
		padding: 0 3%;
	}
</style>
