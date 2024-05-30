<template>
  <div class="step" v-for="(step, index) in steps" :key="index">
    <div class="text title_step">{{step.overview}}</div>
    <elem_form :frames="frames" v-for="(step, index) in step.data"
               :key="index"
               :title="step.title"
               :placeholder="step.placeholder"
               :label="step.label"
               :elem_class="step.class"
               :value="step.value"
               :overview="step.overview"
               :type="step.type"
               :mask="step.mask"
               :max_value="step.max_value"
               :min_value="step.min_value"
    />
  </div>
</template>

<script>
import Elem_form from "components/Elem_form.vue";
import {ref} from "vue";

export default {
  props:{
    steps:{
      type: Array,
      required: true
    }
  },

  components: {
    Elem_form,

  },
  setup(){
    const frames = ref([
      {id: 0,
        title: 'Фамилия',
        label: '*',
        placeholder: 'Введите фамилию',
        class: 'form_elem small',
        overview: 'Укажите не менее 3х символов для поиска',
        value: '',
        rules: [val => val.length > 2 || "Залупа"],
        fill: true
      },
      {id: 0,
        title: 'Имя',
        label: '*',
        placeholder: 'Введите имя',
        class: 'form_elem small',
        overview: 'Укажите не менее 3х символов для поиска',
        value: '',
        rules: 'val.length > 2'
      },
      {id: 1,
        title: 'Отчество',
        label: '',
        placeholder: 'Введите отчество',
        class: 'form_elem small',
        value: '',
        rules: '[val => val.length > 2 || \'Укажите не менее 3х символов для поиска\']'
      }
    ])

    return {
      frames,

    }

  },

}
</script>

<style lang="scss" scoped>

</style>
