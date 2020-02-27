<template>
  <v-card
    class="mx-auto"
    max-width="344"
    outlined
  >
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">
          メニュー詳細
        </div>
        <v-list-item-title class="headline mb-1">
          {{ item.name }}
        </v-list-item-title>
        <v-list-item-subtitle v-html="$md.render(item.description)" />
      </v-list-item-content>
    </v-list-item>
  </v-card>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData ({ params }) {
    const { data } = await axios.get(
      `https://yasutomog.microcms.io/api/v1/menudetails/${params.id}`,
      {
        headers: { 'X-API-KEY': process.env.API_KEY }
      }
    )
    return {
      item: data
    }
  }
}
</script>
