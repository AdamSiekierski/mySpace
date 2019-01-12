<template>
	<div id="imagesWrapper">
		<div class="image" v-for="item in apiResponse" :key="item.data[0].nasa_id">
			<a :href="item.links[0].href" download>
				<spaceImage :apiObject="item"/>
			</a>
		</div>
	</div>
</template>
<script>
	import spaceImage from "./image.vue";
	import electronDl from "electron-dl";

	export default {
		name: "images",
		props: {
			apiResponse: Array
		},
		components: {
			spaceImage
		}
	};
</script>
<style lang="scss" scoped>
	#imagesWrapper {
		display: grid;
		grid-gap: 15px;
		grid-template-columns: auto auto;
		grid-row-gap: 15px;
		grid-column-gap: 15px;
		justify-content: center;
		.image {
			width: 360px;
			overflow: hidden;
			height: 300px;
			background-color: #111111;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			cursor: pointer;
			&:hover {
				.img {
					opacity: 0.6;
					transform: scale(1.05);
				}
			}
		}
	}
</style>
