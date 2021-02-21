<template>
  <v-tool-bar dense fixed>
    <br />
    <v-toolbar-title class="text-center">
      <nuxt-link to="/"><h2>H e a l t h f y</h2></nuxt-link>
    </v-toolbar-title>
    <br />
    <v-tabs color="blue" centered v-model="tab">
      <v-tab>
        <nuxt-link to="/">HOME</nuxt-link>
      </v-tab>
      <v-toolbar-items>
      <v-menu offset-y>
        <template v-slot:activator="{on}">
        <v-btn v-on="on" text>CHECK</v-btn>
        </template>
        <v-list>
          <v-list-item>
            <v-list-item-content>
              <nuxt-link to="/check1">脂質異常症リスクチェック</nuxt-link>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <nuxt-link to="/check2">糖尿病リスクチェック</nuxt-link>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <nuxt-link to="/check3">高血圧症リスクチェック</nuxt-link>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>
      </v-toolbar-items>
      <v-tab>
        <nuxt-link to="/about">ABOUT</nuxt-link>
      </v-tab>
      <v-tab>
        <nuxt-link to="/contact">CONTACT</nuxt-link>
      </v-tab>
    </v-tabs>
  </v-tool-bar>
</template>
