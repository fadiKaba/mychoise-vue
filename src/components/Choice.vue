<template>
    <div class="col px-1 choice-col">
        <div class="">
            <button 
            :class="['delete-btn', isedit? 'show-x': '']" 
            @click="deleteChoice(choi.id)">
            <img src="../assets/ics/cancel.png" alt="x">
            </button>
            <img :src="getImgurl(choi.src)" :alt="choi.name">
        </div>
    </div> 
</template>

<script>
//:class="['delete-btn', isedit? 'show-x': '']"
//:style="isedit? 'visibility: visible': 'visibility:hidden'"
export default {
    name: 'Choice',
    props:{
        choi: Object,
        elementid: Number,
        itemid: Number,
        isedit: Boolean
    },
    mounted: function(){
       // console.log(this.isedit)
    },
    methods:{
        getImgurl: function(url){
            return require('../assets/imgs/'+url)
        },
        deleteChoice: function(id){
            this.$emit('deletechoice', id);
        }
    },
}
</script>

<style lang="scss" scoped>
    .items{
        position: relative;
        .items-row{
            .col{
                z-index: 2;
                div{
                    text-align: right;
                    .delete-btn{
                        transform: scale(0.5) translate(15px, 20px);
                        background-color:transparent;
                        border: none;
                        visibility: hidden;
                        &.show-x{
                            animation: showx 0.3s forwards;
                        }
                        img{
                            width: 25px;;
                        }
                        }
                    img{
                        width: 100%;
                        border-radius: 50%;
                    }
                }
            }    
        }
    }

    @keyframes showx{
        0%{ 
            visibility: visible;
            transform: scale(0.5) translate(15px, 20vh);
        }
        100%{
            visibility: visible;
            transform: scale(0.5) translate(15px, 20px);
        }

    }

    @media screen and (max-width: 764px) {
        // .choice-max-height{
        //     max-height: 10vh;
        // }
    }
</style>