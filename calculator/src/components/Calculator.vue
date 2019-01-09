<template>
    <div class="calculator">
        <div class="display">
            <div class="input">
                {{input}}
            </div>
            <div class="output">
                {{output}}
            </div>
        </div>
        <div class="row-1">
            <div class="button" @click="clear">CE</div>
            <div class="button" @click="cancel">&larr;</div>
            <div class="button" @click="enter('%')">%</div>
            <div class="button" @click="enter('/')">/</div>
        </div>
        <div class="row-2">
            <div class="button" @click="enter(7)">7</div>
            <div class="button" @click="enter(8)">8</div>
            <div class="button" @click="enter(9)">9</div>
            <div class="button" @click="enter('*')">*</div>
        </div>
        <div class="row-3">
            <div class="button" @click="enter(4)">4</div>
            <div class="button" @click="enter(5)">5</div>
            <div class="button" @click="enter(6)">6</div>
            <div class="button" @click="enter('-')">-</div>
        </div>
        <div class="row-4">
            <div class="button" @click="enter(1)">1</div>
            <div class="button" @click="enter(2)">2</div>
            <div class="button" @click="enter(3)">3</div>
            <div class="button" @click="enter('+')">+</div>
        </div>
        <div class="row-5">
            <div class="button" @click="enter(0)">0</div>
            <div class="button" @click="enter('.')">.</div>
            <div class="button equal" @click="equal">=</div>
        </div>
    </div>
    
</template>
<script>
export default {
    data() {
        return {
            input: '',
            output:'',
            calculated:false
        }
    },
    methods: {
        clear() {
            this.input=''
            this.output=''
        },
        cancel(){
            //this.input = this.input.slice(0, -1);
            const arr = this.input.split('')
            arr.pop()
            this.input = arr.join('')
        },
        enter(keys){
            if(!this.calculated){
                this.input +=keys
            }
            else{
                this.calculated = false
                this.input=''
                this.output=''
                this.input +=keys                
            }
        },
        equal(){
            if(this.input.includes('%')){
                const arr = this.input.split('')
                const newArr = []
                for(let i=0;i<arr.length;i++){
                    if(arr[i]!='%'){
                        newArr.push(arr[i])
                    }
                    else{
                        newArr.push('/100')
                    }
                }
                this.input = newArr.join('')
                console.log(newArr)
            }
            console.log(this.input)
            this.output = eval(this.input)
            this.calculated = true
        }
    },
    
}
</script>
<style scoped>
.calculator{
    min-width: 320px;
    font-size: 2rem;
    width:35%;
    height:30rem;
    margin:auto;
    margin-top:2rem;
    background-color: #f28080;
    border: 1px solid goldenrod;
    border-radius: 0.5rem;
    -webkit-border-radius: 0.4rem;
    -moz-border-radius: 0.4rem;
    -ms-border-radius: 0.4rem;
    -o-border-radius: 0.4rem;
    -webkit-box-shadow: 1rem 1rem 0.5rem #b55858;
    box-shadow: 0.1rem 0.1rem 0.5rem #b55858;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
}
.display{
    min-width: 300px;
    font-size:1.8rem;
    width:90%;
    height:6rem;
    border:1px solid grey;
    border-radius: 0.5rem;
    background-color: beige;
    margin:1rem auto;
    text-align: right;
}
.row-1,.row-2,.row-3,.row-4,.row-5{
    width:90%;
    height:auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin:auto;
    margin-top:0.5rem;
}
.button{
    width:20%;
    height:3rem;
    background-color: beige;
    border: 1px solid grey;
    -webkit-box-shadow: 0.1rem 0.1rem 0.3rem rgb(85, 65, 65);
    box-shadow: 0.1rem 0.1rem 0.3rem rgb(85, 65, 65);
    transition: all 0.1s;
    -webkit-transition: all 0.1s;
     -webkit-border-radius: 0.5rem;
    -moz-border-radius: 0.5rem;
    -ms-border-radius: 0.5rem;
    -o-border-radius: 0.5rem;
    border-radius: 0.5rem;
    text-align: center;
}
.button.equal{
    width:47%;
}

.button:hover,.button.button.equal:hover{
    color: #f28080;
    -webkit-box-shadow: 0.3rem 0.3rem 0.5rem #b55858;
    box-shadow: 0.3rem 0.3rem 0.5rem #b55858;
}
.button:active,.button.button.equal:active{
    transform: translate(0.05rem,0.05rem);
    -moz-transform: translate(0.05rem,0.05rem);
    -webkit-transform: translate(0.05rem,0.05rem);
}

.input,output{
    min-width: 280px;
    width:100%;
    margin:auto 0;
}
.input{
    color:#b55858;
}
</style>