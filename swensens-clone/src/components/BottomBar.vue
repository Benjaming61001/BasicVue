<template>
	<div class="main">
		<section class="top">
			<a href="#" target="_blank">
				<img
					src="https://seeklogo.com/images/S/swensen-s-logo-B0148BB776-seeklogo.com.png"
				/>
			</a>
			<ul class="list">
				<li><a href="#">ไอศกรีมของเรา</a></li>
				<li><a href="#">สิทธิพิเศษ</a></li>
				<li><a href="#">รีวอร์ด</a></li>
				<li><a href="#">คูปองของฉัน</a></li>
				<li><a href="#">บัตรกำนัลเงินสด</a></li>
				<li><a href="#">บัจนสเวนเซ่นส์การ์ด</a></li>
				<li><a href="#">ข้อมูลของฉัน</a></li>
			</ul>
		</section>
		<section class="bottom">
			<ul class="icon">
				<li>
					<a href="#"
						><svg
							xmlns="http://www.w3.org/2000/svg"
							class="icon icon-tabler icon-tabler-brand-facebook"
							width="24"
							height="24"
							viewBox="0 0 24 24"
							stroke-width="2"
							stroke="currentColor"
							fill="none"
							stroke-linecap="round"
							stroke-linejoin="round"
						>
							<path
								stroke="none"
								d="M0 0h24v24H0z"
								fill="none"
							></path>
							<path
								d="M7 10v4h3v7h4v-7h3l1 -4h-4v-2a1 1 0 0 1 1 -1h3v-4h-3a5 5 0 0 0 -5 5v2h-3"
							></path></svg
					></a>
				</li>
				<li>
					<a href="#"
						><svg
							xmlns="http://www.w3.org/2000/svg"
							class="icon icon-tabler icon-tabler-brand-instagram"
							width="24"
							height="24"
							viewBox="0 0 24 24"
							stroke-width="2"
							stroke="currentColor"
							fill="none"
							stroke-linecap="round"
							stroke-linejoin="round"
						>
							<path
								stroke="none"
								d="M0 0h24v24H0z"
								fill="none"
							></path>
							<rect
								x="4"
								y="4"
								width="16"
								height="16"
								rx="4"
							></rect>
							<circle cx="12" cy="12" r="3"></circle>
							<line
								x1="16.5"
								y1="7.5"
								x2="16.5"
								y2="7.501"
							></line></svg
					></a>
				</li>
				<li>
					<a href="#"
						><svg
							xmlns="http://www.w3.org/2000/svg"
							class="icon icon-tabler icon-tabler-brand-youtube"
							width="24"
							height="24"
							viewBox="0 0 24 24"
							stroke-width="2"
							stroke="currentColor"
							fill="none"
							stroke-linecap="round"
							stroke-linejoin="round"
						>
							<path
								stroke="none"
								d="M0 0h24v24H0z"
								fill="none"
							></path>
							<rect
								x="3"
								y="5"
								width="18"
								height="14"
								rx="4"
							></rect>
							<path d="M10 9l5 3l-5 3z"></path></svg
					></a>
				</li>
			</ul>
			<ul class="list">
				<li><a href="#">คำถามที่พบบ่อย</a></li>
				<li><a href="#">ข้อกำหนดการใช้งาน</a></li>
				<li><a href="#">นโยบายความเป็นส่วนตัว</a></li>
			</ul>
		</section>
	</div>
</template>

<script>
export default {
	name: "BottomBar",
};
</script>

<style scoped>
.main {
	margin: 0;
	padding: 0%;
}

section {
	color: white;
	display: flex;
	justify-content: space-between;
	align-content: center;
	padding-left: 24px;
	padding-right: 24px;
}

.top {
	height: 40px;
	background: #e21c23;
	padding: 24px;
}

.top a img {
	height: 40px;
}

.top .list {
	height: 40px;
	display: grid;
	grid-template-columns: repeat(7, auto);
	place-items: center;
}

.top .list li a {
	font-size: 20px;
	font-weight: 500;
}

.bottom {
	height: 24px;
	background: #cb191f;
	padding: 16px 24px;
	display: flex;

	justify-content: space-between;
	align-content: center;
	overflow: hidden;
}

.bottom .list,
.bottom .icon {
	display: grid;
	grid-template-columns: repeat(3, auto);
	place-items: center;
}

.bottom .list li a {
	font-size: 16px;
	font-weight: 300;
}

.bottom .icon {
	gap: 24px;
}
.bottom .icon li a svg {
	transform: translateY(-24px);
	outline: 2px solid white;
	border-radius: 50%;
	outline-offset: 2px;
}

li {
	list-style: none;
	margin: 0;
}

li a {
	color: white;
	text-decoration: none;
	padding: 0 12px;
}
</style>
