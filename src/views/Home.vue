<template>
  <ion-page>
    <ion-header>
      <ion-toolbar color="primary">
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
      <div id="container">
        <ion-card>
          <ion-card-content>
            <div>img</div>
            <ion-list>
              <ion-item lines="none">
                <ion-label>Last game</ion-label>
                <ion-note slot="end">99</ion-note>
              </ion-item>
              <ion-item lines="none">
                <ion-label>Games played</ion-label>
                <ion-note slot="end">99</ion-note>
              </ion-item>
              <ion-item lines="none">
                <ion-label>Average</ion-label>
                <ion-note slot="end">99</ion-note>
              </ion-item>
              <ion-item lines="none">
                <ion-label>High score</ion-label>
                <ion-note slot="end">99</ion-note>
              </ion-item>
            </ion-list>
          </ion-card-content>
        </ion-card>
        <ion-button router-link="/game" expand="block">Play</ion-button>
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
  IonCard,
  IonCardContent,
  IonList,
  IonItem,
  IonLabel,
  IonNote,
} from "@ionic/vue";
import { defineComponent } from "vue";
import About from "./About.vue";

export default defineComponent({
  name: "Home",
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonButtons,
    IonButton,
    IonIcon,
    IonCard,
    IonCardContent,
    IonList,
    IonItem,
    IonLabel,
    IonNote,
  },
  setup() {
    const openAbout = async () => {
      const modal = await modalController.create({
        component: About,
        cssClass: "my-custom-class",
        componentProps: {
          title: "About",
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
}
ion-note {
  --color: black;
}
</style>