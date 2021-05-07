<template>
  <div class="writeoff">
    <div class="form">
      <div class="form-group">
        <label for="name">Název</label>
        <input type="text" id="name">
      </div>
      <div class="form-group">
        <label for="price">Cena</label>
        <input type="text" id="price">
      </div>
      <div class="form-group">
        <label for="date">Rok pořízení</label>
        <input type="number" id="date">
      </div>
      <div class="form-group">
        <label for="group">Odpisová skupina</label>
        <select id="group">
          <option value="1">1 (3 roky)</option>
          <option value="2">2 (5 let)</option>
          <option value="3">3 (10 let)</option>
          <option value="4">4 (20 let)</option>
          <option value="5">5 (30 let)</option>
          <option value="6">6 (50 let)</option>
        </select>
      </div>
      <div class="checkbox">
        <input id="fastWriteOff" type="checkbox">
        <label for="fastWriteOff">Zrychlený odpis</label>
      </div>
    </div>
    <write-off-table></write-off-table>
  </div>
</template>

<script>
import WriteOffTable from "@/components/WriteOffTable";
export default {
  name: "WriteOff",
  components: {
    WriteOffTable
  },
  methods: {

  }
}
</script>

<style scoped lang="scss">
.writeoff{
  display: flex;
  justify-content: center;
  flex-flow: column;
  align-items: center;
}
.form{
  max-width: 420px;
}
.form-group{
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: flex-start;
  width: 100%;
}
</style>
