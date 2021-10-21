<template>
    <PublicLayout>
        <v-card class="mx-auto pa-5" max-width="500px">
            <v-card-title>
                <h1 class="font-weight-thin">SignUp</h1>
            </v-card-title>
             <v-card-text>
                 <form @submit.prevent="submit">
                     <div class="mt-4">
                         <v-text-field
                             outlined
                             id="name"
                             type="text"
                             label="Name"
                             v-model="form.name"
                             required
                             autofocus
                             autocomplete="name" />
                     </div>

                     <div class="mt-4">
                         <v-text-field
                             outlined
                             id="email"
                             type="email"
                             label="Email"
                             v-model="form.email"
                             required
                         />
                     </div>

                     <div class="mt-4">
                         <v-text-field
                             outlined
                             label="Password"
                             id="password"
                             type="password"
                             v-model="form.password"
                             required
                             autocomplete="new-password"
                         />
                     </div>

                     <div class="mt-4">
                         <v-text-field
                             outlined
                             label="Confirm Password"
                             id="password_confirmation"
                             type="password"
                             v-model="form.password_confirmation"
                             required
                             autocomplete="new-password"
                         />
                     </div>

                     <div class="mt-4" v-if="$page.props.jetstream.hasTermsAndPrivacyPolicyFeature">
                         <div class="flex items-center">
                             <v-switch name="terms" id="terms" v-model="form.terms" />

                             <div class="ml-2">
                                 I agree to the <a target="_blank" :href="route('terms.show')" class="underline text-sm text-gray-600 hover:text-gray-900">Terms of Service</a> and <a target="_blank" :href="route('policy.show')" class="underline text-sm text-gray-600 hover:text-gray-900">Privacy Policy</a>
                             </div>
                         </div>
                     </div>

                     <v-btn
                         :disabled="form.processing"
                         :loading="form.processing"
                         block
                         color="success"
                         type="submit"
                     >
                         Register
                     </v-btn>

                     <div class="d-flex justify-center mt-10">
                         <inertia-link :href="route('login')"  >
                             Already registered? LogIn
                         </inertia-link>
                     </div>
                 </form>
             </v-card-text>

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
                    name: '',
                    email: '',
                    password: '',
                    password_confirmation: '',
                    terms: false,
                })
            }
        },

        methods: {
            submit() {
                this.form.post(this.route('register'), {
                    onFinish: () => this.form.reset('password', 'password_confirmation'),
                })
            }
        }
    }
</script>
