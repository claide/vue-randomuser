<template>
  <div>
    <h1>Vue Random users with avatar component</h1>
    <table>
      <tr v-for="(user, index) in users" :key="index">
        <td>
          <avatar :image="user.picture.medium" :size="96"/>
        </td>
        <td>{{ user.name.first }} {{ user.name.last }}</td>
        <td>{{ user.email }}</td>
        <td>{{ user.phone }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import Avatar from 'vue-avatar-component'

export default {
  components: { Avatar },
  data () {
    return {
      users: {}
    }
  },
  mounted () {
    fetch('https://randomuser.me/api/?results=6&nat=us')
    .then((response) => {
      return response.json()
    })
    .then((data) => {
      this.users = data.results
    })
  }
}
</script>

<style>

</style>
