<script setup>
const supabase = useSupabaseClient();
const detail = ref([]);
const loading = ref(true);

const getDetail = async () => {
  const { data } = await supabase.from("detail").select(`*,deskripsi,cover`)
  if (data) {
  }
  detail.value = data[0];
  loading.value = false;
};
onMounted(() => {
  getDetail();
});
definePageMeta ({
    layout: 'homepage'
})
</script>

<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-1">
        <a href="/" class="btn btn-grey mt-3"><-</a>
      </div>
      <div class="col-sm-10">
        <h2 class="text-center mb-5 mt-5 fw-bold">DETAIL PESANAN</h2>
    </div>
    <hr>
      <div class="flex-container">
        <div class="col-lg-2">
          <span v-if="loading">Sedang memuat gambar...</span>
          <span v-else><img :src="detail.cover" alt="cover" class="cover" /></span>
        </div>
        <div v-if="loading">Sedang memuat data...</div>
        <div v-else>
          <h1>{{ detail.deskripsi }}</h1>
          <button type="button" class="btn btn-secondary" disabled>order</button>
        </div>
      </div>
    </div>
  </div>
  <div class="footer">
            <p>Copyright © 2024 i, Inc. All rights reserved.</p>
        </div>
</template>

<style scoped>
.cover {
    width: 500px;
    height: 100%;
}
.flex-container {
  display: flex;
  height: 10%;
}
h1{
    margin-left: 50%;
    width: 550px;
}
.footer {
    text-align: center;
    background-color:#D9D9D9;
    height: 4em;
    margin-top: 7%;
}
.btn {
    margin-left: 150%;
    margin-bottom: 30px;
}

</style>