<template>
    <h1>kategori</h1>
    <div class="py-8 px-4 mx-auto max-w-screen-xl lg:py-16">
        <div class="grid md:grid-cols-3 gap-8">
            <div v-for="kategori in cek" :key="kategori.id"
                class="w-full max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
                <a href="#">
                    <img :src="getImgSrc(kategori.img)" alt="Category image">
                </a>
                <div class="px-5 pb-5">
                    <a href="#">
                        <h5 class="text-xl font-semibold tracking-tight text-gray-900 dark:text-white">{{ kategori.namakategori }}</h5>
                    </a> <br>
                        <div>
                        <router-link class="container" :to="{ name: 'DetailKategori', params: { id_kategori: kategori.id } }" style="text-decoration: none; color: black;">
                       <h4 class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Lihat Kategori</h4>
                        </router-link>
                    </div>
                    
                </div>
            </div>
        </div>





    </div>
</template>
<script>
import { onMounted, reactive } from 'vue';
import { kategori } from '@/assets/Kategori';

export default{
    setup(props,context){

        const cek = reactive(kategori["kategori"]);

        const getImgSrc = (imgFileName) => {
            return '../src/assets/img/' + imgFileName + '';
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