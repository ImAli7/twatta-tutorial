<template>
    <div class="user-profile container d-flex">
        <div class="user-profile__user-panel col-3">
            <h1 class="user-profile__username">
                @{{ user.username }}
                <span :class="user.isOnline ? 'user-profile__online-badge' : 'user-profile__offline-badge'"></span>
            </h1>
            <div class="user-profile__follower-count">
                <strong>Followers: </strong> {{ followers }}
            </div>
            <form class="user-profile__create-twoot" @submit.prevent="createNewTwoot" :class="{ '--exceeded': newTwootCharacterCount > 20 }">
                <div class="form-group">
                    <label for="newTwoot"><strong>New Twoot:</strong> ({{ newTwootCharacterCount }}/20) </label>
                    <textarea id="newTwoot" rows="4" class="form-control" v-model="newTwootContent" />
                </div>

                <div class="user-profile__create-twoot-type form-group">
                    <label for="newTwootType"><strong>Type: </strong></label>
                    <select for="newTwootType" v-model="selectedTwootType" class="form-control">
                        <option v-for="option in twootTypes" :key="option" :value="option.value">
                            {{ option.name }}
                        </option>
                    </select>
                </div>

                <button class="btn btn-success">Twoot !</button>
            </form>
        </div>
        <div class="user-profile__twoots-wrapper col-8">
            <TwootItem
                v-for="twoot in user.twoots" 
                :key="twoot.id" 
                :username="user.username" 
                :twoot="twoot" 
                @favorite="toggleFavorite"
            />
        </div>
    </div>
</template>

<script>
import TwootItem from "./TwootItem";

export default {
    name: "UserProfile",
    components: { TwootItem },
    data() {
        return {
            newTwootContent: "",
            selectedTwootType: "instant",
            twootTypes: [
                { value: "draft", name: "Draft" },
                { value: "instant", name: "Instant Twoot" }
            ],
            followers: 0,
            user: {
                id: 1,
                username: "ar_ielz",
                firstName: "Alireza",
                lastName: "Far",
                email: "aariow01@gmail.com",
                isAdmin: true,
                isOnline: true,
                twoots: [
                    { id: 1, content: "Vue.js is amazing"},
                    { id: 2, content: "Subscribe here"},
                    { id: 3, content: "I'm using Ubuntu"},
                    { id: 4, content: "Hi there"}
                ]
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
        },
        newTwootCharacterCount() {
            return this.newTwootContent.length;
        },
        getUserIsAdmin() {
            return this.user.isAdmin;
        }
    },
    methods: {
        followUser() {
            this.followers++;
        },
        toggleFavorite(id) {
            console.log(`Favorited Tweet #${id}`);
        },
        createNewTwoot() {
            if(this.newTwootContent && this.selectedTwootType !== 'draft') {
                this.user.twoots.unshift({
                    id: this.user.twoots.length + 1,
                    content: this.newTwootContent
                });
                this.newTwootContent = '';
            }
        }
    },
    mounted() {
        console.log("Component mounted");
    },
    unmounted() {
        console.log("Component unmounted");
    }
}
</script>

<style lang="scss" scoped>
.user-profile {
    .user-profile__admin-badge {
        background-color: red;
        width: 50px;
        height: 25px;
    }
    .user-profile__online-badge {
        background-color: #28a745;
        border-radius: 50%;
        width: 15px;
        height: 15px;
        position: relative;
        top: 20px;
        left: 25px;
    }
    .user-profile__offline-badge {
        background-color: #9ca79e;
        border-radius: 50%;
        width: 15px;
        height: 15px;
        position: relative;
        top: 20px;
        left: 25px;
    }
    .user-profile__user-panel {
        display: flex;
        flex-direction: column;
        margin-right: 50px;
        padding: 20px;
        background-color: #fff;
        border-radius: 5px;
        border: 1px solid #dfe3e8;
    }
    .user-profile__follower-count {
        font-size: 16px;
        margin-top: 15px;
    }
    h1 {
        display: flex;
        margin: 0;
    }
    .user-profile__create-twoot {
        display: flex;
        flex-direction: column;
        margin-top: 20px;

        &.--exceeded {
            color: red;
            border-color: red;
        }
    }
}
</style>