<template>
  <div id = "container">
    <div id="nav" v-if="user">
      <router-link to="home" class="routerlink" style="margin-right: 1vw;"> Profile </router-link> |
   
      <router-link to="sell" class="routerlink"> Sell </router-link>
      <hr>
     
    </div>
    
    <router-view />
    
  </div>


  
</template>

<script>
import { getAuth, onAuthStateChanged } from 'firebase/auth'

export default {
  data() {
    return {
      user: false
    }
  },

  created() {
    const auth = getAuth()
    onAuthStateChanged(auth, (user) => {
        this.user = !!user;
    })
  }
}
</script>

<style scoped>

.logo {
  display: block;
  margin: 0 auto 2rem;
}
.routerlink {
  color: rgba(76, 0, 0, 0.832);
  font-family: gill sans, sans-serif;
  font-size: 26px;
  font-style: italic;
  margin-left: 1vw;
  border-bottom: 2px solid  rgba(76, 0, 0, 0.832);
  
}

.routerlink:hover {
  color: rgb(156, 130, 154);
  border-bottom: 2px solid   rgb(156, 130, 154);
}

a { text-decoration: none; }
  

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }
} 

#container {
  margin-top: 3vh;
  font-weight: bold;

}

hr {
    height: 1px;
    width: 10vw;
    background-color: black;
}


</style>
