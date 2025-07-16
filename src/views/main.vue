<template>
  <div class="main-wrap">
    <header class="header">
      <div class="header-inner">
        <a href="" class="header-logo"
          ><img src="@/assets/images/logo.svg" alt=""
        /></a>
      </div>
    </header>
    <div class="main">
      <div class="main-inner" ref="curtain">
        <h1 ref="mainTitle" class="main-title">PUBLISHER <br /></h1>
        <p ref="subTitle" class="main-sub-title ko">
          <span ref="word1" class="main-word">"Welcome to </span>
          <span ref="word2" class="main-word">my </span>
          <span ref="word3" class="main-word"> portfolio" </span>
        </p>
        <!-- <button ref="ctaButton" class="cta-button">scroll</button> -->
      </div>
      <div class="main-content">
        <!-- 배경 비디오 -->
        <video
          class="background-video"
          autoplay
          width="100vw"
          muted
          loop
          playsinline
        >
          <source src="@/assets/images/bg.mp4" type="video/mp4" />
          Your browser does not support the video tag.
        </video>
        <div class="inner-cont container">
          <div class="txt-area">
            <div class="txt-top fill">
              <h2 class="headline ko" ref="title1">
                <span
                  class="word"
                  style="
                    translate: none;
                    rotate: none;
                    scale: none;
                    transform: translate(0px, 0px);
                  "
                  >도전을 즐기고</span
                >
              </h2>
              <h2 class="headline ko" ref="title2">
                <span
                  class="word"
                  style="
                    translate: none;
                    rotate: none;
                    scale: none;
                    transform: translate(0px, 0px);
                  "
                  >문제해결에
                </span>
              </h2>
            </div>
            <div class="txt-bottom fill">
              <h2 class="headline ko" ref="title3">
                <span
                  class="word"
                  style="
                    translate: none;
                    rotate: none;
                    scale: none;
                    transform: translate(0px, 0px);
                  "
                >
                  흥미를</span
                >
              </h2>
              <h2 class="headline ko" ref="title4">
                <span
                  class="word"
                  style="
                    translate: none;
                    rotate: none;
                    scale: none;
                    transform: translate(0px, 0px);
                  "
                  >느끼는 UI 개발자</span
                >
              </h2>
            </div>
          </div>
        </div>
        <img
          ref="circle1"
          src="@/assets/images/one1.svg"
          alt=""
          class="circle circle1"
        />
        <img
          ref="circle2"
          src="@/assets/images/one2.svg"
          alt=""
          class="circle circle2"
        />
      </div>
    </div>
    <about />
    <project />
    <work />
    <contact />
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import gsap from "gsap";

import About from "./components/about.vue";
import Contact from "./components/contact.vue";
import Project from "./components/project.vue";
import Work from "./components/work.vue";

export default {
  name: "App",
  components: { About, Contact, Project, Work },
  setup() {
    const mainTitle = ref(null);
    const ctaButton = ref(null);

    // 각 단어에 대한 ref
    const word1 = ref(null);
    const word2 = ref(null);
    const word3 = ref(null);
    const circle1 = ref(null);
    const circle2 = ref(null);
    const curtain = ref(null);

    const title1 = ref(null);
    const title2 = ref(null);
    const title3 = ref(null);
    const title4 = ref(null);

    onMounted(() => {
      // GSAP 타임라인 생성
      const tl = gsap.timeline();

      // 메인 타이틀: 위에서 아래로 슬라이드 + 페이드인
      tl.fromTo(
        mainTitle.value,
        { y: -50, opacity: 0 },
        { y: 0, opacity: 1, duration: 0.8, ease: "power2.out" }
      );

      // 서브 타이틀: 약간의 딜레이 후 페이드인
      // tl.fromTo(
      //   subTitle.value,
      //   { opacity: 0 },
      //   { opacity: 1, duration: 0.8, ease: "power2.out" },
      //   "-=0.5" // 이전 애니메이션과 0.5초 겹치게
      // );

      // 각 단어에 순차적으로 애니메이션 적용
      tl.fromTo(
        word1.value,
        { opacity: 0, y: 20 },
        { opacity: 1, y: 0, duration: 0.6, ease: "power2.out" },
        "-=0.2"
      )
        .fromTo(
          word2.value,
          { opacity: 0, y: 20 },
          { opacity: 1, y: 0, duration: 0.6, ease: "power2.out" },
          "-=0.3" // 이전 애니메이션과 0.3초 겹치게
        )
        .fromTo(
          word3.value,
          { opacity: 0, y: 20 },
          { opacity: 1, y: 0, duration: 0.6, ease: "power2.out" },
          "-=0.3"
        );

      // 6. 커튼 올라감
      tl.to(curtain.value, {
        y: "-100%",
        duration: 1.5,
        display: "none",
        opacity: 0,
        ease: "power4.inOut",
      });

      // 버튼: 아래에서 위로 슬라이드 + 페이드인
      tl.fromTo(
        ctaButton.value,
        { opacity: 0, y: 30 },
        { opacity: 1, y: 0, duration: 0.8, ease: "power2.out" },
        "-=0.3"
      );
      // 1. 타이틀 애니메이션: 단어 단위로 타이핑 느낌
      tl.fromTo(
        title1.value,
        { opacity: 0, x: -10 },
        { opacity: 1, x: 0, duration: 0.6, ease: "power2.out" }
      )
        .fromTo(
          title2.value,
          { opacity: 0, x: -10 },
          { opacity: 1, x: 0, duration: 0.6, ease: "power2.out" },
          "-=0.2"
        )
        .fromTo(
          title3.value,
          { opacity: 0, x: -10 },
          { opacity: 1, x: 0, duration: 0.6, ease: "power2.out" },
          "-=0.3"
        )
        .fromTo(
          title4.value,
          { opacity: 0, x: -10 },
          { opacity: 1, x: 0, duration: 0.6, ease: "power2.out" },
          "-=0.4"
        );

      // 2. 원 애니메이션: 타이틀 애니메이션 후 등장 (opacity 제외, scale로 등장 효과)
      tl.fromTo(
        [circle1.value, circle2.value],
        { scale: 0 },
        { scale: 1, duration: 1, ease: "power2.out" },
        "-=0.3"
      );

      // 3. 원의 멀어졌다가 가까워지는 반복 애니메이션
      gsap.to(circle1.value, {
        x: -100, // 왼쪽으로 이동
        duration: 2,
        ease: "sine.inOut",
        repeat: -1, // 무한 반복
        yoyo: true, // 왕복 애니메이션
      });

      gsap.to(circle2.value, {
        x: 100, // 오른쪽으로 이동
        duration: 2,
        ease: "sine.inOut",
        repeat: -1,
        yoyo: true,
      });
    });

    return {
      mainTitle,
      word1,
      word2,
      word3,
      ctaButton,
      circle1,
      circle2,
      curtain,
      title1,
      title2,
      title3,
      title4,
    };
  },
};
</script>

<style></style>
