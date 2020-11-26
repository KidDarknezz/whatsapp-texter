<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-secondary">
      <q-toolbar>
        <q-toolbar-title>
          Whatsapp Texter
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <q-page>
        <q-card class="absolute-center" style="width: 700px; max-width: 80vw;">
          <q-form @submit="openChat()">
            <q-card-section>
              <i
                class="fab fa-whatsapp fa-3x text-center full-width q-mb-md text-secondary"
              ></i>
              <div class="text-h6 text-bold">
                Text to any Whatsapp Number
              </div>
            </q-card-section>
            <q-card-section>
              <q-input
                type="number"
                filled
                lable="Number"
                placeholder="65656565"
                color="secondary"
                v-model="phoneNumber"
                :rules="[(val) => !!val || 'Field is required']"
              />
            </q-card-section>
            <q-card-actions class="q-px-md">
              <q-btn
                push
                color="secondary"
                label="Open Chat"
                class="full-width q-mb-md text-bold"
                type="submit"
              />
            </q-card-actions>
          </q-form>
        </q-card>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      phoneNumber: "",
    };
  },
  methods: {
    openChat() {
      window.location.href = `https://wa.me/507${this.phoneNumber}`;
    },
  },
  mounted() {
    let displayMode = "browser tab";
    if (navigator.standalone) {
      displayMode = "standalone-ios";
    }
    if (window.matchMedia("(display-mode: standalone)").matches) {
      displayMode = "standalone";
    }
    console.log("DISPLAY_MODE_LAUNCH:", displayMode);
  },
};
</script>

<style></style>
