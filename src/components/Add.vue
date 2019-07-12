<template>
  <div class="add container">
    <Alert v-if="alert" v-bind:message="alert"></Alert>
    <h1 class="page-header">添加用户</h1>
    <form v-on:submit="addCustomer">
      <div class="well">
        <h4>用户信息</h4>
        <div class="form-group">
          姓名
          <input type="text" class="form-control" placeholder="姓名" v-model="customer.name">
        </div>
        <div class="form-group">
          电话
          <input type="text" class="form-control" placeholder="电话" v-model="customer.phone">
        </div>
        <div class="form-group">
          邮箱
          <input type="text" class="form-control" placeholder="邮箱" v-model="customer.email">
        </div>
        <div class="form-group">
          学历
          <input type="text" class="form-control" placeholder="学历" v-model="customer.education">
        </div>
        <div class="graduationschool">
          毕业学校
          <input type="text" class="form-control" placeholder="毕业学校" v-model="customer.graduationschool">
        </div>
        <div class="form-group">
          职业
          <input type="text" class="form-control" placeholder="职业" v-model="customer.profession">
        </div>
        <div class="form-group">
          <p>个人简介</p>
          <textarea class="from-control"  rows="10" v-model="customer.profile"></textarea>
        </div>
        <button type="submit" class="btn btn-primary">添加</button>
      </div>
    </form>
  </div>
</template>

<script>
  import Alert from './Alert'
  export default {
    name: 'Add',
    components: {Alert},
    data(){
      return{
        customer:{},
        alert:""
      }
    },
    methods:{
      addCustomer(e){
        if(!this.customer.name||!this.customer.phone||!this.customer.email){
          this.alert="请添加对应信息！"
        }else {
          let newCustomer={
            name:this.customer.name,
            phone:this.customer.phone,
            email:this.customer.email,
            education:this.customer.education,
            graduationschool:this.customer.graduationschool,
            profession:this.customer.profession,
            profile:this.customer.profile
          }

          this.$http.post("http://localhost:3000/users",newCustomer).then(function (data) {
            this.$router.push({path:"/Customers",query:{alert:"用户信息添加成功！"}})
          e.preventDefault()
          })
        }
        e.preventDefault()
      }
    }
  }
</script>

<style scoped>

</style>
