<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="minha logo">
        </h1>
     <button class="button" @click="changeTheme" >{{textButtton}}</button>

    </header>
</template>
<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent ({
    name: 'App',
    emits:['aoChangedTheme'],
    data (){
      return {
        IsDarkthemeAtive: false,
      };
    },
    computed:{
      textButtton () {
        if (this.IsDarkthemeAtive){
        
          return 'Desativar dark theme';
        }
        return 'Ativar dark theme';
      },
    },
  methods:{
    changeTheme () {
      this.IsDarkthemeAtive = !this.IsDarkthemeAtive;
this.$emit('aoChangedTheme', this.IsDarkthemeAtive);
    }
  },
});

</script>

<style scoped>
img{
    border-radius: 50px
}
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
   text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
   
  }
}

</style>
