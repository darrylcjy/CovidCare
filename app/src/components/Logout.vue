<template>
  <button id="btn" @click="signOut()">Logout</button>
</template>

<script>
import {getAuth, onAuthStateChanged, signOut} from "firebase/auth"

export default {
    name: 'Logout',

    data() {
        return {
            user: false,
        }
    },

    mounted() {
        const auth = getAuth();
        onAuthStateChanged(auth,(user) => {
            if (user) {
                this.user = user
            }
        })
    },

    methods: {
        signOut() {
            const auth = getAuth()
            const user = auth.currentUser
            signOut(auth, user)
            this.$router.push({name:'Home'})

        }
    }
}

</script>

<style>

</style>