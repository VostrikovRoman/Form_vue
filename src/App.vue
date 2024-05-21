<script>
import { useQuasar } from 'quasar'
import {ref} from 'vue'

export default {
  setup() {

    const form = ref();
    const surname = ref(null);
    const name = ref(null);
    const lastname = ref(null);
    const birth_place = ref(null);
    const email = ref(null);
    const birthdate = ref(null);
    const snils = ref(null);
    const passport = ref(null);
    const give_date = ref(null);
    const code = ref(null);
    const who_give = ref(null);
    const address = ref(null);
    const inn = ref(null);

    return {
      surname,
      name,
      lastname,
      birth_place,
      email,
      birthdate,
      snils,
      passport,
      give_date,
      code,
      who_give,
      address,
      inn,
      form,

      async onSubmit() {
        const success = await form.value.validate();
        if (success) {
          alert("Регистрация прошла успешно!");
        } else {
          alert("Заполните, пожалуйста, все поля!");
        }
      }
    }
  }
}
</script>

<template>
  <body>
  <div class="step">
    <div class="text title_step">Шаг 3. Укажите персональную информацию</div>
    <q-form ref="form" id="form" @submit="onSubmit" class="q-gutter-md" autocorrect="off" autocapitalize="off" autocomplete="off" spellcheck="false">
      <div class="form_elem small">
        <p class="title_elem text">Фамилия<span class="label">*</span></p>
        <q-input
          type="name"
          outlined
          class="form_data"
          v-model='surname'
          placeholder='Введите фамилию'
          lazy-rules :rules="[ val => val && val.length >= 3 || 'Укажите не менее 3х символов для поиска']"/>
      </div>
      <div class="form_elem small">
        <p class="title_elem text">Имя<span class="label">*</span></p>
        <q-input
          type="name"
          outlined
          class="form_data"
          v-model='name'
          placeholder='Введите имя'
          lazy-rules :rules="[ val => val && val.length >= 3 || 'Укажите не менее 3х символов для поиска']"/>
      </div>
      <div class="form_elem small">
        <p class="title_elem text">Отчество</p>
        <q-input
          type="name"
          outlined
          class="form_data"
          v-model='lastname'
          placeholder='Введите фамилию'/>
      </div>
      <div class="form_elem big">
        <p class="title_elem text">Место рождения<span class="label">*</span></p>
        <q-input
          type="text" outlined
          class="form_data"
          v-model='birth_place'
          placeholder='Введите место рождения'
          lazy-rules :rules="[ val => val && val.length >= 3 || 'Рекомендуется писать как в паспорте']"/>
      </div>
      <div class="form_elem small">
        <p class="title_elem text">Email<span class="label">*</span></p>
        <q-input
          type="email"
          outlined
          class="form_data"
          v-model='email'
          placeholder='Введите email'
          lazy-rules :rules="[ val => val && val.length >= 3|| 'Укажите не менее 3х символов для поиска']"/>
      </div>
      <div class="form_elem small">
        <p class="title_elem text">Дата рождения<span class="label">*</span></p>
        <q-input
          type="date"
          outlined
          class="form_data"
          v-model='birthdate'
          placeholder='Введите дату рождения'
          lazy-rules :rules="[ val => val && val.length > 0 || 'Укажите не менее 3х символов для поиска']"/>
      </div>
      <div class="form_elem small">
        <p class="title_elem text">СНИЛС (не обязательно)</p>
        <q-input
          type="text"
          outlined
          class="form_data"
          v-model='snils'
          placeholder='Введите СНИЛС'/>
      </div>
    </q-form>
  </div>
  <div class="step">
    <div class="text title_step">Шаг 4. Укажите паспортные данные, ИНН</div>
    <q-form @submit="onSubmit" class="q-gutter-md">
      <div class="form_elem small">
        <p class="title_elem text">Серия и номер паспорта<span class="label">*</span></p>
        <q-input
          type="text"
          outlined
          class="form_data"
          v-model='passport'
          placeholder='Введите серию и номер паспорта'
          lazy-rules :rules="[ val => val && val.length > 0 || '']"/>
      </div>
      <div class="form_elem small">
        <p class="title_elem text">Дата выдачи<span class="label">*</span></p>
        <q-input
          type="date"
          outlined
          class="form_data"
          v-model='give_date'
          placeholder='Введите дату выдачи'
          lazy-rules :rules="[ val => val && val.length > 0 || '']"/>
      </div>
      <div class="form_elem small">
        <p class="title_elem text">Код подразделения<span class="label">*</span></p>
        <q-input
          type="number"
          outlined
          class="form_data"
          v-model='code'
          placeholder='Введите код подразделения'
          lazy-rules :rules="[ val => val && val.length > 0 || '']"/>
      </div>
      <div class="form_elem medium">
        <p class="title_elem text">Кем выдан<span class="label">*</span></p>
        <q-input
          type="text"
          outlined
          class="form_data"
          v-model='who_give'
          placeholder='Кем выдан'
          lazy-rules :rules="[ val => val && val.length > 0 || '']"/>
      </div>
      <div class="form_elem medium">
        <p class="title_elem text">Адрес регистрации<span class="label">*</span></p>
        <q-input
          type="text"
          outlined
          class="form_data"
          v-model='address'
          placeholder='Введите адрес регистрации'
          lazy-rules :rules="[ val => val && val.length > 0 || '']"/>
      </div>
      <div class="form_elem small">
        <p class="title_elem text">ИНН<span class="label">*</span></p>
        <q-input
          type="number"
          outlined
          class="form_data"
          v-model='inn'
          placeholder='Введите ИНН'
          lazy-rules :rules="[ val => val && val.length > 0 || '']"/>
      </div>
    </q-form>
  </div>
  <q-btn @click="onSubmit" class="send_butt" label="Отправить"/>
  </body>
</template>

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
  margin-left: 40px;
  margin-bottom: 40px;
  margin-top: 40px;
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
