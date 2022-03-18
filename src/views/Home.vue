<template>
  <div class="home-wrap">
    <!-- <div class="question-inner" v-for="item in questionList" :key="item.id"> -->
    <div class="question-inner">
      <questionitem :questionitem.sync="currentQuestion"></questionitem>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import questionitem from '@/components/question'
export default {
  name: 'Home',
  components: {
    questionitem
  },
  data() {
    return {
      questionList: [],
      currentQuestion: {}
    }
  },
  mounted() {
    this.getQuestionList();
  },
  methods: {
    getQuestionList() {
      this.questionList = [
        {
          id: '123',
          content: '题目',
          answer: 'A',
          answerList: [
            { name: 'key1', content: '选项'},
            { name: 'key2', content: '选项'},
            { name: 'key3', content: '选项'},
            { name: 'key4', content: '选项'},
          ],
          explain: '解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释解释'
        }
      ]
      this.currentQuestion = this.questionList[0]
    }
  }
}
</script>
<style lang="scss" scoped>
.home-wrap {
  height: 100%;
  width: 95%;
  margin: 0 auto;
  background-color: #fff;
  .question-inner {
    padding-top: 40px;
    box-sizing: border-box;
    height: 100%;
  }
}
</style>
