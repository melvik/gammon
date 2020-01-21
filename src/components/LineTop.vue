<template>
    <div class="top-row">
        <ul :style="{ left: lft + 'px' }">
            <li v-for="(n, i) in pieceValue.n" :key="i" :style="{height: hgt + 'px'}" @click="move">
                <img src="@/assets/circle-white.png" alt="" v-if="pieceValue.c == 'w'">
                <img src="@/assets/circle-black.png" alt="" v-if="pieceValue.c == 'b'">
            </li>
        </ul>
    </div>
</template>

<script>
export default {
  name: 'LineTop',
  props: {
      column: {
          type: Number,
          required: true
      },
      piece: {
          type: Object,
          required: true
      }
  },
  data () {
      return {
          pieceValue: {}
      }
  },
  methods: {
      move() {
          console.error('MOVE-T')
          if(this.pieceValue.c == 'w') {
              this.$emit('move-white')
              console.warn('move-white')
          } else {
              this.$emit('move-black')
              console.warn('move-black')
          }
      }
  },
  computed: {
      lft () {
          return this.column <= 6 ? this.column * 50 : this.column * 50 + 35
      },
      hgt () {
          return this.pieceValue.n <= 5 ? 50 : 40
      }
  },
  mounted () {
    this.pieceValue = this.piece
  }  
}
</script>

<style>
.top-row ul {
     position: absolute;
     top: 13px;
 }
 ul li {
     list-style:none;
 }
 ul li img{
     height: 50px;
 }
</style>