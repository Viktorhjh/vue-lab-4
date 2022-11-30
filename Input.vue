
<template>
        <slot class="slotClass"> </slot>
        <input v-model="this.content" :class="userInputClass"/>       
        <button @click="clear()"    class="user-button">Clear</button>            
</template>

<script>
export default {
    emits:['change', 'error'],
    props:{
        isNumber: Number,
        minCountCharackters: Number,
        minVal: Number       
    },
    name: 'Input',      
    data(){
        return{
            content: '',
            userInputClass: 'user-input'
        };
    },
    methods: {
        clear(){                        
            this.content = '';
        },
        numberCheck(){
            if(this.isNumber == 0 && !isNaN(this.content)){                                
                return false
            }
            
            if(this.isNumber == 1 && isNaN(this.content)){
                return false
            }
            else
                return true
        },

        minCountCharacktersCheck(){
            if(this.content.length != this.minCountCharackters)
                return false
            else
                return true
        },

        diapasonCheck(){
            if(this.isNumber == 1 && parseInt(this.content) <= this.minVal)
                return false
            else
                return true
        }

    },
    watch: {
        content(){
            this.$emit('change', this.content)
            console.log(this.userInputClass)      
            if(this.numberCheck())
                this.userInputClass = 'user-input'              
            else{
                this.userInputClass = 'user-input-error'
                this.$emit('error', 'Wrong charackters!')                              
            }

            if(this.minCountCharacktersCheck())
                this.userInputClass = 'user-input'              
            else{
                this.userInputClass = 'user-input-error'                                                                          
            }

            if(this.diapasonCheck())
               this.userInputClass = 'user-input'              
            else{
                this.userInputClass = 'user-input-error'                                                                          
                this.$emit('error', 'Out of range!')
            }
        }
    }
    
}
</script>

<style scoped>
    .user-button, .user-input, .user-input-error, .slotClass{
        font-size: 120%;
    }

    .user-button{
        padding: 4px;
        margin: 10px;
        background-color: transparent;
        border-color: white;
        border-width: 1px;
        border-radius: 2px;
        color: rgb(173, 173, 173);
    }

    .user-input, .user-input-error{
        margin-left: 20px;                      
        outline: none;
        border: none;
    }

    .user-input{           
        /* border-bottom-color: ;         */
        border-bottom: solid 3px transparent;
    }

    .user-input-error{                
        /* border-bottom-color: */
         border-bottom: solid 3px rgb(255, 80, 80)
    }
</style>