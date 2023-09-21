<script setup>
import {onMounted, reactive, nextTick, onBeforeUnmount, onUnmounted} from "vue";
let carousel = null
const slides = reactive([
  {id:1,title:'Carousel One',imgUrl:'https://media.istockphoto.com/id/701007458/photo/wedding-photographer-takes-pictures-of-bride-and-groom-in-nature-fine-art-photo.webp?s=170667a&w=0&k=20&c=S83uOsxfg9lxn1xazv6oQq1fJuLICsW4YKohrbP3kMo='},
  {id:2,title:'Carousel Two',imgUrl:'https://media.istockphoto.com/id/802496602/photo/wedding-couple-on-nature-bride-and-groom-hugging-at-wedding.webp?s=170667a&w=0&k=20&c=zGnsXuGIFD2935vHjVsyjs9JC3-dnHR1PHQrjMMorQU='},
  {id:3,title:'Carousel Three',imgUrl:'https://media.istockphoto.com/id/1168141832/photo/mother-and-daughter-in-nature.jpg?s=612x612&w=0&k=20&c=ardk7IM63ZmmnjiJIp10uHSggbDROKlNe1LavwUfXWo='},
  {id:4,title:'Carousel Four',imgUrl:'https://media.istockphoto.com/id/1220635809/photo/newlyweds-are-standing-against-the-backdrop-of-a-beautiful-landscape-with-an-umbrella.jpg?s=612x612&w=0&k=20&c=PdSSnJVSNhzMqzusfOzAvpUNUwJ-6CWdU43Omco2aCs='},
  {id:5,title:'Carousel Five',imgUrl:'https://media.istockphoto.com/id/1023105948/photo/young-brother-and-sister-walk-with-miniature-horse-in-field.jpg?s=612x612&w=0&k=20&c=vVQljPuWSr-FG_tWAAq-VASiknXVt-cHquNEyvHEwmA='},
  {id:6,title:'Carousel Six',imgUrl:'https://media.istockphoto.com/id/186907962/photo/wedding-couple-in-a-wheat-land.jpg?s=612x612&w=0&k=20&c=UV_T3t09HD9y4_F7f6jLcC3Tw793ZQxCNUanS2JRTcw='},
])

const deleteSlide = (id)=>{
  let index = slides.findIndex((slide)=>{return slide.id===id})
  if (slides.length>1){
    slides.splice(index,1)
    carousel.destroy()
    nextTick(()=>{
      carousel = new Flickity( '#carousel', {
        // options
      })
    })
  }else {
    alert('At least one slide should keep here !!!')
  }
}

onMounted(()=>{
  carousel = new Flickity( '#carousel', {
    // options
  })
})

onBeforeUnmount(()=>{
  slides.length = 0
})
</script>

<template>
  <div class="container">
    <div class="row mb-5">
      <div class="col-lg-8 offset-lg-2">
        <div class="items mx-auto py-2" id="carousel">
          <div class="item" :style="`background-image:url(${slide.imgUrl})`" v-for="slide in slides" :key="slide.id"><h5 class="text-center fw-bold">{{slide.title}}</h5></div>
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col-lg-2 col-sm-4" v-for="slide in slides" :key="slide.id">
        <img class="thumb" :src="slide.imgUrl" :alt="slide.title">
        <button class="btn btn-danger btn-sm form-control rounded-0" @click="deleteSlide(slide.id)"><i class="fa fa-trash"></i> Delete Slide</button>
      </div>
    </div>
  </div>


</template>

<style scoped>
.items{
  width: 600px;
  height: 400px;
}

.item{
  width: 600px;
  height: 400px;
  background-color: #ccc;
  background-size: cover;
}

.thumb{
  width: 100%;
}
</style>
