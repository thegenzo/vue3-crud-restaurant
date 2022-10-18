<template>
	<Header />
	<h1>Hello user, welcome on home page</h1>
	<button type="button" @click="logout" onclick="return confirm('are you sure to logout?')">Logout test</button>
</template>

<script>
import Header from './Header.vue'
export default {
	name: 'home-page',
	components: {
		Header
	},
	mounted() {
		let user = localStorage.getItem('user-info')
		if (!user) {
			this.$router.push({name: 'SignUp'})
		}
	},
}
</script>