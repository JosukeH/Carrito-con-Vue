<template>
  <nav-bar> </nav-bar>
  <cart :items="carrito" v-on:pagar="pagar" v-on:remover-item="removerProducto">
  </cart>
  <div class="container">
    <div class="row">
      <div class="col-md-12">
        <div class="row">
          <div
            class="col-lg-3 col-md-6 col-sm-12"
            v-for="prod in productos"
            :key="prod.id"
          >
            <producto
              :estaEnCarrito="estaEnCarrito(prod)"
              :producto="prod"
              v-on:agregar-carro="agregarProdCarro"
            >
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
    return { productos, carrito:[] };
  },
  methods: {
    agregarProdCarro(producto) {
      this.carrito.push(producto);
    },
    estaEnCarrito(producto) {
      const item = this.carrito.find((item) => item.id === producto.id);
      if (item) {
        return true;
      }
        return false;
      },
removerProducto(producto){
 this.carrito=this.carrito.filter(item => item.id != producto.id);
} ,
pagar(){
  this.carrito=[];
  alert('Venta completada')
}
},

};
</script>

<style>
body {
  margin-top: 20px;
}
</style>
