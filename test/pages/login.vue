<template>
<div>
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
    </v-form>
    <v-btn
        @click="submit"
    >
        submit
    </v-btn>
    </div>
</template>

<script>
 // import axios from 'axios'
export default {
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
         datas: {
           email: this.email,
           password: this.password
         }
       })
       //   .then(() => {})
     },
     clear () {
       this.$refs.form.reset()
     }
   }
 }
</script>
