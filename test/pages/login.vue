<template>
    <div id="app">
  <v-app id="inspire">
    <v-content>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title>Please Login</v-toolbar-title>
                <v-spacer></v-spacer>
              </v-toolbar>
              <v-card-text>
                <v-form ref="form" v-model="valid" lazy-validation>
                  <v-text-field
                      v-model="email"
                      :rules="emailRules"
                      label="Email"
                      required
                  ></v-text-field>
                  <v-text-field
                    v-model="password"
                      :rules="passwordRules"
                      label="Password"
                      type="password"
                      required
                  ></v-text-field>
                  </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn 
                  :disabled="!valid"
                  @click="submit">submit
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</div>
</template>

<script>
export default {
  auth: false,
  data: () => ({
    valid: false,
    password: '',
    passwordRules: [
      v => !!v || 'Password is required'
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+/.test(v) || 'E-mail must be valid'
    ]

  }),
  methods: {
    submit () {
      if (this.$refs.form.validate()) {
        this.$auth.loginWith('local', {
          data: {
            email: this.email,
            password: this.password
          }
        })
          .then(() => this.$router.push('/user'))
      }
    },
    clear () {
      this.$refs.form.reset()
    }
  }
}
</script>