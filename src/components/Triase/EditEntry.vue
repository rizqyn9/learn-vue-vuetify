<template>
  <v-card>
    <v-container>
      <v-row>
        <!-- Tugas 5 : buat tamplian untuk edit entry yang sudah ada -->
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
export default {
  name: 'EditEntry',
  props: {
    patients: {
      type: Object,
      default: () => null,
    },
  },
  data() {
    return {
      input: {
        id: '',
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
    editPatient() {
      // Tugas 5 : buat fungsi untuk merubah
    },
  },
};
</script>

<style></style>
