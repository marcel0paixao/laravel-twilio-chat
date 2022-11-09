<script setup>
    import AppLayout from '@/Layouts/AppLayout.vue';
    import ChatLayout from '@/Layouts/ChatLayout.vue';
    import { ref, onMounted } from 'vue';
    import ChatRoom from './Chat/ChatRoom.vue';
    import UsersList from './Chat/UsersList.vue';

    const activeUser = ref(null);

    const defineActive = (user) => {
        activeUser.value = user;
    }
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
                        <UsersList @defineActive="defineActive" :activeUser="activeUser" />
                        <ChatRoom v-if="activeUser" :activeUser="activeUser" />
                    </ChatLayout>
                </div>
            </div>
        </div>
    </AppLayout>
</template>
