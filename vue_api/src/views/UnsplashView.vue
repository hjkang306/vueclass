<template>
  <div>
    <HeaderCont />
    <TitleCont name1="Unsplash" name2="Api" />

    <section className="unsplash__list">
      <div className="container">
        <div className="unsplash__box">
          <ul className="unsplash__random">
            <Swiper
              :effect="'coverflow'"
              :grabCursor="true"
              :centeredSlides="true"
              :slidesPerView="'auto'"
              :initialSlide="1"
              :autoplay="{
                delay: 1500,
                disableOnInteraction: false,
              }"
              :coverflowEffect="{
                rotate: 50,
                stretch: 0,
                depth: 100,
                modifier: 1,
                slideShadows: true,
              }"
              :pagination="true"
              :modules="modules"
              class="mySwiper"
            >
              <swiper-slide v-for="slider in sliders" :key="slider.id">
                <li>
                  <a :href="slider.links.download">
                    <img
                      :src="slider.urls.regular"
                      :alt="slider.urls.alt_description"
                    />
                  </a>
                </li>
              </swiper-slide>
            </Swiper>
          </ul>
        </div>
      </div>
    </section>
    <!-- swiper -->

    <!-- <div className="unsplash__btn">
      <div className="container">
        <button type="submit" v-on:click="onClick1">spring</button>
        <button type="submit" v-on:click="onClick2">summer</button>
        <button type="submit" v-on:click="onClick3">fall</button>
        <button type="submit" v-on:click="onClick4">winter</button>
        <button type="submit" v-on:click="onClick5">sky</button>
        <button type="submit" v-on:click="onClick6">space</button>
        <button type="submit" v-on:click="onClick7">green</button>
        <button type="submit" v-on:click="onClick8">sea</button>
      </div>
    </div> -->
    <!-- unsplash__btn -->

    <div className="unsplash__search">
      <div className="container">
        <h2>검색하기</h2>
        <form @submit.prevent="SearchSplash()">
          <input
            type="search"
            id="search"
            placeholder="검색하세요!"
            v-model="search"
          />
          <button type="submit">검색</button>
        </form>
      </div>
    </div>
    <!-- unsplash__search -->

    <section className="cont__unsplash">
      <div className="container">
        <div className="unsplash__inner">
          <ul>
            <li v-for="splash in splashes" :key="splash.links">
              <a :href="splash.links.download">
                <img
                  :src="splash.urls.regular"
                  :alt="splash.urls.alt_description"
                />
              </a>
            </li>
          </ul>
        </div>
      </div>
    </section>
    <!-- cont__unsplash -->

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

import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/effect-coverflow";
import "swiper/css/pagination";
import { Autoplay, EffectCoverflow, Pagination } from "swiper";

export default {
  components: {
    HeaderCont,
    TitleCont,
    ContactCont,
    FooterCont,
    Swiper,
    SwiperSlide,
  },

  setup() {
    const splashes = ref([]);
    const sliders = ref([]);
    const search = ref("retro");

    const SearchSplash = async () => {
      // 서치이미지
      await fetch(
        `https://api.unsplash.com/search/photos?client_id=pwTcmZX1BLEZXpcol69V_Z-fxMzCGK8nvL8kQ1iV8Hk&query=${search.value}&per_page=32`
      )
        .then((response) => response.json())
        .then((result) => {
          console.log(result);
          splashes.value = result.results;
          search.value = "";
        })
        .catch((error) => console.log("error", error));
    };
    SearchSplash();

    const SplashSlide = () => {
      // 랜덤이미지(슬라이드)
      fetch(
        "https://api.unsplash.com/photos/random?client_id=pwTcmZX1BLEZXpcol69V_Z-fxMzCGK8nvL8kQ1iV8Hk&count=10"
      )
        .then((response) => response.json())
        .then((result) => (sliders.value = result))
        // .then((result) => console.log(result))
        .catch((error) => console.log("error", error));
    };
    SplashSlide();

    return {
      splashes,
      sliders,
      search,
      SearchSplash,
      modules: [Autoplay, EffectCoverflow, Pagination],
    };
  },
};
</script>

<style lang="scss">
// cont__unsplash
.cont__unsplash {
  ul {
    column-count: 4;
    column-gap: 20px;
    width: 100%;
  }

  li {
    margin-bottom: 20px;

    img {
      border-radius: 5px;
    }
  }
}

// unsplash__search
.unsplash__search {
  margin-bottom: 100px;

  .container {
    position: relative;
  }
  h2 {
    color: var(--black);
    font-size: 40px;
    text-indent: -9999px;
    height: 0;
  }
  input {
    background: var(--bg-light);
    border: 1px solid var(--bg-dark-border);
    border-radius: 50px;
    color: var(--black);
    width: 100%;
    padding: 10px 30px;
    font-family: var(--font-kor2);
  }
  button {
    position: absolute;
    right: 5px;
    top: 15px;
    width: 50px;
    height: 35px;
    background: var(--bg-dark);
    color: var(--white);
    border-radius: 20px;
    border: 0;
    font-family: var(--font-kor3);
    z-index: 100;
    cursor: pointer;
  }
}
</style>
