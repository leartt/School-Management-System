<template>
  <v-container id="user-profile" fluid tag="section">

    <v-row justify="center">
      
      <v-col cols="12" md="8">
        <base-material-card>
          <template v-slot:heading>
            <div class="display-2 font-weight-light">{{profileHeading}}</div>

            <div class="subtitle-1 font-weight-light">{{profileDescription}}</div>
          </template>

          <v-form>
            <v-container class="py-0">
              <v-row>
                <v-col cols="12" md="6">
                  <v-text-field label="First Name" class="purple-input" :value="user.name" disabled/>
                </v-col>

                <v-col cols="12" md="6">
                  <v-text-field label="Last Name" class="purple-input" :value="user.surname" disabled/>
                </v-col>

                <v-col cols="12">
                  <v-text-field label="Email Address" class="purple-input" :value="user.User.email" disabled />
                </v-col>

                <v-col cols="12">
                  <v-text-field label="Adress" class="purple-input" :value="user.address" disabled/>
                </v-col>

                <v-col cols="12" md="6">
                  <v-text-field label="Phone" class="purple-input" :value="user.phone" disabled/>
                </v-col>

                <v-col cols="12" md="6">
                  <v-text-field label="Birthday" class="purple-input" :value="user.birthday" disabled/>
                </v-col>
              </v-row>
            </v-container>
          </v-form>
        </base-material-card>
      </v-col>

      <v-col cols="12" md="4">
        <base-material-card
          class="v-card-profile"
          :avatar="`http://localhost:5000/${user.photo_path}`"
        >
          <v-card-text class="text-center">
            <h6 class="display-1 mb-1 grey--text">
              <!-- {{user.}} -->
            </h6>

            <h4 class="display-2 font-weight-light mb-3 black--text">{{user.name}} {{user.surname}}</h4>

            <p
              class="font-weight-light grey--text"
            >Role: {{user.User.role.toUpperCase()}}</p>

          </v-card-text>
        </base-material-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { ReactWrapper } from 'vuera'
export default {
  name: "UserProfile",
  props: ['profileHeading', 'profileDescription'],
  computed: {
    user() {
      return this.$store.state.Auth.user;
    },
  },
  created() {
    this.$store.dispatch("Auth/getProfile");
  }
};
</script>
