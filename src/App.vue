<template>
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <div class="flex flex-col w-full px-9 bg-mobile md:flex-row md:justify-center md:bg-desktop md:h-screen">
    <article class="flex flex-col my-24 justify-center space-y-6 text-center text-white
        md:max-w-xl md:pr-20 md:my-0 md:text-left">
      <TextField />
    </article>  
    <section class="flex flex-col mb-20 w-full justify-center md:max-w-xl md:mb-0">
      <div class="flex justify-center align-middle mb-7 py-4 px-10 rounded-lg shadow-grey bg-accent-blue text-center text-white">
        <p><b>Try it free 7 days</b> then $20/mo. thereafter</p>
      </div>
      <FormField :fieldsData="this.fieldsData" :errorStyles="this.errorStyles">
        <template v-slot:submit-section>
          <button
            @click.prevent="getFormValues"
            type="submit"
            class="mb-4 p-4 shadow-default-green bg-primary-green active:shadow-active-green active:bg-green-300 focus:outline-none rounded-md text-md font-normal text-white">
            CLAIM YOUR FREE TRIAL
          </button>
          <p class="text-center text-xs text-gray-400">
            By clicking the button, you are agreeing to our 
            <b class="cursor-pointer font-bold text-red-400"> Terms and Services</b>
          </p>
        </template>
      </FormField>
    </section>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
import TextField from './components/TextField.vue';
import FormField from './components/FormField.vue';

export default {
  name: 'App',
  components: {
    TextField,
    FormField
  },
  data() {
    return {
      fieldsData: [
        {
          id: 'first-name',
          placeholder: 'First Name',
          type: 'text',
          value: 'default value',
          error: false,
          errorMsg: 'First Name cannot be empty'
        },
        {
          id: 'last-name',
          placeholder: 'Last Name',
          type: 'text',
          value: 'default value',
          error: false,
          errorMsg: 'Last Name cannot be empty'
        },
        {
          id: 'email',
          placeholder: 'Email',
          type: 'email',
          value: 'default value',
          error: false,
          errorMsg: 'Email cannot be empty'
        },
        {
          id: 'password',
          placeholder: 'Password',
          type: 'password',
          value: 'default value',
          error: false,
          errorMsg: 'Password cannot be empty'
        }
      ],
      errorStyles: {
        icon: 'absolute right-0 mr-4 mt-4 p-3 icon-error bg-no-repeat',
        input: 'border-primary-red text-primary-red focus:border-primary-red',
        msg: 'block'
      }
    }
  },
  methods: {
    getFormValues() {
      for(let i = 0; i < this.fieldsData.length; i++) {
        const data = this.fieldsData[i];
        if (data.value === "") {
          data.error = true;
        } else if (data.type === "email") {
          if(!data.value.includes("@")) {
            data.errorMsg = "Looks like this is not an email"
            data.error = true;
          } else {
            data.error = false;
          }
        } else {
          data.error = false;
        }
      }
    }
  }
}
</script>
