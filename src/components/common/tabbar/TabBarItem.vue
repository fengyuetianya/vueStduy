<template>
    <div class="tab-bar-item" @click="itemClick">
        <!-- slot要被替换，所有要用div封装 -->
        <div v-if= "!isActive">
            <slot  name="item-icon"></slot>
        </div>
        <div v-else>
            <slot  name="item-icon-active"></slot>
        </div>        
        <div :style="activeStyle">
            <slot  name="item-text"></slot>
        </div>
        
    </div>
</template>

<script>
export default {
    name: 'TabBarItem',
    props: {
        path: String,
        activeColor:{
            type: String,
            default:'red'
        }
    },
    data(){
        return {
            //isActive: true
        }
    },
    computed:{
        isActive() {
            //判断路径里面有没有这个PATH,!==  -1 代表找到
            return this.$route.path.indexOf(this.path) !== -1
        },
        activeStyle(){
            //如果活跃，则赋值，否则为空
            return this.isActive ? {color:this.activeColor} : ''
        }
    },
    methods: {
        itemClick(){
            this.$router.replace(this.path)
        }
    }
}
</script>

<style  scoped>
    .tab-bar-item {
        flex: 1;
        text-align: center;
        height: 49px;
        font-size: 14px;
    }

    .tab-bar-item img{
        width: 24px;
        height: 24px;
        margin-top: 3px;
        vertical-align: middle;
    }
</style>
