<template>
  <div>
    <h2>フード</h2>
    <v-data-table
      :headers="headers"
      :items="items"
      class="elevation-1"
      hide-default-footer
    >
      <template v-slot:item.id="{ item }">
        <nuxt-link :to="'posts/' + item.id">
          {{ item.id }}
        </nuxt-link>
      </template>
    </v-data-table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData ({ params }) {
    const { data } = await axios.get(
      `https://yasutomog.microcms.io/api/v1/menudetails?filters=menu[equals]${params.id}`,
      {
        headers: { 'X-API-KEY': process.env.API_KEY }
      }
    )
    return {
      headers: [
        { text: 'ID', value: 'id' },
        { text: 'NAME', value: 'name' },
        { text: 'PRICE', value: 'price' },
        { text: 'CREATE', value: 'createdAt' },
        { text: 'UPDATE', value: 'updatedAt' }
      ],
      items: data.contents
    }
  },
  data () {
    return {
      items: []
    }
  }
}
</script>
