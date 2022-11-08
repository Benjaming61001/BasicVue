<template>
	<section>
		<TopBar class="shadow topbar" :loginUser="loginUser" />
		<router-view
			class="body"
			@save="insertUser"
			@login="login"
			:userList="user"
		></router-view>
		<bottom-bar />
	</section>
</template>

<script>
import TopBar from "./components/TopBar.vue";
import BottomBar from "./components/BottomBar.vue";

export default {
	name: "App",
	components: {
		TopBar,
		BottomBar,
	},
	data() {
		return {
			loginUser: {
				name: "",
			},
			user: [],
		};
	},
	methods: {
		insertUser(data) {
			this.user.push(data);
		},
		login(data) {
			this.loginUser.name = data;
		},
	},
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Kanit:wght@200;300;400;500;600;700&display=swap");

html {
	min-height: 100vh;
}

* {
	margin: 0;
	padding: 0;
	font-family: "Kanit", sans-serif;
	text-align: center;
}

section {
	widows: 100vw;
}

.body {
	padding-top: 72px;
	min-height: calc(100vh - 216px);
}

.shadow {
	box-shadow: 0 5px 30px rgba(0, 0, 0, 0.05);
}
.topbar {
	z-index: 3;
}

::selection {
	color: #ffffff;
	background: #e21c23;
}
</style>
