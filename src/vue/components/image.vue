<template>
	<img :src="apiObject.links[0].href" class="img">
</template>
<script>
	export default {
		name: "spaceImage",
		props: {
			apiObject: Object,
		}
	};
</script>
<style lang="scss" scoped>
	.img {
		object-fit: contain;
		max-width: 360px;
		max-height: 300px;
		transition: all 0.3s ease-in-out;
		transform: scale(1);
	}
</style>
