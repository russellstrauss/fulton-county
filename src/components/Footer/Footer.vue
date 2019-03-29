<template>

	<div class="footer container-fluid">
		
		{{ contact.title }}
		
	</div>
	
</template>

<script>

	import axios from 'axios';
	
	export default {
		name: 'Footer',
		
		data() {
			return {
				contact: {},
				menuItems: [],
				social: [],
				legal: ""
			}
		},
		
		mounted: function() {
			
			let self = this;
			let endpointID = this.$el.parentElement.getAttribute('data-endpoint-id');
			if (endpointID) {
				
				let endpoint = location.protocol + '//' + window.location.host + '/SampleData/' + endpointID + '.json';
	
				axios.get(endpoint).then(function(response) {
					
					self.contact = response.data.contact;
				})
				.catch(function (error) {
					/* eslint-disable no-console */
					console.log(error);
				});
			}
		}
	}
	
</script>

<style lang="scss" scoped>
	
</style>