<template>
	<section>
		<router-link to="/">
			<img
				src="https://seeklogo.com/images/S/swensen-s-logo-B0148BB776-seeklogo.com.png"
			/>
		</router-link>
		<div class="list">
			<div class="location">
				<router-link to="/">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="icon icon-tabler icon-tabler-map-pin"
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
						<circle cx="12" cy="11" r="3"></circle>
						<path
							d="M17.657 16.657l-4.243 4.243a2 2 0 0 1 -2.827 0l-4.244 -4.243a8 8 0 1 1 11.314 0z"
						></path>
					</svg>
					<span>กรุณาเลือกที่อยู่จัดส่ง</span>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="icon icon-tabler icon-tabler-caret-down"
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
						<path d="M6 10l6 6l6 -6h-12"></path>
					</svg>
				</router-link>
			</div>

			<router-link to="/register">
				<button class="reg">สมัครสมาชิก</button>
			</router-link>
			<router-link to="/login">
				<button class="login">เข้าสู่ระบบ</button>
			</router-link>
			<div class="language">
				<router-link to="/">
					<span>TH</span>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="icon icon-tabler icon-tabler-caret-down"
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
						<path d="M6 10l6 6l6 -6h-12"></path></svg
				></router-link>
			</div>
		</div>
	</section>
</template>

<script>
export default {
	name: "TopBar",
	data() {
		return {
			userName: "",
		};
	},
	props: ["loginUser"],
	watch: {
		loginUser: {
			handler: function () {
				console.log("here");
				if (!this.loginUser.name) {
					this.userName = "";
				} else {
					this.userName = this.loginUser.name;
				}
				return this.userName;
			},
			deep: true,
		},
	},
};
</script>

<style scoped>
section {
	position: fixed;
	width: 100vw;
	height: 72px;
	background: white;
	display: flex;
	justify-content: space-between;
	align-content: center;
	padding-left: 24px;
	padding-right: 24px;
}

section a {
	display: grid;
	place-items: center;
}

a {
	text-decoration: none;
}

a img {
	height: 35%;
}

.list {
	height: 100%;
	margin-right: 48px;
	display: grid;
	grid-template-columns: repeat(4, auto);
	place-items: center;
}

.list div {
	height: 100%;
	display: grid;
	place-items: center;
}

.location {
	border-left: 1px solid #f4f4f4;
	border-right: 1px solid #f4f4f4;
	width: 327px;
}
.location a {
	gap: 24px;
	font-size: 18px;
}

.location a,
.language a {
	width: 100%;
	height: 100%;
	color: #7c7c7c;
	text-decoration: none;
	display: flex;
	justify-content: center;
	transition: all 0.2s;
}
.location a:hover,
.language a:hover {
	color: #e21c23;
}

button {
	margin-right: 24px;
	padding: 0 15px 0;
	width: 140px;
	height: 48px;
	border-radius: 24px;
	cursor: pointer;
	background: white;
	font-size: 14px;
	font-weight: 300;
}

.reg {
	margin-left: 24px;
	border: 1px solid #e21c23;
	color: #e21c23;
	transition: all 0.3s;
}

.reg:hover {
	border: 1px solid #f04343;
	color: #f04343;
}

.login {
	background: #e21c23;
	border: none;
	color: white;
	transition: all 0.3s;
}

.login:hover {
	background: #f04343;
}

.language {
	border-left: 1px solid #f4f4f4;
	width: 72px;
}
</style>
