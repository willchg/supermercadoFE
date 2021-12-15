<template>
  <h1 style="text-align: center">
    ¡Bienvenid@ a Productos <span> {{ username }} </span>!
  </h1>
    
 
  <table class="table">
    <thead>
      <tr>
        <th>id</th>
        <th>nombre</th>
        <th>precio</th>
        <th>categoria</th>
        <th>fechavencimiento</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="producto in productos" :key="producto.id">
        <td>{{ producto.id }}</td>
        <td>{{ producto.nombre }}</td>
        <td>{{ producto.precio }}</td>
        <td>{{ producto.categoria }}</td>
        <td>{{ producto.fechavencimiento }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import gql from "graphql-tag";

export default {
  name: "productos",
  props: ["producto"],
  data: function () {
    return {
      
      
      productos: {
        id: "",
        nombre: "",
        precio: "",
        categoria: "",
        fechavencimiento: "",
      },
    };
  },
  apollo: {
    productos: {
      query: gql`
        query Query {
          productos {
            id
            nombre
            precio
            categoria
            fechavencimiento
          }
        }
      `,
      variables() {
        return {
          productoId: this.productos,
        };
      },
    },
  },

  methods: {
    },
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
