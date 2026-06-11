<script setup>
import { ref} from 'vue'

let name = ref('')
let email = ref('')
let phone = ref('')
let coneFlavor = ref('')
let iceFlavors = ref('')
let quantity = ref('')
let notes = ref('')

const postOrder = () => {
    const order = {
        name: name.value,
        email: email.value,
        phone: phone.value,
        coneFlavor: coneFlavor.value,
        iceFlavors: iceFlavors.value,
        quantity: quantity.value,
        notes: notes.value

    }

    console.log(order)
     const api_url = 'http://localhost:3000/api/v1/icecream'
         fetch(api_url, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'

      },
              body: JSON.stringify(order)

})
.then(response => response.json())
    .then(data => {
        console.log('Success:', data);
         name.value = "";
         email.value = "";
         phone.value = "";
         coneFlavor.value = "";
         iceFlavors.value = "";
         quantity.value = "";
         notes.value = "";



        
    })
    .catch((error) => {
        console.error('Error:', error)
    });

}

const emit = defineEmits(['flavorChanged'])

// verander v-model op de select naar @change:
const onFlavorChange = (e) => {
    iceFlavors.value = e.target.value
    emit('flavorChanged', e.target.value)
}


</script>

<template>
  <div class="order-form">
    <h1>Ben & Jerry's Order Formulier</h1>
    
    <div class="form">
      <h2>Contact gegevens</h2>

      <div class="infoLable">
        <label class="placeholder" for="name">Naam</label>
        <input class="inputs inputPadding" type="text" id="name" name="name" v-model="name">
      </div>

      <div class="infoLable">
        <label class="placeholder" for="email">E-mail</label>
        <input class="inputs inputPadding" type="text" id="email" v-model="email">
      </div>

      <div class="infoLable">
        <label class="placeholder" for="phone">Gsm nummer</label>
        <input class="inputs inputPadding" type="text" id="phone" name="phone" v-model="phone">
      </div>
    </div>

    <div class="form">
      <h2>Ben & Jerry's Bestelling</h2>
      
      <div class="infoLable">
        <label class="placeholder" for="coneFlavor">Hoorntje Smaak</label>
        <select class="inputs inputPadding" id="coneFlavor" v-model="coneFlavor">
          <option disabled value="">Kies een smaak</option>
          <option value="Chocolade">Chocolade</option>
          <option value="Vanilla">Vanilla</option>
        </select>
      </div>

      <div class="infoLable">
        <label class="placeholder" for="iceFlavors">Ijs Smaak</label>
        <select class="inputs inputPadding" id="iceFlavors" @change="onFlavorChange">
          <option disabled value="">Kies een smaak</option>
          <option value="Chocolade">Chocolade</option>
          <option value="Vanilla">Vanilla</option>
          <option value="Aardbei">Aardbei</option>
          <option value="Moka">Moka</option>
        </select>
      </div>

      <div class="infoLable">
        <label class="placeholder" for="quantity">Hoeveelheid</label>
        <input class="inputs inputPadding" type="text" id="quantity" v-model="quantity">
      </div>

   

      <div class="infoLable">
        <label class="placeholder" for="notes">Notitie</label>
        <textarea class="inputs textereaPadding" id="notes" v-model="notes"></textarea>
      </div>


    </div>

    <button class="btn" @click.prevent="postOrder">Bestelling verzenden</button>
  </div>
</template>


<style scoped>

.order-form{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 35%;
    height: 100%;
    background-color: #FAFAFA;
    padding: 2rem;
    border-radius: 50px;
    border-color: #4E3629;
    margin: 2rem 0 0 0;
    font-family: "BenJerry-Chunk", sans-serif;

}

.form{
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    justify-content: space-between;
    
}

.infoLable {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    justify-content: space-between;
    margin: 1rem 0;
}

.inputs {
    padding: 0.5rem;
    border-radius: 50px;
    border: 1px solid #4E3629;
    outline: none;
}

.inputPadding {
    padding: 0.9rem 0.5rem;
}
.textereaPadding {
    padding: 4rem 0.5rem;
}

.btn {
    color: #FAFAFA;
    font-weight: 600;
    font-family:  'ChunkFive', sans-serif;
    font-size: large;
    background-color: #00A1E4;
    border-color: #4E3629;
    border-radius: 50px;
    padding: 1rem 0;
    margin: 1rem 0;
    cursor: pointer;
}
input:focus {
    outline: none;
    border: 1px solid #4E3629;
}

/* @media screen and (max-width: 768px) {
    .order-form {
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
    }
} */


</style>