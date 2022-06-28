<template>
    <div class="posts">
        <div class="name">
            <p>{{ "Name : " + username }}</p>
        </div>
        <div class="content">
            <p>{{ content }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'PostContent',
    props: {
        username: String,
        content: String
    },
}
</script>

<style>
.posts {
    border: none;
    border-radius: 10%;
    background-color: rgb(47, 47, 47);
    color: white;
    font-weight: bold;
    max-width: 75%;
    margin-left: auto;
    margin-right: auto;
}

.posts :hover {
    transform: translateY(-3px);
}
</style>