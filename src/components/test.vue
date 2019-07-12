<template>
    <div>
      <div class="container">
        <form class="form-signin" v-on:submit="login">
          <h2 class="form-signin-heading">Please sign in</h2>
          <label for="inputEmail" class="sr-only">Email address</label>
          <input type="email" id="inputEmail" class="form-control" placeholder="Email address" required autofocus v-model="adm">
          <label for="inputPassword" class="sr-only">Password</label>
          <input type="password" id="inputPassword" class="form-control" placeholder="Password" required>
          <div class="checkbox">
            <label>
              <input type="checkbox" value="remember-me"> Remember me
            </label>
          </div>
          <button class="btn btn-lg btn-primary btn-block" type="submit">Sign in</button>
        </form>
      </div> <!-- /container -->
      <!-- IE10 viewport hack for Surface/desktop Windows 8 bug -->
    </div>
</template>

<script>
    export default {
        name: "test",
        data(){
          return{
            msg:"",
            adm:""
          }
        },
        methods:{
          login(){
            this.$router.push({path:"/Customers",query:{admin:this.adm}})
          }
        }
    }
</script>

<style scoped>

</style>
