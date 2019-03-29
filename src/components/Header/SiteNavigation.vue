<template>
		
	<nav class="site-navigation">
		{{ title }}
	</nav>
		
</template>

<script>

	import axios from 'axios';

	export default {
		name: 'SiteNavigation',

		data() {
			return {
				title: ""
			}
		},
		
		mounted: function() {
			
			/* eslint-disable no-console */
			let self = this;
			let endpointID = this.$el.parentElement.getAttribute('data-endpoint-id');
			if (endpointID) {
				
				let endpoint = location.protocol + '//' + window.location.host + '/SampleData/' + endpointID + '.json';
	
				axios.get(endpoint).then(function(response) {
					
					self.title = response.data.title;
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