<script>

export default {
        
        name: 'Button',
        props: {
            text: String,
            color: String,
        },
        methods: {
            onClick() {
                this.$emit('toggle-add-task')
            },
        },
    }


</script>

<template>
    <button @click="onClick()" :style="{ background: color }" class="btn">
        {{ text }}
    </button>
</template>

<style scoped>

.btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
}

</style>