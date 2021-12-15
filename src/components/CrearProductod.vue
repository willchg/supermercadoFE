<template>
  <h1 style="text-align: center">
    ¡Bienvenid@ a Productos <span> {{ username }} </span>!
  </h1>
  <br />
  <br />
  <div class="container">
    <div class="row">
      <div class="col">
        <h2>crear</h2>
        <form v-on:submit.prevent="processCreate">
          <input
            type="text"
            class="form-control"
            v-model="producto.nombre"
            placeholder="Nombre"
          />
          <br />
          <input
            type="number"
            class="form-control"
            v-model="producto.precio"
            placeholder="Precio"
          />
          <br />
          <input
            type="text"
            class="form-control"
            v-model="producto.categoria"
            placeholder="categoria"
          />
          <br />
          <input
            type="number"
            class="form-control"
            v-model="producto.cantidadcompra"
            placeholder="Cantidad"
          />
          <br />
          <input
            type="number"
            class="form-control"
            v-model="producto.stock"
            placeholder="Stock"
          />
          <br />
          <input
            type="date"
            class="form-control"
            v-model="producto.fechavencimiento"
            placeholder="Fecha"
          />
          <br />
          <button type="submit" class="btn btn-primary">Crear</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";

export default {
  name: "nuevosproductos",
 
  data: function () {
    return {
      
      
      producto: {
        
        nombre: "",
        precio: "",
        categoria: "",
        cantidadcompra:"",
        stock: "",
        fechavencimiento: ""
      },
    };
  },
  
  methods:{
  
  processCreate: async function(){
    
  await this.$apollo 

    .mutate ({
        mutation: gql`
  
        mutation Mutation($producto: ProductoInput!) {
          nuevoProducto(producto: $producto) {
            id
            nombre
            precio
            categoria
            cantidadcompra
            stock
            fechavencimiento
          }
        }

      `,
     variables: {
        producto: this.producto,
        
      },
    })
  }
  }
};
  
</script>
<style>
h1 {
  font-size: 50px;
  color: #283747;
}
span {
  color: crimson;
  font-weight: bold;
}
</style>
