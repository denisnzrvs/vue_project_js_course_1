<template>
    <header class="header" :style="{ backgroundColor: headerBgColor }">
        <div>
            <img src="../assets/logo_white.svg" />
            <div id="circular" v-show="isLoggedIn"></div>
            <h1>OCTOPUS</h1>
        </div>
        <div>
            <ul>
                <li id="full_name" v-show="isLoggedIn">{{ full_name }}</li>
                <li><button href="#" @click="toggleLogin">{{ isLoggedIn ? "Logout" : "Login" }}</button></li>
            </ul>
        </div>
    </header>
</template>

<script>
import { computed } from 'vue';

export default {
    name: "HeaderComponent",
    props: ["isLoggedIn"],
    data() {
        return {
            user: {
                name: "Denis",
                surname: "Nazarovs",
                code: "IT21005",
            },
            headerBgColor: "#473d4b",
        };
    },
    computed: {
        full_name() {
            return this.user.name + ' ' + this.user.surname;
        },
    },
    methods: {
        toggleLogin() {
            if (!this.isLoggedIn) {
                confirm("Do you want to log in?");
            } else {
                confirm("Do you want to log out?");
            }
            this.headerBgColor = this.isLoggedIn ? "#473d4b" : "#0C7489";
            this.$emit("update:isLoggedIn", !this.isLoggedIn);
        },
    },
};
</script>



<style scoped>
body {
    margin: 0px;
}

div {
    display: flex;
    align-items: center;
    gap: 1rem;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    margin: none;
    width: 100%;
    /* Set the width to 100% to make it span the entire page */
}

.logo {
    font-size: 24px;
    font-weight: bold;
    color: white;
    /* Adjust the color to match your design */
}

/* Style for the button or other element on the right */
.but {
    background-color: #f1f1f1;
    /* Adjust the background color */
    color: #473d4b;
    /* Adjust the text color */
    padding: 10px 20px;
    /* Adjust padding as needed */
    border: none;
    border-radius: 4px;
    font-weight: bold;
    text-decoration: none;
}

h1 {
    all: none;
    color: white;
    font-family: "Roboto", sans-serif;

}

#circular {
    height: 100px;
    width: 100px;
    background-color: aqua;
    border-radius: 50%;
}

ul,
li {
    display: inline;
    margin-right: 1rem;
    color: white;
    font-family: "Roboto", sans-serif;

}

#full-name {
    color: white;
}

button {
    font-family: "Roboto", sans-serif;
    background-color: #292934;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 50px;
    font-weight: bold;
    text-decoration: none;
}
</style>