<template lang="html">
    <v-tooltip left>
       <span slot="activator">
         <p class="grey--text text--darken-2">
           <b class="indigo--text" v-if="isMyHandle(chat.handle)">{{chat.handle}} :</b>
           <b class="pink--text" v-else>Me :</b>
           {{chat.message}}
         </p>
       </span>
       <span>{{chat.created | moment("HH:MM, DD-MM-YY")}}</span>
    </v-tooltip>
</template>

<script>
export default {
  props : ['chat'],
  methods : {
    isMyHandle(handle){
      if (handle == this.$store.getters.HANDLE) {
        return true
      }else{
        return false
      }
    }
  },
}
</script>
