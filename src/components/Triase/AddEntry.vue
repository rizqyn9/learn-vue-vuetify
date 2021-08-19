<template>
  <v-card>
    <v-container class="pa-8">
      <h1>Add Data</h1>
      <v-form >
        <v-text-field
          v-model="form.name"
          :rules="rules.namaPasien"
          label="Nama Pasien"
          required
        ></v-text-field>
        <v-text-field
          type="text"
          v-model="form.address"
          :rules="rules.address"
          label="Alamat"
          required
        ></v-text-field>
        <v-select
          v-model="form.gender"
          :items="genders"
          :rules="rules.gender"
          item-text="name"
          item-value="id"
          label="Jenis Kelamin"
          required
        ></v-select>
        <v-text-field
          type="text"
          v-model="form.parentName"
          :rules="rules.parentName"
          label="Nama Orang tua"
          required
        ></v-text-field>
        <v-text-field
          type="text"
          v-model="form.guarantorName"
          :rules="rules.guarantorName"
          label="Nama Penanggung Jawab"
          required
        ></v-text-field>
        <v-select
          v-model="form.awareness"
          :items="resource.awarenessType"
          :rules="rules.awareness"
          item-text="text"
          item-value="value"
          label="Kesadaran"
          required
        ></v-select>
        <v-text-field
          type="number"
          v-model="form.sistole"
          :rules="rules.sistole"
          label="Tekanan Darah"
          required
        ></v-text-field>
        <v-text-field
          type="number"
          v-model="form.pulse"
          :rules="rules.pulse"
          label="Nadi"
          required
        ></v-text-field>
        <v-text-field
          type="number"
          v-model="form.rr"
          :rules="rules.rr"
          label="RR"
          required
        ></v-text-field>
        <v-text-field
          type="number"
          v-model="form.temperature"
          :rules="rules.temperature"
          label="Suhu"
          required
        ></v-text-field>
        <v-text-field
          type="number"
          v-model="form.saturation"
          :rules="rules.saturation"
          label="Saturasi O2"
          required
        ></v-text-field>
        <v-text-field
          type="number"
          v-model="form.saturation"
          :rules="rules.saturation"
          label="Nyeri"
          required
        ></v-text-field>
        <v-text-field
          type="number"
          v-model="form.weight"
          :rules="rules.weight"
          label="Berat badan"
        ></v-text-field>
        <v-text-field
          type="number"
          v-model="form.height"
          :rules="rules.height"
          label="Tinggi Badan"
        ></v-text-field>
      </v-form>
    </v-container>
  </v-card>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Add Entry',
  data() {
    const defaultInput = Object.freeze({
        name: '',
        address: '',
        gender: 0,
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
    })
    return {
      form : Object.assign({}, defaultInput),
      rules : {
        namaPasien : [
          (val) => this.rulesAlphabet(val),
          (val) => this.checkLength(val, 10,50)
        ],
        address : [
          val => this.rulesAlphanumeric(val),
          val => this.checkLength(val, 10,100)
        ],
        gender : [
          val => { val != 0 || "Perlu mengisi jenis kelamin"}
        ],
        parentName : [
          val => this.rulesAlphabet(val),
          val => this.checkLength(val, 10,50)
        ],
        guarantorName:[
          val => this.rulesAlphabet(val),
          val => this.checkLength(val, 10,50)
        ],
        awareness : [

        ],
        sistole : [
          val => val != 0 || "Perlu mengisi tekanan darah",
          val => (val > 9 && val < 100) || "Cek lagi datanya"
        ],
        pulse : [
          val => val != 0 || "Perlu mengisi nadi",
          val => (val > 9) || "Cek lagi datanya"
        ],
        rr : [
          val => val != 0 || "Perlu mengisi respiration rate",
          val => (val > 9) || "Cek lagi datanya"
        ],
        temperature:[
          val => val != 0 || "Perlu mengisi suhu",
          val => (val > 9) || "Cek lagi datanya"
        ],
        saturation :[
          val => val != 0 || "Perlu mengisi saturasi O2",
          val => (val > 9) || "Cek lagi datanya"
        ],
        painLevel : [
          val => val != 0 || "Perlu mengisi angka nyeri",
          val => (val > 9) || "Cek lagi datanya"
        ],
        weight : [
          val => (val > 9 && val < 100) || "Cek lagi datanya"
        ],
        height: [
          val => (val > 9 && val < 100) || "Cek lagi datanya"
        ]
      },
      genders : [
        {name : "Pilih salah satu", id: 0},
        {name : "Laki-laki" , id: true},
        {name : "Perempuan" , id: false}
        ],
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
    rulesAlphabet(val) {
      return /^[a-zA-Z ]*$/.test(val) || "Text mus alphabet"
    },
    rulesAlphanumeric(val) {
      return /^[a-zA-Z0-9]+$/.test(val) || "Text mus alphanumeric"
    },
    checkLength(val, min, max) {
      return (val || '').length < min ? "Text wajib diisi" : (val || '').length < max || "text kebanyakan" 
    },
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
