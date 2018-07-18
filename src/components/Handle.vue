<template lang="html">
  <v-card class="pl-3 pr-3 pt-5 pb-5 mt-5">
    <h3 class="text-xs-center mb-3">ENTER A HANDLE</h3>
    <v-text-field
      label="Solo"
      placeholder="Type Your Message"
      v-model="handle"
      outline
      single-line
      ref="message">
    </v-text-field>
    <v-btn class="primary" large @click="saveHandle">Save Handle</v-btn>
  </v-card>

</template>

<script>
export default {
  data(){
    return{
      handle : ""
    }
  },
  methods : {
    saveHandle(){
      this.$store.dispatch("SET_HANDLE",this.handle);
    },
  }
}
</script>

<style lang="css">
</style>
