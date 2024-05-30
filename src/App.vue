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
      {id: "0", overview: "Шаг 3. Укажите персональную информацию", data: [
          {
            title: 'Фамилия',
            label: '*',
            placeholder: 'Введите фамилию',
            class: 'form_elem small',
            overview: 'Укажите не менее 3х символов для поиска',
            value: '',
            rules: [val => val.length > 2 || "Залупа"],
            fill: true
          },
          {
            title: 'Имя',
            label: '*',
            placeholder: 'Введите имя',
            class: 'form_elem small',
            overview: 'Укажите не менее 3х символов для поиска',
            value: '',
            rules: 'val.length > 2'
          },
          {
            title: 'Отчество',
            label: '',
            placeholder: 'Введите отчество',
            class: 'form_elem small',
            value: '',
            rules: '[val => val.length > 2 || \'Укажите не менее 3х символов для поиска\']'
          },
          {
            title: 'Место рождения',
            label: '*',
            placeholder: 'Место рождения',
            class: 'form_elem big',
            overview: 'Рекомендуется писать как в паспорте'
          },
          {
            title: 'Email',
            label: '*',
            placeholder: 'Введите email',
            class: 'form_elem small',
            overview: 'Укажите не менее 3х символов для поиска'
          },
          {
            title: 'Дата рождения',
            label: '*',
            placeholder: 'Дата рождения',
            class: 'form_elem small',
            overview: 'Укажите не менее 3х символов для поиска'
          },
          {
            title: 'СНИЛС (не обязательно)',
            label: '',
            placeholder: 'Введите СНИЛС',
            class: 'form_elem small',
            overview: 'Укажите не менее 3х символов для поиска'
          }
        ]},
      {id: "1", overview: "Шаг 4. Укажите паспортные данные, ИНН", data: [
          {
            title: 'Серия и номер паспорта',
            label: '*',
            placeholder: 'Номер паспорта',
            class: 'form_elem small',
            overview: ''
          },
          {
            title: 'Дата выдачи',
            label: '*',
            placeholder: 'Дата выдачи',
            class: 'form_elem small',
            overview: ''
          },
          {
            title: 'Код подразделения',
            label: '*',
            placeholder: 'Код подразделения',
            class: 'form_elem small',
            overview: ''
          },
          {
            title: 'Кем выдан',
            label: '*',
            placeholder: 'Кем выдан',
            class: 'form_elem medium',
            overview: ''
          },
          {
            title: 'Адрес регистрации',
            label: '*',
            placeholder: 'Адрес регистрации',
            class: 'form_elem medium',
            overview: 'Укажите не менее 3х символов для поиска'
          },
          {
            title: 'ИНН',
            label: '*',
            placeholder: 'Введите ИНН',
            class: 'form_elem small',
            overview: ''
          }

        ]}
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
