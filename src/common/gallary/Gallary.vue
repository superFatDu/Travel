<template>
	<div class="container" @click="handleShowOrNot">
		<div class="wrapper">
			<swiper :options="swiperOptions">
	      <!-- slides -->
	      <swiper-slide v-for="(item,index) in imgs" :key="index
	      ">
	        <img class="gallary-img" :src="item" alt="">
	      </swiper-slide>
	      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
		</div>
	</div>
</template>

<script>
export default {
	name: 'CommonGallary',
	props: {
		imgs: Array
	},
	data () {
		return {
			swiperOptions: {
				pagination : '.swiper-pagination',
				paginationType: 'fraction',
				observeParents: true,
				observer: true
			}
		}
	},
	methods: {
		handleShowOrNot () {
			this.$emit("closeGallary")
		}
	}
}
</script>

<style lang="stylus" scoped>
	.container >>> .swiper-container
		overflow inherit
	.container
		position fixed
		top 0
		left 0
		right 0
		bottom 0
		background #000
		z-index 99
		display flex
		flex-direction column
		justify-content center
		align-items center
		.wrapper
			width 100%
			.gallary-img
				width 100%
			.swiper-pagination
				color #fff
				bottom -1rem
</style>