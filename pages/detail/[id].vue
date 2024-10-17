<template>
  <div class="row">
    <div class="col-12">
      <a href="/" class="btn btn-grey mt-3">
        <button style="background-color: transparent; border: none; ">
          <img src="~/assets/img/kembali.png" alt="kembali" style="width: 30px; height: 30px; margin-top: 10px;">
        </button></a>
    </div>
  </div>

  <div class="row">
    <div class="col-12">
      <h2 class="text-center">DETAIL PESANAN</h2>
    </div>
  </div>

  <div class="row">
    <div class="col-12">
      <hr>
    </div>
  </div>

  <div class="row detail">
    <div class="col-sm-3"><img :src="detail.cover" class="cover img-fluid" width="200%" /></div>
    <div class="col-sm-4">
      <div class="judul">
        {{ detail.judul }}
      </div>
      <div class="deskripsi">
        {{ detail.deskripsi }}
      </div>
      <div class="navigasi">
        <NuxtLink class="btn bg-abu btn-lg rounded-5"
        :to="`https://wa.me/6285724948649?text=Halo saya ingin pesan bouquet: ${detail.judul}. https://onlinebouket.com/detail/${detail.id}`"
        target="_blank">
        <button style="background-color: transparent; border: none;">
          <img src="~/assets/img/whatsapp.png" alt="whatsapp" style="width: 30px; height: 30px;">
          Order Disini
        </button>
      </NuxtLink>
    </div>
    </div>
    
    
  </div>



  <!-- <div class="row">
    <div class="col-lg-1">
      <a href="/" class="btn btn-grey mt-3">
        <button style="background-color: transparent; border: none; ">
          <img src="~/assets/img/kembali.png" alt="kembali" style="width: 30px; height: 30px; margin-top: 10px;">
        </button></a>
    </div>
  </div>
  <div class="row">
    <div class="col-sm-12 justify-content-center">
      <h2 class="text-center mb-5 mt-5 fw-bold">DETAIL PESANAN</h2>
    </div>
  </div>
  <div class="row">
    <div class="col-12">
      <hr>
    </div>
  </div>
  <div class="row">
    <div class="col-sm-3">
      <img :src="detail.cover" class="cover img-fluid" alt="cover">
    </div>
    <div class="col">
      <ul class="list-group">
        <li class="list-group-item"> {{ detail.judul }}</li>
        <li class="list-group-item"> Deskripsi : </li>
        <li class="list-group-item deskripsi"> {{ detail.deskripsi }}</li>
      </ul>
      <NuxtLink class="btn bg-abu btn-lg rounded-5"
        :to="`https://wa.me/6285724948649?text=Halo saya ingin pesan bouquet: ${detail.judul}. https://onlinebouket.com/detail/${detail.id}`"
        target="_blank">
        <button style="background-color: transparent; border: none; "> -->
  <!-- <img src="~/assets/img/whatsapp.png" alt="whatsapp" style="width: 30px; height: 30px;">
        Order Disini
       </button> -->
  <!-- </NuxtLink>
    </div>
  </div> -->
</template>


<script setup>
definePageMeta({
  layout: 'homepage'
})

useHead({
  title: `Detail Bouquet`,
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

const supabase = useSupabaseClient()

const route = useRoute()
const detail = ref([])

const getDetailById = async () => {
  const { data, error } = await supabase.from('detail').select(`*`)
    .eq('id', route.params.id)
  if (data) detail.value = data[0]
}
onMounted(() => {
  getDetailById()
})
definePageMeta({
  layout: 'homepage'
})
</script>

<style scoped>
.detail {
  display: flex;
  justify-content: center;
}

.deskripsi {
  white-space: pre-line;
  margin: 20px 10px;
  height: auto;
  border-radius: 1rem;
}

.cover {
  width: 100%;
  max-width: 340px;
  border-radius: 1rem;
  margin: 20px 14px;
}

.card.mb-8 {
  margin-top: 50px;
  height: auto;
  width: 100%;
}

ul {
  width: 100%;
}

.list-group-item {
  font-size: 1.2rem;
  width: 100%;
  margin: 15px 0;
}

.list-group {
  width: 100%;
}


@media only screen and (max-width: 768px) {
  .list-group-item {
    font-size: 1rem;
  }
}
</style>
