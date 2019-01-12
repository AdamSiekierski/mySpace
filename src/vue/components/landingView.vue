<template>
	<div>
		<div id="landingView">
			<h1>mySpace🚀</h1>
			<label
				for="searchInput"
				id="searchLabel"
			>Type some space-related text and begin your journey through Space with photos from NASA Database. Click on image to download</label>
			<input type="text" id="searchInput" @input="search" v-model="searchString">
		</div>
		<images :apiResponse="results" v-if="results && loaded === true && found === 1"/>
	</div>
</template>
<script>
	import debounce from "lodash.debounce";
	import axios from "axios";
	import images from "./images";

	const API = "https://images-api.nasa.gov/search";

	export default {
		name: "landingView",
		data() {
			return {
				searchString: "",
				results: [],
				loaded: true,
				found: 0
			};
		},
		components: {
			images
		},
		methods: {
			search: debounce(function() {
				this.loaded = false;
				this.found = 0;
				axios
					.get(`${API}?q=${this.searchString}&media_type=image`)
					.then(response => {
						this.results = response.data.collection.items;
						console.log(this.results);
						this.loaded = true;
						this.found = 1;
					});
			}, 1000)
		}
	};
</script>
<style lang="scss" scoped>
	#landingView {
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		height: 100vh;
		text-align: center;
		h1 {
			font-size: 50px;
			margin: 0;
		}
		#searchInput {
			outline: none;
			font-size: 26px;
			padding: 5px;
			border: none;
			border-bottom: 2px solid #111111;
			width: 250px;
			margin-top: 10px;
			text-align: center;
			background-color: #efefef;
			box-shadow: 0px 2px 2px -2px rgba(0, 0, 0, 0);
			transition: all 0.2s ease-in-out;
		}
		#searchInput:focus {
			box-shadow: 0px 2px 2px -2px rgba(0, 0, 0, 0.75);
		}
		#searchLabel {
			width: 70vw;
			margin-top: 10px;
		}
	}
</style>
