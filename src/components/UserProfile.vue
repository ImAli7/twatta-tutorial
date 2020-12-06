<template>
    <div class="user-profile">
        <div class="user-profile__user-panel">
            <h1 class="user-profile__username">@{{ user.username }}</h1>
            <div class="user-profile__follower-count">
                <strong>Followers: </strong> {{ followers }}
            </div>
            <button class="btn btn-info mt-4" @click="followUser">Follow</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "UserProfile",
    data() {
        return {
            followers: 0,
            user: {
                id: 1,
                username: "ar_ielz",
                firstName: "Alireza",
                lastName: "Far",
                email: "aariow01@gmail.com",
                isAdmin: true
            }
        }
    },
    watch: {
        followers(newFollowerCount, oldFollowerCount) {
            if (oldFollowerCount < newFollowerCount) {
                console.log(`${this.user.username} has gained a follower`);
            }
        }
    },
    computed: {
        fullName() {
            return `${this.user.firstName} ${this.user.lastName}`;
        }
    },
    methods: {
        followUser() {
            this.followers++;
        }
    },
    mounted() {
        console.warn("Component mounted");
    },
    unmounted() {
        console.warn("Component unmounted");
    }
}
</script>

<style scoped>

</style>