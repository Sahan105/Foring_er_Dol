<template>
  <div id="footer-gap">
    <div class="row clearfix">
      <div class="col-md-4">
        <div class="widget clearfix">
          <div>
            <div class="footer-contant">
              <div class="footer-logo">
                <router-link :to="{ path: '/' }">
                  <img
                    alt="logo"
                    src="../assets/images/icons/Foringer-Dol.png"
                  />
                </router-link>
              </div>
              <div
                class="clearfix"
                id="icons"
                data-class-lg="fright"
                data-class-md="fright"
                data-class-sm="fright"
                data-class-xs=""
                data-class-xxs=""
              >
                <a
                  href="https://www.facebook.com/travelforing/"
                  target="_blank"
                  class="social-icon si-rounded si-small si-colored si-facebook"
                >
                  <i class="icon-facebook"></i>
                  <i class="icon-facebook"></i>
                </a>
                <a
                  href="https://instagram.com/foringer_dol?utm_medium=copy_link"
                  target="_blank"
                  class="
                    social-icon
                    si-rounded si-small si-colored si-instagram
                  "
                >
                  <i class="icon-instagram"></i>
                  <i class="icon-instagram"></i>
                </a>
                <a
                  href="https://youtube.com/channel/UC-CGAoKw4Cf4xJt8kT8B-ZQ"
                  target="_blank"
                  class="social-icon si-rounded si-small si-colored si-youtube"
                >
                  <i class="icon-youtube"></i>
                  <i class="icon-youtube"></i>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="col-md-8 col-sm-6 bottommargin">
        <div class="col-md-4 col-sm-6 bottommargin">
          <div class="">
            <h3>Office Location:</h3>
            <address style="font-size: 1.7rem">
              Sector: 11, Road: 14, House: 76<br />
              Uttara, Dhaka<br />
            </address>
          </div>
        </div>
        <div class="col-md-4 col-sm-6 bottommargin">
          <div class="">
            <h3>Call Us On:</h3>
            <address style="font-size: 1.7rem">
              01880089100<br />01880089101<br />01880089102<br />
            </address>
          </div>
        </div>
        <div class="col-md-4 col-sm-6 bottommargin">
          <div>
            <h3>Email Us:</h3>
            <address style="font-size: 1.7rem">travelforing@gmail.com</address>
          </div>
        </div>
      </div>

      <div id="copyrights">
        <div class="container center uppercase clearfix">
          &copy; 2021 Developed by
          <a href="https://www.facebook.com/catchbitflex" target="_blank"
            >BitFlex </a
          >|
          <a href="https://www.facebook.com/catchbangladesh" target="_blank"
            >Catch Bangladesh</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>
<style scoped>
#footer-gap {
  padding-top: 2%;
}
.title {
  font-size: 1.8rem;
}
.row {
  padding-top: 2%;
  padding-bottom: -4%;
  background-color: #dddddd;
}
.row img {
  height: 65px;
  width: 210px;
}
#icons {
  padding-left: 39%;
}
#copyrights {
  margin-top: -6%;
  width: 100%;
  background-color: #cfcfcf;
}
</style>
