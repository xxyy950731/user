<template>
    <div class="customers container">
      <Welcome v-if="admin" v-bind:ad="admin"></Welcome>
      <Alert v-if="alert" v-bind:message="alert"></Alert>
      <h1 class="page-header">用户管理系统</h1>
      <input type="text" class="form-control" placeholder="搜索" v-model="filterInput">
      <br>
      <table class="table table-stripe">
        <thead>
        <tr>
          <th>姓名</th>
          <th>电话</th>
          <th>邮箱</th>
          <th></th>
        </tr>
        </thead>

        <tbody>
        <tr v-for="customer in filterBy(customers,filterInput)">
          <td>{{ customer.name }}</td>
          <td>{{ customer.phone }}</td>
          <td>{{ customer.email }}</td>
          <td><router-link class="btn btn-default" v-bind:to="'/customer/'+customer.id">详情</router-link></td>
        </tr>
        </tbody>
      </table>
    </div>
</template>

<script>
  import Alert from "./Alert"
  import Welcome from "./Welcome"
    export default {
        name: "Customers",
        data(){
          return{
            customers:[],
            alert:"",
            filterInput:"",
            admin:""
          }
        },
        methods:{
          fetchCustomers(){
            this.$http.get("http://localhost:3000/users").then(function(data){
              this.customers=data.body
            })
          },
          filterBy(customers,vaule){
            return customers.filter(function (customer) {
              return customer.name.match(vaule)
            })
          }
        },
        created(){
            this.fetchCustomers();
            if (this.$route.query.alert){
              this.alert=this.$route.query.alert;
            }
            if (this.$route.query.admin){
              this.admin=this.$route.query.admin;
            }
        },
        updated() {
          this.fetchCustomers();
        },
      components:{
          Alert,
          Welcome
      }
    }
</script>

<style scoped>

</style>
