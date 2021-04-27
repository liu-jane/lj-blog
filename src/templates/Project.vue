<template>
  <Layout class="l_project_container">
    <h1 class="l_title" :style="{color: $page.project.color}">{{$page.project.title}}</h1>
    <p class="l_category" :style="{color: $page.project.color}">
      <span>Categories</span>
      <span>photography pink</span>
    </p>
    <img class="l_cover" :src="GRIDSOME_API_URL + $page.project.cover.url" alt="">
  </Layout>
</template>
<page-query>
  query($id: ID!){
    project(id: $id){
      id,
      title,
      color,
      cover{
        url
      }
    }
  }
</page-query>
<script>
export default {

}
</script>

<style lang='scss' scoped>
.l_project_container{
  max-width: 860px;
  .l_title{
    margin-bottom: 40px;
  }
  .l_category{
    display: flex;
    flex-direction: column;
    margin-bottom: 50px;
  }
  .l_cover{
    max-width: 100%;
  }
}
</style>