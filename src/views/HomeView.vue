
<template>
  <v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col cols="12" sm="6">
          <v-text-field v-model="firstName" label="Nombres" :rules="[v => !!v || 'El nombre es requerido']"></v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-text-field v-model="lastName" label="Apellidos" :rules="[v => !!v || 'El apellido es requerido']"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="6">
          <v-text-field v-model="idNumber" label="Número de Identificación" :rules="[v => !!v || 'El número de identificación es requerido']"></v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-text-field v-model="expedition" label="Expedido en" :rules="[v => !!v || 'El lugar de expedición es requerido']"></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="6">
          <v-text-field v-model="address" label="Dirección" :rules="[v => !!v || 'La dirección es requerida']"></v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-select v-model="city" label="Ciudad" :rules="[v => !!v || 'La ciudad es requerida']">
          <v-list-item v-for="item in cities" :key="item.value" :value="item.value" v-text="item.label"></v-list-item>
        </v-select>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="6">
          <v-text-field v-model="phone" label="Teléfono" :rules="[v => !!v || 'El número de teléfono es requerido']"></v-text-field>
        </v-col>
        <v-col cols="12" sm="6">
          <v-text-field v-model="email" label="Correo Electrónico" :rules="[v => !!v || 'El correo electrónico es requerido', v => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'El correo electrónico no es válido']"></v-text-field>
        </v-col>
      </v-row>
            <v-card>
        <v-card-title>Tipo de trámite</v-card-title>
        <v-container grid>
          <v-row>
            <v-col cols="12" sm="6">
              <v-checkbox v-model="complaint" label="Queja"></v-checkbox>
            </v-col>
            <v-col cols="12" sm="6">
              <v-checkbox v-model="appeal" label="Apelación"></v-checkbox>
            </v-col>
          </v-row>
        </v-container>
      </v-card>
      <v-card>
        <v-card-title>Seleccione el medio por el cuál desea recibir respuesta</v-card-title>
        <v-container grid>
          <v-row>
            <v-col cols="12" sm="6">
              <v-checkbox v-model="writtenResponse" label="Por escrito"></v-checkbox>
            </v-col>
            <v-col cols="12" sm="6">
              <v-checkbox v-model="emailResponse" label="E-mail"></v-checkbox>
            </v-col>
          </v-row>
        </v-container>
      </v-card>
      <v-row>
      <v-col cols="12">
        <v-card>
          <v-card-title>Detalle su solicitud</v-card-title>
          <v-card-text>
            <strong>Aviso:</strong> En el presente campo describa detalladamente su solicitud, respondiendo las siguientes preguntas: ¿Cuál es el objeto de su petición, queja/reclamo o apelación? ¿Cuáles son los hechos en que se fundamenta la queja o apelación? Puede adicionar las pruebas que considere pertinentes.
            <v-textarea v-model="requestDetail" outlined rows="5"></v-textarea>
          </v-card-text>
        </v-card>
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
import Swal from 'sweetalert2'
export default {
  data() {
    return {
      firstName: '',
      lastName: '',
      idNumber: '',
      expedition: '',
      address: '',
      phone: '',
      email: '',
      complaint: false,
      appeal: false,
      writtenResponse: false,
      emailResponse: false,
      requestDetail: '',
      cities: [
        { value: 'Pereira', label: 'Pereira' },
        { value: 'Bogotá', label: 'Bogotá' },
        { value: 'Medellín', label: 'Medellín' },
        { value: 'Cali', label: 'Cali' },
        { value: 'Barranquilla', label: 'Barranquilla' },
        { value: 'Cartagena', label: 'Cartagena' },
        { value: 'Cúcuta', label: 'Cúcuta' },
        { value: 'Santa Marta', label: 'Santa Marta' },
        { value: 'Manizales', label: 'Manizales' },
        { value: 'Bucaramanga', label: 'Bucaramanga' }
      ],
    };
  },
  methods: {
        submitForm() {
          Swal.fire({
      title: 'Radicación',
      text: 'La radicación del presente documento lo puede hacer a través de correo certificado a la dirección Avenida 30 de agosto No. 30-23 Pereira - Risaralda o en la ventanilla única de radicación en las instalaciones del CDA CERTI EXPRESS PEREIRA S.A.S; en la dirección referenciada anteriormente.',
      icon: 'warning',
      showCancelButton: true,
      confirmButtonColor: '#3085d6',
      cancelButtonColor: '#d33',
      cancelButtonText: 'Cancelar',
      confirmButtonText: 'Acepto',
      customClass: {
        confirmButton: 'btn-custom-class',
        cancelButton: 'btn-custom-class2'
      }
    }).then((result) => {
      if (result.isConfirmed) {
        Swal.fire(
          'Recibido',
          'Tu solicitud ha sido procesada',
          'success'
        )
      }
    })
      // Lógica con backend
      console.log('Datos del formulario:', this.firstName, this.lastName, this.idNumber, this.expedition, this.address, this.phone, this.email);
      console.log('Tipo de trámite:', this.complaint ? 'Queja' : '', this.appeal ? 'Apelación' : '');
      console.log('Medio de respuesta:', this.writtenResponse ? 'Por escrito' : '', this.emailResponse ? 'E-mail' : '');
    },
  },
};
</script>

<style>

.btn-custom-class {
  font-size: 58px;
  padding: 10px 64px;
}

.btn-custom-class2 {
  font-size: 58px;
  padding: 10px 64px;
}

</style>

