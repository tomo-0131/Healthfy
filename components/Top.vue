<template>
  <v-row justify="center" align="center">
    <v-col cols="12" lg="12" xs="12">
      <v-row>
        <br>
        <v-img
          class="img1"
          width="1500"
          height="250"
          v-bind:src="require('@/assets/images/one.png')"
        ></v-img>
      </v-row>
    </v-col>
    <div>
      <h2 class="content-title">Let's Health Check !!</h2>
      <p class="text-center">生活習慣病リスクを今すぐに調べましょう！</p>
      <v-divider></v-divider>
    <br>
    <br>
    <div>
      <div class="about">
        <div class="me">
          <h2><font-awesome-icon icon="pen" class="icon" />脂質異常症チェック</h2>
          <p class="text">脂質異常症チェック</p>
          <v-btn
            class="white--text"
            color=blue
            link to="/check1"
            >
            脂質異常症：危険度チェック
           </v-btn>
        </div>
        <br>
        <div class="me">
          <h2><font-awesome-icon icon="school" class="icon" />糖尿病チェック</h2>
          <p class="text">糖尿病危険度チェック</p>
          <v-btn
            class="white--text"
            color=blue
            link to="/check1"
            >
            脂質異常症：危険度チェック
          </v-btn>
        </div>
        <br>
        <div class="me">
          <h2><font-awesome-icon icon="birthday-cake" class="icon" />高血圧症チェック</h2>
          <p class="text">高血圧症危険度チェック</p>
          <v-btn
            class="white--text"
            color=blue
            link to="/check1"
            >
            高血圧症：危険度チェック
           </v-btn>
        </div>
      </div>
    </div>
    <br>
    <br>
      <v-divider />
      <br>
      </div>
      <br>
  </v-row>
</template>

<style>
@media screen and (max-width: 768px){
  .img1 {
    display: inline-block;
  }
	.about {
		flex-direction: column;
	}
	.me {
    margin: 0 auto;
	}
  .about-image {
   height: 300px;
   margin-top: -10px;
  }
  .content-title {
    margin-top: 30px;
  }
}

@media screen and (min-width: 1025px){
  .img1 {
    margin-right: 190px;
  }

  .content-title {
    text-align: center;
    margin-top: 35px;
  }

  .about {
    display:inline-flex;
  }

  .me{
      margin:0 50px;
  }

  .about-image {
    height: 300px;
    margin-top: -70px;
  }
}
</style>
