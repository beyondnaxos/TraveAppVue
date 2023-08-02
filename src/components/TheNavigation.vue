<template>
    <div id="nav">

      <router-link id="logo" to="/">Vue School Trave App</router-link>
      <router-link 
            v-for="dest in destinations" 
            :key="dest.id" 
            :to="{name :'destination.show', params: {id : dest.id, slug: dest.slug  }}"
            >
              {{ dest.name }}
            </router-link>
  </div>
</template>

<script setup>
import sourceData  from '@/data.json'

import { ref } from 'vue'

const data = ref(sourceData)
const destinations = ref(data.value.destinations)


</script>



