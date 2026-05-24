<template>
  <div class="bg-[#1c1c1c] text-yellow-300 font-sans">

    <!-- NAV -->
    <nav class="fixed top-0 w-full z-50 bg-[#1a1208]/80 backdrop-blur-md border-b border-white/5">
      <div class="max-w-6xl mx-auto px-6 py-5 flex justify-between items-center">
        <span style="font-family: 'Playfair Display', serif" class="text-lg tracking-wide text-amber-100">Pčelarstvo
          Vojinović</span>
        <div class="hidden md:flex gap-10 text-sm font-light tracking-widest uppercase text-stone-400">
          <a @click="scrollTo('pocetna')" class="cursor-pointer hover:text-amber-300 transition">Početna</a>
          <a @click="scrollTo('proizvodi')" class="cursor-pointer hover:text-amber-300 transition">Proizvodi</a>
          <a @click="scrollTo('onama')" class="cursor-pointer hover:text-amber-300 transition">O nama</a>
          <a @click="scrollTo('kontakt')" class="cursor-pointer hover:text-amber-300 transition">Kontakt</a>
        </div>
        <button @click="meni = !meni" class="md:hidden text-stone-400 hover:text-amber-300 transition">
          <svg v-if="!meni" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
            stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
          <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
            stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>
      <div v-if="meni"
        class="md:hidden bg-[#1a1208] border-t border-white/5 px-6 py-6 flex flex-col gap-6 text-stone-400 text-sm tracking-widest uppercase">
        <a @click="scrollTo('pocetna'); meni = false" class="cursor-pointer hover:text-amber-300 transition">Početna</a>
        <a @click="scrollTo('proizvodi'); meni = false"
          class="cursor-pointer hover:text-amber-300 transition">Proizvodi</a>
        <a @click="scrollTo('onama'); meni = false" class="cursor-pointer hover:text-amber-300 transition">O nama</a>
        <a @click="scrollTo('kontakt'); meni = false" class="cursor-pointer hover:text-amber-300 transition">Kontakt</a>
      </div>
    </nav>

    <!-- HERO -->
    <section id="pocetna" class="relative min-h-screen flex items-center justify-center text-white px-6 overflow-hidden">
      <video autoplay muted loop playsinline class="absolute inset-0 w-full h-full object-cover">
        <source src="/video/video.mp4" type="video/mp4" />
      </video>
      <div class="absolute inset-0 bg-gradient-to-b from-black/70 via-black/50 to-[#1c1c1c]"></div>
      <div class="relative text-center max-w-3xl">
        <p class="text-amber-400 uppercase tracking-[0.3em] text-xs mb-6">Porodično pčelarstvo.</p>
        <h1 style="font-family: 'Playfair Display', serif" class="text-5xl md:text-7xl leading-tight mb-6">Pravi
          med<br />Pravi ukus</h1>
        <p class="text-base md:text-lg text-stone-300 mb-10 leading-relaxed max-w-xl mx-auto font-light">Čist
          med i pčelinji proizvodi direktno iz naših košnica. Sa Pešterske visoravni i obronaka planine Rudnik</p>
        <a @click="scrollTo('proizvodi')"
          class="cursor-pointer inline-block border border-amber-400 text-amber-300 px-8 py-4 rounded-full hover:bg-amber-400 hover:text-stone-900 transition font-light tracking-widest text-sm uppercase">Pogledaj
          proizvode</a>
      </div>
    </section>

    <!-- PROIZVODI -->
    <section id="proizvodi" class="py-24 px-6 bg-[#1c1c1c]">
      <div class="max-w-6xl mx-auto">
        <p class="text-amber-500 uppercase tracking-[0.3em] text-xs text-center mb-4">Šta nudimo</p>
        <h2 style="font-family: 'Playfair Display', serif" class="text-3xl md:text-4xl text-center text-amber-100 mb-16">
          Naši proizvodi</h2>

        <div class="space-y-20 md:space-y-32">
          <div v-for="(p, i) in proizvodi" :key="p.naziv" class="flex flex-col md:flex-row items-center gap-8 md:gap-16"
            :class="i % 2 === 1 ? 'md:flex-row-reverse' : ''">
            <div class="w-full md:flex-1 rounded-2xl overflow-hidden shadow-2xl h-64 md:h-80">
              <img :src="p.slika" :alt="p.naziv"
                class="w-full h-full object-cover hover:scale-105 transition duration-700" />
            </div>
            <div class="w-full md:flex-1">
              <p class="text-amber-500 text-xs uppercase tracking-[0.3em] mb-3">{{ p.kategorija }}</p>
              <h3 style="font-family: 'Playfair Display', serif" class="text-2xl md:text-3xl text-amber-100 mb-4">{{
                p.naziv }}</h3>
              <p class="text-stone-400 text-base md:text-lg leading-relaxed mb-6 font-light">{{ p.opis }}</p>
              <span class="text-lg md:text-xl font-light text-amber-300 border-b border-amber-700 pb-1">{{ p.cena
              }}</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- O NAMA -->
    <section id="onama" class="py-24 px-6 bg-[#120d05]">
      <div class="max-w-6xl mx-auto">
        <p class="text-amber-500 uppercase tracking-[0.3em] text-xs text-center mb-4">Ko smo mi</p>
        <h2 style="font-family: 'Playfair Display', serif" class="text-3xl md:text-4xl text-center text-amber-100 mb-16">O
          nama</h2>
        <div class="flex flex-col md:grid md:grid-cols-2 gap-12 md:gap-20 items-center">
          <div class="w-full rounded-2xl overflow-hidden shadow-2xl h-72 md:h-96">
            <img src="https://images.unsplash.com/photo-1558642452-9d2a7deb7f62?w=900&q=80" alt="Pčelar"
              class="w-full h-full object-cover" />
          </div>
          <div>
            <p class="text-stone-400 text-base md:text-lg leading-relaxed mb-6 font-light">Porodično pčelarstvo Vojinović
              bavi se uzgojem pčela i proizvodnjom meda već više od 20 godina. Naše košnice su smeštene u stacionarnom
              pčelinjaku u Kraljevu. Tokom sezone naše pčele sakupljaju nektar na Pešterskoj visoravni, obroncima planine
              Rudnik, stalni smo gosti na paši u okolini Ljiga odakle nam dolazi lipov med.</p>
            <p class="text-stone-400 text-base md:text-lg leading-relaxed mb-10 font-light">Članovi smo dobre pčelarske
              prakse
              što znači da iza kvaliteta našeg meda stoji <a href="https://spos.info/" target="_blank">SPOS (Savez
                pčelarskih organizacija Srbije)</a>, testiranja naših proizvoda su veoma česta i rigorozna.
              Što potvrđuje i tegla u koju skladištimo naš med, obzirom da nemaju svi pčelari pravo na SPOS-ovu ambalažu.
            </p>
            <div class="grid grid-cols-3 gap-3 md:gap-4 text-center">
              <div class="border border-amber-900 rounded-2xl p-4 md:p-6">
                <div style="font-family: 'Playfair Display', serif" class="text-2xl md:text-3xl text-amber-400 mb-2">20+
                </div>
                <p class="text-stone-500 text-xs tracking-widest uppercase">godina</p>
              </div>
              <div class="border border-amber-900 rounded-2xl p-4 md:p-6">
                <div style="font-family: 'Playfair Display', serif" class="text-2xl md:text-3xl text-amber-400 mb-2">80+
                </div>
                <p class="text-stone-500 text-xs tracking-widest uppercase">košnica</p>
              </div>
              <div class="border border-amber-900 rounded-2xl p-4 md:p-6">
                <div style="font-family: 'Playfair Display', serif" class="text-2xl md:text-3xl text-amber-400 mb-2">200+
                </div>
                <p class="text-stone-500 text-xs tracking-widest uppercase">kupaca</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- INSTAGRAM -->
    <section class="py-20 px-6 bg-[#120d05] text-center">
      <div class="max-w-xl mx-auto">
        <p class="text-amber-500 uppercase tracking-[0.3em] text-xs mb-4">Pratite nas</p>
        <h2 style="font-family: 'Playfair Display', serif" class="text-3xl text-amber-100 mb-4">Naš svakodnevni rad</h2>
        <p class="text-stone-400 font-light leading-relaxed mb-8">Košnice, priroda, med, sajmovi — pratite nas na Instagramu i
          budite deo naše priče.</p>
        <a href="https://instagram.com/gazdinstvo_vojinovic" target="_blank"
          class="inline-flex items-center gap-3 border border-amber-700/50 text-amber-300 px-8 py-4 rounded-full hover:bg-amber-500/10 transition group">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"
            stroke-width="1.5">
            <rect x="2" y="2" width="20" height="20" rx="5" ry="5" />
            <circle cx="12" cy="12" r="4" />
            <circle cx="17.5" cy="6.5" r="0.5" fill="currentColor" />
          </svg>
          <span class="text-sm uppercase tracking-widest font-light">Poseti Instagram profil</span>
          <span class="group-hover:translate-x-1 transition">→</span>
        </a>
      </div>
    </section>
    <!-- KONTAKT -->
    <section id="kontakt" class="py-24 px-6 bg-[#1a1208]">
      <div class="max-w-2xl mx-auto">
        <p class="text-amber-500 uppercase tracking-[0.3em] text-xs text-center mb-4">Kontakt</p>
        <h2 style="font-family: 'Playfair Display', serif" class="text-3xl md:text-4xl text-center text-amber-100 mb-4">
          Pišite nam</h2>
        <p class="text-center text-stone-500 mb-12 font-light">Za cene, dostupnost ili bilo kakvo pitanje — tu smo.</p>

        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 text-center mb-12">
          <div class="p-4 border border-white/5 rounded-2xl">
            <p class="font-light text-amber-300 mb-1 text-xs tracking-widest uppercase">Telefon</p>
            <p class="text-stone-400 text-sm">+381 66 241 229</p>
          </div>
          <div class="p-4 border border-white/5 rounded-2xl">
            <p class="font-light text-amber-300 mb-1 text-xs tracking-widest uppercase">Lokacija</p>
            <p class="text-stone-400 text-sm">Kraljevo</p>
          </div>
        </div>

        <form action="https://formspree.io/f/mvzyqokb" method="POST" class="space-y-4">
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <input name="ime" type="text" placeholder="Ime i prezime" required
              class="w-full bg-transparent border border-white/10 rounded-xl px-5 py-4 focus:outline-none focus:border-amber-500 text-stone-200 placeholder-stone-600 font-light" />
            <input name="email" type="email" placeholder="Email adresa" required
              class="w-full bg-transparent border border-white/10 rounded-xl px-5 py-4 focus:outline-none focus:border-amber-500 text-stone-200 placeholder-stone-600 font-light" />
          </div>
          <textarea name="poruka" rows="6" placeholder="Vaša poruka..." required
            class="w-full bg-transparent border border-white/10 rounded-xl px-5 py-4 focus:outline-none focus:border-amber-500 text-stone-200 placeholder-stone-600 font-light"></textarea>
          <button type="submit"
            class="w-full border border-amber-500 text-amber-300 py-4 rounded-xl font-light tracking-widest uppercase text-sm hover:bg-amber-500 hover:text-stone-900 transition">
            Pošalji poruku
          </button>
        </form>
      </div>
    </section>

    <!-- FOOTER -->
    <footer
      class="bg-[#120d05] border-t border-white/5 text-stone-600 text-center py-8 text-sm font-light tracking-widest">
      © 2026 Pčelarstvo Vojinović · Kraljevo
    </footer>
    <!-- PCELICA POPUP -->
    <transition name="bee">
      <div v-if="pcelica" class="fixed bottom-6 right-6 z-50 max-w-sm">
        <div class="bg-[#120d05] border border-amber-700/40 rounded-3xl p-6 shadow-[0_0_40px_rgba(180,100,0,0.15)]">
          <button @click="pcelica = false"
            class="absolute top-4 right-5 text-stone-600 hover:text-amber-300 text-base transition">✕</button>

          <!-- Pcelica i kantica -->
          <div class="flex items-end gap-3 mb-4">
            <span class="text-6xl leading-none" style="filter: drop-shadow(0 0 12px rgba(251,191,36,0.4))">🐝</span>
            <span class="text-4xl leading-none animate-bounce">🍯</span>
          </div>

          <p style="font-family: 'Playfair Display', serif" class="text-amber-100 text-xl mb-2">Svež med je stigao!</p>
          <p class="text-stone-400 text-sm font-light leading-relaxed mb-4">Upravo smo iscedili Bagremov med iz netaknute
            prirode u okolini Kraljeva. Poručite odmah Vaš kilogram svežeg meda.
          </p>

          <a @click="scrollTo('kontakt'); pcelica = false"
            class="cursor-pointer flex items-center justify-between w-full bg-amber-500/10 hover:bg-amber-500/20 border border-amber-700/50 rounded-xl px-4 py-3 transition group">
            <span class="text-amber-300 text-xs uppercase tracking-widest font-light">Kontaktirajte nas</span>
            <span class="text-amber-400 group-hover:translate-x-1 transition">→</span>
          </a>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const meni = ref(false)
