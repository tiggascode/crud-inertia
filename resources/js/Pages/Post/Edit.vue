<template>
        <h1 class="text-lg mb-2">Edit</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sky-500 text-sm mb-8">Back</Link>
        </div>
        <form @submit.prevent="update">
            <div class="mb-4">
                <input v-model="title" class=" w-full rounded-full border-gray-300" type="text" placeholder="title">
                <div v-if="errors.title" class="text-red-600 text-sm">{{ errors.title }}</div>
            </div>
            <div class="mb-4">
                <textarea v-model="content" class=" w-full rounded-full border-gray-300" placeholder="content"></textarea>
                <div v-if="errors.content" class="text-red-600 text-sm">{{ errors.content }}</div>    
            </div>
            <div>
                <button class="ml-auto hover:bg-white hover:text-sky-500 border border-sky-500 block p-2 w-32 bg-sky-500 rounded-full text-center text-white" type="submit">Update</button>
            </div>

        </form>
</template>

<script>
import MainLayout from '@/Layouts/MainLayout.vue';
import {Link} from '@inertiajs/vue3';
export default {
    name: 'Edit',

    layout: MainLayout,

    props: [
        'post',
        'errors'
    ],


    components: {
        Link
    },

    data(){
        return {
            id: this.post.id,
            title: this.post.title,
            content: this.post.content,
        }
    },

    methods: {
        update(){
            this.$inertia.patch(`/posts/${this.id}`, {title: this.title, content: this.content} )
        }
    },
}
</script>

<style scoped>

</style>

