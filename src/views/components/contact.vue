<template>
  <div class="contact" ref="contact">
    <div class="container h-100">
      <div class="flex-box">
        <div class="contact-left">
          <p ref="contactTitle" class="name">Kim HyeSung</p>
          <p ref="subTitle" class="desc ko">
            공부하고 만들어본 작업의 결과물들을 담았습니다.<br />
            배울것이 아직 더 많지만 쌓여가는 경험과 함께<br />
            성장하는 사람이 되고싶습니다.
          </p>
        </div>
        <div class="contact-right">
          <p class="email">E-mail : gptjd8611@naver.com</p>
          <div class="bototm">
            <div class="list">
              <a href="">github</a>
              <a href="">velog</a>
            </div>
            <p class="copyright">© 2025 Kim-HyeSung All Rights Reserved</p>
          </div>
        </div>
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
    const contact = ref(null);
    const contactTitle = ref(null);
    const subTitle = ref(null);

    onMounted(() => {
      // GSAP 타임라인 생성
      gsap.registerPlugin(ScrollTrigger);

      const tl = gsap.timeline({
        scrollTrigger: {
          trigger: contact.value,
          start: "top 100%", // 섹션이 화면 80% 지점에 도달하면 애니메이션 시작
          toggleActions: "play none none none", // 스크롤 시 한 번만 재생
        },
      });

      // 메인 타이틀: 위에서 아래로 슬라이드 + 페이드인
      tl.fromTo(
        contactTitle.value,
        { y: -80, opacity: 0 },
        { y: 0, opacity: 1, duration: 1.2, ease: "power2.out" },
        "-=0.2"
      );

      // 서브 타이틀: 약간의 딜레이 후 페이드인
      tl.fromTo(
        subTitle.value,
        { opacity: 0 },
        { opacity: 1, duration: 1.1, ease: "power2.out" },
        "-=0.2" // 이전 애니메이션과 0.5초 겹치게
      );
    });
    return {
      contact,
      contactTitle,
      subTitle,
    };
  },
};
</script>

<style></style>
