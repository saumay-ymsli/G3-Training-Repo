<script setup>
import { useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';

import childSubPagePage from '/src/views/m001/childPage-001.vue';

const { t } = useI18n();
const lockScreenUtils = useLockScreen();
const lockScreen = lockScreenUtils.lockScreen;

defineOptions({
  name: 'parentPage',
});

const form = ref();
const parentInput = ref();
const childSubPage = ref();

const formData = reactive({
  parentInput: '',
});

const childEmitHandler = (evt) => {
  console.log(evt);
};
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData">
    <VueFormItem

      label="Parent Input"

      prop="parentInput"
    >
      <VueInput

        id="parentInput"

        ref="parentInput"
        v-model="formData.parentInput"

        data-type="string"
      />
    </VueFormItem>

    <childSubPagePage

      id="childSubPage"

      ref="childSubPage"

      :first-name="formData.parentInput"
      @on-child-emit="childEmitHandler"
    />
  </VueForm>
</template>
