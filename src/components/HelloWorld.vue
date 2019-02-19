<template>
  <div>
    <h1>Vue Random users with avatar component</h1>

    <div class="container">
      <div class="user-card" v-for="(user, index) in users" :key="index">
        <div class="user-card__content">
          <div class="user-card__img">
            <avatar :image="user.picture.medium" :size="80"/>
          </div>
          <div class="user-card__name">
            {{ user.name.first }} {{ user.name.last }}
          </div>
          <div class="user-card__phone">
            {{ user.phone }}
          </div>
        </div>
      </div>
    </div>

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

<style lang="scss">
  .container {
    text-align: center;
  }

  .user-card {
    width: 18rem;
    border: 1px solid rgba(0,0,0,.125);
    border-radius: .25rem;
    margin: .3rem;
    display: inline-block;

    .user-card__content {
      padding: 1.25rem;

      .user-card__img,
      .user-card__name,
      .user-card__phone {
        margin-bottom: 8px;
      }
    }
  }
</style>
