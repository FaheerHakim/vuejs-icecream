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