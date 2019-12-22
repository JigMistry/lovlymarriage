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
export default {
  name: 'app',
  components: {
    HeartLoader
  },
  data() {
    return {
      slide: true,
      loader: true,
    }
  },
  mounted() {
    setTimeout(() => {
      this.loader = false;
    }, 5000);
  }
}
</script>

<style lang="scss">
  @import '@/assets/scss/app.scss';
</style>
