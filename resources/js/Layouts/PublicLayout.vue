<template>
    <v-app id="inspire">
        <v-app-bar
            clipped-left
            dark
            elevate-on-scroll
            app
            color="primary"
        >
            <v-toolbar-title>
                Laravel & Vuetify
            </v-toolbar-title>
            <v-spacer/>
            <Link color="success" as="Button" class="mx-1"  href="/">
                Home
            </Link>

            <Link color="success" as="Button" class="mx-1"  href="/login">
                SignIn
            </Link>


            <Link color="white" as="Button"  class="mx-1"  href="/register">
                Register
            </Link>

        </v-app-bar>
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
