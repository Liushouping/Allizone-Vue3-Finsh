<script>
import { ref, reactive, onBeforeMount, computed, onMounted, onUnmounted } from "vue";
import _ from 'underscore';
import gsap from 'gsap';

import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default{
  name: "Home",
  setup() {
    const triggers = ScrollTrigger.getAll();
    // 第一幕
    const txtzero = ref(null);
    const logo = ref(null);
    const logotxt= ref(null);
    const lineone =ref(null);
    // 第二幕
    const txtone = ref(null);
    const titleone = ref(null);
    // 第三幕
    const txttwo = ref(null);
    const titletwo = ref(null);
    // 第三幕
    const txtthree = ref(null);
    const titlethree = ref(null);
    // 邊角文字
    const topbgtxt = ref(null);
    const bgtxt = ref(null);
    // 上面
    const topl = ref(null);
    const topll = ref(null);
    const topi = ref(null);
    const topz = ref(null);
    const topo =ref(null);
    const topn =ref(null);
    const tope =ref(null);
    // 左邊
    const leftl = ref(null);
    const leftll = ref(null);
    const lefti = ref(null);
    const leftz = ref(null);
    const lefto =ref(null);
    const leftn =ref(null);
    const lefte =ref(null);
    // 右下
    const righta = ref(null);
    const rightl = ref(null);
    const rightll = ref(null);
    const righti = ref(null);
    const rightz = ref(null);
    const righto = ref(null);
    const rightn = ref(null);
    const righte = ref(null);
    // 頁尾
    const Bottomdata = reactive({
      info : 'Copyright © 2022 ALLIZONE All Rights Reserved',
      year: new Date().getFullYear(),
      updatedInfo: computed(() => `Copyright © ${Bottomdata.year} ALLIZONE All Rights Reserved`)
    });

    const debounceFunc = (func, delay) => {
       let timer;
        return function(...args) {
           const context = this;
           clearTimeOut(timer);
           timer = setTimeOut(() => {
               func.apply(context, args);
           }, delay)
         }
    };
    function gsapSet() {
      ScrollTrigger.matchMedia({
        "(min-width: 368px)": () => {
          //
          gsap.from(logo.value, {
            y: 2000,
            opacity: 0,
            scale: 0,
            delay: 0.25,
            duration: 0.5,
          });
          gsap.to(logo.value, {
           scrollTrigger: {
            start: "top -80",
            end: "99999", 
            toggleClass: {
              className: 'logo-to', 
              targets: logo.value
            },
           },
           scale: 1
          });
          //
          gsap.from(logotxt.value, {
            y: 2000,
            opacity: 0,
            scale: 0,
            delay: 0.75,
            duration: 0.5,
          });
          gsap.to(logotxt.value, {
           scrollTrigger: {
            start: "top -10",
            end: "99999",
            toggleClass: {
              className: 'logotxt-to', 
              targets: logotxt.value
            },

           },
           scale: 1,
          });
          //
          gsap.set(topbgtxt.value, {
            opacity: 0,
          });

          gsap.to(topbgtxt.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=600px",
            end: "99999",
            scrub: true,
            toggleClass: "active",
            markers: false,
            toggleClass: {
              className: 'topbgtxt-to', 
              targets: topbgtxt.value
            },
           },
           // opacity:1,
          });
          //
          gsap.set(bgtxt.value, {
            opacity:0,
          });

          gsap.to(bgtxt.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=600px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity:1,
          });
          //
          gsap.set(titleone.value, {
            y: 300,
            opacity: 0,
            scale: 3,
          });

          gsap.to(titleone.value, {
           scrollTrigger: {
            trigger: txtzero.value,
            start: "top -30",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           onEnter() {
              async function play() {
                const sleep = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

                // 過渡動畫的時間間隔和延遲時間
                const intervalTime = 1000;
                const delayTime = 2000;

                // 設定文字的初始狀態
                $('.center').removeClass('hidden');
                $('.blurtext span:nth-child(1)').addClass('active');

                // 使用防抖函數控制 play 函數的執行次數
                const debouncedPlay = _.debounce(play, delayTime + 2 * intervalTime);

                // 隱藏第一個單字，並等待 0.5 秒後執行下一步動作
                $('.t').addClass('hidden');
                await sleep(3500);

                // 過渡動畫
                for (let i = 1; i < $('.blurtext span').length; i++) {
                  // 移除透明濾鏡動畫
                  $('.blurtext span.past').removeClass('past');
                  // 新增 past class, 移除 active class
                  $('.blurtext span.active').addClass('past').removeClass('active');
                  // 新增 active class，清除濾鏡動畫
                  $('.blurtext span.past + span').addClass('active');

                  // 如果所有單字都已經過渡完成，則跳出迴圈
                  if ($('.blurtext span.active').length == 0) {
                    break;
                  }

                  // 等待一段時間後繼續下一步動作
                  await sleep(intervalTime);
                }

                // 隱藏第一個單字，並等待 2 秒後執行下一步動作
                $('.t').addClass('hidden');
                await sleep(delayTime);

                // 使用防抖函數來控制函數的執行次數
                debouncedPlay();
              }

              play();

          },
           y: 200,
           scale: 1,
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.from(lineone.value, {
            y: 200,
            opacity: 0,
            scale: 0,
            delay: 1,
            duration: 0.5,
          });
          gsap.to(lineone.value, {
           scrollTrigger: {
            start: "top -10",
            end: "99999",
            toggleClass: {
              className: 'line-to', 
              targets: lineone.value
            },
           },
           scale: 1,
          });
          //
          gsap.set(titletwo.value, {
            y: 40,
            filter: "blur(16px)",
            opacity: 0,
            scale: 3,
          });

          gsap.to(titletwo.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           y: 0,
           scale: 1,
           opacity: 1,
           filter: "blur(0px)",
           duration: 0.25,
          });
          //
          gsap.set(titlethree.value, {
            y: 40,
            filter: "blur(16px)",
            opacity: 0,
            scale: 3,
          });

          gsap.to(titlethree.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           y: 0,
           scale: 1,
           opacity: 1,
           filter: "blur(0px)",
           duration: 0.25,
          });
          //
          gsap.set(leftl.value, {
            opacity: 0.1,
          });

          gsap.to(leftl.value, {
           scrollTrigger: {
            trigger: txtone.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftll.value, {
            opacity: 0.1,
          });

          gsap.to(leftll.value, {
           scrollTrigger: {
            trigger: txtone.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(lefti.value, {
            opacity: 0.1,
          });

          gsap.to(lefti.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftz.value, {
            opacity: 0.1,
          });

          gsap.to(leftz.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(lefto.value, {
            opacity: 0.1,
          });

          gsap.to(lefto.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(leftn.value, {
            opacity: 0.1,
          });

          gsap.to(leftn.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(lefte.value, {
            opacity: 0.1,
          });

          gsap.to(lefte.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(righta.value, {
            opacity: 0.1,
          });

          gsap.to(righta.value, {
           scrollTrigger: {
            trigger: txtone.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightl.value, {
            opacity: 0.1,
          });

          gsap.to(rightl.value, {
           scrollTrigger: {
            trigger: txtone.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightll.value, {
            opacity: 0.1,
          });

          gsap.to(rightll.value, {
           scrollTrigger: {
            trigger: txtone.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(righti.value, {
            opacity: 0.1,
          });

          gsap.to(righti.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightz.value, {
            opacity: 0.1,
          });

          gsap.to(rightz.value, {
           scrollTrigger: {
            trigger: txttwo.value,
            start: "top +=100px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(righto.value, {
            opacity: 0.1,
          });

          gsap.to(righto.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(rightn.value, {
            opacity: 0.1,
          });

          gsap.to(rightn.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
          //
          gsap.set(righte.value, {
            opacity: 0.1,
          });

          gsap.to(righte.value, {
           scrollTrigger: {
            trigger: txtthree.value,
            start: "top +=300px",
            end: "+=300",
            scrub: true,
            toggleClass: "active",
            markers: false,
           },
           opacity: 1,
           duration: 0.6,
          });
        },
      });
    };
    function shify() {
      let wordArray = ['Z', 'S'];
      let element = document.getElementsByClassName('text-flip')[0];
      let wordIndex = 1;

      let resetAnimation = function() {
        element.classList.remove('flip');
      };

      setInterval(function() {
        switch (wordIndex) {
          case 0:
            element.classList.add('flip');
            element.textContent = wordArray[wordIndex];
            wordIndex = 1;
            setTimeout(resetAnimation, 1000);
          break;

          case 1:
            element.classList.add('flip');
            element.textContent = wordArray[wordIndex];
            wordIndex = 0;
            setTimeout(resetAnimation, 1000);
          break;
        }
      }, 2500);
    }

    onMounted(() => {
      ScrollTrigger.refresh();
      gsapSet();
      shify();
    });
    onUnmounted(() => {
      triggers.forEach((trigger) => {
        trigger.kill();
      });
      ScrollTrigger.clearMatchMedia();
    });
    return {
      // timesRun,
      // interval,
      // 第一幕
      txtzero,
      logo,
      logotxt,
      lineone,
      // 第二幕
      txtone,
      titleone,
      // 第三幕
      txttwo,
      titletwo,
      // 第四幕
      txtthree,
      titlethree,
      // 邊角文字
      topbgtxt,
      bgtxt,
      // 上面
      topl,
      topll,
      topi,
      topz,
      topo,
      topn,
      tope,
      // 左邊
      leftl,
      leftll,
      lefti,
      leftz,
      lefto,
      leftn,
      lefte,
      // 右下
      righta,
      rightl,
      rightll,
      righti,
      rightz,
      righto,
      rightn,
      righte,
      // 頁尾
      Bottomdata
    }
  },
};
</script>
<template>
<div 
class="relative overflow-hidden" style="background: #020020;">
  <!--  -->
  <div ref="topbgtxt">
    <div 
    class="fixed top-[1rem] left-[1rem] sm:left-[2rem] flex flex-row text-[10px] sm:text-[18px] text-white tracking-[18px] sm:tracking-[36px] md:tracking-[50px] z-40 font-RandomNineBold">
        <span>A</span>
        <span ref="topl">L</span>
        <span ref="topll">L</span>
        <span ref="topi">I</span>
        <span ref="topz">Z</span>
        <span ref="topo">O</span>
        <span ref="topn">N</span>
        <span ref="tope">E</span>
    </div>
  </div>
  <div ref="bgtxt">
    <div 
    class="fixed top-[2.9rem] sm:top-[4.8rem] left-[1rem] sm:left-[2rem] flex flex-col text-[10px] sm:text-[18px] text-white z-40 font-RandomNineBold">
        <span ref="leftl">L</span>
        <span ref="leftll" class="mt-[0.7rem] md:mt-[33px]">L</span>
        <span ref="lefti" class="pl-[3px] mt-[0.7rem] md:mt-[33px]">I</span>
        <span ref="leftz" class="mt-[0.7rem] md:mt-[33px]">Z</span>
        <span ref="lefto" class="mt-[0.7rem] md:mt-[33px]">O</span>
        <span ref="leftn" class="mt-[0.7rem] md:mt-[33px]">N</span>
        <span ref="lefte" class="mt-[0.7rem] md:mt-[33px]">E</span>
    </div>
    <div 
    class="fixed bottom-[3.5rem] sm:bottom-[1rem] right-[0rem] flex flex-col text-[10px] sm:text-[18px] text-white  tracking-[18px] sm:tracking-[36px] z-40 font-RandomNineBold">
        <div class="flex flex-row justify-end">
          <span ref="righta">A</span>
          <span ref="rightl">L</span>
          <span ref="rightll">L</span>
        </div>
        <div class="flex flex-row justify-end mt-[10px]">
          <span ref="righti">I</span>
          <span ref="rightz" class="text-flip shiny">Z</span>
        </div>
        <div class="flex flex-row justify-end mt-[10px]">
          <span ref="righto">O</span>
          <span ref="rightn">N</span>
          <span ref="righte">E</span>
        </div>
    </div>
  </div>
  <!-- -->
  <!--  -->
  <div class="fixed left-[8px] lg:left-[450px] top-2 z-10 w-[600px] h-[600px] rounded-full blur-[200px] top_animate"></div>
  <div class="fixed right-8 bottom-8 z-10 w-[600px] h-[600px] rounded-full blur-[200px] right_animate"></div>
  <div class="fixed left-8 bottom-8 z-10 w-[600px] h-[600px] rounded-full blur-[200px] left_animate"></div>
  <!--  -->
  <section 
  ref="txtzero"
  class="w-full h-screen flex flex-col justify-center items-center">
    <img 
    ref="logo"
    src="/allizone-800-t.png" class="logo z-40">
    <h5 
    ref="logotxt"
    class="fixed flex justify-center items-center mt-[8rem] sm:mt-52 text-[1rem] sm:text-2xl md:text-[1.7rem] md:leading-10 text-white font-RandomNineBold tracking-[15px] sm:tracking-[20px] z-40" 
    style="text-indent: 1.1em;">ALLIZONE</h5>
    <span 
    ref="lineone"
    class="absolute left-[50%] divideline mt-[65vh] sm:mt-[580px] lg:mt-[500px] h-[60px] z-40"></span>

    <p 
    ref="titleone"
    class="absolute text-white text-center text-[1rem] sm:text-2xl md:text-[1rem] z-40 leading-[30px] pt-[30vh]">
    <span class="flex flex-row justify-center">
    all things are <span class="t blurtext pl-[0.7rem] w-[100px] h-[10px] leading-[1.9rem]">connecting</span><br>
    <div class="center hidden">
      <div class="blurtext pl-2">
        <span>connecting</span>
        <span>converging</span>
        <span>elevating</span>
        <span>virtualizing</span>
        <span>evolving</span>
        <span>decentralizing</span>
        <span>connecting</span>
      </div>
    </div>
    </span>

    read + write + ownership<br>
    one, two, three
    </p>
  </section>

  <!--  -->
  <section 
  ref="txttwo"
  class="w-full h-screen flex flex-col justify-center items-center">
    <p 
    ref="titletwo"
    class="text-white text-center z-40 leading-[30px]">
    is it virtual... is it reality...<br>
    or anything in between...<br><br>

    lots of questions<br>
    can be answered</p>
  </section>
  <!--  -->
  <section 
  ref="txtthree"
  class="w-full h-screen flex justify-center items-center">
    <p 
    ref="titlethree"
    class="text-white text-center z-40 leading-[30px]">
    one team - one vision<br>
    living and breathing in<br>
    multiple zones<br><br>

    ALLIZONE<br>
    web3 solutions<br>
    <a href="mailto:info@allizone.io" class="underline z-40">contact us</a></p>
  </section>
  <!--  -->
  <footer 
  class="fixed bottom-5 w-full flex flex-col justify-center items-center">
    <div 
    class="flex flex-col justify-center items-center">
      <a 
      class="text-white text-[10px]" 
      href="mailto:info@allizone.io">{{ Bottomdata.updatedInfo }}</a>
    </div>
  </footer>
</div>
</template>
