<!-- (24-02-02-fri) -->

<template>
  <div>
    <table id="list">
      <thead>
        <tr>
          <th>글번호</th>
          <th>글제목</th>
          <th>조회수</th>
          <th>삭제</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="board in list" v-bind:key="board.no">
          <td>{{ board.no }}</td>
          <td @click="showRead(board)">{{ board.title }}</td>
          <td>{{ board.view }}</td>
          <td><button @click="deleteBoard(board.no)">삭제</button></td>
        </tr>
      </tbody>
    </table>
    <button style="float: right" @click="showWrite">글쓰기</button>
  </div>
</template>

<script>
export default {
  props: ['list'], // props -> 부모 컴포넌트의 전달값을 받는 속성
  // BoardView.vue에서 <BoardList v-bind:list="boardList" /> 부모가 전달해준 list 바인더해준 값을 가져온것. (용어는 잘 모르겠음)
  // props : 부모컴포넌트에서 전달값을 받아오기위한 속성
  data() {
    return {

    }
  },
  methods: {
    showWrite() {
      console.log(this);
      //부모컴퍼넌트 데이터를 변경
      this.$emit('show-write'); //부모컴퍼넌트에 정의되어있는 이벤트를 실행하기위한 호출
    },
    showRead(board){
      //상세화면 보여주기
      this.$emit('show-read', board)
    },
    deleteBoard(no){ //파라미터 전달. no는 그냥 변수
      this.$emit('board-delete', no);
    }
  }
}
</script>