<template>
  <div class="container" id="app">
    <main class="main"><br>
      <section class="block">
        <v-row justify="center" align="center">
          <h1 class="block-title">高血圧症危険度チェック</h1>
        </v-row>
        <div class="block-body">
          <div class="contents view"><br>
あZZあZZ
            <!-- 初期表示 --> <br>
            <main justify="center" align="center" class="main top-page" v-show="status === 0">
              <v-card
                data-aos="zoom-in-up"
                data-aos-anchor-placement="top-bottom"
              ><br>
                <p align="center">高血圧症危険度をチェックします。</p><br>
                <p>質問は５問あります。</p><br>
                <ul class="answerList-start">
                  <v-btn
                    justify="center" align="center"
                    class="button1"
                    data-aos='zoom-out'
                    data-aos-duration="1100"
                    outlined
                    >
                    <a href="#" @click.prevent.stop="start" class="">START</a>
                  </v-btn>
                </ul><br>
              </v-card>
            </main>

            <!-- 質問表示 -->
              <transition name="fade" v-for="q in questions">
                <main class="main top-page" v-show="q.num === status">
                  <v-card><br>
                  <h3>質問{{q.num}}</h3><br><br>
                  <h4 class="leadText" v-if="q">{{q.sentence}}</h4><br>
                  <ul class="answerList">
                    <ul class="answerList">
                      <v-btn
                        class="v-btn-1"
                        data-aos='zoom-out'
                        data-aos-duration="1100"
                        outlined
                      >
                        <a href="#" @click.prevent.stop="answer('yes')">はい</a>
                      </v-btn><br><br>
                      <v-btn
                        class="v-btn-1"
                        data-aos='zoom-out'
                        data-aos-duration="1100"
                        outlined
                      >
                        <a href="#" @click.prevent.stop="answer('num')">いいえ</a>
                      </v-btn><br>
                    </ul><br>
                  </ul>
                  </v-card>
                </main>
              </transition>

            <!-- 診断結果 -->
            <transition name="fade">
              <main class="main top-page" v-show="isFinish">
                <h2>診断結果</h2><br>
                <p class="leadText">{{results.sentence}}</p><br>
                <v-btn class="text-center">
                  <a href="#" @click.prevent.stop="reset">最初からやり直す</a>
                </v-btn>
              </main>
            </transition><br>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
  // 表示させる質問(Q1~Q5) (配列)
  let questions = [
    { num: 1, point: 1, sentence: 'めまいを感じることがある' },
    { num: 2, point: 2, sentence: '味付けは濃い方が好きだ' },
    { num: 3, point: 2, sentence: 'タバコをよく吸っている' },
    { num: 4, point: 2, sentence: '最近怒りっぽくなった' },
    { num: 5, point: 3, sentence: 'ストレスを抱え込みやすい' },
  ]
  // 結果表示(ポイントによって変化) (配列)
  let results = [
    { min: 0, max: 4, sentence: '高血圧症の危険度は低いです。'},
    { min: 5, max: 7, sentence: '高血圧症の危険度が高いです。生活を見直しましょう'},
    { min: 8, max: 10, sentence: '既に高血圧症を罹患している可能性があります。すぐに医者に受診して生活を改善しましょう'}
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
      //
      question() {
        return questions.filter(q => q.num === this.status).shift()
      },
      //
      result() {
        return results.filter(a=> this.sum >= a.min && this.sum <= a.max).shift()
      },
      // 質問終了後表示プロパティ
      isFinish() {
        return this.status > questions.length
      }
    },
    // メソッド
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
          // 「はい」をクリックで質問に応じたポイント加算。
          this.sum = this.sum + question.point
        }
        // 次の質問へ行く(+1)
        this.status++
      }
    }
  }
</script>

<style>
  a {
    color: #fff;
  }

  .button1 {
    margin-right: 30px;
  }

  .v-btn-1 {
    display: inline-block;
    padding: 20px;
    border-radius: 4px;
    background: #ffffff;
    color: #fff;
    width: 38%;
    margin-right: 48px;
  }

  .img2 {
    z-index: 1;
  }

  .container {
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
  }

  .main.top-page {
    text-align: center;
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
    margin-top: 10px;
    margin-right: 36px;
    width: 38%;
    text-align: center;
    color: white;
  }

  .answerList li a {
    display: block;
    padding: 16px;
    border-radius: 4px;
    background: #38acc0;
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
