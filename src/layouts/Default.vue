<template>
  <div class="layout">
    <header class="header">
      <div class="h_container">
        <strong>
          <g-link to="/">Home</g-link>
        </strong>
        <nav class="nav">
          <g-link class="nav__link" to="/blogs">Blog</g-link>
          <g-link class="nav__link" to="/contact">Say Hi!</g-link>
        </nav>
      </div>
    </header>
    <slot/>
    <footer class="footer">Copyright © 2021</footer>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style lang='scss'>
body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
}

.layout {
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 84px;
}

.header {
  margin-bottom: 20px;
  height: 80px;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 20;
  background-color: #fff;
  .h_container{
    height: 100%;
    max-width: 860px;
    margin: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}

.nav__link {
  margin-left: 20px;
  text-decoration:none;
  outline: none;
}
.footer{
  padding: 80px 0;
  max-width: 860px;
  margin: 0 auto;
}
</style>
