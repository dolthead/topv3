<template>
  <ion-page>
    <ion-header>
      <ion-toolbar color="primary">
        <ion-title>About Topzee</ion-title>
        <ion-buttons slot="end">
          <ion-button @click="closeAbout">
            <ion-icon slot="icon-only" :icon="closeOutline"></ion-icon>
          </ion-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <div id="container">
        <ion-button expand="block" @click="closeAbout">Close</ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
  import { closeOutline } from "ionicons/icons";
  import {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonButtons,
    IonButton,
    IonIcon,
    modalController,
  } from "@ionic/vue";

  const closeAbout = () => {
    modalController.dismiss();
  };
</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
  padding: 2vw;
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