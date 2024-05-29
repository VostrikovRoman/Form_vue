<template>
  <q-form ref="form" id="form" @submit="onSubmit" class="q-gutter-md" autocapitalize="off" autocomplete="off" spellcheck="false">
    <steps_form :steps="steps"/>
    <q-btn @click="onSubmit" class="send_butt" label="Отправить"/>
  </q-form>
</template>

<script>
import { useQuasar } from 'quasar'
import {ref} from 'vue'
import Steps_form from "components/Steps_form.vue";

export default {
  components: {
    Steps_form
  },

  setup() {
    const form = ref();
    const steps = ref ([
      {id: "0", overview: "Шаг 3. Укажите персональную информацию"},
      {id: "1", overview: "Шаг 4. Укажите паспортные данные, ИНН"}
    ])

    return {
      form, steps,

      async onSubmit() {
        const success = await form.value.validate();
        if (success) {
          alert("Регистрация прошла успешно!");
        }
        else {
          alert("Заполните, пожалуйста, все поля!");
        }
      }
    }
  }
}
</script>

<style >
.text{
  font-size: 25px;
  font-weight: bold;
  color: #393939;
}
.title_step{
  border-bottom: dotted 5px #99c3c6;
  margin-bottom: 20px;
}
.step{
  position: relative;
  margin: 40px 30px 40px 40px;
}
.send_butt{
  position: relative;
  left: 50%;
  transform: translate(-50%, 0px);
  margin-bottom: 50px;
  width: 400px;
  height: 60px;
  background: #87a3a5;
  color: white;
  font-size: 20px;
  border-radius: 10px;
  font-weight: bold;
}
</style>
