<template>
  <h1>Kategori</h1>
  <div class="flex-container">
      <div v-for="kategori in cek" :key="kategori.id" class="card">
        <center><img class="img" :src="getImgSrc(kategori.img)" alt="category image"/></center>
      <router-link class="container" :to="{ name : 'KategoriProduk', params:{id_kategori : kategori.id}}">
          <h4>{{ kategori.nama }}</h4>
      </router-link>
  </div>
  </div>
</template>
<script>
import { onMounted, reactive } from 'vue';
import { kategori } from '@/assets/kategori';

export default{
  setup(props,context){

      const cek = reactive(kategori["kategori"]);
      
      const getImgSrc = (imgFileNama) => {
        return '../src/assets/img/' + imgFileNama + '';
      }
      onMounted(() => {
          context.emit("id-menu",5)
      });

      return{
          cek,
          getImgSrc
      }
  }
}
</script>

<style scoped>

.img{
  width: 100px;
  margin-top: 50px;
}
h1{
  text-align: center;
}
.flex-container {
  display: flex;
  flex-wrap: wrap;
}
.card {
  box-shadow: 0 4px 8px 0 rgba(0,0, 0, 0.2);
  transition: 0.3s;
  margin: 10px;
  min-width: 250px;
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