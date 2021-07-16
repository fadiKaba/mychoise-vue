<template>
    <div id="mychoise-container" class="container p-4">
      
      <Mychoiceelement 
      v-for="element in data" 
      :key="element.id" 
      :element="element"
      @deletechoice="deleteChoice($event)">
      </Mychoiceelement>
 
    </div>
</template>

<script>

import Mychoiceelement from './Mychoiceelement.vue';

export default {
    name: 'Mychoicecontainer',
    components:{
        Mychoiceelement
    },
    data: function(){
        return{
             data: [
                {   
                    id: 1, 
                    erstellt_am: '10/2/2020', 
                    Offen_biss: '23:00',
                    src: 'main_food.jpg',
                    items: [
                        {
                            id: 1,
                            choices:[
                            {id: 1, name: 'Pizza', src: 'food.jpg'},
                            {id: 2, name: 'Hamburger', src: 'eggs.jpg'},
                            {id: 3, name: 'Cheese', src: 'pizza.jpg'} 
                            ]
                        },
                        {
                            id: 2,
                            choices:[
                            {id: 4, name: 'Pizza', src: 'food.jpg'},
                            {id: 5, name: 'Hamburger', src: 'eggs.jpg'},
                            {id: 6, name: 'Cheese', src: 'pizza.jpg'} 
                            ]
                        },
                        
                    ],
                },
                {   
                    id: 2, 
                    date: '9/4/2021', 
                    time: '23:00',
                    src: 'main_food.jpg',
                    items: [
                        {
                            id: 3,
                            choices:[
                            {id: 7, name: 'Pizza', src: 'pizza.jpg'},
                            {id: 8, name: 'Hamburger', src: 'eggs.jpg'},
                            {id: 9, name: 'Cheese', src: 'food.jpg'} 
                            ]
                        },
                        {
                            id: 4,
                            choices:[
                            {id: 10, name: 'Pizza', src: 'food.jpg'},
                            {id: 11, name: 'Hamburger', src: 'eggs.jpg'},
                            {id: 12, name: 'Cheese', src: 'pizza.jpg'} 
                            ]
                        }, 
                    ],
                },
            ],
            deleteTry1: '',
            deleteTry2: '',
        }
    },
    methods:{
        deleteChoice: function(obj){
        console.log(obj.itemId)
         let dataIndex = this.data.findIndex( x => x.id == obj.elementId);
         let itemIndex = this.data[dataIndex].items.findIndex(x => x.id == obj.itemId);
         let choiceId = this.data[dataIndex].items[itemIndex].choices.findIndex(x => x.id == obj.choiceId);
         this.data[dataIndex].items[itemIndex].choices.splice(choiceId, 1);
         console.log(choiceId)
        }
    }
}
</script>

<style lang="sass" scoped>

@import '../scss/main.scss';


</style>