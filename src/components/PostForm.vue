<template>
    <form @submit.prevent="submit">
        <input type="text" v-model="title"/>
        <input type="text" v-model="body"/>
        <button type="submit">create post</button>
    </form>
</template>

<script>
import {mapMutations} from "vuex";
export default {
    data() {
        return {
            title: "",
            body: ""
        };
    },
    methods: {
        ...mapMutations(["createPost"]),
        submit() {
            this.createPost({
                title: this.title,
                body: this.body,
                id: Date.now()
            })
        }
    }
}

</script>


<style scoped>
input {
    width: 100%;
    border: 1px solid #ccc;
    border-radius: 2px;
    padding: 10px;
    margin-bottom: 10px;
}

</style>