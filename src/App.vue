<script setup>
import { ref } from "vue";

const name = ref("");
const count = ref(0);
</script>

<template>
  <provet-stack class="n-reset">
    <provet-input label="Your name" v-model="name"></provet-input>
    <p>{{ name }}</p>

    <provet-button variant="primary" @click="count++">
      Count: {{ count }}
    </provet-button>
  </provet-stack>
</template>
