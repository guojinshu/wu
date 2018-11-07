<script>
export default {
    methods:{
        headClick(){
            this.collipse.isShow = !this.collipse.isShow;
            this.$emit('handleCollipse',this.collipse.isShow);
        }
    },
    props:{
        collipse:{
            type:Object,
            default(){
                return {
                    isShow:false
                }
            }
        }
    }
}
</script>
<template>
    <div class="collipse-wrap">
        <div class="collipse-head dragbox" @click="headClick">
            <slot name="head"></slot>
        </div>
        <div class="collipse-body dragbox" v-show="collipse.isShow">
            <slot></slot>
        </div>
    </div>
</template>
<style scoped>
.dragbox{
        width:100px;height:100px;background:red;cursor:pointer;
    }
</style>


