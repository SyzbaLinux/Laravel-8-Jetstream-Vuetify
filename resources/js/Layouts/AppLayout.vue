<template>
    <v-app id="inspire">
        <v-navigation-drawer
            v-model="drawer"
            clipped
            app
        >
            <!--  -->
        </v-navigation-drawer>

        <v-app-bar app clipped-left>
            <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

            <v-toolbar-title>Task Manager App</v-toolbar-title>
        </v-app-bar>

        <v-main>
           <v-container fluid>
               <slot></slot>
           </v-container>
        </v-main>
    </v-app>
</template>

<script>
    export default {
        data: () => ({ drawer: null }),
    }
</script>
