<template>
    <section class="destination" v-if="data">
        <h1>{{ data.name }}</h1>
        <div class="destination-details">
            <img :src="`/images/${data.image}`" :alt="data.name">
            <p>{{ data.description }}</p>
        </div>
    </section>
</template>

<script setup>
import { ref, watchEffect } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const data = ref(null)

const fetchDestinationData = async () => {
    try { 
        const response = await fetch(`https://travel-dummy-api.netlify.app/${route.params.slug}`)
        data.value = await response.json()    
    } catch (error) {
        console.log(error)
    }
}

watchEffect(() => {
    fetchDestinationData()
})
</script>

<style lang="scss" scoped></style>   
