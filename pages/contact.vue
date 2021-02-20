<template>
  <v-container>
    <v-row justify="center">
      <v-breadcrumbs :items="items" divider="/"></v-breadcrumbs>
    </v-row>
    <br>
      <div data-aos='fade-up' class="text-center">
          <h2>C O N T A C T</h2>
          <br>
          <div class="contact-card">
            <v-card height="200px" width="370px" data-aos='fade-up'>
              <br>
              <br>
              <h3 data-aos='fade-up' class="text-center"> E-MAIL : {{ email }} </h3>
            </v-card>
          </div>
      </div>
      <v-card-text>
        <div data-aos='fade-up' class="btn-center">
        <v-btn
          v-for= "icon in icons"
          :key= "icon"
          class="mx-3 gray--text"
          icon
        >
          <v-icon size="30px">
            {{ icon }}
          </v-icon>
        </v-btn>
        </div>
      </v-card-text>
  </v-container>
</template>

<style>
.contact-card {
  display: inline-block;
}

@media screen and (max-width: 768px){
  .btn-center {
    text-align: center;
    margin-top: -100px;
  }
}

@media screen and (min-width: 1025px){
  .btn-center {
    text-align: center;
    margin-top: -100px;
  }
}
</style>

<script>
export default {
  data: () => ({
    email: 'tmyk.engineer@gmail.com',
    icons: [
      'mdi-facebook',
      'mdi-twitter',
      'mdi-github',
      'mdi-instagram',
    ],
    items: [
      {
        text: "home",
        disabled: false,
        href: "/",
      },
      {
        text: "contact",
        disabled: false,
        href: "/contact",
      },
    ],
  }),
};
</script>
