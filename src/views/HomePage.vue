<template>
  <ion-content class="ion-padding header">
    <div class="welcome">
      <h1>Metric Converter</h1>
      <p class="name">by <span>Rezky Wahyudi M.</span></p>
    </div>

    <ion-select
      class="s-blue"
      label="Metric units :"
      fill="outline"
      shape="round"
      v-model="metricSelected"
    >
      <ion-select-option value="mLength">Length</ion-select-option>
      <ion-select-option value="mMass">Mass</ion-select-option>
      <ion-select-option value="mTime">Time</ion-select-option>
      <ion-select-option value="mEc">Electric Current</ion-select-option>
      <ion-select-option value="mTemp">Temperature</ion-select-option>
      <ion-select-option value="mLi">Light Intensity</ion-select-option>
      <ion-select-option value="mAos">Amount of Substance</ion-select-option>
    </ion-select>
  </ion-content>

  <ion-content class="ion-padding">
    <ion-item>
      <p class="from result">
        {{ !metricSelected || !selectedFromValue ? "" : fromValue || 0 }}
      </p>

      <ion-select
        v-if="!metricSelected"
        class="metric"
        :disabled="!metricSelected"
        justify="end"
        label="Select Metric unit first.."
      >
      </ion-select>

      <ion-select
        v-else:
        class="metric"
        :disabled="!metricSelected"
        justify="end"
        v-model="selectedFromValue"
      >
        <ion-select-option v-if="metricSelected === 'mLength'" value="km"
          >Kilometer</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="hm"
          >Hektometer</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="dam"
          >Dekameter</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="m"
          >Meter</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="dm"
          >Desimeter</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="cm"
          >Centimeter</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="mm"
          >Milimeter</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mMass'" value="mg"
          >Miligram</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mMass'" value="g"
          >Gram</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mTemp'" value="c"
          >Celcius</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mTemp'" value="f"
          >Fahrenheit</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mTime'" value="h"
          >Hour</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mTime'" value="min"
          >Minute</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mEc'" value="amp"
          >Ampere</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mEc'" value="mA"
          >Milliampere</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLi'" value="lx"
          >Lux</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLi'" value="fc"
          >Footcandle</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mAos'" value="mol"
          >Mole</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mAos'" value="kmol"
          >Kilomole</ion-select-option
        >
      </ion-select>
    </ion-item>
    <br />
    <ion-item>
      <p class="from result">
        {{ !metricSelected || !selectedToValue ? "" : toValue || 0 }}
      </p>

      <ion-select
        v-if="!metricSelected"
        class="metric"
        :disabled="!metricSelected"
        justify="end"
        label="Select Metric unit first.."
      ></ion-select>

      <ion-select
        v-else:
        class="metric"
        :disabled="!metricSelected"
        justify="end"
        v-model="selectedToValue"
      >
        <ion-select-option v-if="metricSelected === 'mAos'" value="kmol"
          >Kilomole</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mAos'" value="mol"
          >Mole</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLi'" value="fc"
          >Footcandle</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLi'" value="lx"
          >Lux</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mEc'" value="mA"
          >Milliampere</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mEc'" value="amp"
          >Ampere</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mTime'" value="min"
          >Minute</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mTime'" value="h"
          >Hour</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="mm"
          >Milimeter</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="cm"
          >Centimeter</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="dm"
          >Desimeter</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="m"
          >Meter</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="dam"
          >Dekameter</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="hm"
          >Hektometer</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mLength'" value="km"
          >Kilometer</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mMass'" value="g"
          >Gram</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mMass'" value="mg"
          >Miligram</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mTemp'" value="f"
          >Fahrenheit</ion-select-option
        >
        <ion-select-option v-if="metricSelected === 'mTemp'" value="c"
          >Celcius</ion-select-option
        >
      </ion-select>
    </ion-item>

    <div class="ion-padding numpad grid">
      <ion-button class="item1" @click="inputEl(7)">7</ion-button>
      <ion-button class="item2" @click="inputEl(8)">8</ion-button>
      <ion-button class="item3" @click="inputEl(9)">9</ion-button>
      <ion-button class="c-red item4" @click="inputEl('del')"
        ><svg
          width="22"
          height="18"
          viewBox="0 0 22 18"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M6.43429 0H20.8991C21.4514 0 21.8991 0.44772 21.8991 1V17C21.8991 17.5523 21.4514 18 20.8991 18H6.43429C6.09993 18 5.7877 17.8329 5.60224 17.5547L0.268902 9.5547C0.0449689 9.2188 0.0449689 8.7812 0.268902 8.4453L5.60224 0.4453C5.7877 0.1671 6.09993 0 6.43429 0ZM6.96947 2L2.3028 9L6.96947 16H19.8991V2H6.96947ZM12.8991 7.5858L15.7275 4.75736L17.1418 6.17157L14.3133 9L17.1418 11.8284L15.7275 13.2426L12.8991 10.4142L10.0707 13.2426L8.65646 11.8284L11.4849 9L8.65646 6.17157L10.0707 4.75736L12.8991 7.5858Z"
            fill=""
          />
        </svg>
      </ion-button>
      <ion-button class="item5" @click="inputEl(4)">4</ion-button>
      <ion-button class="item6" @click="inputEl(5)">5</ion-button>
      <ion-button class="item7" @click="inputEl(6)">6</ion-button>
      <ion-button class="c-red item8" @click="inputEl('AC')">AC</ion-button>
      <ion-button class="item9" @click="inputEl(1)">1</ion-button>
      <ion-button class="item10" @click="inputEl(2)">2</ion-button>
      <ion-button class="item11" @click="inputEl(3)">3</ion-button>
      <ion-button class="item12" @click="inputEl(0)">0</ion-button>
      <ion-button class="item13" @click="inputEl('.')">.</ion-button>
      <ion-button
        class="item14"
        v-if="metricSelected === 'mTemp'"
        :disabled="false"
        @click="inputEl('-')"
        >+/_</ion-button
      >
      <ion-button class="item14" v-else :disabled="true">+/_</ion-button>
      <ion-button class="c-blue item15" @click="presentToast('middle')"
        ><svg
          id="copy"
          width="18"
          height="20"
          viewBox="0 0 18 20"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M3.99989 4V1C3.99989 0.44772 4.44761 0 4.99989 0H16.9999C17.5522 0 17.9999 0.44772 17.9999 1V15C17.9999 15.5523 17.5522 16 16.9999 16H13.9999V18.9991C13.9999 19.5519 13.55 20 12.9931 20H1.00675C0.450682 20 9.15527e-05 19.5554 9.15527e-05 18.9991L0.00269151 5.00087C0.00279151 4.44811 0.452731 4 1.00951 4H3.99989ZM2.00251 6L2.00028 18H11.9999V6H2.00251ZM5.99989 4H13.9999V14H15.9999V2H5.99989V4Z"
            fill=""
          />
        </svg>
      </ion-button>
    </div>
  </ion-content>
