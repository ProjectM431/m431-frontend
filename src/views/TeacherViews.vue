<template>
  <div class="teacher">
        <div>     
        <div v-if="token == null" class="flex h-screen bg-gray-200">
            Vous n'avez pas la permissions d'accéder à cette page
        </div>   
        <div v-if="token != null" class="flex h-screen bg-gray-200">
            <div class="flex-1 flex flex-col overflow-hidden">
                <main class="flex-1 overflow-x-hidden overflow-y-auto bg-gray-200">
                    <div class="container mx-auto px-6 py-8">
                        <h3 class="text-gray-700 text-3xl font-medium">Bienvenue {{userInfo.first_name}} </h3>
                        <div class="mt-4">
                            <div class="flex flex-wrap -mx-6">
                                <div class="w-full px-6 sm:w-1/2 xl:w-1/3">
                                    <div class="flex items-center px-5 py-6 shadow-sm rounded-md bg-white">
                                        <div class="p-3 rounded-full bg-indigo-600 bg-opacity-75">
                                            <svg class="h-8 w-8 text-white" viewBox="0 0 28 30" fill="none" xmlns="http://www.w3.org/2000/svg">
                                                <path d="M18.2 9.08889C18.2 11.5373 16.3196 13.5222 14 13.5222C11.6804 13.5222 9.79999 11.5373 9.79999 9.08889C9.79999 6.64043 11.6804 4.65556 14 4.65556C16.3196 4.65556 18.2 6.64043 18.2 9.08889Z" fill="currentColor"></path>
                                                <path d="M25.2 12.0444C25.2 13.6768 23.9464 15 22.4 15C20.8536 15 19.6 13.6768 19.6 12.0444C19.6 10.4121 20.8536 9.08889 22.4 9.08889C23.9464 9.08889 25.2 10.4121 25.2 12.0444Z" fill="currentColor"></path>
                                                <path d="M19.6 22.3889C19.6 19.1243 17.0927 16.4778 14 16.4778C10.9072 16.4778 8.39999 19.1243 8.39999 22.3889V26.8222H19.6V22.3889Z" fill="currentColor"></path>
                                                <path d="M8.39999 12.0444C8.39999 13.6768 7.14639 15 5.59999 15C4.05359 15 2.79999 13.6768 2.79999 12.0444C2.79999 10.4121 4.05359 9.08889 5.59999 9.08889C7.14639 9.08889 8.39999 10.4121 8.39999 12.0444Z" fill="currentColor"></path>
                                                <path d="M22.4 26.8222V22.3889C22.4 20.8312 22.0195 19.3671 21.351 18.0949C21.6863 18.0039 22.0378 17.9556 22.4 17.9556C24.7197 17.9556 26.6 19.9404 26.6 22.3889V26.8222H22.4Z" fill="currentColor"></path>
                                                <path d="M6.64896 18.0949C5.98058 19.3671 5.59999 20.8312 5.59999 22.3889V26.8222H1.39999V22.3889C1.39999 19.9404 3.2804 17.9556 5.59999 17.9556C5.96219 17.9556 6.31367 18.0039 6.64896 18.0949Z" fill="currentColor"></path>
                                            </svg>
                                        </div>
                                        <div class="mx-5">
                                            <h4 class="text-2xl font-semibold text-gray-700">{{ userList.length }} </h4>
                                            <div class="text-gray-500">Eleves</div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="mt-8">
                        </div>
                        <div class="flex flex-col mt-8">
                            <div class="-my-2 py-2 overflow-x-auto sm:-mx-6 sm:px-6 lg:-mx-8 lg:px-8">
                                <div class="align-middle inline-block min-w-full shadow overflow-hidden sm:rounded-lg border-b border-gray-200">
                                    <table class="min-w-full">
                                        <thead>
                                            <tr>
                                                <th class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">
                                                    Nom et prénom
                                                </th>
                                                <th class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">
                                                    Ajouter appréciations
                                                </th>
                                                <th class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">
                                                    Date de l'appréciations
                                                </th>
                                                <th class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">
                                                    Envoyez l'appréciations
                                                </th>
                                            </tr>
                                        </thead>
        
                                        <tbody class="bg-white">
                                            <tr v-bind:key="userList.id" v-for="userList in userList">
                                                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200">
                                                    <div class="flex items-center">
                                                        <div class="ml-4">
                                                            <div class="text-sm leading-5 font-medium text-gray-900"> {{ userList.first_name }} {{ userList.last_name }}
                                                            </div>
                                                            <div class="text-sm leading-5 text-gray-500">{{userList.email}}</div>
                                                        </div>
                                                    </div>
                                                </td>
        
                                                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200">
                                                    <div class="text-sm leading-5 text-gray-900"></div>
                                                    <select v-model="observationSelected" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                                                    <option v-for="observationList in observationList" v-bind:key="observationList.id">{{observationList.title}}</option>
                                                    </select>
                                                </td>
                                                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200">
                                                   <input v-model="observationDate" type="datetime-local" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                                                </td>
                                                <td class="px-6 py-4 whitespace-no-wrap border-b flex justify-center border-gray-200">
                                                   <button @click="sendAppreciation(userList)" class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow">
                                                        Envoyez
                                                    </button>
                                                </td>
                                            </tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                        </div>
                    </div>
                </main>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",

  data: () => ({
    isLogged: null,
    token: null,
    user_id_cache: null,
    user_first_name_cache: null,
    user_last_name_cache: null,
    userInfo: {},
    userList: {},
    observationList: {},
    selectedList: {},
    observationSelected: null,
    username: null,
    observationDate: null,
    apiUser: "http://127.0.0.1:8003/profile/user",
    apiUserId: "http://127.0.0.1:8003/profile/user/",
    apiObservation: "http://127.0.0.1:8003/observation",
    apiAppreciation: "http://127.0.0.1:8003/appreciations",
  }),

  methods: {

    sendAppreciation(userList){

    if (this.observationSelected == "Absence non excusée") {
        this.observationSelected = 3
    } 

    if (this.observationSelected == "Absence Excusée") {
        this.observationSelected = 4
    } 

    if (this.observationSelected == "Arrivé Tardive") {
        this.observationSelected = 5
    } 

    if (this.observationSelected == "Renvoi") {
        this.observationSelected = 6
    } 

    if (this.observationSelected == "Devoir non fait") {
        this.observationSelected = 7
    } 
    
    if (this.observationSelected == "Oublie") {
        this.observationSelected = 8
    } 

    var userInfoAPI = {
        date_time: this.observationDate,
        appreciation: this.observationSelected,
        user: userList.id
    }

    console.log(userInfoAPI)
   
   console.log(this.observationSelected)

    axios.post(this.apiAppreciation, userInfoAPI).then(response => { 
      console.log('response');
      console.log(response);
    });
    },

  },

  mounted() {
    this.token = localStorage.getItem('token'); // Token de l'API d'authentification (Comp. AccountLogin.vue) et le stock dans le navigateur
    this.user_id_cache = localStorage.getItem('user.id'); // Token de l'API d'authentification (Comp. AccountLogin.vue) et le stock dans le navigateur
    this.user_first_name_cache = localStorage.getItem('user.first_name'); // Token de l'API d'authentification (Comp. AccountLogin.vue) et le stock dans le navigateur
    this.user_last_name_cache = localStorage.getItem('user.last_name'); // Token de l'API d'authentification (Comp. AccountLogin.vue) et le stock dans le navigateur
    axios.get(this.apiUser).then((response) => (this.userList = response.data)); // API User
    axios.get(this.apiObservation).then((response) => (this.observationList = response.data)); // API Observation
    axios.get(this.apiUserId + this.user_id_cache).then((response) => (this.userInfo = response.data)); // API UserID
    
   
  },
};
</script>