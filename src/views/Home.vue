<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Login</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Login</ion-title>
        </ion-toolbar>
      </ion-header>
    
      <div id="container">
        <form @submit.prevent="handleLogin">
      <ion-card>
        <ion-item>
          <h3>Please Sign In!</h3>
        </ion-item>
        <ion-item>
          <ion-label position="floating">Username</ion-label>
          <ion-input v-model="form.username" id="username"></ion-input>
        </ion-item>

        <ion-item>
          <ion-label position="floating">Password</ion-label>
          <ion-input type="password" v-model="form.password" id="password"></ion-input>
        </ion-item>

        <ion-item>
          <ion-button type="submit" shape="round">
            Sign In
          
          </ion-button>
        </ion-item>
        <ion-item>
          <p>Or</p>
        </ion-item>
        <ion-item>
          <ion-button type="button" shape="round">
            Sign Up
           
          </ion-button>
        </ion-item>
      </ion-card>
    </form>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage,IonHeader,IonContent,IonToolbar, IonCard,IonTitle, IonItem, IonLabel, IonButton, IonInput, alertController, IonIcon } from '@ionic/vue'
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Home',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar
  },
  data() {
    return {
      form: {
        username: "",
        password: ""
      }
    };
  },
  methods: {
    async handleLogin(){
      console.log(this.form.username)
      if(this.form.username !='' && this.form.password !=''){
        //alert("here")
        if(this.form.username == 'admin@moreyou.com' && this.form.password == 'admin'){
          const errorAlert = await alertController
            .create({
              header: 'Success',
              
              message: "Logged in successfully",
              buttons: ['OK'],
            });
          await errorAlert.present()
        }else{
          const errorAlert = await alertController
            .create({
              header: 'Failed',
              subHeader: 'Sign in Failed',
              message: "Invalid username or password",
              buttons: ['OK'],
            });
        await errorAlert.present()
        }
      }else{
       // alert("Please fill the required fields")
        const errorAlert = await alertController
            .create({
              header: 'Failed',
              subHeader: 'Sign in Failed',
              message: "Please fill username and password",
              buttons: ['OK'],
            });
        await errorAlert.present()
      }
    }
  }
});
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>