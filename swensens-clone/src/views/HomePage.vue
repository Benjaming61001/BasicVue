<template>
	<section class="main-content">
		<PageTop class="shadow page-top" />
		<PageBody class="shadow page-body" />
		<PageBottom />
	</section>
</template>

<script>
import PageTop from "../components/PageTop.vue";
import PageBody from "../components/PageBody.vue";
import PageBottom from "../components/PageBottom.vue";
export default {
	name: "MainBody",
	components: {
		PageTop,
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
.page-top {
	z-index: 2;
}

.page-body {
	z-index: 1;
}
</style>
