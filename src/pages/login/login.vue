<template>
  <div class="login">
    <div class="con">
      <h2>登录</h2>
      <div>
        <input type="text" v-model="user.username" />
        <!-- <input type="text" name="" id=""> -->
      </div>
      <div>
        <input type="text" v-model="user.password" />
        <!-- <input type="text" name="" id=""> -->
      </div>
      <div><button @click="login">登录</button></div>
      <!-- <div><button @click="$router.push('/index')">登录</button></div> -->
    </div>
  </div>
</template>
<script>
import { reqUserLogin } from "../../util/request";
import { mapActions, mapGetters } from "vuex";
export default {
  components: {},
  data() {
    return {
      user: {
        username: "",
        password: "",
      },
    };
  },
  methods: {
    ...mapActions({
      requsetUserLogin: "user/requsetUserLogin",
    }),
    // 登录
    login() {
      reqUserLogin(this.user).then((res) => {
        this.$router.push("/index");
        this.requsetUserLogin(res.data.list);
        // console.log(res.data.list);
      });
      console.log(111);
    },
  },
  mounted() {},
};
</script>
<style scoped>
.login {
  width: 100vw;
  height: 100vh;
  background: linear-gradient(to right, #553443, #303D60);
}
.con {
  position: relative;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 360px;
  height: 260px;
  background: #fff;
  border-radius: 10px;
  text-align: center;
  overflow: hidden;
}
.con h2 {
  margin: 30px;
}
.con input {
  margin-bottom: 20px;
  width: 60%;
  height: 30px;
  font-size: 24px;
}
.con button {
  width: 60%;
  background: #409EFF;
  height: 30px;
  border: none;
  color: #fff;
  font-size: 20px;
}
</style>