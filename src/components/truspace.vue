<template>
  
  <v-app>
<div class="parent">
       <v-app-bar  dark>
            <v-toolbar-title>
              <div class="display-1 green--text">
                  SAS.site
              </div>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn
            class="hidden-xs-only"
             text v-for="nav in navs" :key="nav.name" >
                <span class="green--text">{{nav.name}}</span>
            </v-btn>
            <v-spacer></v-spacer>
            <v-app-bar-nav-icon color="green" class="hidden-sm-and-up" @click="dialog=true"></v-app-bar-nav-icon>
          </v-app-bar>
           <v-navigation-drawer dark app v-model="dialog">
              <v-container class="green--text ">
                 <v-row>
                   <v-col >    <v-btn large fab
                    text @click="dialog=false" ><span class="headline green--text">x</span></v-btn>
                  </v-col>
                 </v-row>
               </v-container>
             <v-list class="pt-0 my-16">
               <v-list-item @click="dialog=!dialog" color="green"  href="" v-for="nav in navs" :key="nav.name">
                 <v-list-item-content>
                   <div class="green--text ">{{nav.name}}</div>
                 </v-list-item-content>
               </v-list-item>
             </v-list>
           </v-navigation-drawer>
          <v-carousel
              cycle
              height="80vh"
              hide-delimiter-background
              show-arrows-on-hover
            >

              <v-carousel-item 
               v-for="(item,i) in items" :src="item.src"
      :key="i"
      
      gradient="to right, rgba(0,0,0,.6), rgba(0,0,0,.6)"
              >
              
            
              </v-carousel-item>
            </v-carousel>
            <div class="gsap  text-uppercase hidden-sm-and-down">
                <div class="head green--text">
                    we offer you! 
                </div>
                <div class="white--text">
                  <span class="text"></span> 
                  <span class="cursor">|</span>  
                </div>
            </div>
            <div class="gsap2  text-uppercase hidden-md-and-up ">
                <div class="head2 green--text hidden-xs-only">
                    we offer you! 
                </div>
                <div class="head3 green--text hidden-sm-and-up">
                    we offer you! 
                </div>
                <div class="white--text hidden-xs-only">
                  <span class=" text text2"></span> 
                  <span class="cursor2">|</span>  
                </div>
                <div class="white--text small hidden-sm-and-up">
                  <span class=" text text2"></span> 
                  <span class="cursor2">|</span>  
                </div>
             </div>
            
              <v-footer
                dark
              >
              <v-container>
              <v-row class="text-center">
                <v-col>
                  <span class="green--text power">PoweredBy </span>
                  <span class="space grey--text text--lighten-1">| </span>
                  <span class="grey--text text--lighten-1">Facebook,</span>
                  <span class="grey--text text--lighten-1"> Twitter,</span>
                  <span class="grey--text text--lighten-1"> Instagram</span>
                </v-col>
              </v-row>
              <v-row class="text-center"> 
                <v-col class="grey--text text--lighten-1 caption">
                  Copyrite © By SAS 2020
                </v-col>
              </v-row>
              </v-container>
              </v-footer>
            
            
            
  </div>
  </v-app>
  
</template>

<script>
import { gsap } from "gsap";
import { TextPlugin } from "gsap/TextPlugin";

gsap.registerPlugin(TextPlugin);
export default {
    data:()=>({
         text:['Co-Working','&','Private Offices'],
        navs:[
            {name:"home"},
            {name:"about"},
            {name:"contact"}
        ],
        dialog:false,
        items:[{transition:'scroll-y-transition',src:require('@/assets/home-office (1).jpg')},
               {transition:'scroll-x-transition',src:require('@/assets/laptops.jpg')},
               {transition:'fade-transition',src:require('@/assets/office (1).jpg')},
               {transition:'scroll-x-reverse-transition',src:require('@/assets/urban (1) (1).jpg')}]
    }),
    mounted(){
      const words = this.text
        gsap.to('.cursor',{opacity:0,duration:0.5,ease:'power(3)',repeat:-1})
        gsap.to('.cursor2',{opacity:0,duration:0.5,ease:'power(3)',repeat:-1})
        let mt = gsap.timeline({repeat:-1,repeatDelay:1})
        words.forEach(word => {
          let tl = gsap.timeline({repeat:1,yoyo:true,})
          tl.to(".text",{duration:1,text:word,})
          mt.add(tl)
          
        });

    }

}
</script>

<style scoped>
div.parent{
    position: relative;
}
div.gsap{
    position: absolute;
    left: 25%;
    top: 35%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    
}
div.gsap2{
    position: absolute;
    left: 25%;
    top: 35%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    
}
div.gsap .head{
font-family: montserrat;
    font-weight: bold;
    font-size: 5em;
}
div.gsap2 .head2{
font-family: montserrat;
    font-weight: bold;
    font-size: 3em;
}
div.gsap2 .head3{
font-family: montserrat;
    font-weight: bold;
    font-size: 2em;
    position: absolute;
    left: -2em;
    width: 200px;
}
.cursor, .text{
  font-size: 2em;
}
.cursor2, .text2{
  font-size: 1em;
}
.small{
  position: relative;
  left: 2em;
  top: 1.5em;
}
span.power{
  font-family: montserrat;
  font-weight:bold;
}
.space{
  font-size: 1.5em;
  font-weight: lighter;
}


</style>