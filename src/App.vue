<script setup>
import {ref, reactive} from 'vue'

const isActive = ref(0)

const images = [
  {
    thumb: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxfHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
  },
  {
    thumb: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDZ8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=300&q=60",
  },
  {
    thumb: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE4fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
  },
  {
    thumb: "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
  }
]


function prev(){
  isActive.value <= 0  ? isActive.value = images.length - 1 : isActive.value--
}

function next(){  
  isActive.value >= images.length - 1 ? isActive.value = 0 : isActive.value++
}

// console.log(isActive)
</script>

<template>
  <div class="text-center fs-1 mb-3">Image Slider</div>
  <div id="carouselExampleSlidesOnly" class="carousel slide">
    <div class="carousel-inner">
      <div class="carousel-item " v-for="(image, index) in images" :key="index" v-show="isActive===index" :class="isActive ===index ? 'active': ''">
        <img class="d-block w-100 h-200" :src="image.thumb" alt="">
      </div>
    </div>
    <button @click="prev" class="carousel-control-prev" type="button">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button @click="next" class="carousel-control-next" type="button">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>
</template>

<style scoped>
  .h-200 {
    height: 200px;
  }
</style>
