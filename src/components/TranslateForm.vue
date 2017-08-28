<template>
  <div class="row" id="translateform">
   <div class="col-md-6 col-md-offset-3">
    <form id="transForm" class="form-inline well" v-on:submit="formSubmit" >
        <input class="form-control" type="text" v-model="textToTranslate" placeholder="Masukkan Kata...">
        <select class="form-control" v-model="languange" >
            <option value="id">Indonesia</option>
            <option value="ja">Jepang</option>
            <option value="de">Jerman</option>
            <option value="ru">Rusia</option>
        </select> 
        <input class="btn btn-primary" type="submit" value="Translate">
    </form>
   </div>
  </div>
</template>

<script>


export default {
  name: 'translateForm',
  data(){
      return{
          textToTranslate:'',
          languange: ''
      }
  },
  created(){
    this.languange = 'id';
  },
  methods: {
      formSubmit(e){
          this.$emit('formSubmit', this.textToTranslate, this.languange);
          e.preventDefault();
      }
  }
  
}
</script>

<style>
    #transForm{
        border-radius: 10px;
        border: 1px #ccc solid;
    }
</style>
