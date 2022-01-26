<template>
  <ion-page>
    <ion-header>
      <ion-toolbar color="primary">
        <ion-title>Rules</ion-title>
        <ion-buttons slot="end">
          <ion-button @click="closeRules">
            <ion-icon slot="icon-only" :icon="closeOutline"></ion-icon>
          </ion-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <div id="container">
        <ion-button expand="block" @click="closeRules">Close</ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
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
import { defineComponent } from "vue";
export default defineComponent({
  name: "About",
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonButtons,
    IonButton,
    IonIcon,
  },
  setup() {
    const closeRules = () => {
      modalController.dismiss();
    };
    return {
      closeOutline,
      closeRules,
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