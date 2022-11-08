<template>
	<section class="page-body">
		<div class="section-deal">
			<div class="container">
				<div class="section-header">
					<h2>ดีลสุดคุ้ม</h2>
				</div>
				<div class="image">
					<ul>
						<li>image-1</li>
						<li>image-2</li>
						<li>image-3</li>
					</ul>
					<ul class="nav">
						<li></li>

						<li></li>
					</ul>
				</div>
			</div>
		</div>

		<div class="section section-news">
			<div class="container">
				<div class="section-header">
					<h2>ข่าว</h2>
				</div>
			</div>
		</div>
	</section>
</template>

<script>
export default {
	name: "PageBody",
};
</script>

<style scoped>
.page-body {
	padding: 64px 0 120px;
	overflow: hidden;
}

.container {
	max-width: 1200px;
	display: flex;
	flex-direction: column;
	align-items: center;
	background: #ffffff;
	color: black;
	gap: 20px;
	margin: 0 auto;
	padding: 0 24px;
}

.container .section-header {
	width: 100%;
}

.container .image {
	height: 235px;
	width: 100%;
	border-radius: 20px;
}

.image {
	display: flex;
	flex-direction: column;
}

.image ul {
	height: 100%;
	width: 100%;
	list-style: none;
	margin: 0;
	padding: 0;
	display: flex;
	justify-content: space-between;
	align-items: center;
}

ul li {
	height: 100%;
	width: 368px;
	display: flex;
	justify-content: center;
	align-items: center;
	border-radius: 10px;
	background: #ececec;
}

.image .nav {
	justify-content: center;
	height: 6px;
	margin: 24px 0 0;
}

.nav li {
	width: 18px;
	margin: 0 3px;
}

.nav li:first-child {
	background: #e21c23;
}

li {
	cursor: pointer;
}

h2 {
	font-size: 32px;
	font-weight: 500;
	text-align: start;
}

.section-news {
	margin-top: 40px;
}
</style>
