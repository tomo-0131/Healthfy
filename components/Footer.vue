<template>
  <div class="wrapper">
    <v-footer>
      <v-col class="text-center" cols="12">
        <div class="footer" color="white">
          {{ new Date().getFullYear() }} — Copyright Tomoyuki Kumagai All rights
          reserved
        </div>
      </v-col>
    </v-footer>
  </div>
</template>

<style>
  .footer {
    position: relative;/*②絶対位置*/
    bottom: 0; /*下に固定*/
  }
</style>
