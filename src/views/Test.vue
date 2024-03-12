<template>
    <div class="container">
        <h1>Тест на знание контента</h1>
        <input type="text" ref="name" @input="check" placeholder="Ваше имя">
        <button @click="start" v-if="allow">Начать тест</button>
    </div>
</template>
<script>
export default{
    name: "test-view",
    mounted(){

    },
    methods:{
        check(){
            if(this.$refs.name.value.length > 1){
                this.allow = true;
            }
            else{
                this.allow = false;
            }
        },
        start(){
            this.$store.state.name = this.$refs.name.value;
            this.$router.push('/test/start');
        }
    },
    data(){
        return {
            allow : false
        }
    }
}
</script>
<style lang="sss" scoped>

</style>
