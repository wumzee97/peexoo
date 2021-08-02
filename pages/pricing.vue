<template>
  <div>
    <v-data-table class="mt-10" hide-default-footer :headers="headers" :items="items">

    </v-data-table>
  </div>
</template>
<script>
export default {
  data () {
    return {
      headers: [
        {text: 'Title', value: 'title'},
        {text: 'Category', value: 'category'},
        {text: 'Items', value: 'items'},
        {text: 'Date Created', value: 'date'},
        {text: 'Amount', value: 'amount'},
      ],
      items: [
        {
          title: 'Wedding Classic',
          category: 'Wedding',
          items: 15,
          date: '5th Sep, 2020',
          amount: 'N350,000'
        },
        {
          title: 'Beauty Campaign',
          category: 'Beauty',
          items: 2,
          date: '5th Sep, 2020',
          amount: '45,000'
        },
        {
          title: 'Prewedding Gold',
          category: 'Wedding',
          items: 2,
          date: '5th Sep, 2020',
          amount: '45,000'
        },
        {
          title: 'Culinary Photography',
          category: 'Food',
          items: 18,
          date: '5th Sep, 2020',
          amount: '75,000'
        },
        {
          title: 'Wedding Classic',
          category: 'Wedding',
          items: 15,
          date: '5th Sep, 2020',
          amount: 'N350,000'
        },
      ]
    }
  }
}
</script>
