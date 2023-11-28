<script>
import { store } from "../store.js";
import AppCard from "./AppCard.vue";
import AppLoader from "./AppLoader.vue";
import AppSearch from "./AppSearch.vue";
import axios from "axios";

export default {
    data() {
        return {
            store
        }
    },
    components: {
        AppCard,
        AppLoader,
        AppSearch
    },
    methods: {
        search() {
            this.store.flagLoading = true;
            axios.get(this.store.apiUrl, {
                params: {
                    archetype: this.store.stringToSearch,
                    num: 20,
                    offset: 20
                }
            }).then((resp) => {
                this.store.cards = resp.data.data;
                this.store.flagLoading = false;
            });
            console.log(this.store.stringToSearch);
        },
        allTheCard() {
            this.store.flagLoading = true;
            axios.get(this.store.apiUrl, {
                params: {
                    num: 20,
                    offset: 20
                }
            }).then((resp) => {
                this.store.cards = resp.data.data;
                this.store.flagLoading = false;
            });
            this.store.stringToSearch = "";
        }
    }
}
</script>

<template>
    <main>
        <div class="container p-4 bg-white my-4 rounded-2">
            <AppLoader v-if="store.flagLoading" />

            <div v-else>
                <div class="d-flex justify-content-between">
                    <div class="alert alert-dark w-25" role="alert">Found {{ store.cards.length }} cards</div>
                    <AppSearch @search="search" @reset="allTheCard" />
                </div>

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