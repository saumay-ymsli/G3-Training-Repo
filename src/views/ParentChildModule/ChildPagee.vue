<script setup>
import { useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';

const props = defineProps(['fullName']);
const emit = defineEmits(['makeFieldEmpty', 'showDataOnParentField']);
const { t } = useI18n();
const lockScreenUtils = useLockScreen();
const lockScreen = lockScreenUtils.lockScreen;

const nameList = ref([]);

defineOptions({
  name: 'ChildPagee',
});

const form = ref();
const addBtn = ref();
const fullName = ref();

const formData = reactive({
  fullName: '',
});

const fullNameProps = computed(() => {
    	return {
    label: 'fullName',
    value: 'fullName',

  };
});

const addBtnClick = () => {
  addNameToList();
};
const fullNameChange = (val, option, oldVal, oldOption) => {
  console.log(val, ' ', option, ' ', oldVal, ' ', oldOption);
  emitShowData(val);
};

const addNameToList = () => {
  nameList.value.push({ fullName: props.fullName });
  emit('makeFieldEmpty');
};

const emitShowData = (val) => {
  console.log(val);
  emit('showDataOnParentField', val);
};
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData">
    <VueButton id="addBtn" ref="addBtn" icon-position="left" @click="addBtnClick">
      Add Name to List
    </VueButton>

    <VueFormItem

      label="Full Name"

      prop="fullName"
    >
      <VueSelect

        id="fullName"
        ref="fullName"

        v-model="formData.fullName"

        :options="nameList"

        :props="fullNameProps"

        @change="fullNameChange"
      />
    </VueFormItem>
  </VueForm>
</template>
