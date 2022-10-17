<template>
	<h1>Hello user, welcome on home page</h1>
	<button type="button" @click="logout" onclick="return confirm('are you sure to logout?')">Logout test</button>
</template>

<script>
	export default {
		name: 'home-page',
		mounted() {
			let user = localStorage.getItem('user-info')
			if (!user) {
				this.$router.push({name: 'SignUp'})
			}
		},
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