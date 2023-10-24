<script setup lang="ts">
import {ref} from 'vue';

const inputItem = ref<string>('');
const items = ref<string[]>([]);

/**
 * Agrega un item a la lista si el input no está vacío
 */
const addItem = () => {
    if (inputItem.value.trim() !== '') {
        items.value.push(inputItem.value);
        inputItem.value = '';
    }
};

/**
 * Elimina un item de la lista
 * @param index Índice del item a eliminar
 */
const deleteItem = (index: number) => {
    items.value.splice(index, 1);
};

/**
 * Escucha la tecla de retroceso
 */
const listenLeftKey = () => {
    if (inputItem.value.trim() === '') {
        if (items.value.length > 0) {
            // Si no hay texto en el input, borra un elemento
            // si hay elementos en la lista
            deleteItem(items.value.length - 1);
        }
    } else {
        // Si hay texto en el input, borra la última letra
        inputItem.value = inputItem.value.slice(0, -1);
    }
};
</script>

<template>
    <div>
        <div class="container">
            <div v-for="(item, index) in items" :key="index" class="item-add">
                {{ item }}
                <button @click="deleteItem(index)">X</button>
            </div>
            <input
                v-model="inputItem"
                placeholder="texto"
                @keyup.left="listenLeftKey"
                @keyup.enter="addItem"/>
        </div>
    </div>
</template>

<style scoped>
.container {
    padding: 5px;
    border: 1px solid #000000;
    border-radius: 3px;
    width: max-content;
    display: flex;
    flex-direction: row;
    align-items: center;
}

.item-add {
    border-radius: 3px;
    border: 1px solid #bbbbbb;
    padding: 5px;
    margin-right: 3px;
}

input {
    border-radius: 0;
    border: transparent;
    outline: none;
}

button {
    border-radius: 0;
    border: transparent;
    outline: none;
    background-color: transparent;
    color: #383838;
    margin-left: 5px;
    cursor: pointer;
}
</style>

