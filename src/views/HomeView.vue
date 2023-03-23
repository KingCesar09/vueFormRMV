<template>
  <v-form>
    <v-container>
      <v-row>
        <v-col cols="12" sm="6">
          <v-text-field v-model="firstName" label="Nombres"></v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-text-field v-model="lastName" label="Apellidos"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="6">
          <v-text-field v-model="idNumber" label="Número de Identificación"></v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-text-field v-model="expedition" label="Expedido en"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="6">
          <v-text-field v-model="address" label="Dirección"></v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-text-field v-model="city" label="Ciudad"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="6">
          <v-text-field v-model="phone" label="Teléfono"></v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-text-field v-model="email" label="Correo Electrónico"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12">
          <v-btn @click="submitForm">Enviar</v-btn>
        </v-col>
      </v-row>
    </v-container>
  </v-form>
</template>

<script>
export default {
  data() {
    return {
      firstName: '',
      lastName: '',
      idNumber: '',
      expedition: '',
      address: '',
      city: '',
      phone: '',
      email: '',
    }
  },
  methods: {
    submitForm() {
      // Logica con baaack-end
      console.log('Datos del formulario:', this.firstName, this.lastName, this.idNumber, this.expedition, this.address, this.city, this.phone, this.email)
    },
  },
}
</script>
