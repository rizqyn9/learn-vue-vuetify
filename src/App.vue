<template>
  <v-app>
    <v-app-bar
      app
      color="white"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Neurovi Logo"
          class="shrink mr-2"
          contain
          src="@/assets/logoHorizontal.png"
          transition="scale-transition"
          width="120"
        />
      </div>

      <v-spacer></v-spacer>
    </v-app-bar>

    <v-main>
      <TriaseIgd/>
    </v-main>
  </v-app>
</template>

<script>
import TriaseIgd from './components/TriaseIgd';
// import logoHorizontal  from '@/assets/logoHorizontal.png'

export default {
  name: 'App',

  components: {
    TriaseIgd,
  },

  data: () => ({
    //
  }),
};
</script>
