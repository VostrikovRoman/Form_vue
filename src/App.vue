
<script>
export default {
  data(){
    return {
      elems: [
        {id: 0, title: 'Фамилия', label: '*', placeholder: 'Введите фамилию', block_size: 'form_data small', overview: 'Укажите не менее 3х символов для поиска'},
        {id: 1, title: 'Имя', label: '*', placeholder: 'Введите имя', block_size: 'form_data small', overview: 'Укажите не менее 3х символов для поиска', value: ''},
        {id: 2, title: 'Отчество', label: '', placeholder: 'Введите отчество', block_size: 'form_data small', overview: 'Укажите не менее 3х символов для поиска'},
        {id: 3, title: 'Место рождения', label: '*', placeholder: 'Место рождения', block_size: 'form_data big', overview: 'Рекомендуется писать как в паспорте'},
        {id: 4, title: 'Email', label: '*', placeholder: 'Введите email', block_size: 'form_data small', overview: 'Укажите не менее 3х символов для поиска'},
        {id: 5, title: 'Дата рождения', label: '*', placeholder: 'Дата рождения', block_size: 'form_data small', overview: 'Укажите не менее 3х символов для поиска'},
        {id: 6, title: 'СНИЛС (не обязательно)', label: '', placeholder: 'Введите СНИЛС', block_size: 'form_data small', overview: 'Укажите не менее 3х символов для поиска'},
      ],
      elems_2: [
        {id: 7, title: 'Серия и номер паспорта', label: '*', placeholder: 'Номер паспорта', block_size: 'form_data small', overview: ''},
        {id: 8, title: 'Дата выдачи', label: '*', placeholder: 'Дата выдачи', block_size: 'form_data small', overview: ''},
        {id: 9, title: 'Код подразделения', label: '*', placeholder: 'Код подразделения', block_size: 'form_data small', overview: ''},
        {id: 10, title: 'Кем выдан', label: '*', placeholder: 'Кем выдан', block_size: 'form_data medium', overview: ''},
        {id: 11, title: 'Адрес регистрации', label: '*', placeholder: 'Адрес регистрации', block_size: 'form_data medium', overview: 'Укажите не менее 3х символов для поиска'},
        {id: 12, title: 'ИНН', label: '*', placeholder: 'Введите ИНН', block_size: 'form_data small', overview: ''}
      ]
    }
  }


}
</script>

<template>
  <body>
  <div class="step">
    <div class="text title_step">Шаг 3. Укажите персональную информацию</div>
    <div class="form_elem" v-for="elem in elems" :key="elem">
      <p class="title_elem text">{{elem.title}}<span class="label">{{elem.label}}</span></p>
      <input v-bind:id=elem.id v-bind:class=elem.block_size v-bind:placeholder=elem.placeholder>
      <p class="overview">{{elem.overview}}</p>
    </div>
  </div>
  <div class="step">
    <div class="text title_step">Шаг 3. Укажите паспортные данные, ИНН</div>
    <div class="form_elem" v-for="elem in elems_2" :key="elem">
      <p class="title_elem text">{{elem.title}}<span class="label">{{elem.label}}</span></p>
      <input v-bind:id=elem.id v-bind:class=elem.block_size v-bind:placeholder=elem.placeholder>
      <p class="overview">{{elem.overview}}</p>
    </div>
  </div>
  <button class="send_butt" >Отправить</button>

  </body>
</template>

<style >
.text{
  font-size: 25px;
  font-weight: bold;
  color: #393939;
  padding-bottom: 10px;
}
.title_step{
  border-bottom: dotted 5px #87a3a5;
}
.step{
  position: relative;
  margin-left: 20px;
  margin-bottom: 40px;
  margin-top: 40px;
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
}
.label{
  color:red;
  font-size: 17px;
  width: fit-content;
  margin-left: 5px;
}
.form_data{
  height: 60px;
  border: solid 2px #b0d2d5;
  border-radius: 15px;
  font-size: 15px;
  padding-left: 20px;
  margin-top: -15px;
}
.overview{
  margin-left: 20px;
  font-size: 13px;
  color: #666666;
  margin-top: 5px;
}
.form_data.small{
  width: 400px;
}
.form_data.medium{
  width: 610px;
}
.form_data.big{
  width: 1240px;
}
.form_data.error{
  border:solid 2px #ff7c7c;
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
  border: 0px;
  border-radius: 10px;
  font-weight: bold;
  transition: 0.5s;
}
.send_butt:hover{
  transform: scale(1.05) translate(-47%, 0px);
  transition: 0.5s;
}

</style>
