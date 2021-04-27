<template>
  <Layout>
    <ul class="l_blogs">
      <li class="l_blog">
        <h2>a wise person once said...</h2>
      </li>
      <li class="l_blog" v-for="blog in $page.blogs.edges" :key="blog.node.id">
        <g-link class="l_item" :to="'/blog/' + blog.node.id">
          <h2>{{blog.node.title}}</h2>
          <p class="l_subtitle">{{blog.node.subtitle}}</p>
        </g-link>
      </li>
    </ul>
  </Layout>
</template>
<page-query>
  query{
    blogs: allBlog{
      edges{
        node{
          id,
          title,
          subtitle
        }
      }
    }
  }
</page-query>
<script>
export default {

}
</script>

<style lang='scss' scoped>
*{
  margin: 0;
  padding: 0;
}
.l_blogs{
  list-style: none;
  padding: 0;
  overflow: hidden;
  .l_blog{
    padding: 70px 0;
    &:hover{
      background-color: #eee;
    }
    .l_item{
      display: block;
      transition: all .2s ease;
      max-width: 860px;
      box-sizing: border-box;
      padding: 0 180px;
      margin: 0 auto;
      text-decoration:none;
      outline: none;
      color: #333;
      .l_subtitle{
        margin: 16px 0;
      }
      &:hover{
        transform: translateX(10%);
      }
    }
    &:first-child{
      opacity: .1;
      padding: 0;
    }
  }
}
</style>