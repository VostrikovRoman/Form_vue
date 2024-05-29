<template>
  <div :class="frame.class" v-for="(frame, index) in frames" :key="index">
    <p class="title_elem text">{{ frame.title }}<span class="label">{{ frame.label }}</span></p>
    <q-input
      class="form_data small"
      type="text"
      :placeholder="frame.placeholder"
      v-model="frame.value"
      outlined
      ref="inputRef"
      :rules='[val => val.length > 2 || frame.overview]'
    />
  </div>

</template>

<script>
export default {

  props:{
    frames:{
      type: Array,
      required: true,
      id: 0
    }
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
