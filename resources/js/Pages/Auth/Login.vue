<template>
   <PublicLayout>
       <v-card class="mx-auto pa-5" max-width="500px">
           <v-card-title>
               SignIn
           </v-card-title>




           <form @submit.prevent="submit" class="pa-5">
               <div>

                   <v-text-field
                       id="email"
                       type="email"
                       outlined
                       v-model="form.email"
                       required
                       autofocus
                       label="Email"
                   />
               </div>

               <div class="mt-4">
                   <v-text-field
                       id="password"
                       type="password"
                       label="Password"
                       outlined
                       v-model="form.password"
                       required
                       autocomplete="current-password"
                   />

               </div>

               <div class="mt-4">
                   <v-switch
                       inset
                       label="Remember me"
                       v-model="form.remember"
                   ></v-switch>
               </div>

               <div>
                   <v-btn block btn-lg  color="primary" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                       Login
                   </v-btn>
                   <br>
                   <inertia-link class="mt-5"   :href="route('password.request')">
                       Forgot your password?
                   </inertia-link>
               </div>
           </form>
       </v-card>
   </PublicLayout>
</template>

<script>
    import PublicLayout from "../../Layouts/PublicLayout";

    export default {

        components:{
            PublicLayout
        },

        data() {
            return {
                form: this.$inertia.form({
                    email: '',
                    password: '',
                    remember: false
                })
            }
        },

        methods: {
            submit() {
                this.form
                    .transform(data => ({
                        ... data,
                        remember: this.form.remember ? 'on' : ''
                    }))
                    .post(this.route('login'), {
                        onFinish: () => this.form.reset('password'),
                    })
            }
        }
    }
</script>
