<template>

        <h1 class="text-lg mb-2">Create</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sky-500 text-sm mb-8">Back</Link>
        </div>
        <form @submit.prevent="store">
            <div class="mb-4">
                <input v-model="title" class="w-full rounded-md border-gray-300" type="text" placeholder="Title">
                <div v-if="errors.title" class="text-red-800 text-sm">{{ errors.title }}</div>
            </div>
            <div class="mb-4">
                <textarea v-model="content" class="w-full rounded-md border-gray-300" placeholder="Content"></textarea>
                <div v-if="errors.content" class="text-red-800 text-sm">{{ errors.content }}</div>
            </div>
            <div>
                <button class="ml-auto hover:bg-white hover:text-sky-500 block p-2 w-32 border border-sky-500 bg-sky-500 rounded-full text-center text-white" type="submit">Store</button>
            </div>
        </form>

</template>

<script>
import {Link} from '@inertiajs/vue3'
import MainLayout from '@/Layouts/MainLayout.vue'

export default {
    name: "Index",
    components: {
        Link
    },

    props: [
        'errors'
    ],

    layout: MainLayout,

    data() {
        return {
            title: '',
            content: '',
        }
    },

    methods: {
        store() {
            this.$inertia.post('/posts', {title: this.title, content: this.content})
        }
    },
}
</script>

<style scoped>

</style>