</template>

<script lang="ts">
import {
  IonContent,
  IonItem,
  IonList,
  IonSelect,
  IonSelectOption,
  IonButton,
  IonTextarea,
  toastController,
} from "@ionic/vue";
import { defineComponent } from "vue";
import { StatusBar, Style } from "@capacitor/status-bar";
import { Clipboard } from "@capacitor/clipboard";

StatusBar.setOverlaysWebView({ overlay: true });

function handleDarkModeChange(e: any) {
  if (e.matches) {
    StatusBar.setStyle({ style: Style.Dark });
  } else {
    StatusBar.setStyle({ style: Style.Light });
  }
}
const darkModeMediaQuery = window.matchMedia("(prefers-color-scheme: dark)");
darkModeMediaQuery.addEventListener("change", handleDarkModeChange);
handleDarkModeChange(darkModeMediaQuery);

export default defineComponent({
  components: {
    IonContent,
    IonItem,
    IonList,
    IonSelect,
    IonSelectOption,
    IonButton,
    IonTextarea,
  },

  data() {
    return {
      fromValue: "",
      toValue: "",
      metricSelected: null,
      selectedFromValue: null,
      selectedToValue: null,
      fromUnit: null,
      toUnit: null,
      negativeMode: false,
    };
  },

  watch: {
    metricSelected() {
      this.selectedFromValue = null;
      this.selectedToValue = null;
      this.fromValue = "";
      this.toValue = "";
    },
    selectedFromValue(newFromUnit) {
      if (newFromUnit !== this.toUnit) {
        this.toUnit = newFromUnit;
        this.updateConversion();
      }
    },
    selectedToValue(newToUnit) {
      if (newToUnit !== this.fromUnit) {
        this.fromUnit = newToUnit;
        this.updateConversion();
      }
    },
  },

  computed: {
    conversionResult() {
      if (this.metricSelected === "mLength") {
        return this.convertLength();
      } else if (this.metricSelected === "mMass") {
        return this.convertMass();
      } else if (this.metricSelected === "mTemp") {
        return this.convertTemperature();
      } else if (this.metricSelected === "mTime") {
        return this.convertTime();
      } else if (this.metricSelected === "mEc") {
        return this.convertElectricCurrent();
      } else if (this.metricSelected === "mLi") {
        return this.convertLightIntensity();
      } else if (this.metricSelected === "mAos") {
        return this.convertAmountOfSubstance();
      } else {
        return "";
      }
    },
  },

  methods: {
    inputEl(dat: any) {
      if (
        (!isNaN(dat) || dat === "." || dat === "0") &&
        this.metricSelected !== null &&
        this.selectedFromValue !== null &&
        this.selectedToValue !== null
      ) {
        if (dat === "." && this.fromValue.includes(".")) {
          return;
        }

        if (this.fromValue.length < 15) {
          if (dat === "." && this.fromValue === "") {
            this.fromValue += "0";
          }
          this.fromValue += dat + "";
          this.toValue = this.conversionResult;

          if (this.toValue.length > 15) {
            this.toValue = parseFloat(this.toValue).toExponential(10);
          }
        }
      }

      if (dat === "AC") {
        this.fromValue = "";
        this.toValue = "";
      }

      if (dat === "del") {
        this.fromValue = this.fromValue.slice(0, this.fromValue.length - 1);
        this.toValue = this.fromValue === "" ? "" : this.conversionResult;
      } else if (dat === "-") {
        if (this.fromValue !== "") {
          this.negativeMode = !this.negativeMode;
          if (this.negativeMode) {
            this.fromValue = "-" + this.fromValue;
          } else {
            this.fromValue = this.fromValue.replace("-", "");
          }
          this.toValue = this.conversionResult;
        }
      }
    },

    updateConversion() {
      if (this.fromValue !== "") {
        this.toValue = this.conversionResult;
      }
    },

    convertLength() {
      const from = parseFloat(this.fromValue);
      let result = "";

      if (this.selectedFromValue === "km" && this.selectedToValue === "hm") {
        result = (from * 10).toFixed();
      } else if (
        this.selectedFromValue === "km" &&
        this.selectedToValue === "dam"
      ) {
        result = (from * 100).toFixed();
      } else if (
        this.selectedFromValue === "km" &&
        this.selectedToValue === "m"
      ) {
        result = (from * 1000).toFixed();
      } else if (
        this.selectedFromValue === "km" &&
        this.selectedToValue === "dm"
      ) {
        result = (from * 10000).toFixed();
      } else if (
        this.selectedFromValue === "km" &&
        this.selectedToValue === "cm"
      ) {
        result = (from * 100000).toFixed();
      } else if (
        this.selectedFromValue === "km" &&
        this.selectedToValue === "mm"
      ) {
        result = (from * 1000000).toFixed();
      } else if (
        this.selectedFromValue === "hm" &&
        this.selectedToValue === "km"
      ) {
        result = (from / 10).toFixed(3);
      } else if (
        this.selectedFromValue === "hm" &&
        this.selectedToValue === "dam"
      ) {
        result = (from * 10).toFixed();
      } else if (
        this.selectedFromValue === "hm" &&
        this.selectedToValue === "m"
      ) {
        result = (from * 100).toFixed();
      } else if (
        this.selectedFromValue === "hm" &&
        this.selectedToValue === "dm"
      ) {
        result = (from * 1000).toFixed();
      } else if (
        this.selectedFromValue === "hm" &&
        this.selectedToValue === "cm"
      ) {
        result = (from * 10000).toFixed();
      } else if (
        this.selectedFromValue === "hm" &&
        this.selectedToValue === "mm"
      ) {
        result = (from * 100000).toFixed();
      } else if (
        this.selectedFromValue === "dam" &&
        this.selectedToValue === "km"
      ) {
        result = (from / 100).toFixed(3);
      } else if (
        this.selectedFromValue === "dam" &&
        this.selectedToValue === "hm"
      ) {
        result = (from / 10).toFixed(3);
      } else if (
        this.selectedFromValue === "dam" &&
        this.selectedToValue === "m"
      ) {
        result = (from * 10).toFixed();
      } else if (
        this.selectedFromValue === "dam" &&
        this.selectedToValue === "dm"
      ) {
        result = (from * 100).toFixed();
      } else if (
        this.selectedFromValue === "dam" &&
        this.selectedToValue === "cm"
      ) {
        result = (from * 1000).toFixed();
      } else if (
        this.selectedFromValue === "dam" &&
        this.selectedToValue === "mm"
      ) {
        result = (from * 10000).toFixed();
      } else if (
        this.selectedFromValue === "m" &&
        this.selectedToValue === "km"
      ) {
        result = (from / 1000).toFixed(3);
      } else if (
        this.selectedFromValue === "m" &&
        this.selectedToValue === "hm"
      ) {
        result = (from / 100).toFixed(3);
      } else if (
        this.selectedFromValue === "m" &&
        this.selectedToValue === "dam"
      ) {
        result = (from / 10).toFixed(3);
      } else if (
        this.selectedFromValue === "m" &&
        this.selectedToValue === "dm"
      ) {
        result = (from * 10).toFixed();
      } else if (
        this.selectedFromValue === "m" &&
        this.selectedToValue === "cm"
      ) {
        result = (from * 100).toFixed();
      } else if (
        this.selectedFromValue === "m" &&
        this.selectedToValue === "mm"
      ) {
        result = (from * 1000).toFixed();
      } else if (
        this.selectedFromValue === "dm" &&
        this.selectedToValue === "km"
      ) {
        result = (from / 10000).toFixed(3);
      } else if (
        this.selectedFromValue === "dm" &&
        this.selectedToValue === "hm"
      ) {
        result = (from / 1000).toFixed(3);
      } else if (
        this.selectedFromValue === "dm" &&
        this.selectedToValue === "dam"
      ) {
        result = (from / 100).toFixed(3);
      } else if (
        this.selectedFromValue === "dm" &&
        this.selectedToValue === "m"
      ) {
        result = (from / 10).toFixed(3);
      } else if (
        this.selectedFromValue === "dm" &&
        this.selectedToValue === "cm"
      ) {
        result = (from * 10).toFixed();
      } else if (
        this.selectedFromValue === "dm" &&
        this.selectedToValue === "mm"
      ) {
        result = (from * 100).toFixed();
      } else if (
        this.selectedFromValue === "cm" &&
        this.selectedToValue === "km"
      ) {
        result = (from / 100000).toFixed(3);
      } else if (
        this.selectedFromValue === "cm" &&
        this.selectedToValue === "hm"
      ) {
        result = (from / 10000).toFixed(3);
      } else if (
        this.selectedFromValue === "cm" &&
        this.selectedToValue === "dam"
      ) {
        result = (from / 1000).toFixed(3);
      } else if (
        this.selectedFromValue === "cm" &&
        this.selectedToValue === "m"
      ) {
        result = (from / 100).toFixed(3);
      } else if (
        this.selectedFromValue === "cm" &&
        this.selectedToValue === "dm"
      ) {
        result = (from / 10).toFixed(3);
      } else if (
        this.selectedFromValue === "cm" &&
        this.selectedToValue === "mm"
      ) {
        result = (from * 10).toFixed();
      } else if (
        this.selectedFromValue === "mm" &&
        this.selectedToValue === "km"
      ) {
        result = (from / 1000000).toFixed(3);
      } else if (
        this.selectedFromValue === "mm" &&
        this.selectedToValue === "hm"
      ) {
        result = (from / 100000).toFixed(3);
      } else if (
        this.selectedFromValue === "mm" &&
        this.selectedToValue === "dam"
      ) {
        result = (from / 10000).toFixed(3);
      } else if (
        this.selectedFromValue === "mm" &&
        this.selectedToValue === "m"
      ) {
        result = (from / 1000).toFixed(3);
      } else if (
        this.selectedFromValue === "mm" &&
        this.selectedToValue === "dm"
      ) {
        result = (from / 100).toFixed(3);
      } else if (
        this.selectedFromValue === "mm" &&
        this.selectedToValue === "cm"
      ) {
        result = (from / 10).toFixed(3);
      } else {
        result = this.fromValue;
      }

      return result;
    },

    convertMass() {
      const from = parseFloat(this.fromValue);
      if (this.selectedFromValue === "mg" && this.selectedToValue === "g") {
        return (from / 1000).toFixed(3);
      } else if (
        this.selectedFromValue === "g" &&
        this.selectedToValue === "mg"
      ) {
        return (from * 1000).toFixed();
      } else {
        return "";
      }
    },

    convertTemperature() {
      const from = parseFloat(this.fromValue);
      if (!isNaN(from)) {
        if (this.selectedFromValue === "c" && this.selectedToValue === "f") {
          const result = (from * 9) / 5 + 32;
          return result.toFixed(1);
        } else if (
          this.selectedFromValue === "f" &&
          this.selectedToValue === "c"
        ) {
          const result = ((from - 32) * 5) / 9;
          return result.toFixed(3);
        } else {
          return "";
        }
      } else {
        return "";
      }
    },

    convertTime() {
      const from = parseFloat(this.fromValue);
      if (this.selectedFromValue === "h" && this.selectedToValue === "min") {
        return (from * 60).toFixed();
      } else if (
        this.selectedFromValue === "min" &&
        this.selectedToValue === "h"
      ) {
        return (from / 60).toFixed(2);
      } else {
        return "";
      }
    },

    convertElectricCurrent() {
      const from = parseFloat(this.fromValue);
      if (this.selectedFromValue === "amp" && this.selectedToValue === "mA") {
        return (from * 1000).toFixed();
      } else if (
        this.selectedFromValue === "mA" &&
        this.selectedToValue === "amp"
      ) {
        return (from / 1000).toFixed(3);
      } else {
        return "";
      }
    },

    convertLightIntensity() {
      const from = parseFloat(this.fromValue);
      if (this.selectedFromValue === "lx" && this.selectedToValue === "fc") {
        return (from / 10.764).toFixed(3);
      } else if (
        this.selectedFromValue === "fc" &&
        this.selectedToValue === "lx"
      ) {
        return (from * 10.764).toFixed(3);
      } else {
        return "";
      }
    },

    convertAmountOfSubstance() {
      const from = parseFloat(this.fromValue);
      if (this.selectedFromValue === "mol" && this.selectedToValue === "kmol") {
        return (from / 1000).toFixed(3);
      } else if (
        this.selectedFromValue === "kmol" &&
        this.selectedToValue === "mol"
      ) {
        return (from * 1000).toFixed();
      } else {
        return "";
      }
    },

    async copyText() {
      try {
        let formattedValue = this.toValue + " ";

        if (this.selectedToValue === "f" || this.selectedToValue === "c") {
          formattedValue += "°";
        }

        formattedValue += this.selectedToValue;

        await Clipboard.write({
          string: formattedValue,
        });
      } catch (error) {
        throw error;
      }
    },

    async presentToast(position: "top" | "middle" | "bottom") {
      if (
        this.metricSelected !== null &&
        this.toValue !== "" &&
        this.selectedToValue !== null
      ) {
        this.copyText();
        const toast = await toastController.create({
          message: "Copied to clipboard!",
          duration: 1500,
          position: position,
        });
        await toast.present();
      }
    },
  },
});
</script>

