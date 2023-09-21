<script setup>
import {products} from "../data/data.js";
import {useRoute} from "vue-router";
import {onMounted, ref} from "vue";
const route = useRoute()
const product = ref([])

function getProduct(productId){
  let res = products.find(function (obj){
    return obj.id === Number(productId)
  });

  product.value.push({
    id:res.id,
    name:res.name,
    price:res.price,
    description:res.description,
    imgUrl:res.imgUrl
  })
}

onMounted(()=>{
   getProduct(route.params.id)
})

</script>

<template>
  <div class="container">
    <div class="row">
      <template v-for="(productDetail,index) in product" :key="index">
        <div class="col-lg-8 offset-lg-2 col-md-10 offset-md-1 col-sm-12 pt-2 px-1">
          <div class="card rounded-0">
            <div class="card-body">
              <img class="card-img" style="width: 300px; height: auto" :src="productDetail.imgUrl" :alt="productDetail.name+' Image'">
              <h5 class="fw-bold">Product: {{ productDetail.name }}</h5>
              <p style="text-align: justify">{{productDetail.description}}</p>
              <p>Price: {{ productDetail.price }} BDT</p>
              <router-link :to="{name:'products'}" class="btn btn-info rounded-0">Back</router-link>
            </div>
          </div>
        </div>
      </template>
    </div>
  </div>
</template>

<style scoped>

</style>
