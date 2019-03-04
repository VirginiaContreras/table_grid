<template>
  <div>
    <table id="schedule-table" class="minimalistBlack">
      <thead>
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
      </thead>
      <!-- Cuerpo -->
      <tbody>
        <tr v-for="(item, index) in hours" :key="index">
          <td>{{ item.texto }}</td>
          <td class="cell" :hour="item.texto" :day="1" colspan="1" rowspan="1"></td>
          <td class="cell" :hour="item.texto" :day="2" colspan="1" rowspan="1"></td>
          <td class="cell" :hour="item.texto" :day="3" colspan="1" rowspan="1"></td>
          <td class="cell" :hour="item.texto" :day="4" colspan="1" rowspan="1"></td>
          <td class="cell" :hour="item.texto" :day="5" colspan="1" rowspan="1"></td>
          <td class="cell" :hour="item.texto" :day="6" colspan="1" rowspan="1"></td>
          <td class="cell" :hour="item.texto" :day="7" colspan="1" rowspan="1"></td>
          <td>{{ item.texto }}</td>
        </tr>
      </tbody>

      <tfoot>
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
      </tfoot>
    </table>
  </div>
  
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    // createTable() {

    // }
  },
  data () {
    return {
      hours: [
        {texto: '05:16'},
        {texto: '05:30',},
        {texto: '06:00'},
        {texto: '06:25'},
        {texto: '06:30'},
        {texto: '06:50'},
        {texto: '07:00'},
        {texto: '07:30'},
        {texto: '08:00'},
        {texto: '08:20'},
        {texto: '08:30'},
        {texto: '08:35'},
        {texto: '09:00'},
        {texto: '09:30'},
       ],
      schedule: [
        {texto: 'AMERICA NOTICIAS: PRIMERA EDICION: LOCAL (GP)', hourstart: '05:16', hourend: '06:49', days: [1, 2, 3, 4, 5]},
        {texto: 'AMERICA NOTICIAS: PRIMERA EDICION (GP)', hourstart: '06:50', hourend: '08:19', days: [1, 2, 3, 4, 5]},
        {texto: 'AMERICA DEPORTES (G)', hourstart: '08:20', hourend: '08:29', days: [1, 2, 3, 4, 5]},
        {texto: 'AMERICA DEPORTES (G)', hourstart: '08:20', hourend: '08:29', days: [1, 2, 3, 4, 5]},
        {texto: 'AMERICA NOTICIAS: EDICIÓN DOMINICAL (GP)', hourstart: '08:20', hourend: '08:29', days: [7]},
        {texto: 'ESTAS EN TODAS (GP)', hourstart: '08:20', hourend: '08:29', days: [6]},
        {texto: 'AMÉRICA ESPECTÁCULOS (REPETICIÓN)', hourstart: '05:30', hourend: '06:25', days: [6]},
        {texto: 'AMÉRICA NOTICIAS MATUTINO (GP)', hourstart: '06:25', hourend: '06:50', days: [6]},
      ] 
    }
  },
  mounted() {
    let list = document.getElementsByClassName('cell');

    //por cada elemento del array schedule
    this.schedule.forEach(item => {

      //recorrer cada celda del horario
      Array.from(list).forEach((cell) => {
        console.log(cell.getAttribute('hour'));
        let day = parseInt(cell.getAttribute('day'));
        let hour = cell.getAttribute('hour');

        if((item.hourstart <= hour && item.hourend > hour) && item.days.includes(day)){
          cell.innerHTML = item.texto;
        }
      });

    });

    //leer tabla y combinar celdas iguales
    let tbl = document.getElementById('schedule-table');
    let rows = tbl.getElementsByTagName('tr');

    //recorrer columnas
    for (let i = 0; i < rows.length; i++){

      let cells = rows[i].getElementsByClassName('cell');

      //recorrer celdas
      for (let j = 0; j < cells.length; j++) {

        if((j - 1) >= 0){
          if(cells[j].innerHTML === cells[j - 1].innerHTML) {

            let actualColspan = cells[j - 1].getAttribute('colspan');
            cells[j - 1].setAttribute('colspan', parseInt(actualColspan) + 1);
            cells[j].remove();
            j = 0;
          } 
        }

      }
      
    }
    
    //recorrer filas
    for (let i = 0; i < rows.length; i++){
      console.log(i, '2')
      if( i >= 2){
        console.log(i, 'i')
        let cell = rows[i].getElementsByClassName('cell');
        let lastCell = rows[i - 1].getElementsByClassName('cell');

        console.log(cell, 'cell')
        console.log(lastCell, 'lastCell')

        // Valida si las celdas no estan vacias  
        // if(typeof cell[0] != 'undefined' && typeof lastCell[0] != 'undefined'){

        // if(cell[0].innerHTML == lastCell[0].innerHTML) {

        //   let actualRowspan = lastCell[0].getAttribute('rowspan');
        //   console.log(actualRowspan, 'actualRowspan')
        //   lastCell[0].setAttribute('rowspan', parseInt(actualRowspan) + 1);
        //     // cell[0].remove();
        //     // i = 0;
        // } 
      // }
      }
      
    }


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
