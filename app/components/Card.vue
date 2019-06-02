<template>
  <div>
      <div class=card :class="{ selected: this.card.status }" 
           @click="clicked"
      >
      </div>
  </div>
</template>

<script>
export default {
  props :{
    card:{
      type: Object,
      required: true
    }
  },
  data: function () {
    return {
      selected: false
    }
  },
  // computed: {
  //   selected: function() {
  //     return this.init
  //   }
  // },

  // mounted: function () {
  //   this.selected = this.init
  // },
  methods: {
    clicked() {
      this.$emit('click-card', this.card)
    }
  }
}
</script>

<style>
.card {
  flex: 1;
  margin: .5em;
  height: 100px;
  min-width: 100px;
  background-color: rgb(201, 219, 223);
  border-radius: 3px;
  filter-drop-shadow: 0px 2px 6px rgba(#000,.4);
  transition: all 1s ease;
}
.card:hover {
  transform: scale(1.20);
  z-index: 1;
  box-shadow: 0 5px 12px rgba(#000,.2);
}

.selected {
  background-color: rgb(199, 65, 121);
}
</style>