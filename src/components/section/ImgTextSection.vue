<template>
  <section id="imgTextType" class="imgText__wrap" :class="attr">
    <h2 class="blind">가깝고도 먼 바다</h2>
    <div class="imgText__inner" :class="layout">
      <div class="imgText__txt">
        <span>이미지 텍스트 유형01</span>
        <h3>가깝고도 먼<br />바다</h3>
        <p>
          바다를 멀리서 볼 때와 가까이서 볼 때의 차이는 아주 색다른 경험이
          됩니다.
        </p>
        <ul>
          <li><a href="#">가까이서 본 파도</a></li>
          <li><a href="#">멀리서 본 파도</a></li>
          <li><a href="#">가까이서 본 해변</a></li>
          <li><a href="#">멀리서 본 해변</a></li>
          <li><a href="#">물 속에서의 바다</a></li>
          <li><a href="#">잔잔한 수평선</a></li>
        </ul>
      </div>
      <div class="imgText__img img1">
        <a href="#">근접 사진 보기</a>
      </div>
      <div class="imgText__img img2">
        <a href="#" class="blue">원거리 사진 보기</a>
      </div>
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
.imgText__inner {
  display: flex;
  justify-content: space-between;
}
.imgText__inner > div {
  width: 32%;
  height: 500px;
}
.imgText__txt {
}
.imgText__txt span {
  font-size: 16px;
  color: #666;
  text-decoration: underline;
  text-underline-position: under;
  margin-bottom: 20px;
  display: block;
}
.imgText__txt h3 {
  font-size: 50px;
  font-weight: 300;
  margin-bottom: 20px;
}
.imgText__txt p {
  font-size: 18px;
  font-weight: 300;
  line-height: 1.5;
  color: #666;
  margin-bottom: 10px;
}
.imgText__txt ul {
  font-size: 18px;
  font-weight: 300;
  line-height: 1.6;
}
.imgText__txt ul li {
  position: relative;
  padding-left: 20px;
}
.imgText__txt ul li a {
  color: #666;
}
.imgText__txt ul li::before {
  content: "";
  width: 5px;
  height: 5px;
  border-radius: 50%;
  position: absolute;
  left: 5px;
  top: 9px;
  background: #666;
}
.imgText__img {
  border-radius: 10px;
  position: relative;
}
.imgText__img a {
  position: absolute;
  left: 30px;
  bottom: 30px;
  background-color: #195048;
  color: #fff;
  font-size: 18px;
  padding: 10px 30px;
  border-radius: 30px;
  display: inline-block;
}
.imgText__img a.blue {
  background-color: #32507e;
}
.imgText__img.img1 {
  background: url(../../assets/img/imgText_bg01.jpg) no-repeat center / cover;
}
.imgText__img.img2 {
  background: url(../../assets/img/imgText_bg02.jpg) no-repeat center / cover;
}
@media (max-width: 960px) {
  .imgText__inner {
    flex-wrap: wrap;
  }
  .imgText__inner h3 {
    font-size: 40px;
  }
  .imgText__inner > div.imgText__txt {
    width: 100%;
    height: auto;
    text-align: center;
  }
  .imgText__txt p {
    margin-bottom: 60px;
  }
  .imgText__inner > div.imgText__txt ul {
    display: none;
  }
  .imgText__inner > div.imgText__img {
    width: 49%;
  }
}
@media (max-width: 600px) {
  .imgText__inner span {
    font-size: 14px;
    margin-bottom: 20px;
  }
  .imgText__inner h3 {
    font-size: 30px;
  }
  .imgText__txt p {
    margin-bottom: 50px;
    font-size: 16px;
  }
  .imgText__inner > div.imgText__img {
    width: 100%;
    height: 200px;
  }
  .imgText__inner > div.imgText__img.img1 {
    margin-bottom: 20px;
  }
  .imgText__img a {
    left: 20px;
    bottom: 20px;
  }
}
</style>
