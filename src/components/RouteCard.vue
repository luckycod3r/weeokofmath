<template>
    <div class="route-card__elem" @click="$router.push(path)">
        <i :class="`fa-solid fa-${icon}`"></i>
        <span>{{name}}</span>
    </div>
</template>
<script>
export default{
    name: 'route-card',
    props : {
        icon: {
            type : String,
        },
        name : {
            type : String,
        },
        path : {
            type : String
        }
    }
}
</script>
<style lang="css" scoped>
    .route-card__elem{
        --size: 16vh;
        --font: 0.9rem;
        height: var(--size);
        margin: 10px;
        width: calc(var(--size) + 0vw);
        border-radius: 5px;
        background: #fff;
        color: #eb8836;
        display: flex;
        padding: 10px;
        gap: 20px;
        flex-direction: column;
        font-weight: bold;
        text-transform: uppercase;
        align-items: center;
        justify-content: center;
        text-align: center;
    }
    span{
        font-size: var(--font);
    }
    i{
        font-size: 2.7em;
    }
</style>