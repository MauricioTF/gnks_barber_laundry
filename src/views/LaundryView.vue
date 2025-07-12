
<template>
  <section class="relative">

    <section class="relative w-full h-screen">
    <div
      class="absolute inset-0 bg-cover bg-center bg-no-repeat bg-fixed"
      style="background-image: url('/laundry/fondo1.jpg')"
    ></div>
    <div class="absolute inset-0 bg-black/70"></div>

    <div class="relative z-10 flex flex-col items-center justify-center h-full text-center px-4 text-white">
      <h1 class="text-4xl md:text-6xl font-extrabold leading-tight uppercase">
        Servicio de lavandería <br />
        y dry cleaning estilo americano
      </h1>
      <p class="text-base md:text-xl mt-4 font-medium tracking-wide max-w-2xl">
        Ropa limpia, fresca y con fragancia, sin complicaciones.
      </p>
      <div class="mt-8">
        <button
          @click="showCalendlyModal = true"
          class="bg-orange-500 hover:bg-orange-600 text-white font-bold py-3 px-6 rounded-lg shadow-lg text-lg transition duration-300"
        >
          Solicitar servicio
        </button>
      </div>
    </div>
  </section>
  

<!-- Sección 1: Imagen izquierda, texto derecha -->
<section class="max-w-7xl mx-auto px-4 py-16">
  <div class="flex flex-col md:flex-row items-center gap-10">
    <!-- Imagen izquierda -->
    <div class="w-full md:w-1/2">
      <img
        src="/laundry/fondo2.jpg"
        alt="Barbería"
        class="w-full h-auto rounded-lg shadow-lg object-cover"
      />
    </div>

    <!-- Texto derecha -->
    <div class="w-full md:w-1/2 text-left">
      <h2 class="text-3xl font-bold mb-4 text-blue-800">Calidad, limpieza y confianza</h2>
      <p class="text-lg leading-relaxed mb-4">
        En nuestra lavandería, combinamos tecnología y cuidado personalizado para ofrecer un servicio de lavado y dry cleaning de alta calidad.
      </p>
      <p class="text-lg leading-relaxed">
        Estamos comprometidos con el buen estado de tus prendas. Descubrí por qué tantas familias y profesionales confían en nosotros semana a semana.
      </p>
    </div>
  </div>
</section>

<!-- Sección 2: Texto izquierda, imagen derecha -->
<section class="max-w-7xl mx-auto px-4 py-16">
  <div class="flex flex-col md:flex-row-reverse items-center gap-10">
    <!-- Imagen derecha -->
    <div class="w-full md:w-1/2">
      <img
        src="/laundry/fondo3.jpg"
        alt="Ambiente del local"
        class="w-full h-auto rounded-lg shadow-lg object-cover"
      />
    </div>

    <!-- Texto izquierda -->
    <div class="w-full md:w-1/2 text-left">
      <h2 class="text-3xl font-bold mb-4 text-blue-800">Un espacio creado para tu comodidad</h2>
      <p class="text-lg leading-relaxed mb-4">
        Nuestra lavandería está diseñada para que tu experiencia sea rápida, cómoda y sin estrés. Instalaciones limpias, ambiente ventilado y atención amable.
      </p>
      <p class="text-lg leading-relaxed">
        Hacé tu pedido en línea y descubrí lo fácil que es mantener tu ropa impecable sin salir de casa.
      </p>
    </div>
  </div>
</section>

    <!-- Galería -->
    <div class="max-w-6xl mx-auto">
      <h3 class="text-2xl font-semibold text-center text-black mb-6">Nuestro trabajo</h3>
        <div class="grid grid-cols-3 sm:grid-cols-2 md:grid-cols-3 gap-6">

        <div
          v-for="(img, i) in imagenes"
          :key="i"
          class="rounded-xl overflow-hidden shadow-md hover:scale-105 transition-transform duration-300"
        >
          <img
            :src="img"
            :alt="`Trabajo de lavanderia ${i + 1}`"
            class="w-full h-80 object-cover"
            loading="lazy"
          />
        </div>
      </div>
    </div>

    <!-- Mapa -->
    <div class="max-w-5xl mx-auto">
      <h3 class="text-2xl font-semibold text-center text-black mb-6">¿Dónde estamos?</h3>
      <div class="rounded-xl overflow-hidden shadow-lg aspect-video">
        <iframe
          class="w-full h-full"
  src= "https://www.google.com/maps/embed?pb=!1m17!1m12!1m3!1d3933.5542368818897!2d-85.157226!3d9.633595!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m2!1m1!2zOcKwMzgnMDAuOSJOIDg1wrAwOScyNi4wIlc!5e0!3m2!1ses!2scr!4v1752354362220!5m2!1ses!2scr"
  allowfullscreen
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
        ></iframe>
      </div>
    </div>

      <!-- Botón para abrir Calendly -->
  <div class="text-center py-16 text-white">
    <h3 class="text-3xl font-bold mb-4 text-emerald-400">Reservá tu cita en línea</h3>
    <p class="mb-6 text-gray-400">Elegí el horario que más te convenga</p>
    <button
      @click="showCalendlyModal = true"
      class="bg-emerald-500 hover:bg-emerald-600 text-white font-semibold py-3 px-6 rounded-lg shadow transition"
    >
      Reservar cita
    </button>
  </div>

  <!-- Modal Calendly -->
  <transition name="fade">
    <div
      v-if="showCalendlyModal"
      class="fixed inset-0 bg-black/70 backdrop-blur-sm flex items-center justify-center z-50 px-4"
    >
      <div class="bg-white rounded-xl w-full max-w-4xl h-[80vh] shadow-2xl relative">
        <!-- Botón cerrar -->
        <button
          @click="showCalendlyModal = false"
          class="absolute top-3 right-4 text-black text-xl hover:text-red-500"
        >
          ✖
        </button>

        <!-- Calendly iframe -->
        <iframe
          src="https://calendly.com/lavanderiaguason/cita"
          width="100%"
          height="100%"
          frameborder="0"
          class="rounded-b-xl"
        ></iframe>
      </div>
    </div>
  </transition>


    <!-- Botón flotante de WhatsApp -->
    <a
      href="https://wa.me/50664626700"
      target="_blank"
      class="fixed bottom-6 right-6 bg-green-500 hover:bg-green-600 text-white text-lg font-semibold py-3 px-5 rounded-full shadow-lg z-50 transition duration-300"
    >
      💬 WhatsApp
    </a>
  </section>
  
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue'

const showCalendlyModal = ref(false)

const imagenes = [
  '/laundry/laund1.png',
  '/laundry/laund2.jpg',
  '/laundry/laund3.jpg',
  '/laundry/laund4.jpg',
  '/laundry/laund5.jpg',
  '/laundry/laund6.jpg',
  '/laundry/laund7.jpg',
  '/laundry/laund8.jpg',
  '/laundry/laund9.png',
]

</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: scale(0.98);
}
</style>