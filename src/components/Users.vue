<script setup lang="ts">
import {ref} from "vue";

const users = ref([
    {
        firstName: 'Frank', lastName: 'Murphy',
        email: 'frank.murphy@test.com', role: 'User'
    },
    {
        firstName: 'Vic', lastName: 'Reynolds',
        email: 'vic.reynolds@test.com', role: 'Admin'
    },
    {
        firstName: 'Gina', lastName: 'Jabowski',
        email: 'gina.jabowski@test.com', role: 'Admin'
    },
    {
        firstName: 'Jessi', lastName: 'Glaser',
        email: 'jessi.glaser@test.com', role: 'User'
    },
    {
        firstName: 'Jay', lastName: 'Bilzerian',
        email: 'jay.bilzerian@test.com', role: 'User'
    }
]);
</script>

<template>
    <h3 class="title">Vue 3 - Display a list of items with v-for</h3>
    <div class="Users">
        <table>
            <thead>
            <tr>
                <th class="headTable name">Name</th>
                <th class="headTable email">Email</th>
                <th class="headTable role">Role</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="user in users" :key="user.email">
                <td class="bodyTable name">{{ user.firstName }} {{ user.lastName }}</td>
                <td class="bodyTable email">{{ user.email }}</td>
                <td class="bodyTable role">{{ user.role }}</td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<style scoped>
.Users {
    margin: 2px;
    border: 1px solid #000000;
    border-radius: 10px;
}

.title {
    color: #000000;
    margin-left: 2px;
    margin-top: 20px;
    margin-bottom: 20px;
}

.headTable {
    padding: 2px;
    border: 1px solid #000000;
    border-radius: 50px;
    text-align: left;
    background-color: yellow;
}

.bodyTable {
    padding: 2px;
    border: 1px solid #000000;
    border-radius: 50px;
    background-color: #6f7e5d;
}

.name {
    width: 100%;
}

.email {
    width: max-content;
}

.role {
    width: max-content;
}
</style>