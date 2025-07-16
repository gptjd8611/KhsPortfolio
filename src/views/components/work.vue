<template>
  <div class="works" ref="works">
    <div class="container h-100">
      <div class="">
        <p ref="worksTitle" class="m-tit">WORKS</p>
        <p ref="workssubTitle" class="m-desc ko">
          제가 개인적으로 작업한 작업물입니다.
        </p>

        <ul ref="worksList" class="works-lists">
          <li
            v-for="(item, index) in workLists"
            :key="index"
            class="works-item"
          >
            <div class="works-img">
              <img :src="item.img" alt="" />
            </div>
            <p class="works-tit">{{ item.title }}</p>
            <p class="works-desc">
              {{ item.desc }}
            </p>
            <div class="works-btn-wrap">
              <a
                v-if="item.link"
                :href="item.link"
                target="blank"
                class="works-link"
              >
                View Site
              </a>
              <a :href="item.linkGit" target="blank" class="works-link git">
                View Github
              </a>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: "App",
  components: {},
  setup() {
    const workLists = ref([
      {
        img: require("@/assets/images/guide.png"),
        title: "React UI Component Guide​",
        desc: " 재사용성과 일관성을 고려해 설계한 React 기반 UI 컴포넌트 라이브러리입니다.디자인 시스템의 원칙을 바탕으로 다양한 UI 요소(예: Button, Select, Modal 등)를 공통화하여, 어디서든 가져다 쓸 수 있도록 컴포넌트화했습니다.",
        skills: ["SCSS", "React.js", "Typescript"],
        linkGit: "https://github.com/gptjd8611/reactGuide/tree/main/src",
      },
      {
        img: require("@/assets/images/movie.png"),
        title: "Search Movie App",
        desc: " OMDb(Open Movie Database) API를 활용하여 영화 데이터를 검색하고 리스트화하며, 상세 정보와 즐겨찾기 기능까지 구현한 React 기반 영화 검색 사이트입니다.",
        skills: ["SCSS", "React", "OMDB API"],
        link: "https://gptjd8611.github.io/movie-app/",
        linkGit: "https://github.com/gptjd8611/movie-app/tree/main/src",
      },
      {
        img: require("@/assets/images/redux.png"),
        title: "학생 출석부 & 입출금 가계부",
        desc: " Redux를 활용해 학생 출석부와 입출금 가계부를 통합 구현한 React 앱으로, 상태 관리 구조화와 반응형 UI, 실시간 통계 처리에 중점을 두었습니다.",
        skills: ["SCSS", "React", "Redux Toolkit"],
        link: "https://gptjd8611.github.io/redux-app/",
        linkGit: "https://github.com/gptjd8611/redux-app/tree/main",
      },
    ]);
    const works = ref(null);
    const worksTitle = ref(null);
    const workssubTitle = ref(null);
    const worksList = ref(null);

    onMounted(() => {
      // GSAP 타임라인 생성
      gsap.registerPlugin(ScrollTrigger);

      const tl = gsap.timeline({
        scrollTrigger: {
          trigger: works.value,
          start: "top 100%", // 섹션이 화면 80% 지점에 도달하면 애니메이션 시작
          toggleActions: "play none none none", // 스크롤 시 한 번만 재생
        },
      });

      // 메인 타이틀: 위에서 아래로 슬라이드 + 페이드인
      tl.fromTo(
        worksTitle.value,
        { y: -80, opacity: 0 },
        { y: 0, opacity: 1, duration: 1.2, ease: "power2.out" },
        "-=0.2"
      );

      // 서브 타이틀: 약간의 딜레이 후 페이드인
      tl.fromTo(
        workssubTitle.value,
        { opacity: 0 },
        { opacity: 1, duration: 1.1, ease: "power2.out" },
        "-=0.2" // 이전 애니메이션과 0.5초 겹치게
      );
      // works: 약간의 딜레이 후 페이드인
      tl.fromTo(
        worksList.value,
        { opacity: 0 },
        { opacity: 1, duration: 1.1, ease: "power2.out" },
        "-=0.2" // 이전 애니메이션과 0.5초 겹치게
      );
    });
    return {
      workLists,
      works,
      worksTitle,
      worksList,
      workssubTitle,
    };
  },
};
</script>

<style></style>
