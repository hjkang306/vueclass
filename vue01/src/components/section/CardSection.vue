<template>
  <section id="cardType" class="card__wrap" :class="attr">
    <h2>하루에 세 번 보는 바다</h2>
    <p>아침, 오후, 밤에 보는 바다의 각기 다른 모습입니다.</p>
    <div class="card__inner" :class="layout">
      <article class="card">
        <figure class="card__header">
          <img src="../../assets/img/card_bg01.jpg" alt="아침 바다 이미지" />
        </figure>
        <div class="card__body">
          <h3 class="tit">아침 바다 사진</h3>
          <p class="desc">
            아침의 바다는 물안개와 아침공기, 그리고 떠오르는 해의 노란 빛이
            오묘한 분위기를 만들어냅니다. 아침 바다만의 독특한 분위기를
            즐겨봅시다.
          </p>
          <a class="btn" href="#">
            더 자세히 보기
            <span aria-hidden="true">
              <svg
                width="65"
                height="8"
                viewBox="0 0 65 8"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M64.3536 4.35355C64.5488 4.15829 64.5488 3.84171 64.3536 3.64645L61.1716 0.464466C60.9763 0.269204 60.6597 0.269204 60.4645 0.464466C60.2692 0.659728 60.2692 0.976311 60.4645 1.17157L63.2929 4L60.4645 6.82843C60.2692 7.02369 60.2692 7.34027 60.4645 7.53553C60.6597 7.7308 60.9763 7.7308 61.1716 7.53553L64.3536 4.35355ZM0 4.5H64V3.5H0V4.5Z"
                  fill="black"
                />
              </svg>
            </span>
          </a>
        </div>
      </article>
      <article class="card">
        <figure>
          <img src="../../assets/img/card_bg02.jpg" alt="오후 바다 이미지" />
        </figure>
        <div class="card__body">
          <h3 class="tit">오후 바다 사진</h3>
          <p class="desc">
            오후의 바다는 슬슬 저물기 시작하는 해가 하늘의 색과 바다의 색을 더욱
            짙게 만들어줍니다. 따뜻하게 데워진 공기와 따뜻한 색감으로 물든
            바다를 즐겨봅시다.
          </p>
          <a class="btn" href="#">
            더 자세히 보기
            <span aria-hidden="true">
              <svg
                width="65"
                height="8"
                viewBox="0 0 65 8"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M64.3536 4.35355C64.5488 4.15829 64.5488 3.84171 64.3536 3.64645L61.1716 0.464466C60.9763 0.269204 60.6597 0.269204 60.4645 0.464466C60.2692 0.659728 60.2692 0.976311 60.4645 1.17157L63.2929 4L60.4645 6.82843C60.2692 7.02369 60.2692 7.34027 60.4645 7.53553C60.6597 7.7308 60.9763 7.7308 61.1716 7.53553L64.3536 4.35355ZM0 4.5H64V3.5H0V4.5Z"
                  fill="black"
                />
              </svg>
            </span>
          </a>
        </div>
      </article>
      <article class="card">
        <figure class="card__header">
          <img src="../../assets/img/card_bg03.jpg" alt="해질녘 바다 이미지" />
        </figure>
        <div class="card__body">
          <h3 class="tit">해질녘 바다 사진</h3>
          <p class="desc">
            해질녘의 바다는 저무는 해의 강렬한 붉은 빛이 바다와 하늘을
            물들입니다. 눈이 부신듯 점점 어두워지는 하늘과 함께 다채롭게 빛나는
            바다를 즐겨봅시다.
          </p>
          <a class="btn" href="#">
            더 자세히 보기
            <span aria-hidden="true">
              <svg
                width="65"
                height="8"
                viewBox="0 0 65 8"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M64.3536 4.35355C64.5488 4.15829 64.5488 3.84171 64.3536 3.64645L61.1716 0.464466C60.9763 0.269204 60.6597 0.269204 60.4645 0.464466C60.2692 0.659728 60.2692 0.976311 60.4645 1.17157L63.2929 4L60.4645 6.82843C60.2692 7.02369 60.2692 7.34027 60.4645 7.53553C60.6597 7.7308 60.9763 7.7308 61.1716 7.53553L64.3536 4.35355ZM0 4.5H64V3.5H0V4.5Z"
                  fill="black"
                />
              </svg>
            </span>
          </a>
        </div>
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
.card__inner {
  display: flex;
  justify-content: space-between; /* 컨텐츠의 양쪽 정렬 */
}
.card {
  width: 32%;
  background: #f5f5f5;
}
.card__body {
  padding: 24px;
}
.card__body .tit {
  font-size: 24px;
  margin-bottom: 10px;
}
.card__body .desc {
  font-size: 18px;
  line-height: 1.4;
  color: #666;
  margin-bottom: 20px;
  font-weight: 300;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 4;
  -webkit-box-orient: vertical;
}
@media (max-width: 960px) {
  .card__inner {
    flex-wrap: wrap;
  }
  .card {
    width: 49%;
  }
  .card:last-child {
    display: none;
  }
}
@media (max-width: 600px) {
  .card {
    width: 100%;
  }
  .card:first-child {
    margin-bottom: 20px;
  }
  .card__body {
    padding: 20px;
  }
  .card__body .desc {
    font-size: 16px;
  }
}
</style>
