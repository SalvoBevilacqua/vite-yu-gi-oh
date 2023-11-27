<script>
import { store } from "../store.js";
import AppCard from "./AppCard.vue";
import AppLoader from "./AppLoader.vue";

export default {
    data() {
        return {
            store
        }
    },
    components: {
        AppCard,
        AppLoader,
    }
}
</script>

<template>
    <main>
        <div class="container p-4 bg-white my-4 rounded-2">
            <AppLoader v-if="store.flagLoading" />

            <div v-else>
                <div class="alert alert-dark" role="alert">Found {{ store.cards.length }} cards</div>

                <div class="row row-cols-5 row-gap-4">
                    <div class="col" v-for="item in store.cards" :key="item.id">
                        <AppCard :card="item" />
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped lang="scss"></style>