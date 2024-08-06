<template>
    <div>
        <div class="flex items-center justify-between p-4 bg-white border-b border-gray-200">
        </div>
    </div>
</template>

<script setup>
import {onMounted, onUnmounted} from "vue";

const props = defineProps({
    currentUser: {
        type: Object,
        required: true,
    },
});

onMounted(() => {
    const user = props.currentUser;
    console.log(user);

    window.Echo.private(`App.Models.User.${user.id}`)
        .listen('ReverbExampleEvent', (e) => {
            alert('Reverb 🚀')
        })

});
</script>
