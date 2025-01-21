<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import NextuViewHelloWorld from './views/NextuViewHelloWorld.vue'
import ProductsListView from './views/ProductsListView.vue'
import { ref, reactive } from "vue";
import type { InscriptionForm } from "@/models/inscription";

const emptyForm: InscriptionForm = {
  name: '',
  lastName: '',
  email: '',
  sex: true,
  adresse: '',
  postalCode: 0,
  city: '',
  instituteName: '',
};

const inscriptionForm: InscriptionForm = reactive({ ...emptyForm });

const onSubmit = ()=>{
  let sex = ""
  if (inscriptionForm.sex == true) {
    sex = 'un homme'
  } else {
    sex = 'une femme'
  }
  alert(`Votre nom est ${inscriptionForm.name}\nVotre prénom est ${inscriptionForm.lastName}\nVotre email est ${inscriptionForm.email}\nVous êtes ${sex}\nVotre adresse est ${inscriptionForm.adresse}\nVotre code postal est ${inscriptionForm.postalCode}\nVotre ville est ${inscriptionForm.city}\nVotre institut est ${inscriptionForm.instituteName}`)
}
const onReset = () => {
  Object.assign(inscriptionForm, { ...emptyForm });
};
</script>

<template>
    <form @submit.prevent="onSubmit">
      <div>
        <label for="fname">Nom</label>
        <input type="text" id="fname" name="firstname" v-model="inscriptionForm.name" required/>
        <label for="lname">Prenoms</label>
        <input type="text" id="lname" name="lastname" v-model="inscriptionForm.lastName" required/>
      </div>
      <label for="email">Email</label>
      <input type="text" id="email" name="email" v-model="inscriptionForm.email" required/>

        <p>Sexe</p>
        <div>
        <label>
          <input type="radio" value="true" v-model="inscriptionForm.sex" />
          Homme
        </label>
        <label>
          <input type="radio" value="false" v-model="inscriptionForm.sex" />
          Femme
        </label>
      </div>
        <label for="adresse">Adresse</label>
        <input type="text" id="adresse" name="adresse" v-model="inscriptionForm.adresse" required/>
        <div>
          <label for="postalCode">Code postal</label>
          <input type="number" id="postalCode" name="postalCode" v-model="inscriptionForm.postalCode" required/>
          <label for="city">Ville</label>
          <input type="text" id="city" name="city" v-model="inscriptionForm.city" required/>
        </div>
        <label for="instituteName">Nom de l'institut</label>
        <input type="text" id="instituteName" name="instituteName" v-model="inscriptionForm.instituteName" required/>
        <div>
        <button type="submit">Valider</button>
        <button type="submit" @click="onReset">Annuler</button>
      </div>
    </form>
</template>
<style scoped>
form{
  margin-left: auto;
  margin-right: auto;
}
label {
  margin-bottom: 5px;
}

input[type="text"],
input[type="email"],
input[type="radio"] {
  margin-bottom: 15px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-right: 10px;
}

input[type="radio"] {
  width: auto;
  margin-right: 10px;
}

div {
  margin-bottom: 20px;
}

button {
  background-color: #007BFF;
  color: white;
}
</style>
