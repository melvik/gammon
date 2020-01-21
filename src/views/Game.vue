<template>
  <div class="game">
    <Board />
    <!-- left top -->
    <LineTop :column="12" :piece="piece[0]" @move-white="moveWhite(0)" @move-black="moveBlack(0)"/>
    <LineTop :column="11" :piece="piece[1]" @move-white="moveWhite(1)" @move-black="moveBlack(1)" />
    <LineTop :column="10" :piece="piece[2]" @move-white="moveWhite(2)" @move-black="moveBlack(2)" />
    <LineTop :column="9" :piece="piece[3]" @move-white="moveWhite(3)" @move-black="moveBlack(3)" />
    <LineTop :column="8" :piece="piece[4]" @move-white="moveWhite(4)" @move-black="moveBlack(4)" />
    <LineTop :column="7" :piece="piece[5]" @move-white="moveWhite(5)" @move-black="moveBlack(5)" />
    <!-- right top -->
    <LineTop :column="6" :piece="piece[6]" @move-white="moveWhite(6)" @move-black="moveBlack(6)" />
    <LineTop :column="5" :piece="piece[7]" @move-white="moveWhite(7)" @move-black="moveBlack(7)" />
    <LineTop :column="4" :piece="piece[8]" @move-white="moveWhite(8)" @move-black="moveBlack(8)" />
    <LineTop :column="3" :piece="piece[9]" @move-white="moveWhite(9)" @move-black="moveBlack(9)" />
    <LineTop :column="2" :piece="piece[10]" @move-white="moveWhite(10)" @move-black="moveBlack(10)" />
    <LineTop :column="1" :piece="piece[11]" @move-white="moveWhite(11)" @move-black="moveBlack(11)" />
    <!-- left Bottom -->
    <LineBottom :column="13" :piece="piece[12]" @move-white="moveWhite(12)" @move-black="moveBlack(12)" />
    <LineBottom :column="14" :piece="piece[13]" @move-white="moveWhite(13)" @move-black="moveBlack(13)" />
    <LineBottom :column="15" :piece="piece[14]" @move-white="moveWhite(14)" @move-black="moveBlack(14)" />
    <LineBottom :column="16" :piece="piece[15]" @move-white="moveWhite(15)" @move-black="moveBlack(15)" />
    <LineBottom :column="17" :piece="piece[16]" @move-white="moveWhite(16)" @move-black="moveBlack(16)" />
    <LineBottom :column="18" :piece="piece[17]" @move-white="moveWhite(17)" @move-black="moveBlack(17)" />
    <!-- right Bottom -->
    <LineBottom :column="19" :piece="piece[18]" @move-white="moveWhite(18)" @move-black="moveBlack(18)" />
    <LineBottom :column="20" :piece="piece[19]" @move-white="moveWhite(19)" @move-black="moveBlack(19)" />
    <LineBottom :column="21" :piece="piece[20]" @move-white="moveWhite(20)" @move-black="moveBlack(20)" />
    <LineBottom :column="22" :piece="piece[21]" @move-white="moveWhite(21)" @move-black="moveBlack(21)" />
    <LineBottom :column="23" :piece="piece[22]" @move-white="moveWhite(22)" @move-black="moveBlack(22)" />
    <LineBottom :column="24" :piece="piece[23]" @move-white="moveWhite(23)" @move-black="moveBlack(23)" />
  </div>
</template>

<script>
import Board from '@/components/Board'
import LineTop from '@/components/LineTop'
import LineBottom from '@/components/LineBottom'

export default {
  name: 'game',
  components: {
    Board,
    LineTop,
    LineBottom
  },
  data () {
      return {
          piece: [
              {c: 'w', n: 2},
              {c: '', n: 0},
              {c: '', n: 0},
              {c: '', n: 0},
              {c: '', n: 0},
              {c: 'b', n: 5},
              {c: '', n: 0},
              {c: 'b', n: 3},
              {c: '', n: 0},
              {c: '', n: 0},
              {c: '', n: 0},
              {c: 'w', n: 5},
              {c: 'b', n: 5},
              {c: '', n: 0},
              {c: '', n: 0},
              {c: '', n: 0},
              {c: 'w', n: 3},
              {c: '', n: 0},
              {c: 'w', n: 5},
              {c: '', n: 0},
              {c: '', n: 0},
              {c: '', n: 0},
              {c: '', n: 0},
              {c: 'b', n: 2}
            ]
      }
  },
  methods: {
    moveWhite (src) {
        console.error('moveWhite')
        const move = 1
        // debugger
        if (this.piece[src + move].n == 0) {
            this.piece[src + move].n = 1
            this.piece[src + move].c = 'w'
            this.piece[src].n--
            console.log('move 0 - ok', src + move)
        } else {
            if(this.piece[src + move].c == 'w' || this.piece[src + move].c == '') {
                this.piece[src + move].n++
                this.piece[src].n--
                console.log('move 1 - ok', src, src + move)
            } else {
                if(this.piece[src + move].n > 1) {
                    console.log('cant', src, src + move)
                } else {
                    console.log('HIT', src, src + move)
                }
                // this.piece[src + move].n++
            }
        }
    },
    moveBlack (src) {
        console.error('moveBlack')
        const move = -1
        // debugger
        if (this.piece[src + move].n == 0) {
            this.piece[src + move].n = 1
            this.piece[src + move].c = 'b'
            this.piece[src].n--
            console.log('move 0 - ok', src + move)
        } else {
            if(this.piece[src + move].c == 'b' || this.piece[src + move].c == '') {
                this.piece[src + move].n++
                this.piece[src].n--
                console.log('move 1 - ok', src, src + move)
            } else {
                if(this.piece[src + move].n > 1) {
                    console.log('cant', src, src + move)
                } else {
                    console.log('HIT', src, src + move)
                }
                // this.piece[src + move].n++
            }
        }
    }
  }
}
</script>
