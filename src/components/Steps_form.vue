<template>
  <div class="step" v-for="(step, index) in steps" :key="index">
    <div class="text title_step">{{step.overview}}</div>
    <div v-for="(step, index) in step.data" :key="index" :class="step.class">
      <elem_form :frames="step"
                 :title="step.title"
                 :placeholder="step.placeholder"
                 :label="step.label"
                 :elem_class="step.class"
                 :value="step.value"
                 :type="step.type"
                 :mask="step.mask"
                 :max_value="step.max_value"
                 :min_value="step.min_value"
                 :rules="step.rules"
                 v-if="step.type_of_input === 'input'"
      />
      <select_form :frames="step"
                   :title="step.title"
                   :placeholder="step.placeholder"
                   :label="step.label"
                   :elem_class="step.class"
                   :value="step.value"
                   :type="step.type"
                   :mask="step.mask"
                   :max_value="step.max_value"
                   :min_value="step.min_value"
                   :rules="step.rules"
                   v-else-if="step.type_of_input === 'select'"
                   :options="step.options"
      />
    </div>
  </div>
</template>

<script>
import elem_form from "components/Elem_form.vue";
import select_form from "components/Select_form.vue";
import {ref} from "vue";

export default {
  props:{
    steps:{
      type: Array,
      required: true
    }
  },

  components: {
    elem_form, select_form

  },
  setup(){
    return {
      frames
    }

  },

}
</script>

<style lang="scss" scoped>
.form_elem{
  display: inline-grid;
  margin-right: 20px;
  margin-top: 20px;
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
