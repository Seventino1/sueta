<template>
<div className="user">
    <button @click="deleteUser(index)"> Удалить </button>
    <h3> {{ user.name }}</h3>
    <h1> {{ user.email }} - {{ user.pass }} </h1>
 
</div>
</template>

<script>
export default {
    props: {
        user: {
            type: Object,
            Required: true,
        },
        index: {
            type: Number,
            Required: true
        },
        deleteUser: {
            type: Function,
            Required: true
        }
    }
}
</script>

<style scoped>
button {
    border: 0;
    border-radius: 5px;
    outline: none;
    padding: 10px 15px;
    background: #b93e3e;
    color: red;
    font-weight: bold;
    cursor: pointer;
    transition: transform 500ms ease;
    float: right;
    display: flex;
    text-align: end;
}

button:hover {
    transform: translateY(5px);
}
</style>