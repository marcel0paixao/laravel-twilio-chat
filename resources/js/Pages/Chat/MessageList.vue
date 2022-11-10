<script setup>
    import { onMounted, computed } from 'vue'
    import {usePage} from "@inertiajs/inertia-vue3";

    const props = defineProps({
        messages: {
            type: Object,
            default: null
        },
    })

    const user = computed(() => usePage().props.value.user);
</script>

<template>
    <div className="ml-6 h-[80%] overflow-y-auto overflow-x-hidden">
        <ul className="pt-4 space-y-4 mr-6">
            <li :class="'min-h-12 p-4 rounded-md bg-gray-100 min-w-[30%] max-w-[60%] message break-all break-words ' + (user.id == msg.from ? 'ml-auto' : '')" v-for="msg in props.messages">
                <p>{{ msg.message }}</p> 
                <p className="text-xs mt-2 text-gray-700">{{ new Date(msg.created_at).toLocaleDateString('en-GB', { hour: '2-digit', minute: '2-digit', weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }) }}</p>
            </li>
        </ul>
    </div>
</template>