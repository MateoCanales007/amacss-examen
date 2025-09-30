<template>
  <form id="app" @submit="checkForm" action="https://vuejs.org/" method="post" novalidate>
    <p v-if="errors.length">
      <b>Por favor, corrija el(los) siguiente(s) error(es):</b>
      <ul>
        <li v-for="error in errors" :key="error">{{ error }}</li>
      </ul>
    </p>

    <p>
      <label for="name">Nombre</label>
      <input v-model="name" type="text" id="name" name="name">
    </p>

    <p>
      <label for="age">Edad</label>
      <input v-model="age" type="number" id="age" name="age">
    </p>

    <p>
      <label for="movie">Película favorita</label>
      <select v-model="movie" id="movie" name="movie">
        <option value="">Selecciona una película</option>
        <option value="Star Wars">Star Wars</option>
        <option value="Vanilla Sky">Vanilla Sky</option>
        <option value="Atomic Blonde">Atomic Blonde</option>
      </select>
    </p>

    <p>
      <input type="submit" value="Enviar">
    </p>
  </form>
</template>

<script>
export default {
  data() {
    return {
      errors: [],
      name: null,
      age: null,
      movie: null
    };
  },
  methods: {
    checkForm(e) {
      this.errors = [];
      if (!this.name) {
        this.errors.push('El nombre es obligatorio.');
      }
      if (!this.age) {
        this.errors.push('La edad es obligatoria.');
      }
      if (!this.movie) {
        this.errors.push('Por favor, seleccione una película favorita.');
      }
      if (!this.errors.length) {
        return true;
      }
      e.preventDefault();
    }
  }
};
</script>

<style>
#app {
  max-width: 400px;
  margin: 40px auto;
  padding: 24px;
  background: #f9f9f9;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(60, 60, 60, 0.08);
  font-family: 'Segoe UI', 'Roboto', 'Arial', sans-serif;
}

label {
  display: block;
  margin-bottom: 6px;
  font-weight: 500;
  color: #42b983;
}

input[type="text"],
input[type="number"],
select {
  width: 100%;
  padding: 8px 10px;
  margin-bottom: 16px;
  border: 1px solid #d3d3d3;
  border-radius: 6px;
  font-size: 16px;
  box-sizing: border-box;
  transition: border-color 0.2s;
}

input[type="text"]:focus,
input[type="number"]:focus,
select:focus {
  border-color: #42b983;
  outline: none;
}

input[type="submit"] {
  background: #42b983;
  color: #fff;
  border: none;
  padding: 10px 24px;
  border-radius: 6px;
  font-size: 16px;
  cursor: pointer;
  transition: background 0.2s;
}

input[type="submit"]:hover {
  background: #369870;
}

p {
  margin-bottom: 18px;
}

ul {
  margin: 8px 0 0 18px;
  color: #d32f2f;
}

b {
  color: #d32f2f;
}
</style>