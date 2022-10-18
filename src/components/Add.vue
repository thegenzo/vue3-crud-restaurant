<template>
	<Header />
	<h1>Hello user, welcome on add restaurant page</h1>
</template>

<script>
import Header from './Header.vue'
export default {
	name: 'add-page',
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