<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import ChatLayout from '@/Layouts/ChatLayout.vue';
import ChatRoom from './Chat/ChatRoom.vue';
import UsersList from './Chat/UsersList.vue';
</script>

<template>
    <AppLayout title="Chat">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Chat
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <ChatLayout>
                        <UsersList />
                        <ChatRoom v-if="false" />
                    </ChatLayout>
                </div>
            </div>
        </div>
    </AppLayout>
</template>
