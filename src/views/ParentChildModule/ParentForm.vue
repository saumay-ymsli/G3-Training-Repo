<script setup>
import { useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';

import childSubPagePage from '/src/views/ParentChildModule/ChildPagee.vue';

const { t } = useI18n();
const lockScreenUtils = useLockScreen();
const lockScreen = lockScreenUtils.lockScreen;

const selectedName = ref('Common Name');

defineOptions({
  name: 'ParentForm',
});

const form = ref();
const fullName = ref();
const childSubPage = ref();

const formData = reactive({
  fullName: '',
});

const makeFieldEmpty = () => {
  formData.fullName = '';
};

const displayData = (evt) => {
  selectedName.value = evt;
};
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData">
    <VueFormItem

      label="Full Name"

      prop="fullName"
    >
      <VueInput

        id="fullName"

        ref="fullName"
        v-model="formData.fullName"

        data-type="string"
      />
    </VueFormItem>

    <VueText id="showSelectedName" ref="showSelectedName" :style="{ width: '100%', display: 'inline-block' }" v-html="selectedName" />
    <childSubPagePage

      id="childSubPage"
      ref="childSubPage"

      :full-name="formData.fullName"

      @make-field-empty="makeFieldEmpty"
      @show-data-on-parent-field="displayData"
    />
  </VueForm>
</template>
