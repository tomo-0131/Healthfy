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
            <v-card height="200px" width="400px" data-aos='fade-up'>
              <br>
              <h3 data-aos='fade-up' class="text-center"> E-MAIL : {{ email }} </h3>
            </v-card>
          </div>
      </div>
  </v-container>
</template>

<style>
.contact-card {
  display: inline-block;
}
</style>

<script>
export default {
  data: () => ({
    email: 'tmyk.engineer@gmail.com',
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
