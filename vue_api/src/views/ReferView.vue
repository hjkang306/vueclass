<template>
  <div>
    <HeaderCont />
    <TitleCont name1="Reference" name2="Api" />

    <section className="cont__refer">
      <div className="container">
        <div className="refer__inner">
          <h2>CSS Properties</h2>
          <ul class="refer__list">
            <li v-for="refer in refers" :key="refer.title">
              <span className="num">{{ refer.num }}</span>
              <span className="star__name">
                <span className="descStar">{{ refer.descStar }}</span>
                <span className="name">{{ refer.name }}</span>
              </span>
              <span className="desc">{{ refer.desc }}</span>
              <!-- <span className="values__initial">
                <span className="values__d">{{ refer.values }}</span>
                <span className="initial">{{ refer.initial }}</span>
              </span> -->
              <span className="syntax">{{ refer.syntax }}</span>
              <span className="descApple">{{ refer.descApple }}</span>
              <!-- <span className="definition__d">{{ refer.definition }}</span> -->
              <span className="ver__link">
                <span className="descVer">{{ refer.descVer }}</span>
                <a
                  :href="`https://developer.mozilla.org/en-US/docs/Web/CSS/${refer.name}`"
                >
                  MDN
                </a>
              </span>
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
    const refers = ref([]);

    const reference = () => {
      fetch("https://hjkang306.github.io/react_api/src/utils/reference01.json")
        .then((response) => response.json())
        // .then((result) => console.log(result.cssRefer))
        .then((result) => (refers.value = result.cssRefer))
        .catch((error) => console.log("error", error));
    };
    reference();

    return {
      refers,
      reference,
    };
  },
};
</script>

<style lang="scss">
.refer__inner {
  padding-bottom: 200px;

  h2 {
    font-size: 30px;
    color: var(--black);
  }
}

.refer__list {
  // border: 1px solid var(--bg-light-border);

  li {
    margin: 10px 0;
    border-radius: 10px;
    border: 1px solid var(--bg-light-border);
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: center;
    color: var(--black);
    background: var(--bg-light);
    text-align: justify;
    transition: transform 0.3s;

    &:hover {
      transform: scale(1.2);
    }

    a,
    details,
    details > span,
    span {
      display: inline-block;
      padding: 5px;
    }
    a {
      color: var(--black);
      flex: 0.5;
      text-align: center;
    }

    .num {
      text-align: center;
      flex: 0.5;
      border-right: 1px solid var(--bg-light-border);
    }
    .star__name {
      text-align: center;
      flex: 1;
      border-right: 1px solid var(--bg-light-border);
    }
    .descStar {
      display: block;
      // flex: 1;
      border-bottom: 1px solid var(--bg-light-border);
    }
    .name {
      display: block;
      // flex: 1;
      // border-right: 1px solid var(--bg-light-border);
    }
    .desc {
      flex: 4;
      border-right: 1px solid var(--bg-light-border);
      word-break: keep-all;
    }
    .values__initial {
      flex: 2;
      border-right: 1px solid var(--bg-light-border);
    }
    .values__d {
      // flex: 1;
      display: block;
      border-bottom: 1px solid var(--bg-light-border);
    }
    .initial {
      display: block;
      // flex: 1;
      // border-right: 1px solid var(--bg-light-border);
    }
    .syntax {
      flex: 2;
      border-right: 1px solid var(--bg-light-border);
    }
    .descApple {
      flex: 3;
      border-right: 1px solid var(--bg-light-border);
    }
    .ver__link {
      flex: 1;
    }
    .descVer {
      display: block;
      border-bottom: 1px solid var(--bg-light-border);
      // flex: 1;
      // border-right: 1px solid var(--bg-light-border);
    }
    .definition__d {
      flex: 2;
    }
  }
}
</style>
