<template>
  <div>
    <HeaderCont />
    <TitleCont name1="Movie" name2="Api" />
    <section>
      <div className="container">
        <h2>Popular Movies</h2>
        <div className="popular__box">
          <ul className="moviePop__list">
            <Swiper
              :effect="'coverflow'"
              :grabCursor="true"
              :centeredSlides="true"
              :slidesPerView="'auto'"
              :initialSlide="5"
              :autoplay="{
                delay: 2500,
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
              className="mySwiper"
            >
              <swiper-slide v-for="(slider, index) in sliders" :key="slider.id">
                <div className="item">
                  <a :href="`https://www.themoviedb.org/movie/${slider.id}`">
                    <div class="rank">{{ index + 1 }}</div>
                    <img
                      :src="`https://image.tmdb.org/t/p/w500/${slider.poster_path}`"
                      :alt="slider.title"
                    />
                  </a>
                </div>
              </swiper-slide>
            </Swiper>
          </ul>
        </div>
      </div>
    </section>

    <div className="movie__search">
      <div className="container">
        <h2>검색하기</h2>
        <form @submit.prevent="SearchMovies()">
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
    <!-- search -->

    <section className="cont__movie">
      <div className="container">
        <div className="movie__inner">
          <h2>Movies</h2>
          <ul className="movie__list">
            <li v-for="movie in movies" :key="movie.id">
              <a :href="`https://www.themoviedb.org/movie/${movie.id}`">
                <img
                  :src="`https://image.tmdb.org/t/p/w500${movie.poster_path}`"
                  :alt="movie.title"
                />
                <span className="original_title">{{
                  movie.original_title
                }}</span>
                <em>
                  <span className="original_language">
                    {{ movie.original_language }}
                  </span>
                  <span className="vote_average">{{ movie.vote_average }}</span>
                  <span className="popularity">{{ movie.popularity }}</span>
                </em>
                <span className="overview ellipsis6">{{ movie.overview }}</span>
                <span className="release_date">{{ movie.release_date }}</span>
                <span className="title">{{ movie.title }}</span>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </section>

    <ContactCont />
    <FooterCont />
  </div>
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import ContactCont from "@/components/ContactCont.vue";
import { ref } from "vue";

import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, EffectCoverflow, Pagination } from "swiper";
import "swiper/css/effect-coverflow";
import "swiper/css/pagination";
import "swiper/css";

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
    Swiper,
    SwiperSlide,
  },
  setup() {
    const movies = ref([]);
    const sliders = ref([]);
    const search = ref("mission");
    const SearchMovies = async () => {
      await fetch(
        `https://api.themoviedb.org/3/search/movie?api_key=191b7edccc4ad9d9ad42c6a2cce972d7&query=${search.value}&page=1`
      )
        .then((response) => response.json())
        .then((result) => {
          console.log(result);
          movies.value = result.results;
          search.value = "";
        })
        .catch((error) => console.log(error));
    };
    SearchMovies();
    const TopMovies = () => {
      fetch(
        `https://api.themoviedb.org/3/movie/popular?api_key=191b7edccc4ad9d9ad42c6a2cce972d7`
      )
        .then((response) => response.json())
        .then((result) => (sliders.value = result.results))
        .catch((error) => console.log(error));
    };
    TopMovies();
    return {
      movies,
      sliders,
      search,
      SearchMovies,
      modules: [Autoplay, EffectCoverflow, Pagination],
    };
  },
};
</script>

<style lang="scss">
// container
.container {
  h2 {
    color: var(--black);
    font-size: 28px;
    margin-bottom: 10px;
  }
}

// movie__inner
.movie__inner {
  padding-bottom: 200px;

  h2 {
    text-align: center;
    font-size: 28px;
    color: var(--black);
    margin-bottom: 50px;

    span {
      font-weight: 600;
      margin-right: 15px;
      font-size: 34px;
    }
  }
}

.movie__list {
  display: flex;
  flex-wrap: wrap;

  img {
    width: 100%;
    margin-bottom: 10px;
  }
  li {
    border: 1px solid var(--bg-light-border);
    width: 21%;
    margin: 2%;
    padding: 1%;
    justify-content: space-between;

    a {
      align-items: center;
      width: 100%;
      color: var(--black);
      text-align: center;

      em {
        padding: 5px 0;
        font-family: var(--font-kor2);
        border-top: 1px solid var(--bg-light-border);
        border-bottom: 1px solid var(--bg-light-border);
      }

      .original_title {
        width: 100%;
        height: 67px;
        display: inline-block;
        word-break: keep-all;
        margin-bottom: 20px;
        font-size: 24px;
        font-weight: 700;
      }
      .original_language {
        display: inline-block;
        width: 30%;
      }
      .vote_average {
        display: inline-block;
        width: 40%;
      }
      .popularity {
        display: inline-block;
        width: 30%;
      }
      .overview {
        width: 100%;
        height: 135px;
        display: inline-block;
        text-align: justify;
        margin-top: 20px;
      }
      .release_date {
        display: inline-block;
        margin-top: 16px;
        width: 100%;
        font-family: var(--font-kor2);
      }
      .title {
        display: inline-block;
        width: 100%;
        font-size: 12px;
        color: rgba(0, 0, 0, 0.8);
        font-family: var(--font-kor2);
      }
      .ellipsis6 {
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 6;
        -webkit-box-orient: vertical;
      }
    }
  }
}

// movie__search
.movie__search {
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
    background: var(--white);
    border: 1px solid var(--black);
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
    border-radius: 20px;
    border: 0;
    font-family: var(--font-kor3);
    z-index: 100;
    cursor: pointer;
  }
}

// .swiper
// .swiper {
//   padding: 25px !important;
//   user-select: none;
// }
.swiper-coverflow {
  overflow: hidden;
}
.swiper-pagination-bullet {
  background: rgba(0, 0, 0, 0.8) !important;
}
.swiper-pagination-bullet-active {
  background: var(--black) !important;
}
.swiper-slide {
  width: 30%;
  margin-bottom: 30px;
}

// rank
.rank {
  position: absolute;
  font-size: 5vw;
  color: var(--black);
  top: -20px;
  left: 40px;
  transform: translateX(-50%);
  -webkit-text-stroke: 2px var(--white);
  -webkit-text-fill-color: var(--black);
}
</style>
