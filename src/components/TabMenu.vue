<template>
    <div class="tab-content" v-show="title == selectTitle">
       <p> {{title}}</p>
        <slot/>
    </div>
</template>
<script>
import {inject} from 'vue'
export default {
    props:['title'],
    setup() {
        const selectTitle=inject("selectTitle")

        return{
            selectTitle
        }
        
    },
}
</script>
<style lang="scss" scoped>
.tab-content{
    overflow: auto;
    animation: fadeInFromNone 1s ease-out;
   p{
    font-weight: bold;
    
   }
}

@keyframes fadeInFromNone {
    0% {
        display: none;
        opacity: 0;
    }
    
    50% {
        display: block;
        opacity: 0.5;
    }

    100% {
        display: block;
        opacity: 1;
    }
}

</style>