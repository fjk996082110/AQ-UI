<template>
  <div class="question-wrap">
    <div class="question-title">{{_question.content}}</div>
    <div class="question-check">
      <RadioGroup v-model="radio">
        <Radio
          v-for="(item, index) in _question.answerList"
          :name="item.name"
          :key="index"
        >
          {{item.content}}
        </Radio>
      </RadioGroup>
    </div>
    <Popup
      v-model="showPopup"
      position="bottom"
      :style="{ height: '60%' }"
      class="question-popup"
    >
      <div class="popup-title">答案解析</div>
      <div class="popup-inner">{{_question.explain}}</div>
    </Popup>
  </div>
</template>

<script>
import { RadioGroup, Radio, Popup } from 'vant'
export default {
  name: 'question-wrap',
  props: {
    questionitem: {
      type: Object,
      required:  true,
      default: () => {}
    }
  },
  components: {
    RadioGroup,
    Radio,
    Popup,
  },
  watch: {
    radio() {
      this.showResult()
    }
  },
  computed: {
    _question() {
      return this.questionitem
    },
  },
  data() {
    return {
      radio: '',
      showPopup: false,
    }
  },
  methods: {
    showResult() {
      console.log('show result');
      this.showPopup = true;
    }
  }
}
</script>

<style lang="scss" scoped>
.question-wrap {
  height: 100%;
  .question-title {
    font-size: 32px;
  }
  /deep/ .question-check {
    padding-top: 20px;
    padding-left: 20px;
    box-sizing: border-box;

    .van-radio-group {
      margin-top: 30px;
      .van-radio {
        height: 100px;
        font-size: 32px;
      }
    }
  }
  /deep/ .question-popup {
    padding: 20px;
    box-sizing: border-box;
    .popup-title {
      font-size: 32px;
    }
    .popup-inner {
      margin-top: 30px;
      font-size: 34px;
      line-height: 55px;
    }
  }
}
</style>