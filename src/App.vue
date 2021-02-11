<template>
  <nav-bar> </nav-bar>
  <cart :items="carrito"> </cart>
  <div class="container">
    <div class="row">
      <div class="col-md-12">
        <div class="row">
          <div class="col-md-3" v-for="prod in productos" :key="prod.id">
            <producto :producto="prod" v-on:agregar-carro="agregarProdCarro">
            </producto>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Producto from "./components/Producto";
import NavBar from "./components/NavBar.vue";
import Cart from "./components/Cart.vue";
import productos from "./components/productos.json";

export default {
  name: "App",
  components: {
    Producto,
    NavBar,
    Cart,
  },
  data() {
    return { productos, carrito: [] };
  },
  methods: {
    agregarProdCarro(producto) {
      this.carrito.push(producto);
    },
  },
};
</script>

<style></style>
