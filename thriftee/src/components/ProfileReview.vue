<template>

    <div id = "container">
        <div id = "profiledetails">
        <img id = "profilephoto" src="default.png" alt="Profile Photo">
        <div id = "contentofprofile">
            <h1 id = "profilename"> {{ getName }} </h1>
                
                <div class="rate">
                    <p class="mt-2">Rating: {{ value }}/5</p>
                </div>
            
                <div class="Location">
                    <p class="mt-3">Meet up Location: {{ location }}</p>
                </div>
        </div>

        <div id = "buttonsofprofile">
            <div>
            <router-link to="/editprofile"
                custom
                v-slot="{ navigate }" >
                <button @click="navigate" role="link" id = "editbutton" type="button"> Edit Profile</button> 
            </router-link>  
            </div>
            <div><button id = "signoutbutton" type="button" >Sign Out </button> </div>
        </div>
            
        </div>
        
        <div id="linebreak">
            <hr>
        </div>
    
    <div id = "container2">
        <div>
            <router-link to="/"
                custom
                v-slot="{ navigate }" >
                <button @click="navigate" role="link" id = "listingsbutton" type="button"> <em>Listings</em></button> 
            </router-link>  
        </div>

        <div>
            <router-link to="/profilereviews"
                custom
                v-slot="{ navigate }" >
                <button @click="navigate" role="link" id = "reviewsbutton" type="button"> <em>Reviews</em></button> 
            </router-link>  
        </div>
    </div>

    <div id = "container3">
        <h1>reviews</h1>
    </div>
    </div>
    
</template>
    
<script>
import firebaseApp from '../firebase.js';
    import { getFirestore } from "firebase/firestore";
    import { doc, getDoc } from "firebase/firestore";
    const db = getFirestore(firebaseApp);
    
    let user = await getDoc(doc(db, "Profiles", "uniqueUserID")) // replace with unique user id
    let userData = user.data()

  export default {
    data() {
      return {
        value: 4,
        location: userData.Meet_Up,
        name:userData.Name
      }
    },
    methods: {
            
        }, 

    computed: {
        getName() {
            return userData.Name
        }, 

        getLocation() {
            return userData.Meet_Up
        }

    }
}
</script>

    
<style scoped>

#container2 {
    display: flex;
    justify-content: center;
}

#listingsbutton {
    background: transparent;
    border: none;
    margin-left: 0.3vw;
    font-size: 1.8em;
    color: rgb(8, 8, 8);
    margin-right: 5vw;
 }


 #listingsbutton:hover {
    background: transparent;
    border: none;
    margin-left: 0.3vw;
    font-size: 1.6em;
    color: rgb(117, 113, 113);
    border-bottom: 2px solid rgb(160, 154, 154);
 }

 #reviewsbutton {
    background: transparent;
    border: none;
    margin-left: 0.3vw;
    font-size: 1.8em;
    color: rgb(8, 8, 8);
 }


 #reviewsbutton:hover {
    background: transparent;
    border: none;
    margin-left: 0.3vw;
    font-size: 1.6em;
    color: rgb(117, 113, 113);
    border-bottom: 2px solid rgb(160, 154, 154);
 }


#profiledetails {
    margin-top: 5vh;
    display: flex;
    background-color: rgb(246, 241, 241);
    height: 30vh;
    border-radius: 25px;
    border: 1px solid rgb(195, 187, 187);
    
}
    
hr {
    height: 1px;
    width: 30vw;
    background-color: black;
}
    
#contentofprofile {
    margin-left: 5vw;
}

#buttonsofprofile {
    display:block;
    margin-left: 3vw;
    margin-right: 3vw;
}

button{
  margin-bottom:2vh;
  display:block;
}

#editbutton {
  background-color: #d8c6df; /* Green */
  border: 2px solid #d8c6df; /* Green */
  border-radius: 5px;
  border: 0.5px solid black;
  color: rgb(0, 0, 0);
  padding: 10px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  transition-duration: 0.2s;
  margin-top: 10vh;
}

#editbutton:hover {
  /* background-color: 359138; Green */
  color: white;
  border: 0.5px solid #5a525d; /* Green */
}

#signoutbutton {
  background-color: #9c9ca8; /* Green */
  border: 2px solid #9c9ca8; /* Green */
  border-radius: 5px;
  border: 0.5px solid black;
  color: rgb(0, 0, 0);
  padding: 10px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  transition-duration: 0.2s;
}

#signoutbutton:hover {
  background-color: 359138; /* Green */
  color: white;
  border: 0.5px solid #434246; /* Green */
}

#linebreak{
    margin-top: 5vh;
}



#contentofprofile {
    margin-left: 5vw;
}


img {
    width: auto;
    height: auto;
    margin-left: 2vw;
}
    
</style>