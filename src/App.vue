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
                              <span>Mr. &amp; Mrs.</span>
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
              :img-src="require('@/assets/img2.jpg')"
              img-height="200"
            ></b-carousel-slide>
            <b-carousel-slide :img-src="require('@/assets/img3.jpg')">
            </b-carousel-slide>

            <b-carousel-slide :img-src="require('@/assets/img4.jpg')"></b-carousel-slide>

            <!-- <b-carousel-slide>
              <template v-slot:img>
                <img
                  class="d-block img-fluid w-100"
                  width="1024"
                  height="240"
                  src="@/assets/img4.jpg"
                  alt="image slot"
                >
              </template>
            </b-carousel-slide> -->
          </b-carousel>
        </div>
      </section>
      <section class="invitation-section section-padding">
            <div class="container">
                <div class="row" @click="showOnMap">
                    <div class="col col-xs-12">
                        <div class="invitation-box" @click="showOnMap">
                            <div class="left-vec"></div>
                            <div class="right-vec"></div>
                            <div class="inner">
                                <h2>Save the Date</h2>
                                <span>For the wedding of</span>
                                <h4>Lovelesh &amp; Komal</h4>
                                <p>Friday 17 January 2020 <br>At 6'O clock PM <br> Ashoka Garden <br>Hasanpur Chowk, Hodal (Palwal), Haryana</p>
                            </div>
                            <div @click="showOnMap">
                              <b-button variant="outline-primary" @click="showOnMap">Show on map</b-button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <section class="gallery-section">
            <div class="container">
                <div class="row">
                    <div class="col col-lg-6 col-lg-offset-3 col-md-8 col-md-offset-2 col-sm-10 col-sm-offset-1">
                        <div class="section-title">
                            <h2>Captured Moments</h2>
                            <h5>A moment lasts all of a second, but the memory lives on forever.
                                Here are some beautiful memories from ring ceremony</h5>
                            <b-carousel
                              id="carousel-1"
                              :interval="4000"
                              indicators
                              background="#ababab"
                              img-width="1024"
                              img-height="250"
                              style="text-shadow: 1px 1px 2px #333;"
                            >
                              <b-carousel-slide
                                :img-src="require('@/assets/fun1.jpg')"
                              ></b-carousel-slide>
                              <b-carousel-slide :img-src="require('@/assets/fun2.jpg')">
                              </b-carousel-slide>
                              <b-carousel-slide :img-src="require('@/assets/fun3.jpg')"></b-carousel-slide>
                              <b-carousel-slide :img-src="require('@/assets/fun4.jpg')"></b-carousel-slide>
                            </b-carousel>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <section class="wishes-section">
          <div class="row" >
            <div class="section-title">
              <h3>Love is in the air</h3>
              <h5>I fall in love, <br>over and over again, with you. <br>Always with you.</h5>
              <!-- <h4>I fall in love, over and over again, with you. <br>Always with you.</h4> -->
            </div>
            <div class="section-content">
              <!-- <b-button variant="outline-primary">
                Write
              </b-button> -->
              <!-- <div>I fall in love, over and over again, with you. Always with you.</div> -->
            </div>
          </div>
        </section>
        <section>
          <div class="wish-list-section">
            
          </div>
        </section>
        <div class="row footer">
          <h6>Made with <pre>    </pre> by Jignesh</h6><Heart/>
        </div>
    </div>
    <div class="back-to-top" style="display: inline;" v-on:click="onTop()" v-show="backToTop">
      <div class="arrow"></div>
    </div>
  </div>
</template>

<script>
import '@/assets/scss/custom.scss';
import HeartLoader from '@/components/HeartLoader.vue';
import Heart from '@/components/Heart.vue';
// import moment from 'moment';
export default {
  name: 'app',
  components: {
    HeartLoader,
    Heart,
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
      backToTop: false,
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
    this.countdowninterval = setInterval(() => {
      now = new Date().getTime();
      distance = self.marriageDate - now;
      self.cdDays = Math.floor(distance / (1000 * 60 * 60 * 24));
      self.cdHours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      self.cdMins = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      self.cdSecs = Math.floor((distance % (1000 * 60)) / 1000);
    }, 1000);
    window.addEventListener("scroll", self.windowScrolled);
  },
  methods: {
    onTop() {
      window.scroll({
        top: 0,
        behavior: 'smooth'
      });
    },
    windowScrolled(e) {
      if(window.scrollY > 250) {
        this.backToTop = true;
      } else {
        this.backToTop = false;
      }
    },
    showOnMap(e) {
      e.stopPropagation();
      let url = `https://www.google.com/maps/place/Ashoka+Garden/@27.8951793,77.3742437,15z/data=!4m5!3m4!1s0x0:0x84fdf2e7bb6461a!8m2!3d27.8951793!4d77.3742437`
      let inAppBrowser = window.open(url, '_blank', 'location=yes');
    }
  },
  beforeDestroy() {
    clearInterval(this.countdowninterval);
    window.removeEventListener('scroll', this.windowScrolled);
  }
}
</script>

<style lang="scss">
  @import '@/assets/scss/app.scss';
</style>
