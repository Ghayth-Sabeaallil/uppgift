<script setup lang="ts">
defineProps<{ fname: string, lname: string, email: string, avatar: string }>();
function copy(email : string){
    navigator.clipboard.writeText(email);
}
</script>

<template>
    <div class="card-container">
        <img class="avatar" :src=avatar :alt=fname>
        <h2>{{ fname }} {{ lname }}</h2>
        <div> <a :href="'mailto:' + email"><img src="/mail.png" alt="mail"></a>
            <img @click="copy(email)" src="/copy.svg" alt="copy email">
        </div>
    </div>
</template>

<style scoped>
.card-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    max-width: 500px;
    gap: 1em;
}

.avatar {
    border-radius: 50%;
    width: 200px;
    height: 200px;
}

.avatar:hover {
    border: 5px solid salmon;
    -webkit-box-shadow: 0 0 20px #000000;
    box-shadow: 0 0 20px #000000;
}

img {
    width: 35px;
    height: 35px;
    cursor: pointer;
}

h2 {
    color: rgb(108, 110, 110);

}
</style>
