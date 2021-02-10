<template>
  <div class="card my-5" >
    <img :src="producto.imagen" alt="Comida" class="card-img-top"/>
    <div class="card-body text-center">
      <h5 class="card-title">{{producto.nombre}}</h5>
      <p class="card-text text-muted">$ {{(producto.precio)*1}}</p>
      <button class="btn btn-success"> <i class="fas fa-cart-plus"></i> Agregar al carrito</button>
    </div>
  </div>
</template>

<script>
export default {
    name:'Producto',
    props: ['producto']
};
</script>


<style scoped>

</style>