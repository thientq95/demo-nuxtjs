<template>
    <section class="section">
        <h2 class="title is-3 has-text-grey">Home Component</h2>
        <button @click="check">Click</button>
        <select @change="changeSelect">
            <option value="Việt Nam">Việt Nam</option>
            <option value="Thái Lan">Thái Lan</option>
        </select>
        <h2>Users</h2>
        <ul class="users">
            <li v-for="user in users" :key="user.id">
                <NuxtLink :to="'/users/' + user.id">{{ user.name }}</NuxtLink>
            </li>
        </ul>
    </section>
</template>
<script>
import axios from "axios";
export default {
    head: {
        title: "Home Page",
        meta: [
            {
                hid: "description",
                name: "description",
                content: "Home page description"
            }
        ]
    },
    methods: {
        check() {
            console.log('check function working !');
        },
        changeSelect(e) {
            console.log(e.target.value);
            console.log('change');
        }
    },
    async asyncData() {
        const { data } = await axios.get(
            "https://jsonplaceholder.typicode.com/users"
        );
        return { users: data };
    }
};
</script>

<style scoped>
.container {
    text-align: center;
    margin-top: 100px;
    font-family: sans-serif;
}
.users {
    list-style-type: none;
}
.users li a {
    display: inline-block;
    width: 200px;
    border: 1px #ddd solid;
    padding: 10px;
    text-align: left;
    color: #222;
    text-decoration: none;
}
.users li a:hover {
    color: orange;
}
</style>
