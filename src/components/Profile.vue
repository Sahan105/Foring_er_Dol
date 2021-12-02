<template>
  <!-- <div class="list-group" id="list-group">
			<a href="#" class="list-group-item clearfix"><i class="icon-user pr-3"></i>Profile</a>
			<a href="#" class="list-group-item clearfix"> <i class="icon-laptop2 pr-3"></i>My Events</a>
			<a href="#" class="list-group-item clearfix"><i class="icon-envelope2 pr-3"></i>My Hotels </a>
			<a href="#" class="list-group-item clearfix"><i class="icon-cog pr-3"></i>Settings</a>
			<a href="#" class="list-group-item clearfix"><i class="icon-line2-logout pr-3"></i>Logout </a>
		</div> -->
  <div class="dashboard">
    <tabs
      id="list-group"
      :options="{ useUrlFragment: false }"
      @clicked="tabClicked"
      @changed="tabChanged"
      nav-item-class=""
    >
      <tab name="Profile">
        <div id="row">
          <div class="col-12">
            <img
              src="../assets/images/magazine/1.jpg"
              class="alignleft img-circle img-thumbnail"
              alt="Avatar"
            />
            <div class="heading-block noborder">
              <h3>Test</h3>
              <span
                >Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsum
                laboriosam, dignissimos veniam obcaecati!</span
              >
            </div>
            <button
              type="submit"
              class="button button-3d nomargin"
              id="logout-button"
              name="login-form-submit"
              value="logout"
              @click="logout"
            >
              Logout
            </button>
          </div>
        </div>
      </tab>
      <tab name="My Events">
        <div id="row">This is the content of the second tab</div>
      </tab>
      <tab name="My Hotels">
        <div id="row">
          The fragment that is appended to the url can be customized
        </div>
      </tab>
      <tab name="Settings">
        <div id="row">the url can be customized that is appended to</div>
      </tab>
    </tabs>
  </div>
</template>

<script>
import { Tab, Tabs } from "vue3-tabs-component";

export default {
  components: {
    Tab,
    Tabs,
  },
  methods: {
    logout() {
      this.$router.replace({ path: "/" });
    },
  },
};
</script>

<style scoped>
.dashboard {
  margin-top: 6%;
  padding-bottom: 5%;
}
#list-group {
  text-align: left;
  font-size: 1.6rem;
  width: 20%;
  margin-left: 20%;
}
#row {
  width: 500px;
  margin-top: -49%;
  margin-left: 120%;
  margin-bottom: 40%;
}
#row img {
  height: 170px;
  width: 170px;
}
#row h3,
span {
  text-align: left;
}
</style>