<style scoped>
* {
  letter-spacing: -0.4px;
}

ion-content.header {
  --ion-background-color: hsl(222, 80%, 90%);
  max-height: 30vh;
}

.welcome {
  padding-inline-start: calc(31px + var(--ion-safe-area-left, 0px));
}

ion-content h1 {
  margin-top: 1em;
  letter-spacing: -2px;
  font-size: 2.4rem;
  font-weight: var(--bold-font);
}

ion-content p.name {
  color: hsl(0, 0%, 30%);
  font-size: 0.75rem;
  margin-top: -0.6em;
  margin-left: 2px;
}

ion-content p.name span {
  font-weight: var(--medium-font);
}

ion-select.s-blue {
  --background: hsl(222, 80%, 40%);
  --border-radius: 28px;
  --border-style: none;
  --padding-top: 1.3em;
  --padding-bottom: 1.3em;
  color: hsl(0, 0%, 100%);
  max-width: 100%;
  margin-top: 3em;
}

ion-item p.result {
  max-width: 100%;
  margin: 0;
  font-size: 1.5rem;
  font-weight: var(--semibold-font);
  padding-inline-start: calc(16px + var(--ion-safe-area-left, 0px));
}

ion-select::part(icon) {
  color: hsl(0, 0%, 0%);
}

