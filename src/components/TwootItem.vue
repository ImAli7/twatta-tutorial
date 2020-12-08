<template>
    <div class="twoot-item" @click="favoriteTwoot(twoot.id)">
        <div class="user-profile__twoot">
            <div class="twoot-item__user">
                @{{ username }}
            </div>
            <div class="twoot-item__content">
                {{ twoot.content }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "TwootItem",
    props: {
        username: {
            type: String,
            required: true
        },
        twoot: {
            type: Object,
            required: true
        }
    },
    methods: {
        favoriteTwoot(id) {
            this.$emit('favorite', id);
        }
    }
};
</script>

<style lang="scss" scoped>
.twoot-item {
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #dfe3e8;
    box-sizing: border-box;
    cursor: pointer;
    transition: all .25s ease;
    margin-bottom: 5px;

    &:hover {
        transform: scale(1.01, 1.01);
        box-shadow: 0 0 12px 1px rgba(0, 0, 0, 0.1);
    }

    .twoot-item__user {
        font-weight: bold;
    }
}
</style>