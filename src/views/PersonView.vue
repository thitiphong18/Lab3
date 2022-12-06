<script setup lang="ts">
import { reactive, watch } from "vue";
const person = reactive({ name: "", surname: "", gender: "" });
const msg = reactive({ name: "", surname: "", gender: "" });
watch(
  () => person.name,
  (name) => {
    if (name.trim().length === 0) {
      msg.name = "First name is empty!!!";
    }
    msg.name = "";
  }
);

function doSubmit() {
  console.log(person);
  console.log("Name: " + name);
}
</script>

<template>
  <div>
    <form>
      <label for="name">First Name</label>
      <input type="text" id="name" v-model="person.name" autocomplete="off" />

      <label for="surname">Secound Name</label>
      <input
        type="text"
        id="sername"
        v-model="person.surname"
        autocomplete="off"
      />
      <div>{{ msg.name }}</div>
      <label for="gender">Gender</label>
      <select id="gender" v-model="person.gender">
        <option hidden selected>Select Gender</option>
        <option value="M">Male</option>
        <option value="F">Female</option>
      </select>
      <input type="submit" value="Submit" @click.prevent="doSubmit" />
    </form>
    <pre> {{ person }} </pre>
  </div>
</template>

<style scoped>
input[type="text"],
select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type="submit"] {
  width: 100%;
  background-color: #4caf50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type="submit"]:hover {
  background-color: #45a049;
}

div {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}
</style>
