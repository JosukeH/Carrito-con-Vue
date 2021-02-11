<template>
  <div
    class="modal fade"
    id="exampleModal"
    tabindex="-1"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">Carrito</h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <div class="row" v-for="item in items" :key="item.id">
            <div class="col-2">
              <input
                type="number"
                style="width: 100%"
                name=""
                min="0"
                max="5"
                placeholder="0"
              />
            </div>
            <div class="col-3 align-top">
              <img
                :src="item.imagen"
                class="icon"
                alt="comida x"
              />
            </div>
            <div class="col-3">{{item.nombre}}</div>
            <div class="col-2">$ 100</div>
            <div class="col-2"><i class="fas fa-times"></i></div>
            <br>
            <hr />

          </div>
        </div>

        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
          >
            Cerrar
          </button>
          <button type="button" class="btn btn-primary">Comprar</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Cart',
  props: ['items'],
};
</script>

 <style> .icon{
  position:relative;
  top:-8px;
  max-width: 40px;
} </style>