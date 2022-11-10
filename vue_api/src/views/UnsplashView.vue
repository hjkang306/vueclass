<template>
  <div>
    <HeaderCont />
    <TitleCont name1="Unsplash" name2="Api" />

    <section class="cont__refer">
      <div class="container">
        <div class="unsplash__inner">
          <div class="unsplash__slider"></div>
          <div class="unsplash__search"></div>
          <div class="unsplash__images">
            <!-- <img src="" alt=""> -->
            <ul>
              <li v-for="splash in splashes" :key="splash.id">
                <a :href="splash.links.download">
                  <img :src="splash.urls.regular" :alt="splash.id" />
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <ContactCont />
    <FooterCont />
  </div>
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import ContactCont from "@/components/ContactCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import { ref } from "vue";

export default {
  components: {
    HeaderCont,
    TitleCont,
    ContactCont,
    FooterCont,
  },

  setup() {
    const splashes = ref([]);
    const search = ref("retro");

    // const SearchSplash = () => {
    //   fetch(
    //     `https://api.unsplash.com/search/photos?client_id=pwTcmZX1BLEZXpcol69V_Z-fxMzCGK8nvL8kQ1iV8Hk&query=${search.value}&count=12`
    //   )
    //     .then((response) => response.json())
    //     .then((result) => (splashes.value = result))
    //     .catch((error) => console.log("error", error));
    // };
    // SearchSplash();

    const RandomSplash = () => {
      fetch(
        "https://api.unsplash.com/photos/random?client_id=pwTcmZX1BLEZXpcol69V_Z-fxMzCGK8nvL8kQ1iV8Hk&count=12"
      )
        .then((response) => response.json())
        .then((result) => (splashes.value = result))
        // .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    };
    RandomSplash();

    return {
      splashes,
      search,
      // SearchSplash,
      RandomSplash,
    };
  },
};
</script>

<style lang="scss">
.unsplash__images {
}
.unsplash__images ul {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.unsplash__images ul li {
  width: 22%;
  margin: 1%;
}
.unsplash__images ul li a {
}
.unsplash__images ul li a img {
}
</style>
