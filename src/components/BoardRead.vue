<!-- (24-02-02-fri) -->

<template>
  <table id="list">
    <tr>
      <td style="width:50px">글제목</td>
      <td>{{ obj.title }}</td>
    </tr>
    <tr style="height: 200px">
      <td>글내용</td>
      <td colspan="2">{{ obj.content }}</td>
    </tr>
  </table>
  <button style="float:right;" v-on:click="showList">목록</button>
</template>

<script>
export default {
  props: ['obj'],
  data() {
    return {

    }
  },
  methods: {
    showList(){
      this.$emit("show-list")
    }
  }
}
</script>