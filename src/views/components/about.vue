<template>
  <div class="about" ref="aboutSection">
    <div class="container h-100">
      <div class="">
        <div class="about-left">
          <p class="txt ko">
            <span ref="titleWord1" class="title-word">THE </span>&nbsp;
            <span ref="titleWord2" class="title-word"> GOAL</span>
          </p>
          about-
        </div>
        about-
        <div class="about-right">
          <div class="desc ko">
            <p ref="descLine1" class="desc-line">
              저는 퍼블리셔로서, 마치 퍼즐을 맞추듯 섬세하고 정확하게 작업을
              완성하는 것을 좋아합니다.
            </p>
            <p ref="descLine2" class="desc-line">
              디자인과 코드 사이의 요소들을 빈틈없이 조화롭게 연결하며, 깔끔하고
              정돈된 결과물을 추구합니다.
            </p>
            <p ref="descLine3" class="desc-line">
              작은 디테일 하나도 놓치지 않으며, 전체 흐름 속에서 완벽하게
              맞아떨어지도록 만드는 데 집중합니다.
            </p>
            <br />
            <p ref="descLine4" class="desc-line">
              그런 성격 덕분에 웹 퍼블리셔로서 감각적인 디자인을 이해하고,
            </p>
            <p ref="descLine5" class="desc-line">
              책임감 있는 코드 작성과 유지보수를 중요하게 여깁니다.
            </p>
            <br /><br />
            <p ref="descLine6" class="desc-line">
              Vue와 React 같은 자바스크립트 기반 프레임워크를 익히고 활용하며
              빠른 판단력으로 문제를 해결해 나갑니다.
            </p>
            <p ref="descLine7" class="desc-line">
              또한, 소통을 통해 사용자 경험을 극대화하고 협업의 효율성을 높이는
              것을 중요하게 생각합니다. <br />
            </p>
            <p ref="descLine8" class="desc-line">
              접근성을 고려한 개발을 실천함으로써, 더 많은 사람이 편리하게
              이용할 수 있는 웹 환경을 만들어갑니다.
            </p>
            <p ref="descLine9" class="desc-line">
              완성도 높은 결과물을 통해 모두가 만족할 수 있는 웹을 구현하는 것이
              저의 목표입니다.
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { onMounted, ref } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: "AboutSection",
  setup() {
    // 섹션과 각 요소에 대한 ref
    const aboutSection = ref(null);
    const titleWord1 = ref(null);
    const titleWord2 = ref(null);
    const descLine1 = ref(null);
    const descLine2 = ref(null);
    const descLine3 = ref(null);
    const descLine4 = ref(null);
    const descLine5 = ref(null);
    const descLine6 = ref(null);
    const descLine7 = ref(null);
    const descLine8 = ref(null);
    const descLine9 = ref(null);

    onMounted(() => {
      // ScrollTrigger 플러그인 등록
      gsap.registerPlugin(ScrollTrigger);

      // GSAP 타임라인 생성 (ScrollTrigger와 연결)
      const tl = gsap.timeline({
        scrollTrigger: {
          trigger: aboutSection.value,
          start: "top 100%", // 섹션이 화면 80% 지점에 도달하면 애니메이션 시작
          toggleActions: "play none none none", // 스크롤 시 한 번만 재생
        },
      });

      // 1. 타이틀 애니메이션: 단어 단위로 타이핑 느낌
      tl.fromTo(
        titleWord1.value,
        { opacity: 0, x: -10 },
        { opacity: 1, x: 0, duration: 0.7, ease: "power2.out" }
      ).fromTo(
        titleWord2.value,
        { opacity: 0, x: -10 },
        { opacity: 1, x: 0, duration: 0.7, ease: "power2.out" },
        "-=0.2"
      );

      // 2. 본문 텍스트 애니메이션: 문장 단위로 타이핑 느낌
      tl.fromTo(
        descLine1.value,
        { opacity: 0, x: -20 },
        { opacity: 1, x: 0, duration: 0.5, ease: "power2.out" },
        "-=0.2"
      )
        .fromTo(
          descLine2.value,
          { opacity: 0, x: -20 },
          { opacity: 1, x: 0, duration: 0.4, ease: "power2.out" },
          "-=0.2"
        )
        .fromTo(
          descLine3.value,
          { opacity: 0, x: -20 },
          { opacity: 1, x: 0, duration: 0.4, ease: "power2.out" },
          "-=0.2"
        )
        .fromTo(
          descLine4.value,
          { opacity: 0, x: -20 },
          { opacity: 1, x: 0, duration: 0.4, ease: "power2.out" },
          "-=0.2"
        )
        .fromTo(
          descLine5.value,
          { opacity: 0, x: -20 },
          { opacity: 1, x: 0, duration: 0.4, ease: "power2.out" },
          "-=0.2"
        )
        .fromTo(
          descLine6.value,
          { opacity: 0, x: -20 },
          { opacity: 1, x: 0, duration: 0.4, ease: "power2.out" },
          "-=0.2"
        )
        .fromTo(
          descLine7.value,
          { opacity: 0, x: -20 },
          { opacity: 1, x: 0, duration: 0.4, ease: "power2.out" },
          "-=0.2"
        )
        .fromTo(
          descLine8.value,
          { opacity: 0, x: -20 },
          { opacity: 1, x: 0, duration: 0.4, ease: "power2.out" },
          "-=0.2"
        )
        .fromTo(
          descLine9.value,
          { opacity: 0, x: -20 },
          { opacity: 1, x: 0, duration: 0.4, ease: "power2.out" },
          "-=0.2"
        );
    });

    return {
      aboutSection,
      titleWord1,
      titleWord2,
      descLine1,
      descLine2,
      descLine3,
      descLine4,
      descLine5,
      descLine6,
      descLine7,
      descLine8,
      descLine9,
    };
  },
};
</script>

<style></style>
