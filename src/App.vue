<template>
  <div id="board" class="boardClass" tabindex="0" @keydown="rewriteCell">
    <div class="boardMatrix" v-for="(matrix, indexMatrix) in board" :key="indexMatrix">
      <div class="boardCell" :class="{ selectedCell: select[0]==indexMatrix&& select[1]==indexCell }" v-for="(cell, indexCell) in matrix" :key="indexCell" @click="selectCell(indexMatrix, indexCell)">
        {{ cell }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Sudoku',
  components: {
  },
  data() {
    return {
      select: [0,0],
      matrix: [0,0,0,0,0,0,0,0,0],
      board: []
    }
  },
  mounted() {
    for (let index = 0; index < 9; index++) {
      this.board[index]=Array.from(this.matrix);

    }
    
  },
  watch: {
	  select: function name(newBoard) {
        this.checkValidity(newBoard);
	  }
  },
  methods: {
    selectCell(indexBigger, indexSmaller) {
      this.select=[indexBigger, indexSmaller]; 

    },
    rewriteCell(event){
      if(!isNaN(event.key)){
        this.board[this.select[0]][this.select[1]]=event.key;
      }
    },
	checkValidity(newBoard){
		var t=this.board[this.select[0]][this.select[1]]
		for (let index = this.select[0]; index < 9; index++) {
			
			if (this.board[]) {
				
			}
			
		}
	}
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.boardClass{
	width: 900px;
	height: 900px;
  border-style: solid;
  border-color: black;
  display: grid;
  grid-template: 300px 300px 300px/ 300px 300px 300px;
  box-sizing: border-box;
}
.boardMatrix{
  width:300px;
  height:300px;
  position: relative;
  border-style: solid;
  border-color: black;
  display: grid;
  grid-template: 100px 100px 100px/ 100px 100px 100px;
  box-sizing: border-box;
}
.boardCell{
  width:100px;
  height:100px;
  position: relative;
  display: block;
  border-style: solid;
  border-color: black;
  box-sizing: border-box;
  font-size: 50px;
  text-align: center;
  
}
.selectedCell{
  background:cadetblue;
}
</style>
