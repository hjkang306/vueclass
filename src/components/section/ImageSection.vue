<template>
  <section id="imageType01" class="image__wrap" :class="attr">
    <h2>잔잔하거나 거칠거나</h2>
    <p>
      바다의 두가지 모습을 알고 계시나요? 잔잔하거나 거칠거나, 바다의 두가지
      면모
    </p>
    <div class="img__inner" :class="layout">
      <article class="image img1">
        <h3 class="image__tit">잔잔한 바다</h3>
        <p class="image__desc">
          잔잔한 수면 아래로 산란되어 들어오는 햇빛을 보고 있자면 마음이 편안해
          집니다. 천천히 움직이는 물살에 몸을 맡겨보세요.
        </p>
        <a class="image__btn" href="#">자세히 보기</a>
      </article>
      <article class="image img2">
        <h3 class="image__tit">거친 파도의 바다</h3>
        <p class="image__desc">
          비가 오거나 바람이 많이 부는 날이면, 바다의 물결은 거칠게 흔들립니다.
          높이 솟아올라 내리치는 역동적인 바다를 감상해 보세요.
        </p>
        <a class="image__btn" href="#">자세히 보기</a>
      </article>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    attr: String,
    layout: String,
  },
};
</script>

<style>
.img__inner {
  display: flex;
  justify-content: space-between;
}
.image {
  width: 49%;
  height: 370px;
  color: #fff;
  padding: 200px 30px 30px;
  box-sizing: border-box;
}
.image.img1 {
  background: url(../../assets/img/imageType01_01.jpg) no-repeat center;
}
.image.img2 {
  background: url(../../assets/img/imageType01_02.jpg) no-repeat center;
}
.image__tit {
  font-size: 32px;
  margin-bottom: 10px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.image__desc {
  font-size: 16px;
  font-weight: 300;
  margin-bottom: 10px;
  line-height: 1.5;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}
.image__btn {
  font-size: 16px;
  color: #fff;
  background-color: #1f345a;
  padding: 10px 20px;
  display: inline-block;
}
@media (max-width: 960px) {
}
@media (max-width: 600px) {
  .img__inner {
    flex-direction: column;
  }
  .image {
    width: 100%;
    padding: 210px 20px 20px 20px;
  }
  .image:first-child {
    margin-bottom: 20px;
  }
  .image__tit {
    font-size: 24px;
  }
}
</style>
