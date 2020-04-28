<template>
  <div id="app">
		<div class="nav">
			Navbar
		</div>


    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
#app {
  text-align: center;

}
.nav{
	width:100%;
	background: #cdc17b;
	border-bottom: 2px solid grey;
	color: black;
	font-size: 1.5rem;
	font-weight: 600;
}
</style>
