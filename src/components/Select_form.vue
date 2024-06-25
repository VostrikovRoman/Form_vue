<template>
  <div class="form_elem">
    <p class="title_elem text">{{title}}<span class="label">{{label}}</span></p>
    <q-select
      class="form_data select"
      :type=type
      ref="inputRef"
      outlined
      :placeholder=placeholder
      v-model="value_model"
      :rules="rules"
      :mask=mask
      unmasked-value
      fill-mask
      :max=max_value
      :min=min_value
      use-input
      hide-selected
      fill-input
      :options="options"
      @input="Func"
    />
  </div>

</template>

<script>
import { ref } from 'vue';
import Steps_form from "components/Steps_form.vue";

export default {
  computed: {
    Steps_form() {
      return Steps_form
    }
  },

  setup(){
    const url = "https://suggestions.dadata.ru/suggestions/api/4_1/rs/suggest/address";
    const token = "05d7884481091c0ac5e192768bc429321167f571";
    const query = document.getElementsByClassName('form_data select')[0].value_model;

    const options = {
      method: "POST",
      mode: "cors",
      headers: {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Token " + token
      },
      body: JSON.stringify({query: query})
    }
    const value_model = ref('');
    return{
      value_model,

      Func(){
        fetch(url, options)
          .then(response => response.json())
          .then(result => console.log(result))
          .catch(error => console.log("error", error));
        console.log(query);
      }
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
    rules: Array,
    type: Date,
    mask: String,
    max_value: String,
    min_value: String,
    type_of_input: String,
    options: Array
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
  margin-top: 20px;
}
.title_elem{
  font-size: 18px;
  width: fit-content;
  height: fit-content;
  margin-bottom: 5px;
}
.label{
  color: var(--q-negative);
  font-size: 17px;
  width: fit-content;
  margin-left: 5px;
}
</style>
