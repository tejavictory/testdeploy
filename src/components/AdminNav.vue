<template>
<div>
<div class="ui pointing stackable container big menu">
  <div class="item" id="navhead">
    <!-- <img src="/images/logo.png"> -->
    <span class="navhead"> Admin </span>
  </div>
  <a class="item" v-on:click="setActive('codeword')" :class="{ active: isActive('codeword') }">Codeword Sets</a>
  <a class="item" v-on:click="setActive('rmcourse')" :class="{ active: isActive('rmcourse') }">Remove Courses</a>
  <a class="item" v-on:click="setActive('insreq')" :class="{ active: isActive('insreq') }">Instructor Requests</a>
  <a class="item" v-on:click="setActive('rmusers')" :class="{ active: isActive('rmusers') }">Remove Users</a>
  <div class="right menu">
    <a class="item" v-on:click="logout">
      <i class="sign-out icon"></i>
    </a>
  </div>
</div>
</div>
</template>

<script>
export default {
    name: 'AdminNav',
    data() {
        return { activeItem: 'codeword' }
    },
    methods: {
        isActive: function (menuItem) {
            return this.activeItem === menuItem
        },
        setActive: function (menuItem) {
            this.activeItem = menuItem 
            this.$root.$emit('AdminNavContent', menuItem)
        },
        logout() {
            sessionStorage.removeItem('auth-token')
            this.$router.push('/login')
        },
    }
}
</script>

<style scoped>
 #navhead{
    font-weight: bold;
    background-color: rgba(0, 9, 61, 0.705);
    color:whitesmoke;
 }
 .menu{
   background-color: rgb(232, 230, 255)
 }

</style>