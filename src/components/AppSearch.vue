<script>
import { store } from "../store.js";

export default {
    data() {
        return {
            store
        }
    },
}
</script>

<template>
    <div class="d-flex mb-3 gap-3">
        <button @click="$emit('reset')" type="button" class="btn btn-light">Reset</button>

        <select class="form-select" aria-label="archetype" id="select" v-model="store.stringToSearch">
            <option disabled value="">Chose the archetype</option>
            <option value="Alien">Alien</option>
            <option value="Ally of Justice">Ally of Justice</option>
            <option value="Ancient Gear">Ancient Gear</option>
        </select>

        <button @click="$emit('search')" type="button" class="btn btn-light">Search</button>
    </div>
</template>

<style scoped lang="scss"></style>