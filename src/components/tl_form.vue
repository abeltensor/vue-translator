<template>
  <div id="tl_form" class="row">
    <div class="col-md-6 col-md-offset-3">

    </div>
    <form id="form-t" class="form-inline well" v-on:submit="formSubmit">
      <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter words" >
      <select class="form-control" v-model="lang">
        <option value="ru">Russian</option>
        <option value="fr">French</option>
        <option value="es">Spanish</option>
        <option value="zh">Chinese</option>
        <option value="ja">Japanese</option>
        <option value="el">Greek</option>
      </select>

      <input class="btn btn-danger" type="submit" value="submit">
    </form>
  </div>
</template>

<script>
export default {
  name: 'tl_form',
  data(){
    return {
      textToTranslate: "",
      lang: ''
    }
  },
  created(){
    this.lang = 'ja';
  },
  methods: {
    formSubmit(e){
      this.$emit('formSubmit', this.textToTranslate, this.lang);
      e.preventDefault();
    }
  }
}
</script>

<style>
  #form-t {
    border-radius: 10px;
    border: 1px #fff solid;
  }
</style>