ion-select.s-blue::part(icon) {
  color: hsl(0, 0%, 100%);
}

ion-item {
  border-radius: 24px;
}

ion-select.metric {
  --padding-top: 1.5em;
  --padding-bottom: 1.5em;
  margin-top: 0.4em;
  font-size: 0.875rem;
  background-color: transparent;
  padding-inline-end: calc(var(--ion-safe-area-right, 0px) + 16px);
}

ion-button {
  --background: hsl(222, 80%, 90%);
  --color: hsl(0, 0%, 0%);
  --border-radius: 24px;
  --box-shadow: none;
  --ripple-color: hsl(222, 80%, 40%);
  --padding-top: 1.3em;
  --padding-bottom: 1.3em;
  font-size: 1.5rem;
  font-weight: normal;
}

ion-button.c-blue {
  --background: hsl(222, 80%, 40%);
  --color: hsl(0, 0%, 100%);
  --ripple-color: hsl(0, 0%, 100%);
}

ion-button.c-red {
  --background: hsl(0, 80%, 90%);
  --ripple-color: hsl(0, 50%, 50%);
}
.numpad {
  position: fixed;
  bottom: 0;
  right: 0;
  left: 0;
}

.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
}

.item1 {
  grid-area: 1 / 1 / 2 / 2;
}
.item2 {
  grid-area: 1 / 2 / 2 / 3;
}
.item3 {
  grid-area: 1 / 3 / 2 / 4;
}
.item4 {
  grid-area: 1 / 4 / 2 / 5;
}
.item5 {
  grid-area: 2 / 1 / 3 / 2;
}
.item6 {
  grid-area: 2 / 2 / 3 / 3;
}
.item7 {
  grid-area: 2 / 3 / 3 / 4;
}
.item8 {
  grid-area: 2 / 4 / 3 / 5;
}
.item9 {
  grid-area: 3 / 1 / 4 / 2;
}
.item10 {
  grid-area: 3 / 2 / 4 / 3;
}
.item11 {
  grid-area: 3 / 3 / 4 / 4;
}
.item12 {
  grid-area: 4 / 1 / 5 / 2;
}
.item13 {
  grid-area: 4 / 2 / 5 / 3;
}
.item14 {
  grid-area: 4 / 3 / 5 / 4;
}
.item15 {
  grid-area: 3 / 4 / 5 / 5;
}

