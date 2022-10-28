<template>
	<div>
		<h1>{{ message }}</h1>
		<PersonInfo />
		<PersonInfo />
	</div>
</template>

<script>
import PersonInfo from "./PersonInfo.vue";
export default {
	name: "ListData",
	components: {
		PersonInfo,
	},
	data() {
		return {
			message: "show all employee",
		};
	},
};
</script>

<style></style>
