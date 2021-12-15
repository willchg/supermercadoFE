<template>
  <h1 style="text-align: center">
    ¡Bienvenid@ a Informacion <span> {{ username }} </span>!
  </h1>
  <br />
  <br />
  <div class="container">
    <div class="row">
      <div class="col"><img src="@/assets/logo.png" /></div>
      <div class="col">
        <p class="fst-italic">
          Somos un negocio dedicado a actividades dirigidas a la producción, conservación y dispensación de los medicamentos,
          así como a la colaboración en los procesos analíticos, 
          fármaco-terapéuticos y de vigilancia de la salud pública.
        </p>
      </div>
      <div class="col"><img src="@/assets/revuelto.jpg" /></div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Information",
  data: function () {
    return {
      username: localStorage.getItem("username") || "none",
    };
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