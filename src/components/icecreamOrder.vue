<template>
<div class="order-form">
<h1>Ben & Jerry's Order Formulier</h1>
<div class="form">
<h2>Contact gegevens</h2>
<div class="infoLable">

<label class="placeholder" for="name">Naam</label>
<input class="inputs inputPadding" type="text" id="name" name="name" v-model="name"></div>

<div class="infoLable">
<label class="placeholder" for="name">E-mail</label>
<input class="inputs inputPadding" type="text" id="email" v-model="email"></div>

<div class="infoLable">
<label class="placeholder" for="name">Gsm nummer</label>
<input class="inputs inputPadding" type="text" id="phone" name="name" v-model="phone"></div>

<div class="form">
<h2>Ben & Jerry's Bestelling</h2>
<div class="infoLable">
            <label  class="placeholder" for="conFlavor">Hoorntje Smaak</label>
            <select class ="inputs inputPadding" id="conFlavor" v-model="conFlavor">
                
                <option disabled value="">Kies een smaak</option>
                <option>Chocolade</option>
                <option>Vanilla</option>

            </select>

        </div>

<div class="infoLable">
<label class="placeholder" for="iceFlavors">
<input class ="inputs inputPadding" type="text" id="iceFlavors"  v-model="iceFlavors"></label>
<select class ="inputs inputPadding" id="conFlavor" v-model="conFlavor">
                
                <option disabled value="">Kies een smaak</option>
                <option>Chocolade</option>
                <option>Vanilla</option>
                <option>Aardbei</option>
                <option>Moka</option>

            </select>
</div>

<div class="infoLable">
<label class="placeholder" for="quantity">
<input class ="inputs inputPadding" type="text" id="quantity"  v-model="quantity"></label>
</div>

<div class="infoLable">
<label class="placeholder" for="status">
<input class ="inputs inputPadding" type="text" id="status"  v-model="status"></label>
</div>

<div class="infoLable">
<label class="placeholder" for="notes">
<textarea class ="inputs textereaPadding" id="note" v-model="notes"></textarea></label>
</div>

<div class="infoLable">
<label class="placeholder" for="timestamps">
<input class ="inputs inputPadding" type="text" id="timestamps"  v-model="timestamps"></label>
</div>

</div>


<button class ="btn" @click.prevent="postOrder">Bestelling verzenden</button>
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
    border-radius: 50%;
    border-color: #4E3629;
    margin: 2rem 0 0 0;
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
    border-radius: 50%;
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
    font-family:  'Nunito', sans-serif;
    font-size: large;
    background-color: #00A1E4;
    border-color: #4E3629;
    border-radius: 50%;
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