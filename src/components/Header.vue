<template lang="">
	<div class="nav">
		<a href="#">Home</a>
		<a href="#">Add Restaraunt</a>
		<a href="#">Update Restaurant</a>
		<a href="#" @click="logout" onclick="return confirm('are you sure to logout?')">Logout</a>
	</div>
	<h1>Header</h1>
</template>
<script>
export default {
	name: 'header-page',
	methods: {
		async logout() {
			let result = await localStorage.getItem('user-info')
			console.log(result)

			if (result) {
				localStorage.removeItem('user-info')
				this.$router.push('/login')
			}
		}
	}
}
</script>
<style>
	.nav {
		background-color: #333;
		overflow: hidden;
	}
	
	.nav a {
		float: left;
		color: #f2f2f2f2;
		padding: 14px 16px;
		text-align: center;
		font-size: 17px;
		text-decoration: none;
		margin-right: 5px;
	}

	.nav a:hover {
		background: #ddd;
		color: #333; 
	}
</style>