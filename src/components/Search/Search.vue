<template>

	<div class="search container-fluid">
		
		{{ placeholderText }}
		{{ icon }}
		
	</div>
	
</template>

<script>

	import axios from 'axios';
	
	export default {
		name: 'Search',
		
		data() {
			return {
				placeholderText: "",
				icon: ""
			}
		},
		
		mounted: function() {
			
			/* eslint-disable no-console */
			let self = this;
			let endpointID = this.$el.parentElement.getAttribute('data-endpoint-id');
			if (endpointID) {
				
				let endpoint = location.protocol + '//' + window.location.host + '/SampleData/' + endpointID + '.json';
	
				axios.get(endpoint).then(function(response) {
					
					self.placeholderText = response.data.placeholderText;
					self.icon = response.data.icon;
				})
				.catch(function (error) {
					console.log(error);
				});
			}
		}
	}
	
</script>

<style lang="scss" scoped>
	
</style>