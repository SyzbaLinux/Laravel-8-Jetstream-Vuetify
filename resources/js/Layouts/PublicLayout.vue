<template>
    <v-app id="inspire">
        <v-app-bar  app flat color="transparent" ></v-app-bar>
        <v-main>
            <v-container>
                <slot></slot>
            </v-container>
        </v-main>
    </v-app>
</template>

<script>
    import { Link } from '@inertiajs/inertia-vue'
    export default {
        name: "PublicLayout",
        components:{
            Link
        }
    }
</script>

<style scoped>

</style>
