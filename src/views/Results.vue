<template>
    <div class="container">
        <div class="result" v-for="(result,k) of results" :key="k">
            {{ k}} - {{ (result) ? 'Правильно' : 'Неверно' }}
        </div>
        <span>Всего: {{ rights }}/{{ Object.keys(questions).length }}</span>
    </div>
</template>
<style scoped>

</style>
<script>
let list = require("@/questions/test.json")
export default {
    name : "results-view",
    data(){
        return {
            questions : list,
            results : [],
            rights: 0
        }
    },
    methods:{
        validateAnswers(questions, answers) {
            const results = {};

            // Перебираем вопросы
            for (const questionNumber in questions) {
                const selectedOptions = answers[questionNumber];
                const correctOptions = questions[questionNumber].variants;
                const correctOptionsKeys = Object.keys(correctOptions);
                const isValid = correctOptionsKeys.every(key => {
                    const correctOption = correctOptions[key];
                    const isSelected = selectedOptions.includes(key);
                    if (correctOption.valid && !isSelected) {
                        return false;
                    } else if (!correctOption.valid && isSelected) {
                        return false;
                    }
                    return true;
                });
                if(isValid) this.rights += 1;
                results[questionNumber] = isValid;
    }

    return results;
    }
    },
    mounted(){
        let answers = this.$store.state.answers;
        this.results = this.validateAnswers(list,answers);
    }
}
</script>
<style scoped>
.container{
    font-size: 1.4em;
}
span{
    font-size: 1.45em;
}
</style>