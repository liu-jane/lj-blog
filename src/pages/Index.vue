<template>
  <Layout class="l_project_container">
    <h1 class="l_title l_center">Simplicity. Aesthetics. Value.</h1>
    <p class="l_desc l_center">Hi there, I'm an independent Digital Designer & Art Director focused on digital design for brands that like to have fun.</p>
    <div class="l_projects">
      <g-link class="l_project" v-for="project in $page.projects.edges" :key="project.node.id" :to="'/project/' + project.node.id">
        <img class="l_cover" :src="GRIDSOME_API_URL + project.node.cover.url" alt="">
        <p class="l_project_title l_center">{{project.node.title}}</p>
        <p class="l_center">photography {{project.node.color}}</p>
      </g-link>
    </div>
  </Layout>
</template>
<page-query>
  query{
    projects: allProject(sortBy: "created_at", order: ASC){
      edges{
        node{
          id,
          title,
          color,
          cover{
            url
          }
        }
      }
    }
  }
</page-query>
<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style scoped lang='scss'>
.l_project_container{
  max-width: 860px;
  .l_center{
  text-align: center;
  }
  .l_desc{
    opacity: .6;
    margin-bottom: 50px;
  }
  .l_projects{
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-row-gap: 40px;
    grid-column-gap: 30px;
    .l_project{
      grid-column-start: auto;
      grid-column-end: span 2;
      text-decoration:none;
      outline: none;
      color: #333;
      .l_cover{
        width:100% ;
        height: 560px;
        object-fit: cover;
        transition: all .2s ease;
        &:hover{
          transform: scale(1.02);
        }
      }
      .l_project_title{
        font-weight: bold;
      }
    }
    @media screen and (min-width: 860px){
      .l_project{
        grid-column-start: auto;
        grid-column-end: span 1;
      }
    }
    @media screen and (min-width: 860px){
      .l_project:nth-child(3n+1){
        grid-column-start: auto;
        grid-column-end: span 2;
      }
    }
  }
}



</style>
