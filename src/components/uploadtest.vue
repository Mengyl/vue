<template>
  <div>
   <!-- <form action="http://localhost:8083/upload" method="post" enctype="multipart/form-data">
			<input type="file" name="file"/>
			<input type="submit" value="上传"/>
		</form>  --> 
		测试
		clone测试
		<input type="file" name="file"/>
		<input type="submit" value="上传" @click="upload"/>
  </div>
</template>

<script>
export default {
  name: 'uploadtest',  
  methods:{
  	upload:function(){
  		var formData=new FormData();
  		formData.append("file",document.querySelector("input[name=file]").files[0]);
  		formData.append("name","zhangsan");
  		var config={
  			headers:{
  				"Content-type":"multipart/form-data",
  			}
  		}
  		this.$http.post("http://localhost:8083/upload",formData,config).then(
  			function(res){
  				console.log(res);
  				console.log(res.bodyText);
  				alert("文件上传成功！");
  				this.$router.go(0);//刷新当前页面
  			},function(error){
  				console.log(error.body.message);//打印错误信息
  				alert("文件上传失败！");
  			}
  		)
  	}
  	
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
