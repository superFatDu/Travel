<template>
	<div>
		<div class="banner" @click="handleBannerGallary">
			<img :src="bannerImg" alt="" class="banner-img">
			<div class="banner-info">
				<div class="banner-title">{{sightName}}</div>
				<div class="banner-number"><span class="iconfont">&#xe63b;</span><span>{{this.gallaryImgs.length}}</span></div>
			</div>
		</div>
		<fade-animation>
			<common-gallary :imgs="gallaryImgs" v-show="showGallary" @closeGallary="handleCloseGallary"></common-gallary>
		</fade-animation>
	</div>
</template>

<script>
import CommonGallary from '@/common/gallary/Gallary'
import FadeAnimation from '@/common/fade/FadeAnimation'
export default{
	name: 'DetailBanner',
	components: {
		CommonGallary,
		FadeAnimation
	},
	props: {
		sightName: String,
		bannerImg: String,
		gallaryImgs: Array
	},
	data () {
		return {
			showGallary: false
		}
	},
	methods: {
		handleBannerGallary () {
			this.showGallary = true;
		},
		handleCloseGallary () {
			this.showGallary = false;
		}
	}
}
</script>
<style lang="stylus" scoped>
	.banner
		overflow hidden
		height 0
		padding-bottom 55%
		position relative
		.banner-img
			width 100%
		.banner-info
			display flex
			position absolute
			left 0
			right 0
			bottom 0
			line-height .6rem
			color #fff
			background-image linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,.8))
			.banner-title
				flex 1
				font-size .3rem
				padding 0 .2rem
			.banner-number
				margin-right .2rem
				padding 0 .4rem
				height .32rem
				display flex
				justify-content center
				align-items center
				margin-top .14rem
				border-radius .2rem
				font-size .24rem
				background rgba(0,0,0,.6)
				.iconfont
					padding-right .1rem
</style>