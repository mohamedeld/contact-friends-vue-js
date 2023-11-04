<template>
  <form @submit.prevent="sendData">
    <div>
      <label>Name</label>
      <input type="text" name="name" v-model="userName" />
    </div>
    <div>
      <label>Phone</label>
      <input type="text" name="phone" v-model="userPhone" />
    </div>
    <div>
      <label>Email</label>
      <input type="text" name="email" v-model="userEmail" />
    </div>
    <div><button>Add Friend</button></div>
  </form>
</template>

<script>
export default {
  data: () => ({
    userName: "",
    userPhone: "",
    userEmail: "",
    
  }),
  methods: {
    sendData() {
      let userData = {
        id:new Date().toISOString(),
        name: this.userName,
        phone: this.userPhone,
        email: this.userEmail,
        
      };
      this.$emit("addNewFriend", userData);
     
    },
  },
  emits: ["addNewFriend"],
};
</script>

<style></style>
