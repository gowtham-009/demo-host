<template>
    <div>
        <div class="grid grid-cols-1 p-2">
         <div class=" p-1 flex justify-between w-full">
            <div class="mb-1 flex gap-5 justify-start items-center pn">
                <input type="checkbox">
                <label for="checkbox" class="text-gray-500 text-lg font-medium">Information</label>
            </div>
            <div class="mb-1 pn">
              <p class="text-gray-500 text-lg font-medium px-4 py-3">Project Name</p>
            </div>
            <div class="mb-1 flex md:flex-row md:items-center gap-2">
              <div class="relative">
                <input type="text" class="w-full md:w-auto px-4 py-3 focus:outline-none focus:border-blue-500" v-model="searchQuery" placeholder="Search user name...">
              </div>
            <button class="bg-blue-700 p-2 text-white text-md rounded mb-2 md:mb-0 md:mr-2">
              <i class="fa-solid fa-file p-1"></i>
              <span class="hidden md:inline">Team files</span>
            </button>            
            <button class="bg-white p-2 mb-2 md:mb-0 md:mr-2">
            <i class="fa-solid fa-bars text-gray-400"></i>
            </button>
            <button class="bg-white p-2 mb-2 md:mb-0">
              <i class="fa-solid fa-table text-gray-400"></i>
            </button>
            
          </div>
         </div>
      </div>
      <div class="container w-full p-2 bg-white">
        
          <div class="sub-container w-full px-5 py-2" style="background-color: #EFF4FA;">
              <div class="mini-container w-full p-2 bg-white">
                <div class="overflow-x-auto">
  <table class="min-w-full divide-y divide-gray-200">
    <thead>
      <tr>
        <th class="px-6 py-3 text-left text-md font-medium text-gray-600 uppercase tracking-wider">Customer ID</th>
        <th class="px-6 py-3 text-left text-md font-medium text-gray-600 uppercase tracking-wider">Users</th>
        <th class="px-6 py-3 text-left text-md font-medium text-gray-600 uppercase tracking-wider">Joined</th>
        <th class="px-6 py-3 text-left text-md font-medium text-gray-600 uppercase tracking-wider">Status</th>
        <th class="px-6 py-3 text-left text-md font-medium text-gray-600 uppercase tracking-wider">Purchased</th>
        <th class="px-6 py-3 text-left text-md font-medium text-gray-600 uppercase tracking-wider">Profile</th>
        <th class="px-6 py-3 text-left text-md font-medium text-gray-600 uppercase tracking-wider">Action</th>
      </tr>
    </thead>
    <tbody class="bg-white divide-y divide-gray-200">
      <tr v-for="user in sortedUsers":key="user.id">
        <td class="px-6 py-4 whitespace-nowrap"><h4 class="text-black-500 font-medium">{{ user.id }}</h4></td>
        <td class="px-6 py-4 whitespace-nowrap"><h4 class="text-black-500 font-medium">{{ user.name }}</h4><p class="text-gray-400">{{ user.email }}</p></td>
        <td class="px-6 py-4 whitespace-nowrap"><h4 class="text-black-500 font-medium">{{ user.date }}</h4></td>
        <td class="px-6 py-4 whitespace-nowrap"><p class="p-2 bg-green-400 rounded-md text-white flex items-center justify-center">{{ user.status }}</p></td>
        <td class="px-6 py-4 whitespace-nowrap"><h4 class="text-black-500 font-medium">{{ user.purchased }}</h4></td>
        <td class="px-6 py-4 whitespace-nowrap"><nuxt-link :to="`/user/${user.id}`" class="p-2 bg-blue-400 rounded-md text-white flex items-center justify-center">{{ user.profile }}</nuxt-link></td>

        <td class="px-6 py-4 whitespace-nowrap flex gap-3 mt-3">
          <i class="fa-solid fa-pen-to-square text-blue-500"></i>
          <i class="fa-solid fa-circle-check text-green-500"></i>
          <i class="fa-solid fa-trash text-red-500"></i>
        </td>
      </tr>
    </tbody>
  </table>
</div>
              </div>
          </div>
      </div>

    </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: '',
      
       users: [
       { "id":1, "name":"Gowtham", "email":"gowthamramachandran09@gmail.com", "date":"25/03/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":2, "name":"Kabilan", "email":"kabilan@gmail.com", "date":"26/03/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":3, "name":"Abilash", "email":"abilash@gmail.com", "date":"27/03/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":4, "name":"Andrews", "email":"andrews@gmail.com", "date":"28/03/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":5, "name":"Gopi", "email":"gopi@gmail.com", "date":"29/03/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":6, "name":"Diwakar", "email":"diwakar@gmail.com", "date":"30/03/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":7, "name":"Baby", "email":"baby@gmail.com", "date":"31/03/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":8, "name":"Arvindh", "email":"arvindh@gmail.com", "date":"01/04/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":9, "name":"Mosas", "email":"mosas@gmail.com", "date":"02/04/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":10, "name":"Puthi", "email":"puthi@gmail.com", "date":"03/04/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":11, "name":"Reeno", "email":"reeno@gmail.com", "date":"04/04/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":12, "name":"Baskar", "email":"baskar@gmail.com", "date":"05/04/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":13, "name":"Ragava", "email":"ragava@gmail.com", "date":"06/04/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":14, "name":"Dhuruvan", "email":"dhuru@gmail.com", "date":"07/04/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},
       { "id":15, "name":"Akash", "email":"akash@gmail.com", "date":"08/04/2024","status":"Paid","profile":"View","purchased":"Monthly Subscription"},

    
         // Add more user objects as needed
       ]
    }
  },
  computed: {
    sortedUsers() {
      if (this.searchQuery) {
        return this.users.filter(user => {
          return user.name.toLowerCase().includes(this.searchQuery.toLowerCase()) || user.date.toString().includes(this.searchQuery.toString);
        });
      } else {
        return this.users.slice().sort((a, b) => {
          return a.id - b.id;
        });
      }
    }
  }
}
</script>

<style>
@import url('~/assets/css/components.css');
</style>