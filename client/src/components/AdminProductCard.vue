<template>
  <div class="col-lg-4 col-md-6 mb-4">
    <div class="card h-100">
      <div class="card-imgg">
        <img class="card-img-top" :src=ProductData.image alt="product-image" style="object-fit: contain; height: 200px; width: 200px" />
      </div>
      <div class="card-body">
        <h4 class="card-title">
          <span>{{ ProductData.name }}</span>
        </h4>
        <h5>Price: Rp.{{ ProductData.price }}</h5>
        <h6>Stock: {{ ProductData.stock }}</h6>
      </div>
      <div class="card-footer" v-if="$store.state.isLogin">
        <small class="text-muted"><b-button @click.prevent="setUpdateData(ProductData._id)"> <i class="far fa-edit"></i> Update Product </b-button></small>
      </div>
      <div class="card-footer" v-if="$store.state.isLogin">
        <small class="text-muted"><b-button @click.prevent="deleteProduct(ProductData._id)" > <i class="far fa-trash-alt"></i> Delete Product </b-button></small>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'AdminProductCard',
  props: ['ProductData'],
  methods: {
    deleteProduct (productId) {
      this.$store.dispatch('deleteProduct', productId)
    },
    setUpdateData (productId) {
      this.$router.push(`/admin/update-product/${productId}`)
    }
  }

}
</script>

<style scoped>
.card-imgg {
  padding: 5px;
}
</style>
