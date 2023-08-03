<template>
    <h1>Produk</h1>
    <div class="flex-container">
     <div v-for="produk in state" :key="produk.id" class="card">
      <center><img class="img" :src="getImgSrc(produk.img)" alt="category image"/></center>
      <router-link class="container" :to="{ name: 'Detail', params: { id_produk: produk.id }}">
      <h4>{{ produk.nama }}</h4>
      </router-link>
    </div>
    </div>
  </template>
  <script>
  import { onMounted, reactive } from 'vue'
  import { produk } from '@/assets/produk.js'
  export default{
    setup (props, context)
  {
    const state = reactive(produk["produk"]);
  
  onMounted(() => {
        context.emit("id-menu", 1);
    });
    const getImgSrc = (imgFileNama) => {
        return '../src/assets/img/' + imgFileNama + '';
      }
    return{
      state,
      getImgSrc
    }
   }
  }
  </script >
 
 <style scoped>
 h1{
  text-align: center;
 }
 .img{
  width: 200px;
  margin-top: 50px;
}
.flex-container {
  display: flex;
  flex-wrap: wrap;
}
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0, 0, 0.2);
  transition: 0.3s;
  margin: 10px;
  min-width: 380px;
  cursor: pointer;
  text-align: center;
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0, 0, 0.2);
}
.container {
  padding: 2px 16px;
}
</style> 