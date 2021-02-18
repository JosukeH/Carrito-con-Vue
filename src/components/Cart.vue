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
          <h5 class="modal-title" id="exampleModalLabel">
            {{ items.length != 0 ? "Carrito" : "Carrito vacio" }}
          </h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <div v-if="items.length===0">Sin productos</div>
          <div class="row" v-for="item in items" :key="item.id">
            <div class="col-2">
              <input
                type="number"
                style="width: 100%"
                name=""
                min="1"
                max="5"
                value="1"
              />
            </div>
            <div class="col-3 align-top">
              <img :src="item.imagen" class="icon" alt="comida x" />
            </div>

            <div class="col-3">{{ item.nombre }}</div>
            <div class="col-2">$ {{ item.precio }}</div>
            <div class="col-2">
              <button
                :key="item.id"
                @click="removerItem(item)"
                class="btn btn-outline-danger icon"
              >
                <i class="fas fa-times"></i>
              </button>
            </div>
            <br />
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
          <button
            type="button"
            @click="$emit('pagar')"
            :disabled="activo"
            class="btn btn-primary"
          >
            Comprar {{ total }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: ["items"],
  computed: {
    total() {
      return this.items.reduce(
        (acumulador, item) => acumulador + Number(item.precio),
        0
      );
    },
  },
  methods: {
    removerItem(item) {
      this.$emit("remover-item", item);
    },

    pagar() {
      this.carrito = [];
      alert("Venta completada");
    },
  },
};
</script>

<style>
.icon {
  position: relative;
  top: -8px;
  max-width: 40px;
}
</style>
