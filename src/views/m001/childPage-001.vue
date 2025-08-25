<script setup>
import { useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';

const firstName = defineProps(['firstName']);
const emit = defineEmits(['onChildEmit']);
const { t } = useI18n();
const lockScreenUtils = useLockScreen();
const lockScreen = lockScreenUtils.lockScreen;

defineOptions({
  name: 'childPage-001',
});

const form = ref();
const childInput = ref();
const emitter = ref();
const print = ref();

const formData = reactive({
  childInput: '',
});

const emitterClick = () => {
  emitToParent();
};
const printClick = () => {
  console.log(firstName);
};

const emitToParent = () => {
  emit('onChildEmit', formData.childInput);
};
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData">
    <VueFormItem

      label="Child Input"

      prop="childInput"
    >
      <VueInput

        id="childInput"

        ref="childInput"
        v-model="formData.childInput"

        data-type="string"
      />
    </VueFormItem>

    <VueButton id="emitter" ref="emitter" icon-position="left" @click="emitterClick">
      Emit To Parent
    </VueButton>
    <VueButton id="print" ref="print" icon-position="left" @click="printClick">
      Print Parent Data
    </VueButton>
  </VueForm>
</template>
