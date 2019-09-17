<template>
    <div class="add-list">
        <div class="row mb-3">
            <div class="col text-right">
                <button class="btn btn-primary" v-on:click="formShow">Create New Post</button>
            </div>
        </div>
        <div class="card bg-dark mb-3" v-if="formDiv">
            <div class="card-body">
                <form @submit.prevent="addPost">
                   <div class="form-group">
                     <label for="">Post Title</label>
                     <input
                        type="text"
                        v-model="title"
                        name="title"
                        class="form-control"
                        placeholder="Enter Post Title"
                     >
                   </div>
                   <div class="form-group">
                     <label for="">Post Details</label>
                     <textarea
                        type="text"
                        v-model="body"
                        name="body"
                        class="form-control"
                        placeholder="Enter Post Details">
                     </textarea>
                   </div>
                   <div class="row">
                       <div class="col-6 mx-auto">
                           <button class="btn btn-block btn-success">Create Post</button>
                       </div>
                   </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "AddPost",
    data(){
        return{
            formDiv: false,
            title: "",
            body: ""
        }
    },
    methods:{
        formShow(){
            this.formDiv  = true
        },
        addPost(){
            const newPost = {
                title: this.title,
                body: this.body
            };

            // send up to parent
            this.$emit("add-post", newPost);
            (this.title=""), (this.body="");
        }
    }
}
</script>