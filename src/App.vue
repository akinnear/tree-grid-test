<template>
  <div id="app">
    <ejs-treegrid :dataSource='data' childMapping='states' :height='600' :dataStateChange="dataStateChange">
      <e-columns>
        <e-column field='name' headerText='Province' width='195' :template="flagtemplate"></e-column>
        <e-column field='population' headerText='Population (Million)' width='188' textAlign='Right'></e-column>
        <e-column field='unemployment' headerText='Unemployment Rate' :allowFiltering='false' width='200' :template='unemploymentTemplate'></e-column>
      </e-columns>
    </ejs-treegrid>
  </div>
</template>
<script>
  import Vue from "vue";
  import { TreeGridPlugin } from "@syncfusion/ej2-vue-treegrid";
  import Flag from "./components/Flag";

  Vue.use(TreeGridPlugin);

  import countries from "./data-source";
  import Unemployment from "./components/Unemployment";

  export default {
    data() {
      return {
        data: countries,
        unemploymentTemplate: function () {
          return {
            template: Unemployment
          }
        },
        flagtemplate: function() {
          return {
            template: Flag
          }
        },
      };
    },
    mounted() {
      setInterval(
          () => {
            let item = this.data[0];
            item.unemployment += 0.1;
            this.dataStateChange(this.data);
            console.log('New unemployment: '+this.data[0].unemployment);
          }, 10000);
    },
    methods: {
      dataStateChange: function(state) {
        this.data = state;
      }
    }
  }
</script>
<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/bootstrap.css';
  @import '../node_modules/@syncfusion/ej2-vue-treegrid/styles/bootstrap.css';
  @import '../node_modules/@syncfusion/ej2-vue-grids/styles/bootstrap.css';
</style>
