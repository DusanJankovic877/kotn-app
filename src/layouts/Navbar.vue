<template>
    <div>
  <b-navbar toggleable="lg" type="dark" variant="light">
    <b-navbar-brand href="#">
        <router-link to="/">Admin panel</router-link> 
    </b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
    <b-collapse id="nav-collapse" is-nav>
    <b-navbar-nav>
        <b-nav-item href="#">
            <router-link to="/posts">Posts</router-link> 
        </b-nav-item>
        <b-nav-item href="#">
            <router-link to="/create">Create Post</router-link> 
        </b-nav-item>
    </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <p>Dobro došli {{loggedUser.name}}</p>           
        <b-button @click="handleLogout">Odjavi se</b-button>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
</template>
<script>
import { mapActions, mapGetters } from 'vuex'
export default {
  data(){
    return {

    }
  },
  methods: {
    ...mapActions(['logout']),
    async handleLogout(){
      await this.logout({"token": localStorage.token})
      if(this.$route.path != '/')this.$router.push('/');

    }
  },
  computed:{
    ...mapGetters(['loggedUser'])
  }
}
</script>

<style scoped>
a{
    color: black;
}
p{
  margin-top:12px;
}
button {
  margin-left: 10px;
}
</style>