<template>
	<h1>Hello user, welcome on home page</h1>
</template>

<script>
	export default {
		name: 'home-page',
		mounted() {
			let user = localStorage.getItem('user-info')
			if (!user) {
				this.$router.push({name: 'SignUp'})
			}
		}
	}
</script>