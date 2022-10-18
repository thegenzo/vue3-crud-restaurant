<template>
	<Header />
	<h1>Hello user, welcome on update restaurant  page</h1>
</template>

<script>
import Header from './Header.vue'
export default {
	name: 'update-page',
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