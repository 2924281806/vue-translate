<template>
    <div class="translateForm row">
      <div class="col-md-6 col-md-offset-3">
        <form id="transForm"v-on:submit="formSubmit" class="well form-inline">
          <input class="form-control" type="text" placeholder="输入需要翻译的内容" v-model="textToTranslate">
          <select class="form-control" v-model="language">
            <option value="en">English</option>
            <option value="ru">Russian</option>
            <option value="ko">Korean</option>
            <option value="js">Janpenese</option>
          </select>
          <input class="btn btn-primary" type="submit" value="翻译">
        </form>
      </div>

    </div>
</template>

<script>
    export default {
        name: 'translateForm',
        data(){
          return{
              textToTranslate:"",
              language:""
          }
        },
        methods:{
          formSubmit(e) {
            this.$emit("submitForm",this.textToTranslate,this.language)   //事件注册的方法
            e.preventDefault()    //取消默认事件
          }
        },
      created(){
            this.language = 'en'
      }
    }
</script>

<style scoped>
  #transForm{
    border-radius: 10px;
    border:1px solid #ccc;
  }
</style>
