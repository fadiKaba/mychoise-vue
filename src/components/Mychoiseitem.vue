<template>
    <div class="items-container">
        <div class="row items-container-row">
            <div :style="isEdit? 'visibility:visible': 'visibility:hidden'" class="col-2"><button><img src="../assets/ics/return.png" alt=""></button></div>
            <div class="col-8">
                <span>Erstell am 01.072021</span> 
            </div>
            <div class="col-2">
                <span class="bold" id="items-collapse1id-itemsid" @click="editItem('edit-view'+elementid+item.id)">....</span>
            </div>
        </div>
        <div class="items">
        <div class="row items-row px-5">
           <Choice 
           v-for="choi in item.choices" 
           :key="choi.id" :choi="choi" 
           :itemid="item.id" 
           :elementid="elementid"
           :isedit="isE"
           @deletechoice="deleteChoice($event)"></Choice>
        </div>  
        </div> 
        <div :id="'edit-view'+elementid+item.id" :class="['edit-view', isEdit?'height':'']">
            <span v-if="isEdit">Erstell am 01.072021</span> 
        </div>
    </div>
</template>

<script>

import Choice from './Choice.vue';

export default {
    name: 'Mychoiseitem',
    components:{
        Choice
    },
    props:{
        item: Object,
        elementid: Number,
    },
    data: function(){
        return{
            isEdit:false,
        }
    },
    mounted: function(){

    },
    methods:{
       editItem: function(id){
           
        document.querySelectorAll('.edit-view').forEach(el =>{
            el.classList.remove('height');
        })
        this.isEdit = !this.isEdit;
        //    document.querySelector('#'+id).classList.add('height');
       },
       deleteChoice: function(id){
           this.$emit('deletechoice', {'itemId': this.item.id, 'choiceId': id});
       }
    },
    computed:{
        isE: function(){
            return this.isEdit;
        }
    }
}
</script>

<style lang="scss" scoped>
  
    .items-container{
        position: relative;
        padding-bottom: 2vh;
        // background-color: #fff;
        .items-container-row{
            div:nth-child(1){
                z-index: 2;
                button{
                    background-color: transparent;
                    border: none;
                    img{
                    width: 17px;
                    } 
                }  
            }
            div:nth-child(2){
                font-size: 12px;
                text-align: center;
                span{
                    display: inline-block;
                    margin-top: 5px;
                    padding: 0px 5px;
                    border-radius: 5px;  
                }    
            }
            div:nth-child(3){
                z-index: 2;
                span{
                    cursor: pointer;
                    display: inline-block;
                    transform: translateY(-5px);
                    
                }
            }
        }
        .edit-view{
            bottom:0;
            left: 0;
            position: absolute;
            background-color: rgba(255, 255, 255, 0.178);
            height: 0%;
            width: 100%;
            z-index: 0;
            transition: 0.3s;
            text-align: center;
            &.height{
                height: 100%;
            }
            span{
                font-size: 12px;
                background-color: rgb(90, 90, 90); 
                padding: 0px 5px;
                border-radius: 5px; 
            }
        }
        
    }


</style>