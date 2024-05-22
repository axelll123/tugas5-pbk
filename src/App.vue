<template>
  <div>
    <header>
      <div class="container">
        <h1>Mykel Workshop</h1>
        <nav>
          <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </nav>
      </div>
    </header>

    <div class="q-pa-md">
      <q-carousel
        animated
        v-model="slide"
        navigation
        infinite
        :autoplay="autoplay"
        arrows
        transition-prev="slide-right"
        transition-next="slide-left"
        @mouseenter="autoplay = false"
        @mouseleave="autoplay = true"
        class="carousel"
      >
        <q-carousel-slide :name="1" img-src="src/assets/4.jpeg" />
        <q-carousel-slide :name="2" img-src="src/assets/2.jpeg" />
        <q-carousel-slide :name="3" img-src="src/assets/3.jpeg" />
        <q-carousel-slide :name="4" img-src="src/assets/1.jpeg" />
      </q-carousel>
    </div>

    <section id="home" class="hero">
      <div class="container">
        <h2>Welcome to Mykel Workshop</h2>
        <p>Your trusted destination for premium automotive services</p>
        <a href="#services" class="btn">Our Services</a>
      </div>
    </section>

    <div class="q-pa-md row items-start q-gutter-md">
      <q-card class="my-card" flat bordered>
        <q-img src="src/assets/1.jpeg" />

        <q-card-section>
          <div class="text-h5 q-mt-sm q-mb-xs">Mykel CEO</div>
          <div class="text-caption text-grey">
            Leading the Way in Automotive Excellence
          </div>
        </q-card-section>

        <q-card-actions>
          <q-btn flat color="primary" label="Instagram" href="https://www.instagram.com/" target="_blank"/>
          <q-space />
          <q-btn
            color="grey"
            round
            flat
            dense
            :icon="expanded ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
            @click="expanded = !expanded"
          />
        </q-card-actions>

        <q-slide-transition>
          <div v-show="expanded">
            <q-separator />
            <q-card-section class="text-subtitle2">
              {{ lorem }}
            </q-card-section>
          </div>
        </q-slide-transition>
      </q-card>
    </div>

    <section id="services" class="services">
      <div class="container">
        <h2>Our Services</h2>
        <div class="service-grid">
          <div v-for="service in services" :key="service.id" class="service-card">
            <img :src="service.image" :alt="service.name" />
            <h3>{{ service.name }}</h3>
            <p>{{ service.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <section id="about" class="about">
      <div class="container">
        <h2>About Us</h2>
        <p>At Mykel Workshop, we provide top-notch automotive services with a focus on quality and customer satisfaction. Our team of skilled professionals is dedicated to keeping your vehicle in prime condition.</p>
      </div>
    </section>

    <section id="contact" class="contact">
      <div class="container">
        <h2>Contact Us</h2>
        <form @submit.prevent="submitForm">
          <label for="name">Name:</label>
          <input type="text" id="name" v-model="form.name" required />
          
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="form.email" required />
          
          <label for="message">Message:</label>
          <textarea id="message" v-model="form.message" required></textarea>
          
          <button type="submit" class="btn">Submit</button>
        </form>
      </div>
    </section>

    <footer class="bg-body-tertiary text-center text-lg-start">
      <div class="text-center p-3" style="background-color: rgba(0, 0, 0, 0.05);">
        © 2024 Mykel Workshop. All rights reserved.
        <a class="text-body">Powered by Mykel</a>
      </div>
    </footer>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const slide = ref(1);
    const autoplay = ref(true);
    const services = ref([
      { id: 1, name: 'Engine Repair', description: 'High-quality engine repair services to keep your vehicle running smoothly.', image: 'src/assets/service1.jpeg' },
      { id: 2, name: 'Oil Change', description: 'Regular oil changes to maintain optimal engine performance.', image: 'src/assets/service2.jpeg' },
      { id: 3, name: 'Tire Services', description: 'Comprehensive tire services including rotation, balancing, and replacement.', image: 'src/assets/service3.jpeg' },
      { id: 4, name: 'Brake Repair', description: 'Expert brake repair services for your safety and peace of mind.', image: 'src/assets/service4.jpeg' }
    ]);

    const form = ref({
      name: '',
      email: '',
      message: ''
    });

    const submitForm = () => {
      alert(`Name: ${form.value.name}\nEmail: ${form.value.email}\nMessage: ${form.value.message}`);
      form.value.name = '';
      form.value.email = '';
      form.value.message = '';
    };

    return {
      slide,
      autoplay,
      services,
      form,
      submitForm,
      expanded: ref(false),
      lorem: 'Mykel, leading the way in automotive excellence. Our CEO and team are committed to delivering top-notch services to ensure your vehicle remains in prime condition.'
    };
  }
}
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  color: #ddd;
  background-color: #2c2c54;
}

header {
  background-color: #3d3d91;
  color: #fff;
  padding: 1em 0;
}

header .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1em;
}

header nav ul {
  list-style: none;
  display: flex;
  gap: 1em;
}

header nav a {
  color: #fff;
  text-decoration: none;
}

.hero {
  background: url('src/assets/store.jpg') no-repeat center center/cover;
  color: #fff;
  text-align: center;
  padding: 5em 1em;
}

.services {
  padding: 2em 1em;
  background-color: #333;
}

.service-grid {
  display: flex;
  gap: 1em;
  flex-wrap: wrap;
}

.service-card {
  background-color: #444;
  border: 1px solid #555;
  padding: 1em;
  flex: 1 1 calc(33.333% - 2em);
  box-sizing: border-box;
  text-align: center;
}

.service-card img {
  max-width: 100%;
  height: auto;
}

.about, .contact {
  padding: 2em 1em;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1em;
}

.btn {
  background-color: #5e5ee6;
  color: #fff;
  padding: 0.5em 1em;
  text-decoration: none;
  border-radius: 5px;
}

form label {
  display: block;
  margin: 0.5em 0 0.25em;
}

form input, form textarea {
  width: 100%;
  padding: 0.5em;
  margin-bottom: 1em;
  border: 1px solid #555;
  border-radius: 5px;
  background-color: #2c2c54;
  color: #ddd;
}

form button {
  background-color: #5e5ee6;
  color: #fff;
  padding: 0.5em 1em;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.q-card {
  background-color: #3d3d91;
  color: #fff;
}

.q-carousel {
  background-color: #3d3d91;
}

.q-carousel-slide {
  color: #fff;
}

.q-carousel-slide img {
  opacity: 0.8;
}

footer {
  background-color: #3d3d91;
  color: #fff;
}
</style>
