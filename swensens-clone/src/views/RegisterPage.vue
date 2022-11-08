<template>
	<div id="register">
		<div class="card">
			<div class="container">
				<div class="header">
					<div class="text">
						<h1>สร้างบัญชี</h1>
						<h4>สมัครสมาชิกและเริ่มใช้งาน</h4>
					</div>
					<div class="image">
						<img src="" alt="" />
						<h1>image</h1>
					</div>
				</div>
				<div class="form">
					<div class="name">
						<div class="form-item">
							<label for="">ชื่อ</label>
							<input
								type="text"
								placeholder="กรอกชื่อ"
								v-model="user.firstName"
							/>
						</div>
						<div class="form-item">
							<label for="">นามสกุล</label>
							<input
								type="text"
								placeholder="กรอกนามสกุล"
								v-model="user.lastName"
							/>
						</div>
					</div>

					<div class="form-item">
						<label for="">เบอร์โทรศัพท์</label>
						<input
							type="text"
							placeholder="กรอกเบอร์โทรศัพท์"
							v-model="user.tel"
						/>
					</div>

					<div class="form-item">
						<label for="">อีเมล</label>
						<input
							type="text"
							placeholder="กรอกอีเมล"
							v-model="user.email"
						/>
					</div>

					<div class="form-item">
						<p>
							กรุณาตรวจสอบอีเมลที่ระบุให้ถูกต้อง
							คุณจะไม่สามารถเปลี่ยนแปลงอีเมลหลังจากทำการลงทะเบียนแล้วได้
						</p>
					</div>

					<div class="form-item">
						<label for="">รหัสผ่าน</label>
						<input
							type="password"
							placeholder="กรอกรหัสผ่าน"
							v-model="user.password"
						/>
					</div>

					<div class="form-item">
						<label for="">เพศ (ไม่ระบุได้)</label>
						<ul>
							<li>
								<input
									type="radio"
									value="male"
									v-model="user.gender"
									class="radio-gender"
								/>
								<button
									@click="genderToggle(1)"
									id="male"
									ref="male"
								>
									ชาย
								</button>
							</li>
							<li>
								<input
									type="radio"
									value="female"
									v-model="user.gender"
									class="radio-gender"
								/>
								<button
									@click="genderToggle(2)"
									id="female"
									ref="female"
								>
									หญิง
								</button>
							</li>
							<li>
								<input
									type="radio"
									value="none"
									v-model="user.gender"
									class="radio-gender"
								/>
								<button
									@click="genderToggle(3)"
									id="none"
									ref="none"
								>
									ไม่ระบุ
								</button>
							</li>
						</ul>
					</div>

					<div class="form-item">
						<label for="">ของขวัญวันเกิดรอคุณอยู่</label>
						<input
							type="text"
							placeholder="dd/mm/yyyy"
							v-model="user.birthday"
						/>
					</div>

					<div class="form-item radio">
						<div class="radio-container">
							<input
								type="radio"
								value="accept"
								v-model="user.term"
							/>
						</div>
						<span
							>ฉันได้อ่านและยอมรับ
							<span class="highlight">ข้อกำหนดการใช้งาน</span>
							และ
							<span class="highlight">นโยบายความเป็นส่วนตัว</span>
							ของสเวนเซ่นส์
						</span>
					</div>
					<div class="form-item radio">
						<div class="radio-container">
							<input
								type="radio"
								value="accept"
								v-model="user.news"
							/>
						</div>
						<span
							>ฉันยินยอมรับข้อมูลข่าวสาร
							กิจกรรมส่งเสริมการขายต่างๆ จากสเวนเซ่นส์และ
							<span class="highlight">บริษัทในเครือ</span>
							โดยเราจะเก็บข้อมูลของท่านไว้เป็นความลับ
							สามารถศึกษาเงื่อนไขหรือข้อตกลง
							<span class="highlight">นโยบายความเป็นส่วนตัว </span
							>เพิ่มเติมได้ที่เว็บไซต์ของบริษัทฯ
						</span>
					</div>

					<div class="form-item">
						<div class="submit" v-if="accept == true">
							<button
								@click="submit"
								id="submitBtn"
								ref="submitBtn"
								class="accept"
							>
								<span>สมัครสมาชิก</span>
							</button>
						</div>

						<div class="submit" v-else>
							<button
								id="submitBtn"
								ref="submitBtn"
								class="reject"
							>
								<span>สมัครสมาชิก</span>
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
	name: "RegisterPage",
	data() {
		return {
			user: {
				firstName: "",
				lastName: "",
				tel: "",
				email: "",
				password: "",
				gender: "none",
				birthday: "",
				term: "",
				news: "",
			},
			accept: false,
		};
	},
	methods: {
		genderToggle: function (gender) {
			const male = this.$refs.male;
			const female = this.$refs.female;
			const none = this.$refs.none;

			if (gender === 1) {
				male.classList.add("selected");
				female.classList.remove("selected");
				none.classList.remove("selected");
				this.user.gender = "male";
			} else if (gender === 2) {
				male.classList.remove("selected");
				female.classList.add("selected");
				none.classList.remove("selected");
				this.user.gender = "female";
			} else {
				male.classList.remove("selected");
				female.classList.remove("selected");
				none.classList.add("selected");
				this.user.gender = "none";
			}
		},

		submit: function () {
			if (
				!this.user.firstName ||
				!this.user.lastName ||
				!this.user.tel ||
				!this.user.email ||
				!this.user.password ||
				!this.user.gender ||
				!this.user.birthday
			) {
				alert("Invalid data");
				return;
			}
			if (!this.user.term) {
				alert("Please accept term of use");
				return;
			}
			const newUser = {
				firstName: this.user.firstName,
				lastName: this.user.lastName,
				tel: this.user.tel,
				email: this.user.email,
				password: this.user.password,
				gender: this.user.gender,
				birthday: this.user.birthday,
			};
			alert("Register completed");
			this.$emit("save", newUser);
		},

		checkAccept: function () {
			if (
				//No data in form
				!this.user.firstName ||
				!this.user.lastName ||
				!this.user.tel ||
				!this.user.email ||
				!this.user.password ||
				!this.user.gender ||
				!this.user.birthday ||
				!this.user.term
			) {
				//Reject
				return (this.accept = false);
			}
			//Accept
			return (this.accept = true);
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
#register {
	background: #f4f4f4;
	display: flex;
	justify-content: center;
	align-items: center;
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
	width: auto;
	height: 40px;
	padding: 4px 11px;
	border: 1px solid #bfbfbf;
	border-radius: 10px;
	text-align: left;
	color: #9f9a93;
	font-weight: 300;
}

.form-item input::placeholder {
	color: #bfbfbf;
	text-align: left;
}

.form-item p {
	text-align: left;
	color: #e74a4b;
}

.radio .radio-container {
	display: flex;
	flex-direction: column;
	justify-content: flex-start;
}
.radio {
	display: flex;
	flex-direction: row;
}

.radio-container input {
	width: 16px;
	height: 16px;
	margin-top: 3px;
}

.radio span {
	padding: 0 8px;
	text-align: left;
}

.name {
	display: flex;
	justify-content: space-around;
}

.highlight {
	color: #e74a4b;
}

.form-item .submit {
	height: 48px;
	border: none;
	padding: 0;
}

.submit button {
	width: 100%;
	height: 100%;
	margin: 5px 0 0 0;
	padding: 0;
	background: #f4f4f4;
	border: none;
	border-radius: 100px;
	color: #c5c2c3;
	cursor: pointer;
}

.submit .accept {
	background: #e74a4b;
	color: #fff;
	cursor: pointer;
}

.submit .reject {
	background: #f4f4f4;
	color: #c5c2c3;
	cursor: none;
}

ul {
	list-style: none;
	margin: 0;
	padding: 0;
	display: flex;
}

ul li button {
	color: #e74a4b;
	background: none;
	border: 1px solid #bfbfbf;
	margin: 0 8px;
	padding: 12px 32px;
	border-radius: 30px;
	cursor: pointer;
	transition: all 0.2s;
}
.selected {
	color: #ffffff;
	background: #e74a4b;
}

input:focus {
	outline: none !important;
}

.radio-gender {
	display: none;
}
</style>
