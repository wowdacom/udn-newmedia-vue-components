<template>
	<div class="section pageIntro" :style="{backgroundImage: 'url('+ srcRWD(bg, bgWeb) +')', backgroundColor: bgColor}">
        <div class="glass"></div>
        <div class="container content" :style="{color: fontColor}">
            <slot></slot>
            <h6>{{update}}</h6>
            <Share :href='href'></Share>
        </div>            
        <PageArrow :color='arrowColor' :hint='hint' :hintColor='hintColor'/>  
	</div>
</template>

<script>
import PageArrow from './pageArrow.vue'
import Share from './Share.vue'
import srcRWD from '../mixin/srcRWD.js'

export default {
  name: 'PageIntro',
  components: {
    PageArrow,
    Share
  },
  mixins: [srcRWD],
  props: ['arrowColor', 'bg', 'bgWeb', 'bgColor', 'fontColor', 'hint', 'hintColor', 'href', 'update'],
  data () {
    return {

    }
  },
  created() {
    window.addEventListener('resize', () => {
        this.$forceUpdate()
    })       
  }
}
</script>
<style lang="scss" scoped>
h2{
    text-align: left;
    font-size: 25px;
    font-weight: bold;
    line-height: 1.5;
    margin: 0;
}
.container{
    position: relative;
    z-index: 1;
}
.chart-title{
    font-size: 28px;
}
p{
    font-size: 16px;
    margin: 0;
}
.img-say{
    font-size: 17px;
    color: gray;
    margin-top: 5px;
}
h6{
	font-size: 16px;
}
.glass{
    position: absolute;
    top: 0;
    left: 0;
    z-index: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(black, 0.7);
}
@media screen and (max-width: 767px){
    h2{
        font-size: 25px;
    }
    p{
        font-size: 16px;
        line-height: 32px;
    }
    h6{
    	font-size: 13px;
    }
}
@media screen and (min-width: 768px) and (max-width: 1023px){
    .container{
        width: 100%;
    }
    h2{
        font-size: 25px;
    }
    p{
        font-size: 16px;
        line-height: 32px;
    }
    h6{
    	font-size: 13px;
    }
}
@media screen and (min-width: 1024px){
    .container{
        width: 880px;
    }
    p{
        font-size: 18px;
    }
    p>br{
        line-height: 36px;
    }
}
</style>