<template>
<!-- <div>
    <v-form v-model="valid">
    <v-text-field
        v-model="email"
        :rules="emailRules"
        label="Email"
        required
    ></v-text-field>
            {{email}}
    <v-text-field
        v-model="password"
        :rules="passwordRules"
        label="Password"
        required
    ></v-text-field>
      <v-spacer></v-spacer>
    </v-form>
    <v-btn
        @click="submit"
    >
        submit
    </v-btn>
    </div> -->
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
                <v-form>
                  <v-text-field
                      v-model="email"
                      :rules="emailRules"
                      label="Email"
                      required
                  ></v-text-field>
                    {{email}}              
                  <v-text-field
                    v-model="password"
                      :rules="passwordRules"
                      label="Password"
                      required
                  ></v-text-field>
                    </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn 
                  @click="submit" to="/user">submit
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
// import axios from 'axios'
export default {
  auth: false,
  data: () => ({
    valid: false,
    password: '',
    passwordRules: [
      v => !!v || 'Password is required',
      v => /.+@.+/.test(v) || 'Password must be valid'

    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+/.test(v) || 'E-mail must be valid'
    ]
  }),
  methods: {
    submit () {
      this.$auth.loginWith('local', {
        data: {
          email: this.email,
          password: this.password
        }
      })
    },
    clear () {
      this.$refs.form.reset()
    }
  }
}
</script>

