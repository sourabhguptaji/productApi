<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Product Details</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 1</ion-title>
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
      <ion-col size="6">
        <ion-card-subtitle>
        <ion-select placeholder="Select">
          <ion-select-option>1</ion-select-option>
          <ion-select-option>2</ion-select-option>
          <ion-select-option>3</ion-select-option>
        </ion-select>
        </ion-card-subtitle>
      </ion-col>
     </ion-row>
    <ion-row>
      <ion-button @click= "openToast()" ><ion-title>Add to Cart</ion-title></ion-button>
    </ion-row>
    </ion-card-content>
    
  </ion-card>
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent,IonCard,IonImg, toastController } from '@ionic/vue';
import axios from 'axios';
export default  {
  name: 'Tab1',
  props: [],
  components: {  IonHeader, IonToolbar, IonTitle, IonContent, IonPage,IonCard ,IonImg},
  mounted(){
   axios.get("https://fakestoreapi.com/products?limit=6")
    .then(response =>{
      console.log(response.data);
      this.posts= response.data
    })
},
methods:{
  
  async openToast() {
      const toast = await toastController
        .create({
          message: 'Product added to cart',
          duration: 2000
        })
      this.id
      return toast.present();
},
},
 data(){
   return{
     posts: [],
     
   }
 },
}
</script>