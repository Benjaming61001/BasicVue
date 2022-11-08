<template>
	<div id="login">
		<div class="card">
			<div class="container">
				<div class="header">
					<div class="text">
						<h1>ยินดีต้อนรับ</h1>
						<h4>เข้าสู่ระบบเพื่อใช้งาน</h4>
					</div>
					<div class="image">
						<img src="" alt="" />
						<h1>image</h1>
					</div>
				</div>
				<div class="form">
					<div class="form-item">
						<label for="">อีเมล</label>
						<input
							type="text"
							placeholder="กรอกอีเมล"
							v-model="user.email"
						/>
					</div>

					<div class="form-item">
						<label for="">รหัสผ่าน</label>
						<input
							type="password"
							placeholder="กรอกรหัสผ่าน"
							v-model="user.password"
						/>
						<p>ลืมรหัสผ่าน</p>
					</div>

					<div class="form-item">
						<div class="submit" v-if="accept == true">
							<button
								@click="login"
								id="submitBtn"
								ref="submitBtn"
								class="accept"
							>
								<span>เข้าสู่ระบบ</span>
							</button>
						</div>

						<div class="submit" v-else>
							<button
								id="submitBtn"
								ref="submitBtn"
								class="reject"
							>
								<span>เข้าสู่ระบบ</span>
							</button>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "LoginPage",
	data() {
		return {
			user: {
				email: "",
				password: "",
			},
			accept: false,
		};
	},
	props: ["userList"],
	methods: {
		checkAccept: function () {
			if (
				//No data in form
				!this.user.email ||
				!this.user.password
			) {
				//Reject
				return (this.accept = false);
			}
			//Accept
			return (this.accept = true);
		},

		login: function () {
			if (!this.user.email || !this.user.password) {
				alert("Invalid data");
				return;
			}

			let loginName = this.user.email;
			alert("Register completed");
			this.$emit("login", loginName);
		},
	},
	watch: {
		user: {
			handler: function () {
				this.checkAccept();
			},
			deep: true,
		},
	},
};
</script>

<style scoped>
#login {
	background: #f4f4f4;
}

.card {
	padding: 40px;
}

.container {
	background: white;
	width: 480px;
	margin: 0 auto;
	border-radius: 10px;
	overflow: hidden;
}

.header {
	height: 160px;
	display: flex;
	justify-content: space-around;
	align-items: center;
	padding: 32px 40px;
	background: #e74a4b;
	color: white;
}

h1,
h4 {
	text-align: left;
}

.form {
	padding: 40px;
	font-size: 14px;
	font-weight: 300;
}

.form-item {
	display: flex;
	flex-direction: column;
	margin-bottom: 16px;
	padding: 0 8px;
}

.form-item label {
	text-align: left;
	margin-bottom: 8px;
}

.form-item input {
	color: #9f9a93;
	font-weight: 300;
}

.form-item input,
.form-item .submit {
	width: auto;
	height: 40px;
	padding: 4px 11px;
	border: 1px solid #bfbfbf;
	border-radius: 10px;
	text-align: left;
}

.form-item input::placeholder {
	color: #bfbfbf;
	text-align: left;
}

.form-item p {
	text-align: right;
	color: #e74a4b;
	margin-top: 16px;
}

.form-item .submit {
	height: 48px;
	border: none;
	padding: 0;
}

button {
	width: 100%;
	height: 100%;
	margin: 5px 0 0 0;
	padding: 0;
	background: #f4f4f4;
	border: none;
	border-radius: 100px;
	color: #c5c2c3;
}

.submit button {
	cursor: pointer;
}

input:focus {
	outline: none !important;
}

.submit .accept {
	background: #e74a4b;
	color: #fff;
	cursor: pointer;
}

.submit .reject {
	background: #f4f4f4;
	color: #c5c2c3;
	cursor: default;
}
</style>
