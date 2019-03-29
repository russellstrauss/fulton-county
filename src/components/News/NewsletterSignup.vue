<template>

	<div class="newsletter-signup container-fluid">
		
		{{ title }}
		
	</div>
	
</template>

<script>

	import axios from 'axios';
	
	export default {
		name: 'NewsletterSignup',
		
		data() {
			return {
				subtitle: "",
				title: "",
				body: "",
				forms: []
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