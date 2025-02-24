<script setup>
import { ref, onMounted } from "vue";
import { supabase } from "./lib/supabase";

const message = ref("Connecting...");

onMounted(async () => {
  let { data: test, error } = await supabase
    .from('test')
    .select('*')
          
  if (error) {
    message.value = "Error connecting to Supabase";
  } else {
    message.value = `Connected to Supabase. Found ${test.length} rows in 'test' table`;
  }
});
</script>

<template>
  <h1>{{ message }}</h1>
</template>

