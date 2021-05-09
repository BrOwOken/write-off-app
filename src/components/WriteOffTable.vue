<template>
  <transition name="fade" appear>
    <div v-if="show" class="writeoff-table">
      <h3>{{ writeOffName }}</h3>
      <table class="table mt-3 table-striped">
        <tr>
          <th scope="col">Rok</th>
          <th scope="col">Zůstatková cena</th>
          <th scope="col">Roční odpis</th>
          <th scope="col">Odpis celkem</th>
        </tr>
        <tr v-for="writeOff in data" :key="writeOff.year">
          <td scope="row">{{ writeOff.year }}</td>
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

<style scoped lang="scss">
.writeoff-table{
  width: 100%;
  margin-top: 32px;
}
table{
  width: 100% !important;
}
th{
  border-bottom: 1px solid #181717;
  font-weight: bold;
  text-align: left;
  padding: 8px 0
}
td{
  border-bottom: solid 1px #c8c5c5;
  text-align: left;
  padding: 8px 0
}
tr:last-of-type{
  td{
    border-bottom: none;
  }
}
.fade{
  &-enter-active, &-leave-active{
    transition: all 0.5s cubic-bezier(.21,.81,.7,.91);
  }
  &-enter-from{
    transform: translateY(-48px);
    opacity: 0;
  }
}
</style>
