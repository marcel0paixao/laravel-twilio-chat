<script setup>
    import { ref, onMounted, computed } from 'vue'
    import {usePage} from "@inertiajs/inertia-vue3";

    const props = defineProps({
        messages: {
            type: Array,
            default: null
        },
    })

    const user = computed(() => usePage().props.value.user);

    onMounted(() => {
        document.querySelectorAll('.message:last-child')[0]?.scrollIntoView();
    })
</script>

<template>
    <div className="ml-6 h-[80%] overflow-y-auto">
        <ul className="pt-4 space-y-4 mr-6">
            <li :class="'min-h-12 p-4 rounded-md bg-gray-100 min-w-[30%] max-w-[60%] message ' + (user.id == msg.from ? 'ml-auto' : '')" v-for="msg in props.messages">
                <p>{{ msg.message }}</p> 
                <p className="text-xs mt-2 text-gray-700">Today, 22h36</p>
            </li>
        </ul>
    </div>
</template>
