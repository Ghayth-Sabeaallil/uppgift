<script setup lang="ts">
import { ref } from "vue";
import Card from "./Card.vue";
import Button from "./Button.vue";


type data = {
  data: person[];
  total_pages: number;
};
type person = {
  id: number;
  email: string;
  first_name: string;
  last_name: string;
  avatar: string;
};


const datas = ref<data>();

//function to fetch
 const fetchData = async (page: number) => {
  try {
    const response = await fetch(`https://reqres.in/api/users?page=${page}`);
    const result = await response.json();
    datas.value = result;
  } catch (error) {
    console.error("Error fetching data:", error);
  }
};

//fetch data from first page when we load the page
fetchData(1);
</script>

<template>
  <main>
    <h1 class="title">Contact Us</h1>
    <div class="contact-box">
      <Card
        v-for="person in datas?.data"
        :key="person.id"
        :fname="person.first_name"
        :lname="person.last_name"
        :email="person.email"
        :avatar="person.avatar"
      />
    </div>
    <div class="btn-cont">
      <Button :buttonText=pages :onClick="fetchData" v-for="pages in datas?.total_pages" />
    </div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex: 1;
  justify-content: center;
  flex-direction: column;
  gap: 3rem;
}
h1{
  text-align: center  ;
}
.contact-box {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  justify-content: center;
  text-align: center;
  align-items: center;
  padding: 1em;
}
.btn-cont{
    display: flex;
    justify-content: center;
    gap: 0.5em;
}

</style>
