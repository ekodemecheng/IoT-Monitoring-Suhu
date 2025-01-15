Program ini adalah contoh penggunaan sensor DHT11 untuk membaca suhu dan kelembapan, 
kemudian mengirimkan data tersebut ke Firebase Realtime Database menggunakan modul WiFi pada ESP32
Berikut adalah penjelasan dari setiap bagian program:

# 1. Library dan Konstanta:
#include "DHT.h"
#define DHTPIN 5
#define DHTTYPE DHT11

Deskripsi:
- Mengimpor library DHT untuk sensor DHT11.
- Mendefinisikan pin yang digunakan untuk sensor DHT11 (pin 5).
- Mendefinisikan tipe sensor DHT yang digunakan (DHT11).

# 2. Library Tambahan:
#include <Arduino.h>
#if defined(ESP32)
  #include <WiFi.h>
#elif defined(ESP8266)
  #include <ESP8266WiFi.h>
#endif
#include <Firebase_ESP_Client.h>

Deskripsi:
- Mengimpor library Arduino dan WiFi sesuai dengan jenis board (ESP32 atau ESP8266).
- Mengimpor library Firebase untuk ESP.

# 3. Inisialisasi Objek dan Konfigurasi:
DHT dht(DHTPIN, DHTTYPE);
FirebaseData fbdo;
FirebaseAuth auth;
FirebaseConfig config;
bool signupOK = false;

Deskripsi:
- Membuat objek "dht" untuk sensor DHT11.
- Membuat objek "fbdo" untuk data Firebase.
- Membuat objek "auth" dan "config" untuk autentikasi dan konfigurasi Firebase.
- Variabel signupOK untuk mengecek status pendaftaran Firebase

# 4. Konfigurasi WiFi dan Firebase:
void setup(){
  pinMode(DHTPIN, INPUT);
  dht.begin();
  Serial.begin(115200);
  WiFi.begin(WIFI_SSID, WIFI_PASSWORD);
  while (WiFi.status() != WL_CONNECTED){
    delay(300);
  }
  config.api_key = API_KEY;
  config.database_url = DATABASE_URL;
  if (Firebase.signUp(&config, &auth, "", "")){
    signupOK = true;
  }
  config.token_status_callback = tokenStatusCallback;
  Firebase.begin(&config, &auth);
  Firebase.reconnectWiFi(true);
}

Deskripsi:
- Mengatur pin sensor DHT11 sebagai input dan memulai sensor.
- Memulai komunikasi serial dengan baud rate 115200.
- Menghubungkan ke jaringan WiFi menggunakan SSID dan password yang diberikan.
- Mengatur API key dan URL database Firebase.
- Mendaftar ke Firebase dan memulai koneksi Firebase.
