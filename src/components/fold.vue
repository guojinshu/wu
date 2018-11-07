<template>
    <div class="wrap">
        <div class="head" @click='showClick'>
            <h2>你猜</h2>
            <ul class="list" v-show="fold.isShow">
                <li>1</li>
                <li>2</li>
                <li>3</li>
            </ul>
        </div>
        
    </div>
</template>
<script>
export default {
    props:{
        fold:{
            type:Object,
            default(){
                return {
                    isShow:false
                }
            }
        }
    },
    watch:{
        isShow:(a,b)=>{
            console.log(a,b)
        }
    },
    methods:{
        showClick(){
            this.fold.isShow = !this.fold.isShow;
            this.$emit('showClick',this.fold.isShow);//借口
        }
    }
}
</script>
<style>
    /* .head{
        width:100px;
        height:100px;
        background:red;
    } */
</style>
