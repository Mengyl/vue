<template>
  <div id="app">
    <div class="container" id="app">
			<nav class="navbar navbar-default " role="navigation">
				<div class="container-fluid">
					<div class="navbar-header">
						<a class="navbar-brand active" href="javascript:void(0)">首页</a>
					</div>
					<div>
						<ul class="nav navbar-nav">
							<li>
								<router-link to="/">雇员列表</router-link>
							</li>
							<li>
								<router-link to="/empadd">雇员新增</router-link>
							</li>							
							<li>
								<router-link to="/uploadtest">上传文件</router-link>
							</li>
							<!--<input type="text" placeholder="search"/>-->
						</ul>
						<!--<form action="search" class="navbar-form navbar-left" role="search">
							<div class="form-group">
								<input type="text" name="ename" class="form-control" />
							</div> 
							<button type="submit" class="btn btn-default">search</button>
							<a href="add.jsp" class="btn btn-default">Add</a>
						</form>	-->
					</div>
				</div>
			</nav>
			<router-view/>			
		</div>    
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
</style>
