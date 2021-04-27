<template>
  <Layout class="l_blog_container">
    <h1>{{$page.blog.title}}</h1>
    <p class="l_blog">
      <span>Date</span>
      <span>{{$page.blog.created_at | date('MMM DD, YYYY') }}</span>
    </p>
    <p v-html="mdToHtml($page.blog.content)"></p>
  </Layout>
</template>
<page-query>
  query($id: ID!){
    blog(id: $id){
      id,
      title,
      content,
      created_at
    }
  }
</page-query>
<script>
import MarkdownIt from 'markdown-it'
export default {
  methods:{
  //  将md文件转换成html字符串
   mdToHtml(text){
     const _this = this
      const md = new MarkdownIt()
      let html = md.render(text)
      html = html.replace(/<img [^>]*src=['"]([^'"]+)[^>]*>/gi, function (match, capture) {
        const src = _this.GRIDSOME_API_URL + capture
        return `<image src='${src}' alt='图片' style='width: 100%'></image>`
      });
      return html
    }
  }
}
</script>

<style lang='scss' scoped>
.l_blog_container{
  max-width: 860px;
  .l_blog{
    display: flex;
    flex-direction: column;
    margin-bottom: 50px;
  }
}
</style>