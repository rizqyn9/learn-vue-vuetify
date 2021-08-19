<template>
  <v-container>
    <h1>Daftar Pasien Igd</h1>
    <!-- Tugas 1 : menampilkan tanggal dengan format hari, tanggal bulan tahun-->
    <span class="caption">{{ dateNow }}</span>
    <v-data-table :headers="table.headers" :items="table.data">
      <template v-slot:item.actions="{ item }">
        <v-dialog v-model="dialog2">
          <template v-slot:activator="{ on }">
            <v-icon small class="mr-2" v-on="on">
              mdi-pencil
            </v-icon>
          </template>
          <edit-entry />
        </v-dialog>
        <v-icon small @click="deleteItem(item)">
          mdi-delete
        </v-icon>
      </template>
    </v-data-table>
    <v-dialog v-model="dialog" max-width="800">
      <add-entry />
    </v-dialog>
    <v-btn fab bottom right @click="dialog = true">
      <v-icon>mdi-plus</v-icon>
    </v-btn>
  </v-container>
</template>

<script>
import moment from 'moment';
// eslint-disable-next-line no-unused-vars
import axios from 'axios';
import AddEntry from './Triase/AddEntry.vue';
import EditEntry from './Triase/EditEntry.vue';

export default {
  components: { AddEntry, EditEntry },
  name: 'TriaseIgd',
  data() {


    return {
      dialog: false,
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
      table: {
        data: [],
        headers: [
          {
            text: 'No',
            align: 'start',
            sortable: false,
            value: 'no',
          },
          {
            text: 'Nama',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          {
            text: 'Jenis kelamin',
            align: 'start',
            sortable: false,
            value: 'gender',
          },
          {
            text: 'Alamat',
            align: 'start',
            sortable: false,
            value: 'address',
          },
          {
            text: 'Kesimpulan',
            align: 'start',
            sortable: false,
            value: 'result',
          },
          {
            text: '',
            align: 'start',
            sortable: false,
            value: 'actions',
          },
        ],
      },
    };
  },
  computed: {
    dateNow() {
      return moment().locale('id').format("dddd [,] DD MMMM YYYY");
    },
  },
  mounted() {
    this.getData();
    // console.log("hi im mounted")
  },
  methods: {
    // Get all data 
    getData() {
      // Tugas 2: lengkapi fungsi agar dapat menampilkan data pasien yang didapat dari backend
      // dokumentasi vuetify : https://vuetifyjs.com/en/components/data-tables
      axios.get("https://desolate-scrubland-57861.herokuapp.com/patients")
        .then(el => {
          this.table.data = el.data.map((val,i) => {
            return {...val, no : i+1}
          })
          console.log(el.data)
        })
        .catch(el => console.log(el))
    },
    // eslint-disable-next-line no-unused-vars
    deleteItem(item) {
      // Tugas 7: buat fitur untuk menghapus entri
    },
  },
};
</script>

<style></style>
