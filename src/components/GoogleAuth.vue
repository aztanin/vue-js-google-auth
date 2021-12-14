<template>
  <div>
    <button v-google-signin-button="clientId"> Continue with Google</button>
    <table v-if="googleUser != null">
      <tr>
        <th>Name</th>
        <td>{{ googleUser.name }}</td>
      </tr>
      <tr>
        <th>Email</th>
        <td>{{ googleUser.email }}</td>
      </tr>
      <tr>
        <th>Picture</th>
        <td><img :src="googleUser.picture" alt=""></td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      clientId: 'add here your google cliend id',
      googleUser: null

    }
  },
  methods: {
    OnGoogleAuthSuccess(idToken) {
      axios.get('https://oauth2.googleapis.com/tokeninfo?id_token=' + idToken).then((response) => {
        this.googleUser = response.data;
        console.log(this.googleUser);
      });
    },
    OnGoogleAuthFail(error) {
      console.log(error)
    }
  }
}
</script>
