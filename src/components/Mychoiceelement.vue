<template>
      <div>

            <div class="mychoise-element" 
            :style="'background-image: url(' + getImgurl(element.src)+ ');'" 
            type="button" 
            data-bs-toggle="collapse" 
            :data-bs-target="'#collapse' + element.id" 
            aria-expanded="false" 
            aria-controls="collapseExample">
                <div class="layer">
                    <div class="row h-100 inner-container">
                        <div class="menu row">
                        <span >....</span>
                        </div>                
                        <div class="row time-date align-items-end">
                            <div class="col">Offen biss: 23:00</div>
                            <div class="col">erstellt am 10/6/2021</div>
                        </div> 
                    </div>   
                </div>  
            </div>
 
            <div class="collapse mb-4 mychoice-item-content" :id="'collapse' +element.id">
                <div class="card card-body">

                    <Mychoiceitem 
                    v-for="item in element.items" 
                    :key="item.id" :item="item" 
                    :elmentid="element.id"
                    @deletechoice="deleteChoice($event)"></Mychoiceitem>

                    <div class="up-arrow-container">
                        <button class="up-arrow-btn" data-bs-toggle="collapse" :data-bs-target="'#collapse'+element.id">
                            <img src="../assets/ics/upload.png" alt="">
                        </button>
                    </div>
                </div>
            </div>    

      </div>
</template>

<script>

import Mychoiceitem from './Mychoiseitem.vue';

export default {
    name: 'Mychoiceelement',
    components:{
        Mychoiceitem
    },
    props:{
        element: Object
    },
    data: function(){
        return{
         
        }
    },
    mounted: function(){
    //  console.log(this.element)
    },
    methods:{
        getImgurl: function(url){
           return require('../assets/imgs/'+url)
        },
        deleteChoice: function(obj){
         //  console.log(obj)
            this.$emit('deletechoice', {elementId: this.element.id, itemId: obj.itemId, choiceId: obj.choiceId});
        }
    }
}
</script>

<style lang="scss" scoped>

    .mychoise-element{
        border-radius: 20px;
        height: 20vh;
        padding: 2px 5px;
        background-position: center;
        background-size: cover;
        background-repeat: no-repeat;
        margin-bottom: 15px;
        color: #fff;
        font-size: 13px;
        position: relative;
        .layer{
            background-color: rgba(0, 0, 0, 0.288);
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            border-radius: 20px;
            .inner-container{
                .menu{
                    text-align: right;
                    font-weight: bold;
                }
                .time-date{
                    div:nth-child(1){
                        margin-left: 20px;
                    } 
                    div:nth-child(2){
                        text-align: right;
                    } 
               }
            }
           
        }      
   }

   .card{
       background-color: transparent;
        color:#fff; 
        padding: 0 0 1rem 0;
        min-height: 55vh;
        // position: relative;
            .up-arrow-container{
                text-align: center;
              //  position: sticky;
              margin-top:10vh;
                width: 100%;
                // bottom: 1px;
                // left: 0;
                box-sizing: border-box;
                
                .up-arrow-btn{
                    background-color: transparent;
                    border:none;
                    img{
                        width: 35px;
                    }
                }
          }
   }

</style>