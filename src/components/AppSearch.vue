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
    <div class="d-flex mb-3 gap-4">
        <button @click="$emit('reset')" type="button" class="btn btn-light">Reset</button>

        <select class="form-select" aria-label="archetype" id="select" v-model="store.stringToSearch"
            @change="$emit('search')">
            <option disabled value="">Chose the archetype</option>
            <option value="Alien">Alien</option>
            <option value="Ally of Justice">Ally of Justice</option>
            <option value="Ancient Gear">Ancient Gear</option>
        </select>
    </div>
</template>

<style scoped lang="scss"></style>