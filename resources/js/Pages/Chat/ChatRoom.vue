<script setup>
import ChatHeader from './ChatHeader.vue';
import MessageList from './MessageList.vue';
import MessageForm from './MessageForm.vue';
</script>

<template>
    <div className="h-full w-[74%]">
        <ChatHeader />
        <MessageList />
        <MessageForm />
    </div>
</template>
