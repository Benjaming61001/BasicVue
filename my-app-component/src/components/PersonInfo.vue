<template>
	<div>
		<h1>
			{{ message }}
		</h1>
	</div>
</template>

<script>
export default {
	name: "PersonInfo",
	data() {
		return {
			message: "Employee datails",
		};
	},
};
</script>

<style scoped>
h1 {
	color: red;
}
</style>
