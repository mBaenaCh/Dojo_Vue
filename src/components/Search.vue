<template>
  <v-container>
    <v-row>
      <v-col>
        <v-text-field v-model="word" label="OwO Whats dis"></v-text-field>
      </v-col>
      <v-col>
        <v-btn small @click="searchItem">Search</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  name: "Search",
  data: () => ({
      search: [],
      word: '',
  }),
  methods: {
      searchItem(){
          axios
            .get("https://pixabay.com/api/?key=18325849-94cafec8b0f30985ae8cfbdde&q="+this.word+"&image_type=photo")
            .then((response) => {
                this.search = response.data;
                this.$emit("searchResult",response.data);
            })
      }
  }
};
</script>