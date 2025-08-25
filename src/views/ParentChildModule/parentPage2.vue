<script setup>
import { useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';

import allUsersPopUpPopupComp from '/src/views/ParentChildModule/childPage2.vue';

const { t } = useI18n();
const lockScreenUtils = useLockScreen();
const lockScreen = lockScreenUtils.lockScreen;

defineOptions({
  name: 'parentPage2',
});

const form = ref();
const allUsersPopUp = ref();

const formData = reactive({
  allUsersPopUp: '',
});

const allUsersPopUpSelect = (selectedObj) => {
  formData.allUsersPopUp = `${selectedObj.firstName} ${selectedObj.lastName}`;
}

;
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData">
    <VueFormItem

      label="All Users"

      prop="allUsersPopUp"
    >
      <VueValueList

        id="allUsersPopUp"

        ref="allUsersPopUp"

        v-model="formData.allUsersPopUp"

        popup-type="dialog"
        dialog-width="500px"

        :use-popup="true"

        :popup-component="allUsersPopUpPopupComp"

        @select="allUsersPopUpSelect"
      />
    </VueFormItem>
  </VueForm>
</template>