svg {
  fill: hsl(0, 0%, 0%);
}

svg#copy {
  fill: hsl(0, 0%, 100%);
}

@media (prefers-color-scheme: dark) {
  ion-content.header {
    --ion-background-color: hsl(222, 0%, 12%);
  }

  ion-content h1 {
    color: hsl(0, 0%, 92%);
  }

  ion-content p.name {
    color: hsl(0, 0%, 60%);
  }

  ion-select.s-blue {
    --background: hsl(222, 60%, 30%);
    color: hsl(0, 0%, 92%);
  }

  ion-item {
    --border-color: hsl(0, 0%, 22%);
    color: hsl(0, 0%, 92%);
  }

  ion-item p.result {
    color: hsl(0, 0%, 92%);
  }

  ion-select::part(icon) {
    color: hsl(0, 0%, 92%);
  }

  ion-select.s-blue::part(icon) {
    color: hsl(0, 0%, 92%);
  }

  ion-button {
    --background: hsl(222, 0%, 14%);
    --color: hsl(0, 0%, 92%);
    --ripple-color: hsl(222, 80%, 40%);
  }

  ion-button.c-blue {
    --background: hsl(222, 60%, 30%);
    --color: hsl(0, 0%, 92%);
    --ripple-color: hsl(0, 0%, 100%);
  }

  ion-button.c-red {
    --background: hsl(0, 20%, 20%);
    --ripple-color: hsl(0, 50%, 50%);
    color: hsl(0, 0%, 92%);
  }
  svg {
    fill: hsl(0, 0%, 92%);
  }

  svg#copy {
    fill: hsl(0, 0%, 88%);
  }
}
</style>
