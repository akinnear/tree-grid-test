<template>
  <div class="image" style="display: inline">
    <img class="e-image" :alt="data.name" :src="image">   {{data.name }}</img>
  </div>
</template>

<script>
  export default {
    name: "Flag",
    data: function() {
      return {
        data: {},
      }
    },
    computed: {
      image: function () {
        if (this.data.parentItem) {
          return "images/" + this.data.parentItem.name + ".png";
        }
        return "images/" + this.data.name + ".png";
      }
    }
  }
</script>

<style scoped>
  .e-image {
    height: 13px;
    width: 14px;
    vertical-align: middle;
  }
</style>
