<template>
    <div class="card" @before-enter="beforeEnter" @enter="enter" appear>
        <p class="title">{{title}}</p>
        <p class="text">{{text}}</p>
        <img :src="require(`@/assets/${icon}`)" alt="">
    </div>
</template>

<script>
export default {
    props: ['title', 'icon', 'text', 'borderColor'] 
}
</script>

<style>
    .card {
        position: relative;
        max-width: 350px;
        height: 250px;
        background: #FFF;
        box-shadow: 0px 5px 15px rgba(163, 165, 174, 0.541);
        padding: 2rem;
        border-radius: 10px;
        border-top: 5px solid v-bind(borderColor);
    }
    .title {
        font-weight: 600;
        font-size: 1.2rem;
        margin-bottom: 0.5rem;
        color: #4c4e61;
    }
    .text {
        font-weight: 400;
        color:#a3a5ae;
        font-size: 0.9rem;
    }
    .card img {
        position: absolute;
        bottom: 2rem;
        right: 2rem;
    }
</style>