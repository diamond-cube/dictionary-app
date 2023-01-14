<template>
  <form
    class="form-group container w-50"
    style="
      display: flex;
      justify-content: left;
      flex-direction: row;
      column-gap: 3px;
    "
    @submit.prevent="searchWord()"
  >
    <input class="form-control" v-model="word" />
    <button class="btn btn-light" :disabled="word.length === 0">Search</button>
  </form>
  <br />

  <div class="card container p-2" v-if="isSearched === true">
    <h2>{{ wordName }} [ {{ wordPhonetic }} ]</h2>
    <hr />
  </div>
</template>

<script setup>
import { ref } from "vue";
import Axios from "axios";
import Swal from "sweetalert2";

const url = "https://api.dictionaryapi.dev/api/v2/entries/en/";

let isSearched = ref(false);
let word = ref("");
let wordData = ref([]);
let wordName = ref("");
let wordMeanings = ref([]);
let wordPhonetic = ref("");

const searchWord = () => {
  Axios.get(url + word.value.toLowerCase())
    .then((res) => {
      wordData.value = res.data;
      wordName.value = res.data[0].word;
      wordPhonetic.value = res.data[0].phonetics[1].text;
      isSearched.value = true;

      console.log(res);
    })

    .catch(() => {
      isSearched.value = false;
      Swal.fire("No such word exists!", "Enter a valid word", "error");
    });
};
</script>
