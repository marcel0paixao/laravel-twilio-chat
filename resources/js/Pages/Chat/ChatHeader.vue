<script setup>
const props = defineProps({
    user: {
        type: Object,
        default: null
    },
})
</script>

<template>
    <div className="w-full h-16 mx-3 border-b-2 flex">
        <div class="w-12 h-12 mt-2 rounded-full bg-red-100"></div>
        <div class="mt-2 ml-4">
            <h2 className="text-xl font-bold">{{ user.name }}</h2>
            <p className="font-[100] text-sm">Last seen a hour ago</p>
        </div>
    </div>
</template>
