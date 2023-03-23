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
          <v-checkbox v-model="complaint" label="Queja"></v-checkbox>
          <v-checkbox v-model="appeal" label="Apelación"></v-checkbox>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12">
          <v-checkbox v-model="writtenResponse" label="Por escrito"></v-checkbox>
          <v-checkbox v-model="emailResponse" label="E-mail"></v-checkbox>
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
      complaint: false,
      appeal: false,
      writtenResponse: false,
      emailResponse: false,
    }
  },
  methods: {
    submitForm() {
      // Lógica con backend
      console.log('Datos del formulario:', this.firstName, this.lastName, this.idNumber, this.expedition, this.address, this.city, this.phone, this.email)
      console.log('Tipo de trámite:', this.complaint ? 'Queja' : '', this.appeal ? 'Apelación' : '')
      console.log('Medio de respuesta:', this.writtenResponse ? 'Por escrito' : '', this.emailResponse ? 'E-mail' : '')
    },
  },
}
</script>

