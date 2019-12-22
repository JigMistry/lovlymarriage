<template>
  <div id="app">
    <div class="wrapper flower_fixed_body">
      <header class="header_section">
        <div class="topbar">
          <div class="container">
              <div class="row">
                  <div class="col col-xs-12">
                      <div class="site-logo">
                          <a>
                              <h1>Lovlesh &amp; Komal</h1>
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
                  <h2>Lovlesh &amp; Komal</h2>
              </div>
              <div class="wedding-date">
                  <span>17 Jan 2020</span>
              </div>
            </div>
          </div>
          <b-carousel
            id="carousel-1"
            v-model="slide"
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
export default {
  name: 'app',
  components: {
    
  }
}
</script>

<style lang="scss">
  #app {
    font-family: 'Niconne', cursive, 'Avenir', Helvetica, Arial, sans-serif;
  }
  .wrapper {
    .flower_fixed_body {
      
    }
    &:before {
      content: "";
      background: url(./assets/flower1.png) center center/100% no-repeat local;
      width: 250px;
      height: 184px;
      position: fixed;
      left: -100px;
      bottom: 0;
      z-index: 1;
    }
    &:after {
      content: "";
      background: url(./assets/flower2.png) center center/100% no-repeat local;
      width: 250px;
      height: 345px;
      position: fixed;
      right: -70px;
      top: 200px;
      z-index: 1;
    }
    .hero-slider {
      /*width: 100%;*/
      /*height: calc(100vh - 210px);*/
      min-height: 650px;
      display: -webkit-box;
      display: -ms-flexbox;
      display: flex;
      /*position: relative;*/
      z-index: 0;

      @media (max-width: 767px) {
        height: 500px;
        min-height: auto;
      }
      .slide-main-text {
        width: 100%;
        height: 100%;
        position: absolute;
        left: 0;
        top: 0;
        background-size: cover;
        background-position: center;
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-pack: center;
        -ms-flex-pack: center;
        justify-content: center;
        -webkit-box-align: center;
        -ms-flex-align: center;
        align-items: center;
        text-align: center;
        z-index: 10;
        .container {
          padding-right: 15px;
          padding-left: 15px;
          margin-right: auto;
          margin-left: auto;
          .wedding-date {
            color: #fff;
            font-weight: 300;
            font-size: 18px;
            font-size: 1.2rem;
            text-transform: uppercase;
            display: inline-block;
            position: relative;
            letter-spacing: 2px;
            text-shadow: 0px 3px 7px rgba(0, 0, 0, 0.35);
            &:before {
              content: "";
              background: #fff;
              width: 35px;
              height: 1px;
              position: absolute;
              left: -50px;
              top: 13px;
            }
            &:after {
              content: "";
              background: #fff;
              width: 35px;
              height: 1px;
              position: absolute;
              right: -50px;
              top: 13px;
            }
          }
          h2 {
            font-family: 'Niconne', cursive, "aphroditeslimtextregular";
            font-size: 80px;
            font-size: 2.5rem;
            color: #fff;
            margin: 0.3em 0 0;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.6);
          }
          .wedding-date {
            margin: 2em 0 3em;
          }
          &:before {
            display: table;
            content: " ";
          }
        }
      }
      .img-fluid {
        height: max-content;
      }
    }
    .header_section {
      .topbar {
        background: #fff;
        text-align: center;
        padding: 50px 0 30px;
        border-bottom: 1px solid #efefef;
        position: relative;
        z-index: 1;
        .container {
          padding-right: 15px;
          padding-left: 15px;
          margin-right: auto;
          margin-left: auto;
          .site-logo {
            display: inline-block
            a{
                text-decoration: none;
                -webkit-transition: all 0.2s;
                -moz-transition: all 0.2s;
                -o-transition: all 0.2s;
                -ms-transition: all 0.2s;
                transition: all 0.2s;
            }
            h1 {
                  font-family: 'Niconne', cursive, "aphroditeslimtextregular";
                  font-size: 30px;
                  font-size: 2rem;
                  margin: -0.12em 0 0.5em;
                  color: #202a41;
                  +span {
                    color: #797979;
                    font-weight: 300;
                    font-size: 12px;
                    font-size: 0.8rem;
                    text-transform: uppercase;
                    display: inline-block;
                    position: relative;
                    letter-spacing: 2px;
                    &:before{
                      content: "";
                      background: #ece9e9;
                      width: 35px;
                      height: 1px;
                      position: absolute;
                      left: -50px;
                      top: 9px;
                    }
                    &:after {
                      content: "";
                      background: #ece9e9;
                      width: 35px;
                      height: 1px;
                      position: absolute;
                      right: -50px;
                      top: 9px;
                    }
                  }
            }
          }
        }
      }  
    }
  }
</style>
