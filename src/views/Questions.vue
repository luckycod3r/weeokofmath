<template>
    <div class="container">
        <span class="question">{{ $store.state.name }}, {{ questions[currentAnswer]["question"] }}</span>
        <div class="variants">
            <div class="variant" v-for="(variant,k) in questions[currentAnswer]['variants']" :key="variant">
                <input type="checkbox" name="variant" :ref="`${k}_variant`" @input="setAnswer(currentAnswer,k,)" :id="`${k}_variant`">
                <label :for="`${k}_variant`">
                    <span>{{ variant.value }}</span>
                </label>
            </div>
        </div>
        <button v-if="allownext && !isFinal" @click="next">Перейти к следующему вопросу</button>
        <button v-if="allownext && isFinal" @click="results">Результаты</button>
    </div>
</template>
<script>
    let list = require("@/questions/test.json")
    module.exports = {
        name : "questions-view",
        data(){
            return {
                currentAnswer : "1",
                questions : list,
                answers : {},
                allownext: false,
                isFinal : false,
            }
        },
        methods: {
            setAnswer(q,a){
                if(!this.answers[q]){
                    this.answers[q] = []
                }
                if(this.$refs[`${a}_variant`][0].checked){
                    this.answers[q].push(a);
                }
                else{
                    if(this.answers[q].length == 1){
                        this.answers[q] = []    
                    }
                    else{
                        this.answers[q] = this.answers[q].splice(this.answers[q].indexOf(a),1);
                    }
                    
                }
                if(this.answers[q].length > 0) this.allownext = true
                else this.allownext = false
            },
            next(){
                if(this.questions[ ~~this.currentAnswer+ 2] == undefined) {
                    this.isFinal = true;
                }
                this.currentAnswer = ~~this.currentAnswer+ 1;
                this.allownext = false;
                console.log(this.answers)
            },
            results(){
                this.$store.state.answers = this.answers;
                this.$router.push('/results');
            }
        },
        mounted(){
            
        }
    }
</script>
<style scoped>
    .question{
        color: #111;
        display: block;
        font-size: 1.3em;
        margin-top: 1vh;
    }
    .variant{
        
        color: #111;
        margin-top: 10px;
        
    }
    .variant label{
        background: #fff;
        display: block;
        padding: 10px;
        border-radius: 10px;
        transition: .3s linear 0s;
    }
    input[type=checkbox]:checked + label{
        background: yellow;
    }
    input[type=checkbox]{
        display: none;
    }
</style>