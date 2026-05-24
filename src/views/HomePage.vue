<template>
  <ion-page>
    <ion-header :translucent="true" class="ion-no-border">
      <ion-toolbar color="background">
        <ion-title class="header-title">Cuaca Jakarta</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true" class="ion-padding">
      <ion-header collapse="condense" class="ion-no-border">
        <ion-toolbar color="transparent">
          <ion-title size="large" class="header-title-large">Cuaca Jakarta</ion-title>
        </ion-toolbar>
      </ion-header>

      <div class="weather-summary">
        <h2>Prakiraan Per Jam</h2>
        <p>Memantau waktu pengukuran dan temperatur secara real-time.</p>
      </div>

      <div v-if="loading" class="center-container">
        <ion-spinner name="crescent" color="primary"></ion-spinner>
        <p>Memuat data cuaca...</p>
      </div>

      <div v-else-if="error" class="center-container error-text">
        <p>{{ error }}</p>
      </div>

      <ion-list v-else lines="none" class="weather-list">
        <div class="table-header">
          <span>Waktu Pengukuran (Time)</span>
          <span>Suhu (Temperature_2m)</span>
        </div>
        
        <ion-item v-for="(item, index) in weatherList" :key="index" class="weather-item">
          <div class="time-section">
            <ion-icon :icon="timeOutline" class="item-icon time-icon"></ion-icon>
            <ion-label>
              <h3>{{ item.time }}</h3>
            </ion-label>
          </div>
          <div slot="end" class="temp-section">
            <ion-icon :icon="thermometerOutline" class="item-icon temp-icon"></ion-icon>
            <span class="temp-value">{{ item.temperature }}°C</span>
          </div>
        </ion-item>
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import { 
  IonContent, 
  IonHeader, 
  IonPage, 
  IonTitle, 
  IonToolbar,
  IonList,
  IonItem,
  IonLabel,
  IonSpinner,
  IonIcon
} from '@ionic/vue';
import { thermometerOutline, timeOutline } from 'ionicons/icons';
import axios from 'axios';

// Interface struktur data untuk memetakan respon API per baris/item
interface WeatherItem {
  time: string;
  temperature: number;
}

const weatherList = ref<WeatherItem[]>([]);
const loading = ref<boolean>(true);
const error = ref<string | null>(null);

const fetchWeather = async () => {
  try {
    loading.value = true;
    error.value = null;
    
    // Request ke API Open-Meteo sesuai instruksi
    const response = await axios.get('https://api.open-meteo.com/v1/forecast?latitude=-6.2&longitude=106.8&hourly=temperature_2m');
    
    // Destrukturisasi data array hourly dari API
    const { time, temperature_2m } = response.data.hourly;
    
    // Melakukan mapping data array terpisah menjadi array objek tunggal
    weatherList.value = time.map((t: string, index: number) => ({
      time: formatDateTime(t),
      temperature: temperature_2m[index]
    }));
  } catch (err) {
    error.value = 'Gagal memuat data cuaca. Pastikan koneksi internet aktif.';
    console.error(err);
  } finally {
    loading.value = false;
  }
};

// Fungsi pembantu untuk memformat teks ISO Date menjadi format lokal Indonesia yang rapi
const formatDateTime = (isoString: string): string => {
  const date = new Date(isoString);
  return date.toLocaleString('id-ID', {
    day: 'numeric',
    month: 'short',
    hour: '2-digit',
    minute: '2-digit'
  }).replace('.', ':'); // Menyesuaikan format waktu ke standar tanda titik dua (:)
};

// Memanggil fungsi fetchWeather saat komponen berhasil dimuat
onMounted(() => {
  fetchWeather();
});
</script>

<style scoped>
/* Tipografi Header Modern */
.header-title {
  font-weight: 700;
  letter-spacing: -0.5px;
}

.header-title-large {
  font-weight: 800;
  letter-spacing: -1px;
}

.weather-summary {
  margin: 16px 8px 20px 8px;
}

.weather-summary h2 {
  font-size: 22px;
  font-weight: 700;
  margin: 0 0 4px 0;
  color: var(--ion-color-dark);
}

.weather-summary p {
  font-size: 14px;
  color: var(--ion-color-medium);
  margin: 0;
}

/* Style State Loading & Error */
.center-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 50vh;
}

.center-container p {
  margin-top: 12px;
  color: var(--ion-color-medium);
  font-size: 14px;
}

.error-text p {
  color: var(--ion-color-danger);
  font-weight: 500;
}

/* Desain Komponen List/Tabel Minimalis */
.weather-list {
  background: transparent;
  padding: 0;
}

.table-header {
  display: flex;
  justify-content: space-between;
  padding: 0 16px 10px 16px;
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.8px;
  color: var(--ion-color-medium);
}

.weather-item {
  --background: var(--ion-color-light);
  --border-radius: 14px;
  margin-bottom: 10px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.02);
  --padding-start: 16px;
  --padding-end: 16px;
  --inner-padding-end: 0;
}

.time-section {
  display: flex;
  align-items: center;
}

.item-icon {
  font-size: 18px;
  margin-right: 12px;
}

.time-icon {
  color: var(--ion-color-primary);
}

.temp-icon {
  color: var(--ion-color-warning);
  margin-right: 4px;
}

.time-section h3 {
  font-size: 14px;
  font-weight: 500;
  color: var(--ion-color-dark);
  margin: 0;
}

.temp-section {
  display: flex;
  align-items: center;
}

.temp-value {
  font-size: 15px;
  font-weight: 600;
  color: var(--ion-color-dark);
}
</style>