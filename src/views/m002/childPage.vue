


<script setup>
import { useLockScreen, } from 'viy-ui';
import { useI18n } from 'vue-i18n';


const { t } = useI18n();
const lockScreenUtils = useLockScreen();
const lockScreen = lockScreenUtils.lockScreen;


        
defineOptions({
  name: 'childPage',
});
    
const form = ref();
const childInput = ref();
const Print Button = ref();


const formData = reactive({
childInput: '' 
});
    
    
    

                                           
    

    

	

	

   











    






</script>
        
<template>
<VueForm ref="form" :model="formData" v-loading="lockScreen" >    
		

    <VueFormItem 


  label="Child Input"



    prop="childInput"

                             

                                 


  
>
    <VueInput 

data-type="string"
                   

                   

                   

                   

                   
              id="childInput"
			  ref="childInput"
                                       
    
	 		v-model="formData.childInput"
    

              
              
              
              
                  
            
              

    >


    </VueInput>
    </VueFormItem>

<VueButton icon-position="left" id="Print Button" ref="Print Button" >
        Print Parent Data
</VueButton>

        
    </VueForm>
</template>





[{"line":21,"column":12,"message":"Parsing error: ',' expected."}]