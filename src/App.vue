<template>
  <div id="app">
    <h3>Front End Developer Challenge</h3>
    <DataTable @ :dataSource="testData" :columns="columns" :config="config" />
    <DataView  />
  </div>
</template>
<script>
import DataTable from './components/DataTable.vue'
import DataView from './components/DataView.vue'
import { testData } from './testData.js'
export default {

  name: 'app',
  components: {
    DataTable,
    DataView
  },
  data () {
    return {
      testData,
      columns: [
        {
          title: 'ID',
          dataIndex: 'id',
          sortable:true,
        },
        {
          title: 'First Name',
          dataIndex: 'first_name',
          sortable:true
        },
        {
          title: 'Last Name',
          dataIndex: 'last_name',
          sortable:true
        },
        {
          title: 'Email',
          dataIndex: 'email', 
        },
        {
          title: 'Gender',
          dataIndex: 'gender',
        },
        {
          title:"IP Address",
          dataIndex:'ip_address'
        },
        {
          title: 'Date',
          dataIndex: 'date',
        },
        {
          title:"Company",
          dataIndex:'company'
        },
        {
          title:"Address",
          dataIndex:'address'
        },
        {
          title:"Country",
          dataIndex:'country'
        },
        {
          title:"Age",
          dataIndex:'age',
          type:Number,
          sortable:true
        },
        {
          title:"Car Maker",
          dataIndex:'car_make'
        },
        {
          title:"Car Model",
          dataIndex:'car_model'
        },
        {
          title:"Car Color",
          dataIndex:'car_color'
        },
      ],
      config: {
        total: null,
        itemsPerPage: 10,
        frontPagination: true,
        tableClass: '',
        thClass: '',
        tdClass: '',
        hasSearch: true,
      }
    }
  },
  
}
</script>

<style lang="scss">
  div#app {
    padding: 30px;
    text-align: center;
    h3 {
      font-weight: 300;
      font-size: 30px;
      margin-bottom: 25px;
    }
  }
</style>
