<template>
  <div class="project" ref="preoject">
    <div class="slider-container" ref="sliderContainer">
      <div
        class="slide work-item"
        v-for="(slide, index) in slides"
        :key="index"
      >
        <div class="inner">
          <div class="img-box">
            <img :src="slide.img" alt="" />
            <span class="pagination">0{{ index + 1 }}</span>
          </div>
          <h3 class="title">{{ slide.title }}</h3>

          <div class="txt-box">
            <p class="desc">
              {{ slide.desc }}
            </p>
            <div class="keyword">
              <span v-for="(skill, index) in slide.skills" :key="index"
                >#{{ skill }}</span
              >
            </div>
          </div>
          <div class="btn-box">
            <a :href="slide.link" target="_blank">
              {{
                slide.title == "개인(React UI Component Guide)"
                  ? "View github"
                  : "Code Review"
              }}
              <img src="@/assets/images/arrow.svg" alt="" />
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from "vue";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  name: "App",
  components: {},
  setup() {
    // const works = ref(null);

    //슬라이드
    const slides = ref([
      {
        img: require("@/assets/images/lg.png"),
        title: "AIDD TARA",
        desc: " React를 활용해 TARA DataBridge의 ECU 관리 및 설정 UI와 로직/LLM 비교 UI를 개발. ECU 타입별 컴포넌트(디스플레이, Sigfox 등) 관리, Sigfox 설정(백엔드 서버, 페이로드), 로직 TARA와 LLM TARA 비교(보안 속성, 시나리오, 리스크 분석) 기능을 포함. 동적 필터링, 체크박스 선택, 비교 테이블로 사용자 효율성 향상, 반응형 디자인 적용.",
        skills: ["SCSS", "React.js", "Typescript"],
        link: "https://velog.io/@gptjd8611/AIDD-TARA",
      },
      {
        img: require("@/assets/images/hr.png"),
        title: "HDP-사내 HR 솔루션",
        desc: " Vue를 활용해 사내 HR 솔루션의 대시보드 UI를 개발. 워크스페이스 관리, 프로젝트 진행 상황, 근태 관리(출근/퇴근 시간), 캘린더 일정 관리 기능을 포함한 대시보드를 구현. 직원 생산성과 팀 협업을 향상시키기 위한 인터랙티브 UI 제공, 실시간 데이터 업데이트와 반응형 디자인 적용.",
        skills: ["SCSS", "Vue3", "animation", "chart.js"],
        link: "https://velog.io/@gptjd8611/HDP-%EC%82%AC%EB%82%B4-HR-%EC%86%94%EB%A3%A8%EC%85%98-%EB%8C%80%EC%8B%9C%EB%B3%B4%EB%93%9C-%EA%B0%9C%EB%B0%9C%EC%8B%9C%EC%8A%A4%ED%85%9C",
      },
      {
        img: require("@/assets/images/kon.png"),
        title: "곤지암 TV앱 관리자 페이지",
        desc: " Vue를 활용해 곤지암 리조트의 객실 메시지 관리 솔루션 대시보드 UI를 개발. 관리자가 객실 고객에게 메시지를 전송하고, 전송 현황(전체/성공/실패 메시지 수), 통계(월별 메시지 전송 추이, TV 채널별 메시지 분포)를 시각화한 대시보드와 메시지 관리 기능 구현. 실시간 데이터 업데이트와 직관적인 UI로 관리 효율성 향상.",
        skills: ["SCSS", "Vue3", "chart.js"],
        link: "https://velog.io/@gptjd8611/%EA%B3%A4%EC%A7%80%EC%95%94-TV%EC%95%B1-%EA%B4%80%EB%A6%AC%EC%9E%90-%ED%8E%98%EC%9D%B4%EC%A7%80",
      },
      {
        img: require("@/assets/images/lg.png"),
        title: "LG VMS",
        desc: " Vue 3의 Composition API를 활용해 차량 관리 대시보드 UI를 구현. 차량 상태(배터리 잔량, 주행 거리), 데이터 사용량, GPS 상태, 차량 진단(Battery Prognosis) 데이터를 시각화한 차트와 위젯을 포함. SCSS로 반응형 레이아웃 설계, 다양한 화면 크기에서 최적화된 UI 제공.",
        skills: ["SCSS", "Vue3", "chart.js"],
        link: "https://velog.io/@gptjd8611/VMS",
      },
      {
        img: require("@/assets/images/lg.png"),
        title: "LG 튀봇 관리 시스템",
        desc: " Vue를 활용해 LG 튀봇 관리 시스템의 대시보드 UI를 개발. 메뉴 관리(메뉴 목록, 상세 정보), 메시지 관리(메시지 목록, 발송 상태), 서비스 관리 기능을 포함한 관리자 UI 구현. 동적 데이터 테이블과 팝업 UI를 통해 관리자가 메뉴와 메시지를 효율적으로 관리할 수 있도록 지원, 실시간 데이터 업데이트와 반응형 디자인 적용.",
        skills: ["SCSS", "Vue3", "Javascript"],
        link: "https://velog.io/@gptjd8611/LG-%ED%8A%80%EB%B4%87-%EA%B4%80%EB%A6%AC-%EC%8B%9C%EC%8A%A4%ED%85%9C",
      },
      {
        img: require("@/assets/images/benz.png"),
        title: "Benz EQS infotainment system",
        desc: " Mercedes-Benz EQS 차량의 인포테인먼트 시스템 테스트를 위한 고품질UI를 Vue 3로 구현. 운전자 인터페이스(계기판, 내비게이션, 미디어 플레이어)와 설정 패널(밝기 조절, 카메라/센서 ON/OFF 등)을 포함한 대시보드 UI를 퍼블리싱하고, 사용자 입력(range 값 변경)에 따라 실시간으로 데이터(예: 밝기 값, 조명 강도)를 동적으로 업데이트하는 기능을 개발.",
        skills: ["Vue3", "Javascript"],
        link: "https://velog.io/@gptjd8611/Benz-EQS-infotainment-system",
      },
      {
        img: require("@/assets/images/os.png"),
        title: "OSSTEM IMPLANT",
        desc: " Vue 3를 활용해 오스템 임플란트의 사내 시스템 UI 퍼블리싱에 참여. 배치도와 연구 문서 목록 UI를 담당하여, 전시 공간 안내와 연구 문서 데이터를 시각화하는 인터페이스 구현. 직관적인 UI와 반응형 디자인으로 사용자 경험 개선에 기여.",
        skills: ["Vue3", "Javascript", "animation"],
        link: "https://velog.io/@gptjd8611/OSSTEM-IMPLANT",
      },
    ]); // 슬라이드 4개
    const preoject = ref(null); // 섹션 참조
    const sliderContainer = ref(null); // 컨테이너 참조
    let scrollTriggerInstance = null;
    onMounted(() => {
      // GSAP 타임라인 생성
      gsap.registerPlugin(ScrollTrigger);

      // ScrollTrigger 초기화
      ScrollTrigger.normalizeScroll(true); // 터치 스크롤 최적화

      // GSAP 애니메이션 설정
      gsap.to(sliderContainer.value, {
        x: () => -(sliderContainer.value.scrollWidth - window.innerWidth), // 슬라이드 끝까지 이동
        ease: "none",
        scrollTrigger: {
          trigger: preoject.value,
          pin: true, // 섹션 고정
          scrub: 0.5, // 스크롤과 부드럽게 동기화 (값 줄여 반응성 개선)
          start: "top top", // 섹션이 뷰포트 상단에 닿을 때 시작
          end: () =>
            `+=${sliderContainer.value.scrollWidth - window.innerWidth + 100}`, // 추가 여유 공간
          invalidateOnRefresh: true, // 리사이즈 시 재계산
          onUpdate: (self) => {
            // 스크롤 진행도 확인
            console.log("Progress:", self.progress);
          },
          onLeave: () => {
            // 마지막 슬라이드 후 새로고침
            ScrollTrigger.refresh();
          },
        },
      });

      // ScrollTrigger 인스턴스 저장
      scrollTriggerInstance = ScrollTrigger.getAll().find(
        (st) => st.trigger === preoject.value
      );

      // 리사이즈 시 새로고침
      window.addEventListener("resize", () => {
        ScrollTrigger.refresh();
      });
    });
    onUnmounted(() => {
      // 정리
      if (scrollTriggerInstance) {
        scrollTriggerInstance.kill();
      }
      window.removeEventListener("resize", ScrollTrigger.refresh);
    });
    return {
      slides,
      preoject,
      sliderContainer,
    };
  },
};
</script>

<style></style>
