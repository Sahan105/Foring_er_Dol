<template>
  <div>
    <Header />
    <Profile />
    <Footer />
  </div>
</template>
<script>
import Header from '../components/Navbar';
import Profile from '../components/Profile';
import Footer from '../components/Footer1';
export default {
  middleware({ store, redirect }) {
      // If the user is not authenticated
      if (store.state.login.authenticated == false) { 
        return redirect('/login')
      }
  },
  components: {
    Header,
    Profile,
    Footer
  },
  methods: {
    logout(){
      this.$store.commit("login/setAuthentication", false)
      this.$router.push({ path: '/login'})
    }
  } 
}
</script>