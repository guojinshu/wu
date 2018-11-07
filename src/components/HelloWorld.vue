<template>
  <div :style="{left:pos.left+'px',top:pos.top+'px'}" class="hello" @mousedown="this.mousedown">
   
  </div>
</template>

<script>
//事件
// 元素上事件触发
// 1冒泡：从内向外，
// 2捕获：从外向内
function mousemove(ev){
  let x=ev.clientX-this.mx;
  let y=ev.clientY-this.my;
  //console.log(ev.clientX,this.mx)
  if(x<0){//最小移动距离
    x=0;
  }
  if(y<0){
    y=0;
  }
  console.log(ev.target.offsetWidth)//盒子的宽
  console.log(document.documentElement.clientWidth-ev.target.offsetWidth)//最大移动距离=视口宽减去盒子宽
  if(x>document.documentElement.clientWidth-ev.target.offsetWidth){
    x=document.documentElement.clientWidth-ev.target.offsetWidth
  }
  if(y>document.documentElement.clientHeight-ev.target.offsetHeight){
    y=document.documentElement.clientHeight-ev.target.offsetHeight
  }
  this.pos.left=x;
  this.pos.top=y;
}
function mouseup(){
     document.removeEventListener('mousemove',this.bindMove,false);
     document.removeEventListener('mouseup',this.bindUp,false);
}
export default {
  name: 'HelloWorld',
  created() {
    this.bindMove=mousemove.bind(this)
    this.bindUp=mouseup.bind(this)
  },
  data(){
        return {
            pos:this.positionReceive
            
        }
    },
    props:{
      positionReceive:{
          type:Object,
          default:function(){
              return {left:0,top:0}
          }
      }
  },
  methods:{
    mousedown(ev) {
      this.mx=ev.offsetX;
      this.my=ev.offsetY;
      // let my=ev.clientY;
      document.addEventListener('mousemove',this.bindMove,false)
      document.addEventListener('mouseup',this.bindUp,false)
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello{
  width:100px;
  height:100px;
  background:yellow;
  position: absolute;
  top:0;
  left:0;
}
</style>
