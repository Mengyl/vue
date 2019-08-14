<template>
  <div>
    <form class="form-horizontal" role="form">
				<div class="form-group">
					<label for="firstname" class="col-sm-1 control-label">姓名</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="name" v-model="emp.name" placeholder="请输入姓名">
					</div>
				</div>
				<div class="form-group">
					<label for="lastname" class="col-sm-1 control-label">年龄</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="age" v-model="emp.age" placeholder="请输入年龄">
					</div>
				</div>
				<div class="form-group">
					<label for="lastname" class="col-sm-1 control-label">性别</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="sex" v-model="emp.sex" readonly placeholder="请输入性别">
					</div>
				</div>
				<div class="form-group">
					<div class="col-sm-10 col-sm-offset-1">
						<button type="button" class="btn btn-default" @click="update">提交</button>
					</div>
				</div>
			</form>   
  </div>
</template>

<script>
export default {
  name: 'empupdate',
  data () {
    return {
     	emp:{
     		eid:0,
     		name:'',
     		age:'',
     		sex:''
     	},
     	emps:[]
    }
  },
  created:function(){
  	this.info();
  },
  methods:{
  	info:function(){
  		var eid=this.$route.query.eid;
  		this.$http.get("http://localhost:8083/getEmpById",{
  			params:{
  				eid:eid
  			}
  		}).then(function(res){
  			this.emp.name=res.body.name;
  			this.emp.age=res.body.age;
  			this.emp.sex=res.body.sex;  	
  			this.emp.eid=res.body.eid;
  		},function(error){
  			alert("数据加载失败！");
  		})
  	},
  	/*update:function(){
  		var eid=this.$route.query.eid;
  		this.$http.get("http://localhost:8083/empupdate",{
  			params:{
  				eid:eid,
     			age:this.emp.age
  			}  			
  		}).then(function(res){
  			alert("修改成功！");  			
  		},function(error){
  			alert("修改失败！");
  		})
  	}*/
  	
  	update:function(){
  		this.$http.put("http://localhost:8083/emp",{  			
  				eid:this.emp.eid,
  				name:this.emp.name,
     			age:this.emp.age,
     			sex:this.emp.sex     			
  		}).then(function(res){
  			alert("修改成功！");  		
  			/*this.$router.push({
  				path:'/'
  			})*/
  			this.$router.go(-1);
  		},function(error){
  			alert("修改失败！");
  		})
  	}
  	
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
