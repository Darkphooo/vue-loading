<template>
  <div class="loading">
    <div class="box">
      <div class="left">
        <img class="pic-left" :src="imgSrc" />
        <div class="mask-left"></div>
      </div>
      <div class="right">
        <img class="pic-right" :src="imgSrc" />
        <div class="mask-right"></div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'loading',
  props: ['imgSrc', 'bgSrc'],
  data () {
    return {
    }
  },
  mounted: function () {
    var style = document.createElement('style')
    document.head.appendChild(style)
    var sheet = style.sheet
    sheet.addRule('.mask-left::before', 'background: url("' + this.bgSrc + '")')
    sheet.insertRule('.mask-left::before { background: url("' + this.bgSrc + '")}', 0)
    sheet.addRule('.mask-right::before', 'background: url("' + this.bgSrc + '")')
    sheet.insertRule('.mask-right::before { background: url("' + this.bgSrc + '")}', 0)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box {
  position: absolute;
  left: calc(50% - 100px);
  top: calc(50% - 100px);
  height: 200px;
  width: 200px;
  border-radius: 100px;
  text-align: center;
}
.left {
  position: absolute;
  left: 0;
  top: 0;
  height: 200px;
  width: 100px;
  overflow: hidden;
}
.right {
  position: absolute;
  right: 0;
  top: 0;
  height: 200px;
  width: 100px;
  overflow: hidden;
}
.pic-left {
  position: absolute;
  left: 0;
  top: 0;
  height: 200px;
  width: 200px;
  border-radius: 100px;
  border: none;
  z-index: 1;
  clip: rect(0px,100px,200px,0px);
}
.pic-right {
  position: absolute;
  left: -100px;
  top: 0;
  height: 200px;
  width: 200px;
  border-radius: 100px;
  border: none;
  z-index: 1;
  clip: rect(0px,200px,200px,100px);
}
@keyframes rotate-left{
0%   {transform: rotate(0deg);}
25%  {transform: rotate(0deg);}
50%  {transform: rotate(180deg);}
75%  {transform: rotate(180deg);}
100% {transform: rotate(360deg);}
}
@keyframes rotate-right{
0%   {transform: rotate(0deg);}
25%  {transform: rotate(180deg);}
50%  {transform: rotate(180deg);}
75%  {transform: rotate(360deg);}
100% {transform: rotate(360deg);}
}
@keyframes bg-rotate-left{
0%   {transform: rotate(0deg);}
25%  {transform: rotate(0deg);}
50%  {transform: rotate(-180deg);}
75%  {transform: rotate(-180deg);}
100% {transform: rotate(-360deg);}
}
@keyframes bg-rotate-right{
0%   {transform: rotate(0deg);}
25%  {transform: rotate(-180deg);}
50%  {transform: rotate(-180deg);}
75%  {transform: rotate(-360deg);}
100% {transform: rotate(-360deg);}
}
.mask-left {
  animation: rotate-left 5s linear infinite;
  position: absolute;
  left: -25px;
  top: -25px;
  height: 250px;
  width: 250px;
  border-radius: 125px;
  clip: rect(0px,250px,250px,125px);
  z-index: 2
}
.mask-left::before {
  content: "";
  display: block;
  width: 250px;
  height: 250px;
  border-radius: 125px;
  animation: bg-rotate-left 5s linear infinite;
  background-attachment: fixed;
  background-origin: padding-box;
  background-clip: content-box;
  z-index: 3;
}
.mask-right {
  animation: rotate-right 5s linear infinite;
  position: absolute;
  left: -130px;
  top: -25px;
  height: 250px;
  width: 250px;
  border-radius: 125px;
  clip: rect(0px,125px,250px,0px);
  z-index: 2;
}
.mask-right::before {
  content: "";
  display: block;
  width: 250px;
  height: 250px;
  border-radius: 125px;
  animation: bg-rotate-right 5s linear infinite;
  background-attachment: fixed;
  background-origin: padding-box;
  background-clip: content-box;
  z-index: 3;
}
</style>
