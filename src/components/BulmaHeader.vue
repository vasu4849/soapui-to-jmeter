<template>
  <div class="header">
    <nav class="navbar" role="navigation" aria-label="main navigation">
      <div >
      <div class="navbar-brand">
        <a href="#" class="navbar-item">
          <img src="../assets/soapui-logo.png" alt="SOAP UI" width="120" height="40">
        </a>
        <a href="#" class="navbar-item">
          <span class="icon is-small">
            <i :class="`fas fa-${arrow}`"></i>
          </span>
        </a>
        <a class="navbar-item" href="#">
          <img src="../assets/jmeter-logo.png" width="120" height="40">
        </a>
      </div>
      </div>
      <div>
      <div id="navbarBasicExample" class="navbar-menu is-active">
        <div class="navbar-start">
          <a class="navbar-item button is-info">
            <strong>Home</strong>
          </a>

          <a class="navbar-item button is-info">
            <strong>Documentation</strong>
          </a>

          <a class="navbar-item button is-info">
            <strong>Queued Requests</strong>
          </a>
          <a class="navbar-item button is-info" is-static>
            <strong>Metrics</strong>
          </a>
        </div>
      </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  data () {
    return {
      'arrow': 'arrow-alt-circle-right'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/*
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.header{
  max-width: 1080px;
  padding: 20px;
  padding-left: 80px;
  display: 0 auto;
}
.icon{
  height: 40;
  color: brown;
}
.is-info {
  padding: 10px;
  margin-right: 10px;
}
*/
</style>
