<template>
  <v-app id="app" class="fill-height">
    <v-layout row class="fill-height" style="padding-bottom:60px" >
        <v-flex md8 offset-md2 style="overflow:auto;" class="pr-3 pl-3" v-if="HANDLE" ref="chatContainer">
          <div v-for="chat in CHATS" class="mt-4 mb-4" style="max-width:80%">
              <app-chat-item :chat="chat"></app-chat-item>
          </div>
        </v-flex>
        <v-flex v-else md4 offset-md4 class="text-xs-center">
            <app-chat-handle></app-chat-handle>
        </v-flex>
        <v-bottom-nav :value="true" absolute color="blue">
          <v-layout>
            <app-chat-box></app-chat-box>
          </v-layout>
        </v-bottom-nav>
    </v-layout>
  </v-app>
</template>

<script>
import {mapGetters} from 'vuex'
import chatItem from './components/ChatItem'
import chatHandle from './components/Handle'
import chatBox from './components/ChatBox'

export default {
  components : {
    appChatItem : chatItem,
    appChatHandle : chatHandle,
    appChatBox : chatBox,
  },
  computed:{
    ...mapGetters(['CHATS','HANDLE'])
  },
  mounted(){
    this.$store.dispatch("SET_CHAT");
  },
  updated(){
    var container = this.$refs.chatContainer;
    container.scrollTop = container.scrollHeight;
  },
  sockets : {
    connect: function(){
      console.log('socket connected');
    },
    chat : function(val){
      this.$store.dispatch("ADD_CHAT",val);
    }
  }
}

</script>

<style>
html,body{
  height: 100%
}
</style>