const pcelica = ref(false)

setTimeout(() => {
  pcelica.value = true
}, 5000)
const forma = reactive({ ime: '', email: '', poruka: '' })

function scrollTo(id) {
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

const proizvodi = [
  {
    naziv: 'Bagremov med',
    kategorija: 'Med',
    opis: 'Svetao, blag i aromatičan. Kristališe sporo i ostaje tečan dugo. Idealan za čaj, kolače ili direktno sa kašičice. Poreklo meda planina Rudnik',
    cena: '1200 din / kg',
    slika: '../slike/bagrem.png'
  },
  {
    naziv: 'Cvetni med',
    kategorija: 'Med',
    opis: 'Zlatnožut, bogat mineralima. Brzo kristališe u kremast med koji se lako maže. Omiljeni kod dece. Poreklo meda Kraljevački voćnjaci',
    cena: '1200 din / kg',
    slika: '../slike/cvet.jpg'
  },
  {
    naziv: 'Livadski med',
    kategorija: 'Med',
    opis: 'Taman, intenzivnog ukusa, pun antioksidanasa. Pravi izbor za one koji vole jak, prirodan ukus. Poreklo meda Pešterska visoravan',
    cena: '1200 din / kg',
    slika: '../slike/livada1.png'
  },
  {
    naziv: 'Propolis',
    kategorija: 'Pčelinji proizvod',
    opis: 'Prirodni antibiotik koji pčele koriste za zaštitu košnice. 25% rastvor, čist i prirodni propolis.',
    cena: '300 din / 25mℓ',
    slika: '../slike/propolis.png'
  },
  {
    naziv: 'Rakija Medovača',
    kategorija: 'Pčelinji proizvod',
    opis: '',
    cena: '1000 din / 1ℓ',
    slika: 'https://images.unsplash.com/photo-1558642452-9d2a7deb7f62?w=800&q=80'
  },
  {
    naziv: 'Rojevi',
    kategorija: 'Rojevi',
    opis: 'Prodaja jakih rojeva na DB ramu',
    cena: '50 €',
    slika: '../slike/roj1.jpg'
  },
]
</script>
<style>
.bee-enter-active {
  transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.bee-leave-active {
  transition: all 0.3s ease;
}

.bee-enter-from {
  opacity: 0;
  transform: translateY(20px) scale(0.9);
}

.bee-leave-to {
  opacity: 0;
  transform: translateY(10px);
}</style>