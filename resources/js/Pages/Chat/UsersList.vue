<script setup>
    const props = defineProps({
        activeUser: {
            type: Object,
            default: null
        },
    })

    </script>

    <script>
    export default {
        name: 'UsersList',
        data() {
            return {
                users: []
            }
        },
        mounted() {
            axios.get(route('load.users')).then(response => {
                this.$data.users = response.data.users;
            })
        },
    }
</script>

<template>
    <div className="w-[34%] mr-auto h-full border-r hidden md:block">
        <ul className="h-full space-y-2 overflow-y-auto">
            <li v-for="usr in users" @click="$emit('defineActive', usr)"
                :class="(usr == props.activeUser ? 'bg-gray-200' : '') + ' border-2 h-24 rounded-lg p-6 cursor-pointer mr-3 hover:bg-gray-100'">
                <div>
                    <h3 className="font-bold max-w-[70%]">{{ usr.name }}</h3>
                    <div class="flex">
                        <p className="font-thin w-[70%]">Last message</p>
                        <p className="font-thin w-[30%] mt-1.5 text-xs">Sunday, 22h36</p>
                    </div>
                </div>
            </li>
        </ul>
    </div>
</template>
