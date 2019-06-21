<template>
  <div>
    <b-navbar toggleable="lg" type="dark" class="header-background">
     <b-navbar-brand style="color:white" class="app-title" href="#">SOAPUI-Jmeter</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item  href="#"><span class="item-menu">Documentation</span></b-nav-item>
        <b-nav-item class="item-menu" href="#" disabled><span>Metrics</span></b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-item text="Lang" right>
          <span class="item-menu">Contact Us</span>
        </b-nav-item>

        <b-nav-item right>
          <!-- Using 'button-content' slot -->
          <span class="item-menu">Help</span>
        </b-nav-item>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
</template>

<script>
export default {
  data () {
    return {
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.app-title {
  font-size: 32px;
}
.item-menu {
  margin-left: 15px;
  font-weight: 600 !important;
  color:aliceblue;
}
.header-background{
  background-color: #002856;
}
</style>
