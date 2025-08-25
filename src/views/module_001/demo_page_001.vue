<script setup>
import { useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';

const { t } = useI18n();
const lockScreenUtils = useLockScreen();
const lockScreen = lockScreenUtils.lockScreen;

defineOptions({
  name: 'demo_page_001',
});

const form = ref();
const fname = ref();
const printName = ref();
const textArea = ref();

const formData = reactive({
  firstName: '', textArea: '',
});

const printNameClick = () => {
  printHandler();
};

const printHandler = () => {
  formData.textArea = formData.firstName;
};
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData">
    <VueFormItem

      label="First Name"

      prop="firstName"
    >
      <VueInput

        id="fname"

        ref="fname"

        v-model="formData.firstName"
        data-type="string"

        type="text"
      />
    </VueFormItem>

    <VueButton id="printName" ref="printName" :loading="false" icon-position="left" :plain="false" size="default" @click="printNameClick">
      Print
    </VueButton>

    <VueFormItem

      label="Output"

      prop="textArea"
    >
      <VueInput
        id="textArea"

        ref="textArea"
        v-model="formData.textArea"

        type="textarea"
      />
    </VueFormItem>
  </VueForm>
</template>
