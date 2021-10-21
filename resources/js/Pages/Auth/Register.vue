<template>
    <PublicLayout>
        <v-card class="mx-auto pa-5" max-width="500px">

            <form @submit.prevent="submit">
                <div>
                    <v-text-field
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
                        id="email"
                        type="email"
                        label="Email"
                        v-model="form.email"
                        required
                    />
                </div>

                <div class="mt-4">
                    <v-text-field
                        label="Password"
                        id="password"
                        type="password"
                        v-model="form.password"
                        required
                        autocomplete="new-password"
                    />
                </div>

                <div class="mt-4">
                    <v-btn
                        label="Confirm Password"
                        id="password_confirmation" type="password"
                        v-model="form.password_confirmation"
                        required
                        autocomplete="new-password"
                    />
                </div>

                <div class="mt-4" v-if="$page.props.jetstream.hasTermsAndPrivacyPolicyFeature">
                    <v-label for="terms">
                        <div class="flex items-center">
                            <jet-checkbox name="terms" id="terms" v-model="form.terms" />

                            <div class="ml-2">
                                I agree to the <a target="_blank" :href="route('terms.show')" class="underline text-sm text-gray-600 hover:text-gray-900">Terms of Service</a> and <a target="_blank" :href="route('policy.show')" class="underline text-sm text-gray-600 hover:text-gray-900">Privacy Policy</a>
                            </div>
                        </div>
                    </v-label>
                </div>

                <div class="flex items-center justify-end mt-4">
                    <inertia-link :href="route('login')" class="underline text-sm text-gray-600 hover:text-gray-900">
                        Already registered?
                    </inertia-link>

                    <v-btn class="ml-4" :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                        Register
                    </v-btn>
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
