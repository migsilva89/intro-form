<template>
  <!DOCTYPE html>
  <html lang="en">

  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tailwind CSS Sign up Form with Image on Left Side Example</title>
    <link href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css" rel="stylesheet">
  </head>

  <body>
    <!-- previne de enviar a form em caso de x -->
    <form @submit.prevent="validateForm">
      <!-- BANNER -->
      <div style="background-image: url(images/images/bg-intro-desktop.png)" class="bg-redp-500">
        <div class="flex items-center min-h-screen " >
          <div class="md:px-32 mx-auto max-w-screen-2xl rounded-xl flex items-center">
            <div class="max-w-screen-xl flex flex-col md:flex-row mx-auto">
              <!-- PRIMEIRA COLUNA  -->
              <h1 class="md:text-left md:pt-48 md:pr-28 pb-5 text-center h-auto md:w-1/2 text-white px-8 md:text-5xl text-4xl font-extrabold ">
                Lear to code by watching others.
                <p class="md:text-left pt-8 md:h-auto text-white text-base font-light">
                  See how experienced developers solve problems in real-time. Watching scripted tutorials is great,
                  but understanding how developers think is invaluable.
                </p>
              </h1>
              <!-- DIREITA COLUNA  -->
              <div class="flex items-center justify-center md:w-1/2">
                <div class="max-w-full p-4">
                  <h1 class="bg-bluep-500 shadow-xl rounded-lg block w-full lg:px-26 md-16 px-16 py-4 mt-4 mb-4 text-base font-bold text-center text-white">
                    Try it free 7 days <span class="font-thin">then $20/mo. thereafter</span>
                  </h1>

                  <!-- NAME FIELD -->
                  <div class="bg-white shadow-xl rounded-lg block w-full px-4 py-2 sm:p-8 mt-4 mb-4">
                    <div>
                      <label class="block text-sm pb-4 "></label>
                      <div class="relative flex">
                        <input 
                            type="text" 
                            class="w-full px-4 leading-8  py-2 text-sm border rounded-md focus:border-bluep-500 focus:outline-none focus:ring-1 focus:ring-bluep-500"
                            placeholder="Name" 
                            :class="{
                              'border-red-500 placeholder-white':nameHasErrors,
                            }"
                            @focus="resetFormState"
                            />
                            <div
                              v-if="nameHasErrors"
                              class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none"
                            >
                              <ExclamationCircleIcon class="w-5 h-5 text-redp-500" />
                          </div>
                      </div>
                      <p v-if="nameHasErrors" class="italic pt-2 text-redp-500 text-xs text-right">
                        First name cannot be empty 
                      </p>
                    </div>

                    <!-- LAST NAME FIELD -->
                    <div class="mt-4">
                      <div class="relative flex">
                        <label class="block text-sm"></label>
                        <input type="text"
                              class="w-full px-4 leading-8 py-2 text-sm border rounded-md focus:border-bluep-500 focus:outline-none focus:ring-1 focus:ring-bluep-500"
                              placeholder="Last Name"
                              :class="{'border-red-500 placeholder-white':lastnameHasErrors}"
                              @focus="resetFormState"
                        />
                         <div
                              v-if="lastnameHasErrors"
                              class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none"
                            >
                              <ExclamationCircleIcon class="w-5 h-5 text-redp-500" />
                          </div>
                      </div>
                      <p v-if="lastnameHasErrors" class="italic pt-2 text-redp-500 text-xs text-right">
                        Last name cannot be empty 
                      </p>
                    </div>

                    <!-- EMAIL FIELD -->
                      <div class="mt-4">
                      <div class="relative flex">
                        <label class="block text-sm"></label>
                        <input type="text"
                              class="w-full px-4 leading-8 py-2 text-sm border rounded-md focus:border-bluep-500 focus:outline-none focus:ring-1 focus:ring-bluep-500"
                              placeholder="example@mail.com"
                              :class="{'border-red-500 text-md font-extrabold placeholder-redp-500':emailHasErrors}"
                              @focus="resetFormState"
                        />
                         <div
                              v-if="emailHasErrors"
                              class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none"
                            >
                              <ExclamationCircleIcon class="w-5 h-5 text-redp-500" />
                          </div>
                      </div>
                      <p v-if="emailHasErrors" class="italic pt-2 text-redp-500 text-xs text-right">
                        Email cannot be empty 
                      </p>
                    </div>

                    <!-- PASSWORD FIELD -->
                     <div class="mt-4">
                      <div class="relative flex">
                        <label class="block text-sm"></label>
                        <input type="text"
                              class="w-full px-4 leading-8 py-2 text-sm border rounded-md focus:border-bluep-500 focus:outline-none focus:ring-1 focus:ring-bluep-500"
                              placeholder="Password"
                              :class="{'border-red-500 placeholder-white':passwordHasErrors}"
                              @focus="resetFormState"
                        />
                         <div
                              v-if="passwordHasErrors"
                              class="absolute inset-y-0 right-0 pr-3 flex items-center pointer-events-none"
                            >
                              <ExclamationCircleIcon class="w-5 h-5 text-redp-500" />
                          </div>
                      </div>
                      <p v-if="passwordHasErrors" class="italic pt-2 text-redp-500 text-xs text-right">
                        Email cannot be empty 
                      </p>
                    </div>

                    <!-- BUTTON -->
                    
                    <div class="submit">
                    <button 
                        @click="validateForm"
                        class="font-bold uppercase w-full px-8 py-2 mt-4 text-sm leading-8 text-center text-white transition-colors duration-150 bg-greenb-500 border border-transparent rounded-lg active:bg-blue-600 hover:bg-green-300 hover:shadow-md focus:outline-none focus:shadow-outline-black">
                        Claim your free trial
                    </button>
                    </div>

                    <!-- TERMS AND CONDITIONS -->
                    <div class="mt-6 pb-4 md:pb-0 text-center px-8">
                      <p class="text-xs text-gray-400"> By clicking the button, you are agreeing to our 
                        <a href="#" class="text-redp-500 font-normal hover:underline"> Terms and Services.</a>
                        </p>
                    </div>
                    <div class="attribution lg:py-16 text-center fixed left-0 bottom-0 right-0 text-white">Coded by
                      <a href="https://github.com/migsilva89/" target="blank"> 
                        <span class="text-red-100 hover:text-bluep-500">Miguel Silva.</span>
                      </a>
                    </div>
                      <!-- <p>Email: {{ email }}</p>
                      <p>Password: {{ password }}</p> -->
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </form>
  </body>

  </html>
</template>

<script>

import {ExclamationCircleIcon} from "@heroicons/vue/solid";

export default {
  
  components: {
       ExclamationCircleIcon,
  },

  data() {
    return{
      email: '',
      password: '',
      nameHasErrors: '',
      lastnameHasErrors: '',
      emailHasErrors: '',
      passowrdHasErrors: ''
    }
  },

  methods:{
    validateForm(){
      //pedido Ajax para enviar a data do form e caso tenha erros:
      this.nameHasErrors=true
      this.lastnameHasErrors=true
      this.emailHasErrors=true
      this.passwordHasErrors=true
    },
    resetFormState(){
      this.nameHasErrors=false
      this.lastnameHasErrors=false
      this.emailHasErrors=false
      this.passwordHasErrors=false
    }
  }
}

</script>

<style>
</style>