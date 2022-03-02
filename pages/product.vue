<template>
  <div class="container">
    <Navigasi />
    <div class="row">
      <div class="col-md-12">
        <h1>Products</h1>

        <div class="row">
          <div class="col-md-4" v-for="item in items" :key="item.id">
            <div class="card mb-3">
              <div class="card-header">
                <img :src="item.foto" width="100%">
              </div>
              <div class="card-body">
                <h4>{{ item.nama }}</h4>
                <h4>Rp{{ item.harga }}</h4>
                <a :href="item.link_eksternal" class="btn btn-success btn-block"> Meli Atuh AHHHH!!!</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: '',
    }
  },
  mounted() {
    this.ambilData()
  },
  methods: {
    async ambilData() {
      const { data, error } = await this.$supabase
        .from('tbl_produk')
        .select()
      if(data) this.items = data
      if(error) console.log(error)
    }
  }
}
</script>