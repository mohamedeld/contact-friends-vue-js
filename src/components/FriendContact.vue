<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Favorite)':'' }}</h2>
    <button @click="toggleFavorite">Toggle Favorites</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ phone }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ email }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  data() {
    return {
      detailsAreVisible: false,
      
    };
  },
  props:{
    id:{
      type:String,
      required:true
    },
    name:{
      type:String,
      required:true
    },
    phone:{
      type:String,
      required:true
    },
    email:{
      type:String,
      required:true
    },
    isFavorite:{
      type:Boolean,
      required:false,
      default:false
    }
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite(){
      this.$emit('toggleFriendFavor',this.id)
    }
  },
  emits:['toggleFavorite']
};
</script>