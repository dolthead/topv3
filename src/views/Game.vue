<template>
  <ion-page class="page">
    <ion-header>
      <ion-toolbar color="primary">
        <ion-buttons slot="start">
          <ion-back-button></ion-back-button>
        </ion-buttons>
        <ion-title>Topzee</ion-title>
        <ion-buttons slot="end">
          <ion-button @click="openRules">
            <ion-icon slot="icon-only" :icon="helpCircleOutline"></ion-icon>
          </ion-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <div id="container">
        <div class="score-card">
          <ion-grid>
            <ion-row>
              <ion-col>
                <ion-row><ion-col>Ones</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>Twos</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>Threes</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>Fours</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>Fives</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>Sixes</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>Bonus</ion-col><ion-col>[]</ion-col></ion-row>
              </ion-col>
              <ion-col>
                <ion-row><ion-col>3 OAK</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>4 OAK</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>Full house</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>4 straight</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>5 straight</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>5 OAK</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>Any</ion-col><ion-col>[]</ion-col></ion-row>
              </ion-col>
            </ion-row>
            <ion-row>
              <ion-col>
                <ion-row><ion-col>Subtotal</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row><ion-col>TOTAL</ion-col><ion-col>[]</ion-col></ion-row>
              </ion-col>
              <ion-col>
                <ion-row><ion-col>Subtotal</ion-col><ion-col>[]</ion-col></ion-row>
                <ion-row>
                  <ion-col></ion-col>
                  <ion-col>
                    <ion-button size="small">Save</ion-button>
                  </ion-col>
                </ion-row>
              </ion-col>
            </ion-row>
          </ion-grid>
        </div>
        <div class="dice-row">
          <ion-button class="die">1</ion-button>
          <ion-button class="die">2</ion-button>
          <ion-button class="die">3</ion-button>
          <ion-button class="die">4</ion-button>
          <ion-button class="die">5</ion-button>
        </div>
        <div class="roll-row">
          <span class="turn-indicator"></span>
          <span class="turn-indicator"></span>
          <span class="turn-indicator"></span>
          <ion-button>ROLL</ion-button>
        </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { helpCircleOutline } from "ionicons/icons";
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
  IonGrid,
  IonRow,
  IonCol,
} from "@ionic/vue";
import { defineComponent } from "vue";
import Rules from "./Rules.vue";

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
    IonGrid,
    IonRow,
    IonCol,
  },
  setup() {
    const openRules = async () => {
      const modal = await modalController.create({
        component: Rules,
        cssClass: "my-custom-class",
        componentProps: {
          title: "Rules",
        },
      });
      return modal.present();
    };
    return {
      openRules,
      helpCircleOutline,
    };
  },
});
</script>

<style scoped>
#container {
  text-align: center;
}
.score-card {
  border-radius: 4px;
  border: 1px solid lightgray;
  margin: 12px;
}
ion-col:first-child {
  text-align: start;
}
ion-col:last-child {
  text-align: end;
}
.dice-row {
  display: flex;
  flex-direction: row;
  padding: 0 16px;
}
.die {
  display: flex;
  width: 18vw;
  height: 18vw;
  margin: 0 5px 10px 5px;
  justify-content: center;
  align-items: center;
}
.roll-row {
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: flex-end;
  padding: 0 16px;
}
.turn-indicator {
  background-color: green;
  border-radius: 50%;
  width: 24px;
  height: 24px;
  margin: 4px;
}
</style>