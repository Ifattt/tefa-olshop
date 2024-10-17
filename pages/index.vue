<template>
    <div class="container-fluid">
        <div class="card rounded-3 bg-light mb-3">
            <img src="~/assets/img/cover1.png" alt="bouquet" class=" responsive card-img-top rounded-3 mt-4">
        </div>

        <div class="d-flex justify-content-center mb-3">
            <img src="~/assets/img/logo2.png" alt="Logo" class="rounded-circle" style="width: 100px;">
        </div>

        <div class="d-flex justify-content-center mb-3">
            <p class="text">SELAMAT DATANG DI TOKO ONLINE KAMI SEMOGA ANDA PUAS DENGAN PELAYANAN KAMI.</p>
        </div>

        <section id="produk">
            <div class="d-flex justify-content-center mb-3">
                <h1>PRODUK KAMI</h1>
            </div>
            <div class="row mb-3">
                <div v-for="(produk, i) in produks" :key="i" class="col-lg-4 col-md-6 mb-3">
                    <div class="card">
                        <NuxtLink class="btn bg-abu btn-lg rounded-2"
                            :to="`https://wa.me/6285724948649?text= Halo saya ingin pesan bouquet: ${produk.nama} ${produk.harga}. https://tefa-olshop.vercel.app/`"
                            target="_blank">
                            <img :src="produk.cover" class="card-img-top" alt="Category Image"
                                style="object-fit: cover;">
                            <div class="card-body">
                                <div class="text">
                                    <p class="card-text">{{ produk.nama }}</p>
                                    <p class="card-text">{{ produk.harga }}</p>
                                </div>
                            </div>
                        </NuxtLink>
                    </div>
                </div>
            </div>

        </section>
        <section id="kategori">

            <div class="d-flex justify-content-center mb-3">
                <h1>KATEGORI</h1>
            </div>
            <div class="row">
                <div v-for="(kategori, i) in kategoris" :key="i" class="col-lg-4 col-md-6 mb-3">
                    <nuxt-link :to="`/detail/${kategori.id}`">

                        <div class="card">
                            <img :src="kategori.cover" class="card-img-top" alt="Category Image"
                                style="object-fit: cover;">
                            <div class="card-body">
                                <div class="text">
                                    <p class="card-text">{{ kategori.nama }}</p>
                                </div>
                            </div>
                        </div>
                    </nuxt-link>

                </div>
            </div>

        </section>
    </div>
    <footer class="footer bg-abu">
        <p>Copyright © 2024 i, Inc. All rights reserved.</p>
    </footer>
</template>



<script setup>
useHead({
    title: `Home`,
    meta: [
        {
            name: 'description',
            content: `jual bouket: ....`
        },
        {
            property: 'og:image',
            content: '.....'
        }
    ]
})



const supabase = useSupabaseClient();
const produks = ref([]);
const kategoris = ref([]);

const getProduks = async () => {
    const { data, error } = await supabase.from('produk').select(`*`);
    if (data) produks.value = data;
};

const getKategori = async () => {
    const { data, error } = await supabase.from('kategori').select(`*`);
    if (data) kategoris.value = data;
};

onMounted(() => {
    getProduks();
    getKategori();
});
</script>

<style scoped>
.footer {
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    padding-top: 10px;
    left: 0;
    right: 0;
    /* position: relative;
    bottom: 0;
    width: 100%; */
}

.responsive {
    width: 100%;
    max-width: 400%;
    height: 500px auto;
}
</style>