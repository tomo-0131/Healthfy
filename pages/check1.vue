<template>
  <div class="container" id="app">
    <main class="main">
      <section class="block">
        <v-row justify="center" align="center">
           <v-col cols="10">
            <h1 class="block-title">脂質異常症危険度チェック</h1>
           </v-col>
        </v-row>
        <div class="block-body">
          <div class="contents view">
          <br>
            <!-- 初期表示 -->
              <main class="main top-page" v-show="status === 0">
                <p class="leadText">高血圧症危険度をチェックします。</p>
                <ul class="answerList start">
                  <v-btn
                    dark
                    class="white--text"
                    color=blue
                  >
                    <a href="#" @click.prevent.stop="start" class="">スタート</a>
                  </v-btn>
                </ul>
              </main>
            <br>
            <!-- 質問表示 -->
              <transition name="fade" v-for="q in questions">
                <main class="main top-page" v-show="q.num === status">
                  <b>質問{{q.num}}</b>
                  <p class="leadText" v-if="q">{{q.sentence}}</p>
                  <ul class="answerList">
                    <ul class="answerList">
                      <li><a href="#" @click.prevent.stop="answer('yes')">はい</a></li>
                      <li><a href="#" @click.prevent.stop="answer('num')">いいえ</a></li>
                    </ul>
                  </ul>
                </main>
              </transition>

            <!-- 診断結果 -->
            <transition name="fade">
              <main class="main top-page" v-show="isFinish">
                <b>診断結果</b>
                <br>
                <p class="leadText">{{result.sentence}}</p>
                <v-btn class="text-center">
                  <a href="#" @click.prevent.stop="reset">最初からやり直す</a>
                </v-btn>
              </main>
            </transition>
            <br>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>



<script>
  // 表示させる質問(Q1~Q5) (配列)
  let questions = [
    { num: 1, point: 1, sentence: '魚よりは肉をよく食べる' },
    { num: 2, point: 2, sentence: 'ファーストフードをよく食べる' },
    { num: 3, point: 2, sentence: '野菜やきのこ類はあまり食べない' },
    { num: 4, point: 2, sentence: '最近、太り気味だと思う' },
    { num: 5, point: 3, sentence: '運動をあまりしていない' },
  ]
  // 結果表示(ポイントによって変化) (配列)
  let results = [
    { min: 0, max: 4, sentence: '脂質異常症の危険度は低いです。'},
    { min: 5, max: 7, sentence: '脂質異常症の危険度が高いです。生活を見直しましょう'},
    { min: 8, max: 10, sentence: '既に脂質異常症の可能性があります。\* すぐに医者に受診して生活を改善しましょう'}
  ]

  export default {
    // 初期値
    data() {
      return {
      status: 0,
      sum: 0,
      questions: questions
      }
    },
    // 算出プロパティ
    computed: {
      question() {
        return questions.filter(q => q.num === this.status).shift()
      },
      result() {
        return results.filter(a=> this.sum >= a.min && this.sum <= a.max).shift()
      },
      isFinish() {
        return this.status > questions.length
      }
    },
    methods: {
      start() {
        this.status = 1
      },
      reset() {
        this.status = 0
        this.sum = 0
      },
      answer(type) {
        // 現在の質問を取得
        let question = questions.filter((q) => {
          return q.num === this.status
        }).shift()

        // 答えが「はい」の場合
        if (type === 'yes') {
          // 「はい」をクリックでポイント加算。sum。
          this.sum = this.sum + question.point
        }
        // 次の質問へ行く
        this.status++
      }
    }
  }
</script>

<style>
  .img2 {
    z-index: 1;
  }

  .container {
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
  }

  .answerList {
    margin: 0;
    padding: 0;
    list-style: none;
    text-align: center;
  }

  .answerList.start li {
    display: inline-block;
    width: 100%;
    text-align: center;
  }

  .answerList li {
    display: inline-block;
    width: 48%;
    text-align: center;
  }

  .answerList li a {
    display: block;
    padding: 20px;
    border-radius: 4px;
    background: #ff8c00;
    font-weight: bold;
    color: #fff;
  }

  .top-left-enter-active, .top-left-leave-active {
    transform: translate(0px, 0px);
    transition: transform 225ms cubic-bezier(0, 0, 0.2, 1) 0ms;
  }

  .top-left-enter, .top-left-leave-to {
    transform: translateY(-100vh) translateX(-100vh);
  }

  .fade-enter-active {
    transition: opacity 1s;
  }

  .fade-enter,
  .fade-leave-to {
    opacity: 0;
  }
</style>
