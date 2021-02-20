<template>
  <v-row justify="center" align="center">
      <v-row>
        <br>
        <v-img
          data-aos="fade-up"
          class="img1"
          v-bind:src="require('@/assets/images/top.png')"
        ></v-img>
      </v-row>
    <div>
      <h2 data-aos='zoom-in' class="content-title">Let's Health Check !!</h2>
      <p data-aos='fade-up' data-aos-duration="1000" class="text-center">生活習慣病リスクを今すぐに調べましょう！</p>
      <v-divider></v-divider>
    <br>
    <br>
    <div>
      <div class="about">
        <div class="me">
          <h2 data-aos='zoom-in' data-aos-duration="1500" class="text-top">脂質異常症チェック</h2>
          <p class="text-top">脂質異常症チェック</p>
          <v-btn
            data-aos='fade-up' data-aos-duration="1000"
            class="white--text"
            color=blue
            link to="/check1"
            >
            脂質異常症：危険度チェック
           </v-btn>
        </div>
        <br>
        <div class="me">
          <h2 data-aos='zoom-in' data-aos-duration="1500"><font-awesome-icon icon="school" class="icon" />糖尿病チェック</h2>
          <p class="text">糖尿病危険度チェック</p>
          <v-btn
            data-aos='fade-up' data-aos-duration="1000"
            class="white--text"
            color=blue
            link to="/check1"
            >
            脂質異常症：危険度チェック
          </v-btn>
        </div>
        <br>
        <div class="me">
          <h2 data-aos='zoom-in' data-aos-duration="1500"><font-awesome-icon icon="birthday-cake" class="icon" />高血圧症チェック</h2>
          <p class="text">高血圧症危険度チェック</p>
          <v-btn
            data-aos='fade-up' data-aos-duration="1000"
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
    margin-left: 80px;
    max-height: 200px;
    max-width: 300px;
    margin-top: 60px;
  }
	.about {
		flex-direction: column;
    text-align: center;
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
    text-align: center;
  }
  .text-top {
    text-align: center;
  }
}

@media screen and (min-width: 1025px){
  .img1 {
    margin-left: 390px;
    max-height: 200px;
    max-width: 400px;
    margin-top: 60px;
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
