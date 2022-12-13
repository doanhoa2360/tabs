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
    padding-left: 50px;
    overflow: auto;
    animation: fadeInFromNone 1s ease-out;
    border: 1px #ccc solid;
   p{
    font-weight: bold;
    font-size: 25px;
    
   }
}

@keyframes fadeInFromNone {
    0% {
        display: none;
        opacity: 0;
    }

    100% {
        display: block;
        opacity: 1;
    }
}

</style>