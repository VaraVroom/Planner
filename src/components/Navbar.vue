<template>
    <nav class="main-nav">
        <RouterLink :to="{name:'HomePage'} ">Projects</RouterLink>|
        <RouterLink :to="{name:'AddProject'}">Add New Project</RouterLink>
    </nav>
</template>

<script>
export default{
};
</script>

<style>
.main-nav {
  text-align: center;
}
.main-nav a {
  display: inline-block;
  text-decoration: none;
  margin: 0 10px;
  color: black;
  font-size: 25px;
}
a.router-link-active {
  border-bottom: 3px solid ;
  padding-bottom: 4px;
  border-color: #fdd018;
}
</style>