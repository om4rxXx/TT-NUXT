<template>
  <v-container>
    <v-file-input
      v-model="selectedFile"
      label="Seleccionar archivo"
      :rules="img"
      accept="image/png, image/jpeg, image/bmp"
    ></v-file-input>
    <v-btn @click="convertAndLogBase64">Convertir a Base64</v-btn>
  </v-container>
</template>


<script lang="ts">
import axios from "axios";

export default {
  data() {
    return {
      imageSrc: null,
      selectedFile: null,
    };
  },
  methods: {
    handleFileSelect(event: { target: { files: null[] } }) {
      this.selectedFile = event.target.files[0];
    },
    async convertToBase64(file: Blob | null) {
      return new Promise((resolve, reject) => {
        const reader = new FileReader();
        reader.onload = () => {
          const base64 = btoa(reader.result);
          resolve(base64);
        };
        reader.onerror = (error) => {
          reject(error);
        };
        reader.readAsBinaryString(file);
      });
    },
    async convertAndLogBase64() {
      const base64 = await this.convertToBase64(this.selectedFile);
      console.log(base64);

      axios
        .post("http://localhost:8080/xampp/axios/api/enviarfoto.php", {
          foto_veterinario: base64,
        })
        .then((response) => {
          // Manejar la respuesta exitosa
          console.log("Exitoso", response.data);

          //window.location.reload();
        })
        .catch((error) => {
          // Manejar el error
          console.error(error);
        });
    },

    /* async uploadImage() {
      try {
        const longBlob = await this.convertToLongBlob();
        const formData = new FormData();
        formData.append("file", longBlob);
        const response = await axios.post(
          "http://localhost:8080/xampp/axios/api/enviarfoto.php",
          formData,
          {
            headers: {
              "Content-Type": "multipart/form-data",
            },
          }
        );
        console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    },*/
  },
};
</script>




<style>
</style>