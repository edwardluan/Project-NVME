<template>
  <div>
    <nav class="navbar">
      <div class="container-fluid">
        <router-link to="/home">
          <img
            src="https://elearning.ctu.edu.vn/pluginfile.php/1/theme_lambda/logo/1675223774/Asset%2034elearning.png"
            alt=""
            width="416"
            height="84"
          />
        </router-link>
      </div>
    </nav>
    <ul class="nav text-light p-2">
      <li class="nav-item">
        <router-link to="/home">Trang chủ</router-link>
      </li>
      <li class="nav-item">
        <router-link to="/dangky">Đăng ký</router-link>
      </li>
      <li class="nav-item">
        <router-link to="/baocao">Báo cáo</router-link>
      </li>
      <div v-if="mssv" class="ml-auto">
        <li class="nav-item ml-auto">
          <router-link to="/student">Xin chào!, {{ mssv }}</router-link>
        </li>
        <button @click="logout">Đăng Xuất</button>
      </div>
      <button v-else class="ml-auto" @click="login">Đăng nhập</button>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: null,
      mssv: "",
    };
  },
  mounted() {
    this.mssv = localStorage.getItem("mssv");
  },
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push("/").then(() => {
        location.reload();
      });
    },
    login() {
      this.$router.push("/").then(() => {
        location.reload();
      });
    },
  },
};
</script>

<style scoped>
ul {
  background-color: #3A454B;
  list-style: none;
  margin: 0;
  padding: 0;
}

ul li {
  display: inline-block;
  margin-right: 1rem;
  padding: 5px;
}

ul li:last-child {
  margin-right: 0;
}

ul li a {
  color: #ffffff;
  text-decoration: none;
  font-size: 18px;
  transition: color 0.2s ease-in-out;
  font-family:Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

ul li a:hover {
  color: #bababa;
}

button {
  background-color: #007bff;
  color: white;
  font-size: 20px;
  border-radius: 5px;
  border: 2px solid #007bff;
  padding: 0 10px;
}
.navbar {
  border-top: 5px solid #1C57A5;
  padding: 20px 0;
  background-image: linear-gradient(to right, rgba(255, 255, 255, 1), rgba(255, 255, 255, 0)), 
  url('https://www.ctu.edu.vn/images/2022/08/12/hitech-2.jpg');
  background-size: cover;
  background-position: center;
}

</style>
