<template>
  <div :class=elem_class>
    <p class="title_elem text">{{title}}<span class="label">{{label}}</span></p>
    <q-input
      class="form_data"
      type="text"
      ref="inputRef"
      outlined
      :placeholder=placeholder
      v-model="value_model"
      :rules="[ val => val.length > 2 || 'Укажите не менее 3х символов для поиска']"
    />
  </div>

</template>

<script>
import { ref } from 'vue';

export default {

  setup(){
    const value_model = ref('');
    return{
      value_model
    }
  },

  props:{
    frames:{
      type: Array,
      required: true,
      id: 0
    },
    title: String,
    label: String,
    placeholder: String,
    elem_class: String,
    overview: String,
    value: String,
    rules: String
  }
}
</script>

<style lang="scss" scoped>
.text{
  font-size: 25px;
  font-weight: bold;
  color: #393939;
}
.form_elem{
  display: inline-grid;
  margin-right: 20px;
}
.title_elem{
  font-size: 18px;
  width: fit-content;
  height: fit-content;
  margin-bottom: 5px;
}
.label{
  color:red;
  font-size: 17px;
  width: fit-content;
  margin-left: 5px;
}
.form_elem.small{
  width: 30%;
}
.form_elem.medium{
  width: 46.5%;
}
.form_elem.big{
  width: 96%;
}
</style>
