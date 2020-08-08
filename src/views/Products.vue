<template>
  <div class="about">
    <h1>產品列表頁面</h1>
    <table>
      <tr v-for="item in products" :key="item.id">
        <td>{{ item.title }}</td>
        <td>{{ item.origin_price }}</td>
        <td>{{ item.content }}</td>
        <td>
          <router-link :to="`/product/${item.id}`">單一產品列表</router-link>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data () {
    return {
      products: []
    }
  },
  created () {
    // console.log('UUID', process.env.VUE_APP_UUID)
    this.$http.get(`https://course-ec-api.hexschool.io/api/${process.env.VUE_APP_UUID}/ec/products`)
      .then((res) => {
        console.log(res)
        this.products = res.data.data
      })
  }
}
</script>
