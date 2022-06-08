<template>
  <div class="student">
        <div>        
        <div v-if="token == null" class="flex h-screen bg-gray-200">
            Vous n'avez pas la permissions d'accéder à cette page
        </div>
        <div v-if="token != null" class="flex h-screen bg-gray-200">
            <div class="flex-1 flex flex-col overflow-hidden">
                <main class="flex-1 overflow-x-hidden overflow-y-auto bg-gray-200">
                    <div class="container mx-auto px-6 py-8">
                        <div class="flex justify-between">
                            <h3 class="text-gray-700 text-3xl font-medium">Gestioonie</h3>
                            <h3 class="text-gray-700 text-3xl font-medium">Bonjour {{ userInfo.first_name }}, bienvenue sur Gestioonie</h3>
                        </div>
                        <div class="mt-4">
                            <div class="flex flex-wrap -mx-6">
                                <div class="w-full px-6 sm:w-1/2 xl:w-1/3">
                                    <div class="flex items-center px-5 py-6 shadow-sm rounded-md bg-white">
                                        <div class="p-3 rounded-full bg-indigo-600 bg-opacity-75">
                                            <img class="h-8 w-8" src="../assets/runner-silhouette-svgrepo-com.svg" alt="arrivée_tarive">
                                        </div>
                                        <div class="mx-5">
                                            <h4 class="text-2xl font-semibold text-gray-700">2</h4>
                                            <div class="text-gray-500">Arrivées tardives</div>
                                        </div>
                                    </div>
                                </div>
        
                                <div class="w-full mt-6 px-6 sm:w-1/2 xl:w-1/3 sm:mt-0">
                                    <div class="flex items-center px-5 py-6 shadow-sm rounded-md bg-white">
                                        <div class="p-3 rounded-full bg-green-500 bg-opacity-75">
                                            <img class="h-8 w-8" src="../assets/iconmonstr-check-mark-15.svg" alt="absence_excusée">
                                        </div>
                                        <div class="mx-5">
                                            <h4 class="text-2xl font-semibold text-gray-700">24</h4>
                                            <div class="text-gray-500">Absences excusées</div>
                                        </div>
                                    </div>
                                </div>
        
                                <div class="w-full mt-6 px-6 sm:w-1/2 xl:w-1/3 xl:mt-0">
                                    <div class="flex items-center px-5 py-6 shadow-sm rounded-md bg-white">
                                        <div class="p-3 rounded-full bg-red-600 bg-opacity-75">
                                            <img class="h-8 w-8" src="../assets/iconmonstr-door-6.svg" alt="renvoiesimple">
                                        </div>
                                        <div class="mx-5">
                                            <h4 class="text-2xl font-semibold text-gray-700">1</h4>
                                            <div class="text-gray-500">Renvoi simple</div>
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
                                                    Appréciations
                                                </th>
                                                <th class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">
                                                    Date de l'appréciations
                                                </th>
                                                <th class="px-6 py-3 border-b border-gray-200 bg-gray-50 text-left text-xs leading-4 font-medium text-gray-500 uppercase tracking-wider">
                                                    Nom professeur(e)
                                                </th>
                                            </tr>
                                        </thead>
                                        <tbody class="bg-white">
                                            <tr>
                                                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200">
                                                    <div class="flex items-center">
                                                        <div class="ml-4">
                                                            <div class="text-sm leading-5 font-medium text-gray-900">Arrivées tardives</div>
                                                            <div class="text-sm leading-5 text-gray-500">AT</div>
                                                        </div>
                                                    </div>
                                                </td>
                                                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200">
                                                    <div class="text-sm leading-5 text-gray-900"></div>
                                                    <div class="text-sm leading-5 text-gray-900">31.05.2022</div>
                                                </td>
                                                <td class="px-6 py-4 whitespace-no-wrap border-b border-gray-200">
                                                   <div class="text-sm leading-5 text-gray-900">Mme Moto</div>
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
    userInfo : {},
    user_id_cache: null,
    user_first_name_cache: null,
    user_last_name_cache: null,
    apiAuth: "http://127.0.0.1:8003/api-token-auth/",
    apiUser: "http://127.0.0.1:8003/profile/user",
    apiAppreciation: "http://127.0.0.1:8003/appreciations",
    apiUserId: "http://127.0.0.1:8003/profile/user/",
    token: null,
  }),

  methods: {

  },
  mounted() {
    // axios.get(this.apiUser).then((response) => (this.userInfo = response.data)); // API User
    this.token = localStorage.getItem('token'); // Token de l'API d'authentification (Comp. AccountLogin.vue) et le stock dans le navigateur
    this.user_id_cache = localStorage.getItem('user.id'); // Token de l'API d'authentification (Comp. AccountLogin.vue) et le stock dans le navigateur
    this.user_first_name_cache = localStorage.getItem('user.first_name'); // Token de l'API d'authentification (Comp. AccountLogin.vue) et le stock dans le navigateur
    this.user_last_name_cache = localStorage.getItem('user.last_name'); // Token de l'API d'authentification (Comp. AccountLogin.vue) et le stock dans le navigateur
    axios.get("http://127.0.0.1:8003/profile/user/" + this.user_id_cache).then((response) => (this.userInfo = response.data)); // API User

  },
};
</script>