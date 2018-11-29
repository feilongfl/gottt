<template>
  <b-carousel 
    id="carousel1"
    v-model="slide"
    style="text-shadow: 1px 1px 2px #333;"
    controls
    indicators
    background="#ababab"
    img-width="1024"
    img-height="100%"
  >

    <!-- Text slides with image -->
    <b-carousel-slide 
      caption="First slide"
      text="Nulla vitae elit libero, a pharetra augue mollis interdum."
      img-src="https://picsum.photos/1024/480/?image=52"
    />

    <!-- Slides with custom text -->
    <b-carousel-slide img-src="https://picsum.photos/1024/480/?image=54">
      <h1>Hello world!</h1>
    </b-carousel-slide>

    <!-- Slides with image only -->
    <b-carousel-slide img-src="https://picsum.photos/1024/480/?image=58"/>

  </b-carousel>
</template>
