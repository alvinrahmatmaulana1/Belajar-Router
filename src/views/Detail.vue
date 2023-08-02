<template>
    <div v-if="detail == undefined">
    <H2><b>Maaf Id Dengan ID "{{ id_produk }}" tidak Ditemukan</b></H2>
    </div>
    <div v-else>
      <center>  <img :src="getImgSrc(detail.img)" alt="Category image"> </center>
    <h1>Detail {{ detail.nama }}</h1>
    <h4>Harga : {{ detail.harga }}</h4>
</div>
  </template>
<script>
import { produk } from '@/assets/Produk';


export default {
    props: [
        "id_produk",
        
        
    ],
    setup(props){
        const detail = produk["produk"].find(function(item) {
            return item.id == props.id_produk
            
        });
        const getImgSrc = (imgFileName) => {
            return '../src/assets/img/' + imgFileName + '';
        }
        
        
        return{
            detail,
            getImgSrc
            

        }
    }
}
</script>
<style scoped>
img{
    height: 40%;
    width: 40%;
}
</style>