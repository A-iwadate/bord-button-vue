<template>
<div class=card-wrapper>
  <div v-for="(columnCards, columnNumber) in cards"
       :key="columnNumber"
  >
    <card
      v-for="card in columnCards"
      :key="card.id"
      :card="card"
      @click-card="changeUDLRCard"
    >
    </card>
  </div>
</div>
</template>

<script>
import Card from '~/components/Card.vue'

export default {
  components:{
    Card,
  },
  data() {
    return {
      rows:3,
      columns:3, 
      cards:[]
    }
  },
  // computed: {
  // },
  created() {
    let count = 1
    let rowCards
    for (let column = 0; column < this.columns; column++) {
      rowCards = []
      for (let row = 0; row < this.rows; row++) {
        let card = {
              id: count,
              row: row,
              column: column,
              status: false
            }
        rowCards.push(card)
        count++
      }
      this.cards.push(rowCards)
    }
  },
  methods: {
    changeUDLRCard: function(selectedCard){
      // 選択されたカードのStatusを反転
      this.cards[selectedCard.column][selectedCard.row].status = !this.cards[selectedCard.column][selectedCard.row].status

      // 選択されたカードの上にカードがあればStatusを反転
      if(this.cards[selectedCard.column][selectedCard.row-1]){
        this.cards[selectedCard.column][selectedCard.row-1].status = !this.cards[selectedCard.column][selectedCard.row-1].status
      }

      // 選択されたカードの下にカードがあればStatusを反転
　    if(this.cards[selectedCard.column][selectedCard.row+1]){
        this.cards[selectedCard.column][selectedCard.row+1].status = !this.cards[selectedCard.column][selectedCard.row+1].status
      }

      // // 選択されたカードの左にカードがあればStatusを反転
      // if(this.cards[selectedCard.column-1][selectedCard.row]){
      //   this.cards[selectedCard.column-1][selectedCard.row].status = !this.cards[selectedCard.column-1][selectedCard.row].status
      // }

      // // 選択されたカードの右にカードがあればStatusを反転
      // if(this.cards[selectedCard.column+1][selectedCard.row]){
      //   this.cards[selectedCard.column+1][selectedCard.row].status = !this.cards[selectedCard.column+1][selectedCard.row].status
      // }
    }
  }
}
</script>

<style>
.card-wrapper {
  display: flex;
  flex-flow: row wrap;
}
</style>