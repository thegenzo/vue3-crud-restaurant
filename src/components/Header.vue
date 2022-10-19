<template lang="">
	<div class="nav">
		<router-link to="/">Home</router-link>
		<router-link to="/add">Add Restaraunt</router-link>
		<form action="#" @click="logout" onclick="return confirm('are you sure to logout?')">
			<button type="submit">Logout</button>
		</form>
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
				localStorage.clear()
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

	.nav button {
		float: left;
		background-color: #333;
		color: #f2f2f2f2;
		padding: 14px 16px;
		text-align: center;
		font-size: 17px;
		text-decoration: none;
		margin-right: 5px;
		border: none;
		cursor: pointer;
	}


	.nav a:hover, .nav button:hover {
		background: #ddd;
		color: #333; 
	}
</style>