<template>
  <div class="writeoff">
    <div class="form">
      <div class="form-group">
        <label for="name">Název</label>
        <input type="text" v-model="writeOffName" id="name">
      </div>
      <div class="form-group">
        <label for="price">Cena</label>
        <input type="text" v-model="price" id="price">
      </div>
      <div class="form-group">
        <label for="date">Rok pořízení</label>
        <input type="number" v-model="year" id="date">
      </div>
      <div class="form-group">
        <label for="group">Odpisová skupina</label>
        <select id="group" v-model="group">
          <option value="1">1 (3 roky)</option>
          <option value="2">2 (5 let)</option>
          <option value="3">3 (10 let)</option>
          <option value="4">4 (20 let)</option>
          <option value="5">5 (30 let)</option>
          <option value="6">6 (50 let)</option>
        </select>
      </div>
      <div class="checkbox">
        <input id="fastWriteOff" v-model="fastWriteOff" type="checkbox">
        <label for="fastWriteOff">Zrychlený odpis</label>
      </div>
      <button v-on:click="calculateWriteOff()">Vypočítej</button>
    </div>
    <write-off-table :data="writeOffs" :show="showTable" :name="writeOffName"></write-off-table>
  </div>
</template>

<script>
import WriteOffTable from "@/components/WriteOffTable";
export default {
  name: "WriteOff",
  components: {
    WriteOffTable
  },
  data() {
    return{
      price: 0,
      group: 1,
      writeOffName: "",
      year: 2021,
      fastWriteOff: false,
      writeOffs: [],
      showTable: false
    }
  },
  methods: {
    calculateWriteOff: function (){
      console.log(this.price)
      console.log(this.group)
      console.log(this.writeOffName)
      console.log(this.year)

      this.writeOffs = []
      let firstYearC = 0
      let nextYearsC = 0
      let firstYear = 0
      let nextYears = 0
      let yearsCount = 0
      let rest = this.price
      let total = 0
      if(this.group === 1){
        firstYear = 20
        nextYears = 40
        firstYearC = 3
        nextYearsC = 4
        yearsCount = 3
      }
      if(this.group === 2){
        firstYear = 11
        nextYears = 22.25
        firstYearC = 5
        nextYearsC = 6
        yearsCount = 5
      }
      if(this.group === 3){
        firstYear = 5.5
        nextYears = 10.5
        firstYearC = 10
        nextYearsC = 11
        yearsCount = 10
      }
      if(this.group === 4){
        firstYear = 2.15
        nextYears = 5.15
        firstYearC = 20
        nextYearsC = 21
        yearsCount = 20
      }
      if(this.group === 5){
        firstYear = 1.4
        nextYears = 3.4
        firstYearC = 30
        nextYearsC = 31
        yearsCount = 30
      }
      if(this.group === 6){
        firstYear = 1.02
        nextYears = 2.02
        firstYearC = 50
        nextYearsC = 51
        yearsCount = 50
      }

      if(!this.fastWriteOff){
        for (let i = 0; i < yearsCount; i++){
          let yearly = 0
          if(i === 0){
            yearly = (this.price / 100) * firstYear
          }
          else yearly = (this.price / 100) * nextYears

          rest = rest - yearly
          total += yearly
          this.writeOffs.push({year: this.year + i, restPrice: rest, yearly: yearly, total: total})
        }
      } else {
        for (let i = 0; i < yearsCount; i++){
          let yearly = 0
          if(i === 0){
            yearly = this.price / firstYearC
          }
          else yearly = (2*rest) / (nextYearsC - (i+1))

          rest = rest - yearly
          total += yearly
          this.writeOffs.push({year: this.year + i, restPrice: rest, yearly: yearly, total: total})
        }
      }
      this.showTable = true
      console.log(this.showTable)
    }
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
