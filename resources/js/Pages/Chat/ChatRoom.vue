<script setup>
    import ChatHeader from './ChatHeader.vue';
    import MessageList from './MessageList.vue';
    import MessageForm from './MessageForm.vue';
    import { ref, onMounted, watch } from 'vue';
    import axios from 'axios';

    const props = defineProps({
        activeUser: {
            type: Object,
            default: null
        },
    })

    const messages = ref({});

    watch(() => props.activeUser, (active) => {
        axios.get(route('load.messages', { 'user_id': props.activeUser.id ?? 0 })).then(response => {
            messages.value = response.data.messages
            console.log(messages.value);
        })
    });
</script>

<template>
    <div className="h-full w-[74%]">
        <ChatHeader :user="activeUser" />
        <MessageList :messages="messages" />
        <MessageForm />
    </div>
</template>
