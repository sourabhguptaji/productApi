<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 2</ion-title>
      </ion-toolbar>
    </ion-header>
  <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 2</ion-title>
        </ion-toolbar>
      </ion-header>
      
      <ion-card  v-for="post in posts" :key="post.id"  >
    <ion-card-header>
      <ion-row>
        <ion-col size="3">
          <ion-img width="80" height="80" :src="post.image">

          </ion-img>
        </ion-col>
      <ion-col size="7">
      <ion-card-title>{{post.title}}</ion-card-title>
      <ion-card-subtitle>{{post.description}}</ion-card-subtitle>
      
      </ion-col>
      <ion-col size="2">
        <ion-card-subtitle>  {{post.price}}     </ion-card-subtitle>
      </ion-col>
      </ion-row>
    </ion-card-header>

    <ion-card-content>
     <ion-row>
       <ion-col size="6">
        <ion-card-subtitle > {{post.category}}</ion-card-subtitle>
       </ion-col>
      <ion-col size="6">  </ion-col>
     </ion-row>
    <ion-row>
      <ion-button @click= "openToast"><ion-title>Remove From List</ion-title></ion-button>
    </ion-row>
    </ion-card-content>
    
  </ion-card>
 </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import {useRoute} from 'vue-router';
export default  {
  name: 'Tab2',
  
  components: {  IonHeader, IonToolbar, IonTitle, IonContent, IonPage },

  setup(){
    const route = useRoute();
    const {id} = route.params;
    return{ id };
  }
}
</script>