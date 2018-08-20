<template>
  <v-content>
      <v-data-table
      :headers="headers"
      :items="users"
      hide-actions
      class="elevation-1"
      >
    <template slot="items" slot-scope="props">
      <td class="text-xs-right">{{ props.item.id}}</td>
      <td class="text-xs-right">{{ props.item.name}}</td>
      <td class="text-xs-right">{{ props.item.email}}</td>
      <td class="text-xs-right">{{ props.item.created_at}}</td>
      <td class="text-xs-right">{{ props.item.updated_at}}</td>
    </template>
      </v-data-table>
  </v-content>
</template>

<script>
export default {
  auth: true,
  data () {
    return {
      headers: [
        {
          text: 'Users',
          align: 'left',
          sortable: false,
          value: 'users'
        },
        { text: 'ID', value: 'id' },
        { text: 'Name', value: 'name' },
        { text: 'Email', value: 'email' },
        { text: 'Created at', value: 'created_at' },
        { text: 'Updated at', value: 'updated_at' }
      ],
      users: [
      ]
    }
  },
  methods: {
    getUsers () {
      this.$axios.post('http://localhost:8000/api/me', {
      }).then(data => {
        this.token = data.data
      }).catch(err => {
        this.search = err.response.data
      })
    },
    created () {
      this.getUsers()
    }
  }
}
</script>
