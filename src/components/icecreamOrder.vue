<template>
<div class="order-form">
<h1>Ben & Jerry's Order Formulier</h1>
<div class="form">
<h2>Contact gegevens</h2>
<div class="bezoeker-info">
<label class="placeholder" for="name">Naam</label>
<input class="inputs inputPadding" type="text" id="name" name="name" v-model="name"></div>

<label class="placeholder" for="name">E-mail</label>
<input class="inputs inputPadding" type="text" id="email" v-model="email"></div>

<label class="placeholder" for="name">Gsm nummer</label>
<input class="inputs inputPadding" type="text" id="phone" name="name" v-model="phone"></div>

<div class="form">
<h2>Ben & Jerry's Bestelling</h2>
<div class="placeholder" for="icecream">
<input class ="inputs inputPadding" type="text" id="donut"  v-model="coneFlavor">
</div>
</div>



</div>
</template>