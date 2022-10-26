<template>
  <div>
    <HeaderLayout fonts="nexon" />
    <SliderSection fonts="nexon" />
    <image-section attr="nexon section" layout="container" />
    <img-text-section attr="nexon section gray" layout="container" />
    <card-section attr="nexon section" layout="container" />
    <banner-section fonts="gmark" />
    <text-section attr="nexon section" layout="container" />
    <FooterLayout attr="nexon section gray" layout="container" />
  </div>
</template>

<script>
import FooterLayout from "./components/layout/FooterLayout.vue";
import HeaderLayout from "./components/layout/HeaderLayout.vue";
import BannerSection from "./components/section/BannerSection.vue";
import CardSection from "./components/section/CardSection.vue";
import ImageSection from "./components/section/ImageSection.vue";
import ImgTextSection from "./components/section/ImgTextSection.vue";
import SliderSection from "./components/section/SliderSection.vue";
import TextSection from "./components/section/TextSection.vue";

export default {
  name: "App",
  components: {
    HeaderLayout,
    FooterLayout,
    SliderSection,
    ImageSection,
    ImgTextSection,
    CardSection,
    BannerSection,
    TextSection,
  },
};
</script>
