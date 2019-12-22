<template>
  <div id="app">
    <div class="wrapper flower_fixed_body">
      <div class="preloader" v-if="loader">
            <HeartLoader/>
        </div>
      <header class="header_section">
        <div class="topbar">
          <div class="container">
              <div class="row">
                  <div class="col col-xs-12">
                      <div class="site-logo">
                          <a>
                              <h1>Lovelesh &amp; Komal</h1>
                              <span>Just Married</span>
                          </a>
                      </div>
                  </div>
              </div>
          </div>
        </div>
      </header>
      <section class="hero-slider">
        <div>
          <div class="slide-main-text">
            <div class="container">
              <div class="slide-title">
                  <h2>Lovelesh &amp; Komal</h2>
              </div>
              <div class="wedding-date">
                  <span>17 Jan 2020</span>
              </div>
              <div id="clock">
                <div class="box">
                  <div>{{cdDays}}</div>
                  <span>Days</span> 
                </div>
                <div class="box">
                  <div>{{cdHours}}</div> 
                  <span>Hours</span> 
                </div>
                <div class="box">
                  <div>{{cdMins}}</div> 
                  <span>Mins</span> 
                </div>
                <div class="box">
                  <div>{{cdSecs}}</div> 
                  <span>Secs</span> 
                </div>
              </div>
            </div>
          </div>
          <b-carousel
            id="carousel-1"
            :interval="4000"
            indicators
            background="#ababab"
            img-width="1024"
            img-height="480"
            style="text-shadow: 1px 1px 2px #333;"
          >
            <b-carousel-slide
              img-src="https://picsum.photos/1024/480/?image=52"
            ></b-carousel-slide>
            <b-carousel-slide img-src="https://picsum.photos/1024/480/?image=54">
            </b-carousel-slide>

            <b-carousel-slide img-src="https://picsum.photos/1024/480/?image=58"></b-carousel-slide>

            <b-carousel-slide>
              <template v-slot:img>
                <img
                  class="d-block img-fluid w-100"
                  width="1024"
                  height="480"
                  src="https://picsum.photos/1024/480/?image=55"
                  alt="image slot"
                >
              </template>
            </b-carousel-slide>
          </b-carousel>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import '@/assets/scss/custom.scss';
import HeartLoader from '@/components/HeartLoader.vue';
// import moment from 'moment';
export default {
  name: 'app',
  components: {
    HeartLoader
  },
  computed: {

  },
  data() {
    return {
      marriageDate: new Date("Jan 17, 2020 18:00:00").getTime(),
      slide: true,
      loader: true,
      countdowninterval: null,
      cdDays: null,
      cdHours: null,
      cdSecs: null,
      cdMins: null,
    }
  },
  mounted() {
    let days;
    let hours;
    let minutes;
    let seconds;
    let distance;
    let now;
    setTimeout(() => {
      this.loader = false;
    }, 5000);
    let self = this;
    this.countdowninterval = setInterval(function() {
      // Get today's date and time
      now = new Date().getTime();
      distance = self.marriageDate - now;
      // Time calculations for days, hours, minutes and seconds
      self.cdDays = Math.floor(distance / (1000 * 60 * 60 * 24));
      self.cdHours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      self.cdMins = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      self.cdSecs = Math.floor((distance % (1000 * 60)) / 1000);
    }, 1000);
  },
  beforeDestroy() {
    clearInterval(this.countdowninterval)
  }
}
</script>

<style lang="scss">
  @import '@/assets/scss/app.scss';
</style>
