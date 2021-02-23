<template>
  <v-container>
    <!-- <v-row justify="center">
      <v-breadcrumbs :breadclumbs="breadclumbs" divider="/"></v-breadcrumbs>
    </v-row> -->
    <br>
    <div data-aos='fade-up' class="text-center">
      <v-card class="mx-auto" max-width="670px">
        <br>
        <p v-bind:style="txtCenterObj"> お問い合わせ </p>
        <v-card-text>
          <v-form>
            <v-select
              v-model="select"
              :items="items"
              :error-messages="お問い合わせを選択してください"
              label="お問い合わせ内容選択"
              required
              @change="$v.select.$touch()"
              @blur="$v.select.$touch()"
            ></v-select>

            <v-text-field
              v-model="name"
              :error-messages="名前は10文字以内"
              :counter="10"
              label="お名前"
              required
              @input="$v.name.$touch()"
              @blur="$v.name.$touch()"
            ></v-text-field>

            <v-text-field
              v-model="email"
              :error-messages="有効なE-MAILを入力してください"
              label="E-MAIL"
              required
              @input="$v.email.$touch()"
              @blur="$v.email.$touch()"
            ></v-text-field>

            <v-checkbox
              v-model="checkbox"
              :error-messages="チェックしてください"
              label="個人情報保護方針に同意する"
              required
              @change="$v.checkbox.$touch()"
              @blur="$v.checkbox.$touch()"
            ></v-checkbox>

            <v-btn
              class="mr-4"
              color="primary"
              @click="submit"
              >送信
            </v-btn>

            <v-btn
              class="mr-4"
              color="error"
              @click="clear"
            >クリア
            </v-btn>

          </v-form>
          <br>
        </v-card-text>
      </v-card>
    <br><br>
    </div>
      <div data-aos='fade-up' class="text-center">
          <h2>C O N T A C T</h2>
          <br>
          <div class="contact-card">
            <v-card height="200px" width="370px" data-aos='fade-up'>
              <br>
              <br>
              <h3 data-aos='fade-up' class="text-center"> E-MAIL : {{ emailAddress }} </h3>
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
import { validationMixin } from 'vuelidate'
import { required, maxLength, email } from 'vuelidate/lib/validators'

export default {
  mixins: [validationMixin],
  validations: {
    select: {required},
    name: { required, maxLength: maxLength(10) },
    email: { required, email },
    checkbox: {
      checked(val) {
        return val
      }
    }
  },

  data: () => ({
    emailAddress: 'tmyk.engineer@gmail.com',
    icons: [
      'mdi-facebook',
      'mdi-twitter',
      'mdi-github',
      'mdi-instagram',
    ],
    breadclumbs: [
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

    name: '',
    email: '',
    select: null,
    items: [
     'サービス内容に関するお問い合わせ',
     '広報・取材関連に関するお問い合わせ',
     'その他'
    ],
    checkbox: false,
    txtCenterObj: {
      'text-align': 'center',
      'font-size': '32px',
      color: 'gray'
    }

  }),

  computed: {
    nameErrors: function(){
      const errors = []
      if(!this.$v.name.$dirty) return errors
        !this.$v.name.maxLength && errors.push('お名前は10文字以内で入力してください')
        !this.$v.name.required && errors.push('お名前の入力は必須です')
      return errors
    },
    emailErrors: function() {
      const errors = []
      if(!this.$v.email.$dirty) return errors
        !this.$v.email.email && errors.push('有効なE-MAILを入力してください')
        !this.$v.email.required && errors.push('E-MAILの入力は必須です')
      return errors
    },
    checkboxErrors: function() {
      const errors = []
      if (!this.$v.checkbox.$dirty) return errors
      !this.$v.checkbox.checked && errors.push('You must agree to continue!')
      return errors
    },
    selectErrors () {
      const errors = []
      if (!this.$v.select.$dirty) return errors
      !this.$v.select.required && errors.push('Item is required')
      return errors
    }
   },

  methods: {
    submit: function() {
      this.$v.touch()
    },
    clear: function() {
      this.$v.reset
      this.name = ''
      this.email = ''
      this.select = ''
      this.checkbox = ''
     }
  }
};
</script>
