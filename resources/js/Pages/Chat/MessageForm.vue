<script setup>
    import { useForm } from '@inertiajs/inertia-vue3';
    import { computed, watch } from 'vue'

    const emit = defineEmits(['updateMessages']);

    const props = defineProps({
        activeUser: {
            type: Object,
            default: null
        },
    })

    const user = computed(() => usePage().props.value.user);

    const form = useForm({
        message: '',
        from: user.id,
        to: props.activeUser.id
    });

    const submit = () => {
        form.post(route('store.messages'), {
            onSuccess: () => {
                emit('updateMessages')
            },
            onFinish: () => form.reset(),
        });
    };
    
    watch(() => props.activeUser, (usr) => {
        form.to = usr;
    });
</script>

<template>
    <div className="w-full h-12 mx-4">
        <form className="flex mx-4" @submit.prevent="submit">
            <input 
                type="text" 
                name="message"
                placeholder="Text something..."
                v-model="form.message" 
                className="w-full h-12 border-2 border-r-0 rounded-l-xl mt-6 border-gray-300">
            <button type="submit" className="w-12 h-12 rounded-r-xl border-2 border-gray-300 mt-6 font-bold">></button>
        </form>
    </div>
</template>
