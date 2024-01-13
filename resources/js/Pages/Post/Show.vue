<template>
        <h1 class="text-lg mb-8">Post</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sky-500 text-sm mb-8">Back</Link>
        </div>
        <div v-if="post">
            <div  class="mb-8 pt-8 border-t border-gray-300">
                <div>id: {{ post.id }} </div>
                <div>title: {{ post.title }} </div>
                <div>content: {{ post.content }} </div> 
                <div class="text-sm text-right"> {{ post.date }} </div>
            </div>
        </div>
    
</template>

<script>
import MainLayout from '@/Layouts/MainLayout.vue';
import {Link} from '@inertiajs/vue3';
export default {
    name: 'Show',

    layout: MainLayout,

    props: [
        'post'
    ],

    components: {
        Link
    }
}
</script>

<style scoped>

</style>

