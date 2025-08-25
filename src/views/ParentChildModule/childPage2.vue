<script setup>
import { useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';
import { useApi } from '@/composables/useApi';

const emit = defineEmits(['select']);
const { t } = useI18n();
const lockScreenUtils = useLockScreen();
const lockScreen = lockScreenUtils.lockScreen;

defineOptions({
  name: 'childPage2',
});

const form = ref();
const allUsersTable = ref();
const setBtn = ref();

const formData = reactive({
});

const allUsersTableEditConfig = reactive({
  trigger: 'click',

});

const allUsersTableMouseConfig = reactive({

  extension: true,

});

const allUsersTableRowConfig = reactive({
  isCurrent: true,
});

const allUsersDataApi = useApi({
  method: 'post',
  localData: [
    { firstName: 'nameA', lastName: 'nameB' },
    { firstName: 'nameC', lastName: 'nameD' },
    { firstName: 'nameE', lastName: 'nameF' },
  ],

});
const allUsersData = allUsersDataApi.data;

const allUsersTableFirstNameEditRender = computed(() => {
  return {
    enabled: false,
  };
});

const allUsersTableLastNameEditRender = computed(() => {
  return {
    enabled: false,
  };
});

const setBtnClick = () => {
  emitSelectedData();
};

const emitSelectedData = () => {
  console.log('data ', allUsersTable.value.getCurrentRecord());
  emit('select', allUsersTable.value.getCurrentRecord());
};
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData">
    <VueTable

      id="allUsersTable"

      ref="allUsersTable"

      :stripe="true"

      :border="true"

      :show-header="true"
      :show-footer="true"

      :data="allUsersData"

      :edit-config="allUsersTableEditConfig"
      :mouse-config="allUsersTableMouseConfig"
      :row-config="allUsersTableRowConfig"
    >
      <VueInputColumn

        :edit-render="allUsersTableFirstNameEditRender"

        field="firstName"

        width="200px"

        title="First Name"
      />
      <VueInputColumn

        :edit-render="allUsersTableLastNameEditRender"

        field="lastName"

        width="200px"

        title="Last Name"
      />
    </VueTable>

    <VueButton id="setBtn" ref="setBtn" icon-position="left" @click="setBtnClick">
      Set
    </VueButton>
  </VueForm>
</template>
