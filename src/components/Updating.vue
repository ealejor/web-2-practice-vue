<script setup lang="ts">
import {ref} from "vue";

const first = ref('');
const last = ref('');
const name = ref('');
const sex = ref('');
const subjects = ref(
    [
        'Cálculo I', 'Álgebra Lineal',
        'Programación web II', 'Electrónica I',
    ]
);
const selectedSubject = ref('');
const comments = ref('');
</script>

<template>
    <div class="container">
        <label for="paterno">Paterno <input id="paterno" v-model="first"></label>
        <label for="materno">Materno <input id="materno" v-model="last"></label>
        <label for="nombre">Nombre <input id="nombre" v-model="name"></label>
        <div>
            <label>Sexo:</label>
            <input type="radio" id="hombre" value="hombre" v-model="sex">
            <label for="hombre">Hombre</label><br>
            <input type="radio" id="mujer" value="mujer" v-model="sex">
            <label for="mujer">Mujer</label>
        </div>
        <br>
        <label for="combo">Materias</label>
        <select id="combo" v-model="selectedSubject">
            <option
                v-for="subject in subjects"
                :key="subject"
                :value="subject"
            >
                {{ subject }}
            </option>
        </select>
        <br>
        <label for="comment">Comentarios:</label>
        <textarea id="comment" rows="6" cols="28" v-model="comments"></textarea>
        <br>
        <div>
            <label>Paterno: {{ first }}</label>
        </div>
        <div>
            <label>Materno: {{ last }}</label>
        </div>
        <div>
            <label>Nombre: {{ name }}</label>
        </div>
        <div>
            <label>Sexo: {{ sex }}</label>
        </div>
        <div>
            <label>Materias: {{ selectedSubject }}</label>
        </div>
        <div>
            <label>Comentarios: {{ comments }}</label>
        </div>
    </div>
</template>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: start;
}
</style>
