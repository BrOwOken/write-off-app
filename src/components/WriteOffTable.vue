<template>
  <transition>
    <div v-if="show" class="writeoff-table">
      <h3>{{ writeOffName }}</h3>
      <table>
        <tr>
          <th>Rok</th>
          <th>Zůstatková cena</th>
          <th>Roční odpis</th>
          <th>Odpis celkem</th>
        </tr>
        <tr v-for="writeOff in data" :key="writeOff.year">
          <td>{{ writeOff.year }}</td>
          <td>{{ writeOff.restPrice }} Kč</td>
          <td>{{ writeOff.yearly }} Kč</td>
          <td>{{ writeOff.total }} Kč</td>
        </tr>
      </table>
    </div>
  </transition>
</template>

<script>
export default {
  name: "WriteOffTable",
  props: {
    data: {
      type: Array
    },
    show: {
      type: Boolean,
      immediate: true
    },
    writeOffName: {
      type: String
    }
  }
}
</script>

<style scoped>

</style>
