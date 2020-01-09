<template>
  <div>
    <h2>{{ top_text }}</h2>
    <div class="button_container">
      <div>
        <button class="btn-square-shadow" v-on:click="reloadImg">{{more_button_text}}</button>
      </div>
      <div>
        <button class="btn-square-shadow green" v-on:click="searchImg">{{search_button_text}}</button>
      </div>
    </div>
    <img v-bind:style="[styles]" :src="image_src" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      top_text: "美しい風景写真はいかがですか",
      more_button_text: "More Pictures >> ",
      search_button_text: "Search ",
      image_src: "https://source.unsplash.com/random/?nature&landscape",
      styles: [],
      width: "",
      height: ""
    };
  },
  created() {
    this.setImgSize();
  },
  methods: {
    reloadImg() {
      this.setImgSize();
      this.$axios
        .get(
          "https://api.unsplash.com/photos/random?client_id=11a1069c4ee9005f963f6c511d920e6f7eb166ff9b9ba40def101f72e5696477&query=landscape,nature&w=" +
            this.width +
            "&h=" +
            this.height
        )
        .then(response => {
          this.image_src = response.data.urls.small;
        });
    },
    searchImg() {
      location.href = "http://sokkuri-trip.jp/";
    },
    setImgSize() {
      if (navigator.userAgent.match(/(iPhone|iPad|iPod|Android)/i)) {
        // スマホ・タブレット（iOS・Android）の場合の処理を記述
        this.image_src += "&375x375";
        this.styles.width = "375px";
        this.styles.height = "375px";
        this.width = "375";
        this.height = "375";
      } else {
        this.image_src += "&650x650";
        this.styles.width = "650px";
        this.styles.height = "650px";
        this.width = "650";
        this.height = "650";
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #35495e;
}

.btn-square-shadow {
  display: inline-block;
  padding: 0.5em 1em;
  text-decoration: none;
  background: #668ad8; /*ボタン色*/
  color: #fff;
  border-bottom: solid 4px #627295;
  border-radius: 3px;
  margin-bottom: 20px;
}
.btn-square-shadow:active {
  /*ボタンを押したとき*/
  -webkit-transform: translateY(4px);
  transform: translateY(4px); /*下に動く*/
  box-shadow: 0px 0px 1px rgba(0, 0, 0, 0.2); /*影を小さく*/
  border-bottom: none;
}

.button_container {
  display: flex;
  justify-content: space-evenly;
}

.green {
  background: #63cf94; /*ボタン色*/
  border-bottom: solid 4px #5ca88f;
}
</style>
