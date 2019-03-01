<template>
  <div>
    <table class="minimalistBlack">
      <tr>
        <th class="head">HORAS</th>
        <th class="head">LUNES</th> 
        <th class="head">MARTES</th>
        <th class="head">MIERCOLES</th>
        <th class="head">JUEVES</th>
        <th class="head">VIERNES</th>
        <th class="head">SABADO</th>
        <th class="head">DOMINGO</th>
        <th class="head">HORAS</th>
      </tr>
      <!-- Cuerpo -->
      <tr v-for="(item, index) in hours" :key="index">
        <!-- fila 1 col1 -->
        <td rowspan="1" colspan="1">{{item.texto}}</td>
        <!-- fila 1 col2 -->
        <td :rowspan="1" :colspan="1">{{item.texto}}</td>
      </tr>
      
    </table>
  </div>
  
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      hours: [
        {texto: '05:15'},
        {texto: '05:15',},
        {texto: '05:15'},
        {texto: '05:15'},
        {texto: '05:15'},
        {texto: '05:15'},
        {texto: '05:15'},
        {texto: '05:15'},
        {texto: '05:30'},
        {texto: '05:45'},
        {texto: '06:00'},
        {texto: '06:30'},
        {texto: '06:45'},
        {texto: '07:00'},
       ],
      // dayMonday: [
      //   {texto: 'AMERICA NOTICIAS: PRIMERA EDICION: LOCAL (GP)', rowspan: 2, colspan: 2},
      //   {texto: 'AMERICA NOTICIAS: PRIMERA EDICION: LOCAL (GP)', rowspan: 3, colspan: 2},
      //   {texto: 'AMERICA NOTICIAS: PRIMERA EDICION: LOCAL (GP)', rowspan: 1, colspan: 2}
      // ]
      
    }
  },
  created () {

  },
  methods: {
    // createTable() {

    // }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.head {
  width: 2480 / 9;
}
table.minimalistBlack {
  border: 3px solid #000000;
  width: 100%;
  max-width: 2480px;
  max-height: 3508px;
  text-align: left;
  border-collapse: collapse;
}
table.minimalistBlack td, table.minimalistBlack th {
  border: 1px solid #000000;
  padding: 5px 4px;
}
table.minimalistBlack tbody td {
  font-size: 13px;
}
table.minimalistBlack thead {
  background: #CFCFCF;
  background: -moz-linear-gradient(top, #dbdbdb 0%, #d3d3d3 66%, #CFCFCF 100%);
  background: -webkit-linear-gradient(top, #dbdbdb 0%, #d3d3d3 66%, #CFCFCF 100%);
  background: linear-gradient(to bottom, #dbdbdb 0%, #d3d3d3 66%, #CFCFCF 100%);
  border-bottom: 3px solid #000000;
}
table.minimalistBlack thead th {
  font-size: 15px;
  font-weight: bold;
  color: #000000;
  text-align: left;
}
table.minimalistBlack tfoot {
  font-size: 14px;
  font-weight: bold;
  color: #000000;
  border-top: 3px solid #000000;
}
table.minimalistBlack tfoot td {
  font-size: 14px;
}
/* h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
} */
</style>
