<template>
	<section class="main-content">
		<top-banner />
		<PageBody />
		<PageBottom />
	</section>
</template>

<script>
import TopBanner from "./PageTop.vue";
import PageBody from "./PageBody.vue";
import PageBottom from "./PageBottom.vue";
export default {
	name: "MainBody",
	components: {
		TopBanner,
		PageBody,
		PageBottom,
	},
};
</script>

<style scoped>
* {
	background: white;
}

.main-content {
	display: flex;
	flex-direction: column;
}
</style>
