<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <div class="home">
        <h1>All destinations</h1>
        <div class="destinations">
            <router-link 
            v-for="dest in destinations" 
            :key="dest.id" 
            :to="{name :'destination.show', params: {id : dest.id, slug: dest.slug}}"
            >
                <h2>{{ dest.name }}</h2>
                <img 
                :src="`/images/${dest.image}`" 
                :alt="dest.name"
                >
            </router-link>
        </div>
    </div>
</template>


<script setup>

import  sourceData  from '@/data.json'
import { ref } from 'vue'

const data = ref(sourceData)
const destinations = ref(data.value.destinations)

</script>