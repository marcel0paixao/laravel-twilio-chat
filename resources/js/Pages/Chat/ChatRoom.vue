<script setup>
    import ChatHeader from './ChatHeader.vue';
    import MessageList from './MessageList.vue';
    import MessageForm from './MessageForm.vue';
    import { onMounted, ref, watch } from 'vue';
    import axios from 'axios';

    const props = defineProps({
        activeUser: {
            type: Object,
            default: null
        },
    })

    const messages = ref({});

    const getMessages = () => {
        axios.get(route('load.messages', { 'user_id': props.activeUser.id ?? 0 }))
            .then(response => {
                messages.value = response.data.messages;
            }).finally(() => {
                document.querySelectorAll('.message:last-child')[0]?.scrollIntoView();
            })
    }

    const updateMessages = () => {
        getMessages();
    }

    onMounted(() => {
        getMessages();
    })

    watch(() => props.activeUser, () => {
        getMessages();
    });
</script>

<template>
    <div className="h-full md:w-[74%]">
        <ChatHeader :user="activeUser" />
        <MessageList v-if="messages" :messages="messages" />
        <MessageForm :activeUser="activeUser" @updateMessages="updateMessages" />
    </div>
</template>
