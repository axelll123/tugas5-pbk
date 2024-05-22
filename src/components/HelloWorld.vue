<template>
  <q-layout view="hHh lpR fFf">
    
    <!-- Navbar -->
    <q-header elevated class="bg-purple-9 text-white" height-hint="98">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          Bengkel
        </q-toolbar-title>
      </q-toolbar>

      <!-- Tabs -->
      <q-tabs align="left" class="bg-purple-8 text-white">
        <q-route-tab to="/page1" label="Servis" />
        <q-route-tab to="/page2" label="Produk" />
        <q-route-tab to="/page3" label="Kontak" />
      </q-tabs>
    </q-header>

    <!-- Page Container -->
    <q-page-container class="bg-dark text-white">
      <q-page class="q-pa-md">

        <!-- Carousel -->
        <q-carousel
          v-model="slide"
          height="300px"
          control-color="white"
          prev-icon="keyboard_arrow_left"
          next-icon="keyboard_arrow_right"
          class="bg-purple-8 text-white"
        >
          <q-carousel-slide name="1" img-src="src/assets/4.jpeg">
            <div class="absolute-bottom text-center text-subtitle2 text-white">
              Bengkel Slide
            </div>
          </q-carousel-slide>
          <q-carousel-slide v-for="n in 4" :key="n" :name="n + 1" :img-src="'../assets/zz.jpeg'">
            <div class="absolute-bottom text-center text-subtitle2 text-white">
              Slide {{ n + 1 }}
            </div>
          </q-carousel-slide>
        </q-carousel>

        <!-- Cards -->
        <div class="q-gutter-md q-mt-md row q-col-gutter-md">
          <q-card class="q-col-12 q-col-sm-6 q-col-md-4 bg-purple-8 text-white">
            <q-img src="src/assets/1.jpeg" />
            <q-card-section>
              <div class="text-h6">Card Title 1</div>
              <div class="text-subtitle1">Card Subtitle 1</div>
            </q-card-section>
            <q-card-actions align="right">
              <q-btn flat label="Action 1" class="text-white" />
            </q-card-actions>
          </q-card>

          <q-card class="q-col-12 q-col-sm-6 q-col-md-4 bg-purple-8 text-white">
            <q-img src="src/assets/2.jpeg" />
            <q-card-section>
              <div class="text-h6">Card Title 2</div>
              <div class="text-subtitle1">Card Subtitle 2</div>
            </q-card-section>
            <q-card-actions align="right">
              <q-btn flat label="Action 2" class="text-white" />
            </q-card-actions>
          </q-card>

          <q-card class="q-col-12 q-col-sm-6 q-col-md-4 bg-purple-8 text-white">
            <q-img src="src/assets/3.jpeg" />
            <q-card-section>
              <div class="text-h6">Card Title 3</div>
              <div class="text-subtitle1">Card Subtitle 3</div>
            </q-card-section>
            <q-card-actions align="right">
              <q-btn flat label="Action 3" class="text-white" />
            </q-card-actions>
          </q-card>
        </div>

      </q-page>
    </q-page-container>

    <!-- Footer -->
    <q-footer elevated class="bg-purple-9 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          <div>Bengkel</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      slide: 1
    }
  }
}
</script>

<style>
/* Additional styles if needed */
</style>
