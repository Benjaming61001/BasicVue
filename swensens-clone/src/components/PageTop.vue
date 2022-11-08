<template>
	<section>
		<div class="banner">
			<div class="text">
				<h1>
					สมัครเป็นสมาชิก<br />
					สเวนเซ่นส์วันนี้ พร้อมรับ สิทธิพิเศษมากมายรอคุณ อยู่ที่นี่
				</h1>
				<p>
					พิเศษสุดๆ! สำหรับสมาชิกสเวนเซ่นส์ ยิ่งกิน ยิ่งได้ ยิ่งคุ้ม
					ใครๆ ก็สมัครได้
					ใช้ง่ายสะดวกสบายพร้อมสิทธิประโยชน์มากมายเพื่อคนสำคัญเช่นคุณ
					รอไม่ได้แล้ว สมัครเลย
				</p>
				<a href="#">
					<button>
						<img
							src="https://img.freepik.com/free-vector/delivery-service-with-masks-concept_23-2148509518.jpg?w=1380&t=st=1667565920~exp=1667566520~hmac=bd6c64ca06f178a301c32f4bd441f3f0adf36c36d1779c4200c2b2b2f3fae28f"
							alt="..."
						/>
						<span>สั่งออนไลน์</span>
					</button>
				</a>
			</div>
			<img
				src="https://swensens1112.com/images/banner-image.svg"
				alt=""
			/>
		</div>
	</section>
</template>

<script>
export default {
	name: "PageTop",
};
</script>

<style scoped>
* {
	background: white;
}

.banner {
	min-height: 482px;
	padding: 100px 40px;
	background: linear-gradient(180deg, #f87c79, #fd4b47);
	display: flex;
	justify-content: center;
	gap: 15px;
}

.banner .text,
.banner .img {
	padding: 0 15px;
}
.banner .text {
	background: none;
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	max-width: 560px;
}

.banner .text h1 {
	font-size: 48px;
	font-weight: 600;
}

.banner .text p {
	font-size: 18px;
}

.banner .text h1,
.banner .text p {
	margin: 10px 0;
	text-align: left;
	background: none;
	color: white;
}

a {
	width: fit-content;
	margin: 40px 0 0;
	border-radius: 72px;
	text-decoration: none;
}

a button {
	width: 260px;
	height: 66px;
	background: white;
	color: #ff0f0f;
	border: none;
	border-radius: 72px;
	display: flex;
	justify-content: space-between;
	align-items: center;
	cursor: pointer;
	box-shadow: 10px 10px 10px rgba(0, 0, 0, 0.15);
}

.banner .text a button img {
	width: 60px;
	height: 60px;
	border-radius: 50%;
	object-fit: cover;
	margin-left: 5px;
}

a button span {
	margin: auto;
	font-size: 24px;
	font-weight: 800;
	background: none;
}

a button:hover {
	background: #ff0f0f;
	color: white;
}

.banner img {
	width: 550px;
	background: none;
}

button {
	text-transform: uppercase;
}
</style>
