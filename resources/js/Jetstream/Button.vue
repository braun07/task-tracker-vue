<script>

export default {
        
        name: 'Button',
        components: {
            type: {
                type: String,
                default: 'submit',
            },
        },
        props: {
            text: String,
            color: String,
        }
    }


</script>

<template>
    <button :type="type" :style="{ background: color }" class="btn">
        {{text}}
    </button>
</template>
