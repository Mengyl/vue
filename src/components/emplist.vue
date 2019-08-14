<template>
  <div>
    <table class="table table-bordered">
				<caption>雇员信息列表</caption>
				<thead>
					<tr>
						<th>姓名</th>
						<th>年龄</th>
						<th>性别</th>
						<th>操作</th>
					</tr>
				</thead>
				<tbody>
					<tr v-for="(emp,index) in emps">
						<td hidden>{{emp.eid}}</td>
						<td>{{emp.name}}</td>
						<td>{{emp.age}}</td>
						<td>{{emp.sex}}</td>
						<td>
							<button class="btn-default btn" @click="del(emp.eid)">删除</button>
							<button class="btn-default btn" @click="update(emp.eid)">修改</button>
							<!--<a  href="#/empupdate?eid=emp.eid">修改</a>-->
						</td>
					</tr>

				</tbody>
			</table>    
  </div>
</template>

<script>
export default {
  name: 'emplist',
  data () {  	
    return {
      emps:[]
    }
  },
  created:function(){
  	this.loademp();
  },
  methods:{
  	loademp:function(){
	  	this.$http.get("http://localhost:8083/emp").then(
	  		function(res){
		  		this.emps=res.body;
		  	},function(){
		  		console.log("数据加载失败！");
	  		}
		  )
	  },
  	del:function(eid){
  		console.log(this.emps);
  		this.$http.delete("http://localhost:8083/emp",{
  			params:{
  				eid:eid
  			}
  		}).then(
	  		function(res){
		  //	alert("删除成功！");
			  	this.loademp();
		  	},function(){
		  		console.log("数据加载失败！");
	  		}
		  )
  	},  	
  	update:function(eid){
  		this.$router.push({
  			path:"/empupdate",
  			query:{
  				"eid":eid
  			}
  		})
  	}
  	
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
th{
	text-align: center;
}
</style>
