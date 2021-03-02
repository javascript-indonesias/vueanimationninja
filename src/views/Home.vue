<template>
    <div class="home">
        <Toast v-if="showToast" />
        <Todos @badValue="triggerToast" />
    </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue';
import { ref, defineAsyncComponent } from 'vue';

const Toast = defineAsyncComponent(() => import('../components/Toast.vue'));
const Todos = defineAsyncComponent(() => import('../components/Todos.vue'));

export default {
    name: 'Home',
    components: {
        Toast,
        Todos,
    },
    setup() {
        const showToast = ref(false);
        const triggerToast = () => {
            showToast.value = true;
            setTimeout(() => {
                showToast.value = false;
            }, 3000);
        };

        return { showToast, triggerToast };
    },
};
</script>

<style lang="scss"></style>
