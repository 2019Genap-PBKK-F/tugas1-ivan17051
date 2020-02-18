<template>
    <div class="content">
        <div class="row center-block">
            
            <div id="app" ref="spreadsheet"></div>
            <div><input type="button" value="Add new row" @click="() => spreadsheet.insertRow()" /></div>
        
        </div>
    </div>
</template>

<script>
import jexcel from 'jexcel'
import 'jexcel/dist/jexcel.css'
var data = [
  ['05111740000060', 'Honda', '2017', '1999-07-11', '', true],
  ['05111940000156', 'Yamaha', '2019', '2001-05-21', '', true]
]
var options = {
  data: data,
  allowToolbar: true,
  columns: [
    { type: 'text', title: 'NRP', width: '150px' },
    { type: 'text', title: 'Nama', width: '250px' },
    { type: 'dropdown', title: 'Angkatan', width: '120px', source: [ '2014', '2015', '2016', '2017', '2018', '2019' ] },
    { type: 'calendar', title: 'Tgl. Lahir', width: '150px' },
    { type: 'image', title: 'Foto', width: '150px' },
    { type: 'checkbox', title: 'Aktif', width: '100px' }
  ]
}
export default {
  name: 'App',
  mounted: function () {
    let spreadsheet = jexcel(this.$el, options)
    Object.assign(this, { spreadsheet })
  }
}
</script>
