<template>
  <v-container>
    <v-row justify="center">
      <v-breadcrumbs :items="items" divider="/"></v-breadcrumbs>
    </v-row>
    <div data-aos='fade-up' class="text-center">
      <h2>A B O U T</h2>
    </div>
    <br />
    <v-row justify="center">
      <v-img
        data-aos='zoom-out'
        class="justify-center"
        max-height="400"
        max-width="350"
        v-bind:src="require('@/assets/images/three.png')"
      ></v-img>
      <br />
    </v-row>
    <v-row justify="center">
      <div style="white-space: wrap; word-wrap: break-word">
        <br />
        <h2 data-aos='fade-up' class="text-center">H e a l t h f y</h2>
        <br />
        <div data-aos='fade-up' class="text-center">
          Healthfyは、<br><br>数問の質問に答えることで<br /><br>あなたの今の健康度が測れるWebサイトです。
        </div>
        <div data-aos='fade-up' class="text-center">
          <br>質問からあなたの生活習慣病に罹患するリスク、<br><br>
          メンタル面での危険度をチェックすることができます。<br /><br>
          健康に関する様々な質問をこれから増やし充実させていきます。
        </div>
      </div>
    </v-row>
    <br />
    <br />
    <v-row justify="center">
      <v-img
        data-aos='zoom-out'
        class="justify-center"
        lazy-src="https://picsum.photos/id/147/500/300"
        max-height="400"
        max-width="300"
        src="https://picsum.photos/id/147/500/300?greyscale"
      ></v-img>
      <br />
    </v-row>
    <br />
  </v-container>
</template>

<script>
export default {
  data: () => ({
    items: [
      {
        text: "home",
        disabled: false,
        href: "/",
      },
      {
        text: "about",
        disabled: false,
        href: "/about",
      },
    ],
  }),
};
</script>
