<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar color="primary">
        <ion-buttons slot="start">
          <ion-back-button></ion-back-button>
        </ion-buttons>
        <ion-title>Topzee</ion-title>
        <ion-buttons slot="end">
          <ion-button @click="openAbout">
            <ion-icon
              slot="icon-only"
              :icon="informationCircleOutline"
            ></ion-icon>
          </ion-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Topzee</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">
        <p>
          Game
        </p>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { informationCircleOutline } from "ionicons/icons";
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
  IonBackButton,
} from "@ionic/vue";
import { defineComponent } from "vue";
import About from './About.vue';

export default defineComponent({
  name: "Game",
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonButtons,
    IonButton,
    IonIcon,
    IonBackButton,
  },
  setup() {
    const openAbout = async () => {
      const modal = await modalController.create({
          component: About,
          cssClass: 'my-custom-class',
          componentProps: {
            title: 'About'
          },
        });
      return modal.present();
    };
    return {
      openAbout,
      informationCircleOutline,
    };
  },
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