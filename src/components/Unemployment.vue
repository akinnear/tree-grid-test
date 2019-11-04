<template>
  <div id="myProgress">
    <div id="myBar" :class="barClass" :style="{ width: value * 2 + 'px' }">
      <div id="label">{{value}}%</div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Unemployment",
    data: function() {
      return {
        data: {},
      }
    },
    computed: {
      value: function() {
        return this.data.unemployment;
      },
      barClass: function () {
        if (this.value < 4) {
          return 'progressdisable';
        }
      }
    }
  }
</script>

<style scoped>
  #myBar {
    position: absolute;
    width: 10%;
    height: 100%;
    background-color: #00b300;
  }

  #myBar.progressdisable {
    background-color: #df2222;
  }

  #label {
    position: relative;
    left: 10px;
    line-height: 18px;
    font-size: 10px;
    color: black;
  }
  .highcontrast .e-grid #myProgress {
    background-color: black;
  }
  #myProgress {
    position: relative;
    height: 18px;
    width: 10em;
    text-align: left;
    background-color: white;
  }
  #myBar.progressdisable {
    background-color: #df2222;
  }
</style>
