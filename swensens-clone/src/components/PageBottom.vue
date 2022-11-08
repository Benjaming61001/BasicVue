<template>
	<section class="main-content">
		<div class="banner">
			<div class="phone">
				<img
					src="https://swensens1112.com/images/app-screen-webp.webp"
					alt=""
				/>
			</div>
			<div class="link">
				<h2>ดาวน์โหลดที่</h2>
				<div class="store">
					<a href="#">
						<img
							src="https://swensens1112.com/images/google-play.png"
							alt=""
					/></a>
					<a href="#">
						<img
							src="https://swensens1112.com/images/app-store.png"
							alt=""
					/></a>
				</div>
			</div>
		</div>
	</section>
</template>

<script>
export default {
	name: "PageBottom",
};
</script>

<style scoped>
.main-content {
	padding-top: 0;
}
.banner {
	min-height: 420px;
	padding: 0 40px 0;
	background: #ececec;
	color: black;
	display: flex;
	justify-content: center;
	align-items: center;
	gap: 24px;
}

.phone {
	height: 420px;
}

.phone img {
	transform: translateY(70px);
	height: 350px;
}

.link {
	display: flex;
	flex-direction: column;
	padding-left: 15px;
	transform: translateY(35px);
}

.link h2 {
	font-size: 40px;
	font-weight: 500;
	text-align: left;
	margin: 0 0 24px;
	padding-left: 12px;
}

.store {
	display: flex;
}

.store a img {
	height: 60px;
	padding: 0 12px;
}
</style>
