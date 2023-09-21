<script setup>
import {products} from "../data/data.js";


</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-4 col-md-6 col-sm-12 pt-2 px-1" v-for="(product,key) in products" :key="product.id">
        <div class="card rounded-0">
          <div class="card-body">
            <img class="card-img" :src="product.imgUrl" :alt="product.name+' Image'">
            <h5 class="fw-bold">Product: {{ product.name }}</h5>
            <p>Price: {{product.price}} BDT</p>
            <router-link :to="{name:'product',params:{id:product.id}}" class="btn btn-info rounded-0">View Details</router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
