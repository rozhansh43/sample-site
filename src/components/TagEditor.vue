<template>
  <div>
    <b-carousel
      id="carousel-1"
      v-model="slide"
      :interval="4000"
      controls
      indicators
      background="#ababab"
      img-width="1024"
      img-height="480"
      style="text-shadow: 1px 1px 2px #333;"
      @sliding-start="onSlideStart"
      @sliding-end="onSlideEnd"
    >
      <!-- Text slides with image -->
      <b-carousel-slide
        caption="First slide"
        text="Nulla vitae elit libero, a pharetra augue mollis interdum."
        img-src="@/assets/Port_2_Background.jpg"
      ></b-carousel-slide>


      <!-- Slides with img slot -->
      <!-- Note the classes .d-block and .img-fluid to prevent browser default image alignment -->
      <b-carousel-slide>
        <template #img>
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

    <b-container>
      <b-col>
        <img src="@/assets/math-3QbOHeqZnE4-unsplash.jpg" />
      </b-col>

      <b-col>
        hhh
      </b-col>
    </b-container>

    <b-container fluid class="counters">
      <b-row>
        <b-col class="counter" data-count="150">{{ count }}</b-col>
        <b-col class="counter" data-count="150">{{ count }}</b-col>
        <b-col class="counter" data-count="150">{{ count }}</b-col>
      </b-row>
    </b-container>

    <b-container>
      <b-row>
        <b-col class="portfolio-box shadow">
          <b-card
            class="border-0"
            overlay
            img-src="https://img.demo.persina.com/unsafe/720x720/https://static.demo.persina.com/Products/Image/4583cdf554e1427c9b68f31513128765.jpg"
            img-alt="Card Image"
            text-variant="white"
          >
          </b-card>

          <div class="portfolio-info">
            <h4>project name goes here 6</h4>
            <p>category project</p>
          </div>
        </b-col>
        <b-col class="portfolio-box shadow">
          <b-card
            class="border-0"
            overlay
            img-src="https://img.demo.persina.com/unsafe/720x720/https://static.demo.persina.com/Products/Image/4583cdf554e1427c9b68f31513128765.jpg"
            img-alt="Card Image"
            text-variant="white"
          >
          </b-card>

          <div class="portfolio-info">
            <h4>project name goes here 6</h4>
            <p>category project</p>
          </div>
        </b-col>
        <b-col class="portfolio-box shadow">
          <b-card
            class="border-0"
            overlay
            img-src="https://img.demo.persina.com/unsafe/720x720/https://static.demo.persina.com/Products/Image/4583cdf554e1427c9b68f31513128765.jpg"
            img-alt="Card Image"
            text-variant="white"
          >
          </b-card>

          <div class="portfolio-info">
            <h4>project name goes here 6</h4>
            <p>category project</p>
          </div>
        </b-col>
        <b-col class="portfolio-box shadow">
          <b-card
            class="border-0"
            overlay
            img-src="https://img.demo.persina.com/unsafe/720x720/https://static.demo.persina.com/Products/Image/4583cdf554e1427c9b68f31513128765.jpg"
            img-alt="Card Image"
            text-variant="white"
          >
          </b-card>

          <div class="portfolio-info">
            <h4>project name goes here 6</h4>
            <p>category project</p>
          </div>
        </b-col>
      </b-row>
    </b-container>
    {{ counter}}

    <b-container>
      <b-row>
        <b-col>
          <b-card border-variant="info" header="Info" align="center">
            <b-card-text>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</b-card-text>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 8,
      sett:'',
    }
  },
// methods: {
//     todo: function() {
//       console.log(this.counter);
//       var self = this;
//       self.sett = setInterval(function() {
//         self.counter += 1;
//       }, 200);
//     },
//   },
//   mounted() {
//     this.todo();
//     setTimeout(function() {
//         clearInterval(self.sett);
//       }, 3000);
//   }
}
</script>

<style scoped>

.portfolio-box {
  position: relative;
  width: 100%;
  height: 18.5rem;
  overflow: hidden;
}

.portfolio-box img {
  width: 100%;
  height: 100%;
}

.portfolio-box .portfolio-info{
  background-color: #47c9e5;
  opacity: 0;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  text-align: center;
  z-index: 3;
  transition: all ease-in-out 0.3s;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: white;
}

.portfolio-box:hover img {
  transform: scale(1.5);
  transition-duration: 2s;
  transition-property: all;
}

.portfolio-box:hover .portfolio-info {
  opacity: 0.9;
  transition-duration: 1s;
  transition-property: all;
}


.portfolio-box .portfolio-info::after {
    display: block;
    content: "";
    width: 48px;
    height: 48px;
    position: absolute;
    bottom: 35px;
    right: 35px;
    border-bottom: 3px solid #d7dce1;
    border-right: 3px solid #d7dce1;
    transition: all 0.5s ease 0s;
    z-index: 9994;
}


.portfolio-box .portfolio-info::before {
    display: block;
    content: "";
    width: 48px;
    height: 48px;
    position: absolute;
    top: 35px;
    left: 35px;
    border-top: 3px solid #d7dce1;
    border-left: 3px solid #d7dce1;
    transition: all 0.5s ease 0s;
    z-index: 9994;
}
/* counter */
.counters {
  background-color: #000;
  color:#fff;
  margin: 100px auto 0;
  text-align: center;
  display: table;
}

.counter {
  display: table-cell;
  margin:1.5%;
  font-size:50px;
  background-color: grey;
  width:200px;
  border-radius: 50%;
  height:200px;
  vertical-align: middle;
}
</style>