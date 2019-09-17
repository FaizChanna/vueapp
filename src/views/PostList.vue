<template>
    <div class="add-post">
        <div class="card mb-3" v-for="post of posts" :key="post.id">
            <div class="card-body">
                <h3><router-link :to="`/post-details/${post.id}`">{{post.title}}</router-link></h3>
                <p>{{post.body}}</p>
                <button class="btn btn-danger" @click="$emit('del-post', post.id)">Delete</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "PostList",
    props: ["posts"]
}
</script>