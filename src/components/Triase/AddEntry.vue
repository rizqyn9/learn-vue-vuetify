<template>
  <v-card>
    <v-container>
      <h1>Add Data</h1>
      <v-form v-model="valid">
          <v-text-field
            v-model="firstname"
            :rules="nameRules"
            :counter="10"
            label="Nama Pasien"
            required
          >
          </v-text-field>
          <v-text-field
            v-model="lastname"
            :rules="nameRules"
            :counter="10"
            label="Alamat"
            required
          ></v-text-field>

          <v-text-field            
            v-model="email"
            :rules="emailRules"
            label="Jenis Kelamin"
            required
          >
          </v-text-field>

        </v-form>
    </v-container pa-5>
  </v-form>
      <!-- Tugas 3: Buat Tampilan untuk menambahkan data baru
      input berisi  
        1. Nama Pasien :
        - Alphabet
        - min. 10 karakter max. 50 karakter
        - Required
        - Jika text field tidak diisi maka memunculkan message : Perlu mengisi nama
        - Jika text field diisi melebihi 50 karakter maka memunculkan message : Jumlah karakter
        maksimal 50 karakter
        2. Alamat
        - Alpanumeric
        - min. 10 karakter max. 100 karakter
        - Required
        - Show message error required : Perlu mengisi alamat
        3. Jenis Kelamin
        - Laki-laki/Perempuan
        - Pilih salah satu
        - Required
        - Show message error required : Perlu mengisi jenis kelamin
        4. Nama Orang tua
        - Alphabet
        - min. 10 karakter max. 50 karakter
        - Show message error required : Jumlah karakter maksimal 50 karakter
        5. Nama Penanggung Jawab
        - Alphabet
        - min. 10 karakter max. 50 karakter
        - Show message error required : Jumlah karakter maksimal 50 karakter
        6. Kesadaran
        - Pilih salah satu dari Sadar penuh/ Respon Suara/ Respon Nyeri/ Tidak Nyeri
        7. Tekanan Darah
        - numeric
        - min. 2 digit max. 3 digit
        - Required
        - Show message error required : Perlu mengisi tekanan darah
        8. Nadi
        - numeric
        - 2 digit
        - Required
        - Show message error required : Perlu mengisi nadi
        9. RR
        - numeric
        - 2 digit
        - Required
        - Show message error required : Perlu mengisi respiration rate
        10. Suhu
        - numeric
        - 2 digit
        - Required
        - Show message error required : Perlu mengisi suhu
        11. Saturasi O2
        - numeric
        - 2 digit
        - Required
        - Show message error required : Perlu mengisi saturasi O2
        12. Nyeri
        - numeric
        - 1 digit
        - Required
        - Show message error required : Perlu mengisi angka nyeri
        13. Berat badan
        - numeric
        - min. 2 digit max. 3 digit
        14. Tinggi Badan
        - numeric
        - min. 2 digit max. 3 digit
       -->
    </v-container>
  </v-card>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Add Entry',
  data() {
    return {
      input: {
        name: '',
        address: '',
        gender: true,
        parentName: '',
        guarantorName: '',
        awareness: '',
        sistole: 0,
        pulse: 0,
        rr: 0,
        temperature: 0,
        saturation: 0,
        painLevel: 0,
        weight: 0,
        height: 0,
      },
      resource: {
        awarenessType: [
          { value: 'fully_aware', text: 'Sadar Penuh' },
          { value: 'sound_response', text: 'Respons Suara' },
          { value: 'pain_response', text: 'Rspons Nyeri' },
          { value: 'no_response', text: 'Tidak Nyeri' },
        ],
        resultType: [
          { value: 'resuscitation_room', text: 'Ruang Resusitasi' },
          { value: 'non_resuscitation_room', text: 'Ruang Non Resusitasi' },
          { value: 'general_clinic', text: 'Klinik Umum' },
          { value: 'death_on_arrival', text: 'Death On Arrival' },
        ],
      },
    };
  },
  methods: {
    addData() {
      axios.post('https://desolate-scrubland-57861.herokuapp.com/patients', {
        name: 'Amanda Manopo',
        sistole: 110,
        pulse: 80,
        rr: 30,
        temperature: 35,
        saturation: 98,
        painLevel: 0,
        weight: 50,
        height: 170,
        address: 'Solo',
        gender: true,
        parentName: '',
        guarantorName: '',
        awareness: 'fully_aware',
        result: 'resuscitation_room',
      });
      // Tugas 4 buat fungsi untuk menambahkan data ke backend
    },
  },
};
</script>

<style></style>
