<script>
export default {
    props: {
        card: Object,
    }
};
</script>

<template>
    <div class="card bg-warning text-center h-100">
        <img :src="card.card_images[0].image_url" class="card-img-top" :alt="card.id">
        <div class="card-body">
            <h5 class="card-title text-white">{{ card.name }}</h5>
            <p class="card-text">{{ card.archetype }}</p>
        </div>
    </div>
</template>

<style scoped lang="scss"></style>


