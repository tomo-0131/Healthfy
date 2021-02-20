<template>
  <v-tool-bar dense fixed>
    <br />
    <v-toolbar-title class="text-center">
      <nuxt-link to="/"><h1>H e a l t h f y</h1></nuxt-link>
    </v-toolbar-title>
    <br />
    <v-tabs color="blue" centered v-model="tab">
      <v-tab>
        <nuxt-link to="/">HOME</nuxt-link>
      </v-tab>
      <v-tab>
        <nuxt-link to="/about">ABOUT</nuxt-link>
      </v-tab>
    </v-tabs>
  </v-tool-bar>
</template>
