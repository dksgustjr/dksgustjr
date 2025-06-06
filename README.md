<!DOCTYPE html>
<html lang="ko">

<head>
  <meta charset="UTF-8" />
  <title>감사의 다이얼</title>
  <style>
    body {
      position: relative;
      font-family: 'Arial', sans-serif;
      text-align: center;
      padding: 2rem;
      overflow: hidden;
    }

    h1 {
      margin: 80px 0 50px;
      font-size: 2rem;
      color: #282828;
    }

    .dial-wrapper {
      position: relative;
      max-width: 500px;
      max-height: 500px;
      margin: 0 auto;
      position: relative;
      user-select: none;
      top: 0px;
    }

    .dial {
      position: relative;

      width: 100%;
      height: 100%;
      transform-origin: center center;
      transition: transform 0.3s;
    }

    .card {
      position: absolute;

      width: 100px;
      height: 100px;
      background-color: #fff;
      border-radius: 1rem;
      box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
      position: absolute;
      transform: translate(-50%, -50%);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-size: 0.9rem;
      padding: 0.5rem;
      text-align: center;
      transition: transform 0.2s, z-index 0.2s ease, background-color 0.3s ease;
    }

    .card:hover{
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
    }

    .student-name {
      font-weight: bold;
      color: #333;
    }

    .card-preview {
      position: absolute;
      top: 283%;
      left: 50%;
      width: 350px;
      height: 350px;
      background-color: #fff;
      border-radius: 50%;
      box-shadow: 0 2.5px 10px rgba(0, 0, 0, 0.2);
      transform: translate(-50%, -50%) scale(0);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-size: 1.1rem;
      padding: 1rem;
      z-index: 2000;
      pointer-events: none;
      text-align: center;
      transition: transform .5s cubic-bezier(0.645, 0.045, 0.355, 1), opacity 0.3s;
      opacity: 0;
    }

    .card-preview.show {
      transform: translate(-50%, -50%) scale(1);
      opacity: 1;
    }

    .message {
      display: none;
    }

    .card-preview .message {
      display: block;
      color: #555;
      margin-top: 0.5rem;
    }

    .dial-center {
      position: absolute;
      left: 50%;
      width: 1255.555575493141592px;
      height: 1255.555575493141592px;
      background: radial-gradient(#fff, #ffdddd);
      border-radius: 50%;
      transform: translate(-50%, 0);
      box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.2);
      z-index: -1000;
    }

    .dial-center2 {
      position: absolute;
      top: 50%;
      left: 50%;
      width: calc(100% - 50px);
      height: calc(100% - 50px);
      /* background-color:#f7dde1; */
      border-radius: 50%;
      transform: translate(-50%, -50%);
      /* box-shadow: 0 0 6px rgba(0, 0, 0, 0.2); */
      z-index: -999;
    }

    .no1:hover{
      background-color: #b8f1a5;
    }
    .no2:hover{
      background-color: #010101;
      color: #fff;
    }
    
    .no3:hover{
      background-color: rgb(199, 152, 250);
    }
    .no4:hover{
      background-color: #000000;
    }
    .no5:hover{
      background-color: #dc4e4e;
    }
    .no6:hover{
      background-color: #66a2db ;
    }
    .no7:hover{
      background-color: blue;
    }
    .no8:hover{
      background-color: #f60606;
    }
    .no9:hover{
      background-color: skyblue;
    }
    .no10:hover{
      background-color: skyblue;
    }
    .no11:hover{
      background-color: yellowgreen;
    }
    .no12:hover{
      background-color: rgb(152, 63, 236);
    }
    .no13:hover{
      background-color: lightblue;
    }
    .no14:hover{
      background-color: #4f90cc;
    }
    .no15:hover{
      background-color: #515763;
    }
    .no16:hover{
      background-color: green;
    }
    .no17:hover{
      background-color: #8a9352;
    }
    .no18:hover{
      background-color: #88a7c9;
    }
    .no19:hover{
      background-color: #9CD5C2;
    }
    .no20:hover{
      background-color: #D6F1F5;
    }
    .no21:hover{
      background-color: #e9a6d5;
    }
  </style>
</head>

<body>
  <h1>박세희선생님</h1>
  <div class="dial-wrapper" id="wrapper">
    <div class="dial-center">
      <div class="dial" id="dial">

      </div>
    </div>
  </div>
  

  <script>
    const students = [
      ["안드레", "선생님 덕분에 수업이 즐거웠어요!"],
      ["이준호", "한달 동안 즐거웠습니다"],
      ["강민준", "늘 저희에게 웃음과 긍정을 아낌없이 주시는 것 같아 감사했습니다."],
      ["권시후", "항상 웃는 얼굴로 대해주셔서 감사해요."],
      ["김세원", "짧았지만 정말 소중한 시간이었어요!"],
      ["김준엽", "많이 부족했던 저희에게 과분한 사랑 감사했습니다."],
      ["김지원", "짧지만 즐거웠습니다."],
      ["김태준", "정말 좋은 추억이 됐습니다!"],
      ["김효준", "저희반 힘드셨을텐데 봐주셔서 감사했습니다."],
      ["노우영", "다음에 또 뵐 수 있으면 좋겠어요!"],
      ["안현석", "저희 반 아이들 항상 예뻐해주시고 사랑으로 대해주셔서 감사해요.나중에 뵐수 있을 꼭뵈요!"],
      ["오윤석", "짧은 시간 동안 감사했습니다."],
      ["윤서현", "한달동안 감사했습니다!"],
      ["이미선", "앞으로도 멋진 선생님 되세요!"],
      ["이재성", "선생님 덕분에 웃을 일이 많았어요."],
      ["이희찬", "감사한 마음 잊지 않을게요!"],
      ["정시헌", "선생님, 정말 감사했습니다!"],
      ["정하민", "그동안 고생 많으셨습니다."],
      ["최성윤", "선생님 봄이 가득한 오월 보내세요요"],
      ["한지윤", "세희쌤은 이미 눈부시지만 훨씬 빛나기를 바래요!"],
      ["허지애", "선생님 사랑해요! 잊지 않을게요 💕"]
    ];

    // const no1 = document.querySelector(".no1").parentNode
    // no1.parentNode.style.background = "linear-gradient(#fff, #000)"

    const dial = document.getElementById("dial");
    const wrapper = document.getElementById("wrapper");
    const count = students.length;
    const radiusPercent = 40;
    const cards = [];

    let currentRotation = 0;
    let previewCard = null;
    let isDragging = false;
    let startAngle = 0;
    let lastAngle = 0;
    let velocity = 0;
    let animationFrame;

    students.forEach((student, i) => {
      const angle = (360 / count) * i;
      const radians = angle * (Math.PI / 180);
      let index = 1

      const card = document.createElement("div");
      card.className = "card";
      card.classList.add(`no${i + 1}`)
      

      const x = 50 + radiusPercent * Math.cos(radians);
      const y = 50 + radiusPercent * Math.sin(radians);

      card.style.left = `${x}%`;
      card.style.top = `${y}%`;

      card.innerHTML = `
        <div class="student-name">${i + 1}번 ${student[0]}</div>
        <div class="message">${student[1]}</div>
      `;

      card.addEventListener("mouseenter", () => {
        if (previewCard) return;

        previewCard = document.createElement("div");
        previewCard.className = "card-preview";
        previewCard.innerHTML = `
          <div class="student-name">${i + 1}. ${student[0]}</div>
          <div class="message">${student[1]}</div>
        `;

        setTimeout(() => previewCard.classList.add("show"), 10);
        document.body.appendChild(previewCard);
      });

      card.addEventListener("mouseleave", () => {
        if (previewCard) {
          previewCard.classList.remove("show");
          setTimeout(() => {
            previewCard.remove();
            previewCard = null;
          }, 200);
        }
      });

      dial.appendChild(card);
      cards.push(card);
    });

    function updateCardRotation() {
      cards.forEach((card) => {
        const rect = card.getBoundingClientRect();
        const centerX = window.innerWidth / 2;
        const centerY = window.innerHeight / 2;

        const distance = Math.sqrt(
          Math.pow(rect.left + rect.width / 2 - centerX, 2) +
          Math.pow(rect.top + rect.height / 2 - centerY, 2)
        );
        

        const scale = Math.max(1, 2 - distance );
        card.style.transform = `translate(-50%, -50%) rotate(${-currentRotation}deg) scale(${scale.toFixed(2)})`;
        card.style.zIndex = Math.floor(1000 - distance); 
      });
    }

    function getAngle(cx, cy, ex, ey) {
      return Math.atan2(ey - cy, ex - cx) * (180 / Math.PI);
    }

    function animateInertia() {
      if (Math.abs(velocity) < 0.01) {
        cancelAnimationFrame(animationFrame);
        return;
      }

      currentRotation += velocity;
      velocity *= 0.99; // 관성 감쇠 비율

      dial.style.transform = `rotate(${currentRotation}deg)`;
      updateCardRotation();

      animationFrame = requestAnimationFrame(animateInertia);
    }

    wrapper.addEventListener("mousedown", (e) => {
      isDragging = true;
      const rect = wrapper.getBoundingClientRect();
      const centerX = rect.left + rect.width / 2;
      const centerY = rect.top + rect.height / 2;
      startAngle = getAngle(centerX, centerY, e.clientX, e.clientY) - currentRotation;
      lastAngle = currentRotation;
      cancelAnimationFrame(animationFrame);
    });

    window.addEventListener("mousemove", (e) => {
      if (!isDragging) return;
      const rect = wrapper.getBoundingClientRect();
      const centerX = rect.left + rect.width / 2;
      const centerY = rect.top + rect.height / 2;
      const angle = getAngle(centerX, centerY, e.clientX, e.clientY);
      currentRotation = angle - startAngle;

      velocity = currentRotation - lastAngle;
      lastAngle = currentRotation;

      dial.style.transform = `rotate(${currentRotation}deg)`;
      updateCardRotation();
    });

    window.addEventListener("mouseup", () => {
      if (!isDragging) return;
      isDragging = false;
      animateInertia();
    });

    wrapper.addEventListener("touchstart", (e) => {
      isDragging = true;
      const touch = e.touches[0];
      const rect = wrapper.getBoundingClientRect();
      const centerX = rect.left + rect.width / 2;
      const centerY = rect.top + rect.height / 2;
      startAngle = getAngle(centerX, centerY, touch.clientX, touch.clientY) - currentRotation;
      lastAngle = currentRotation;
      cancelAnimationFrame(animationFrame);
    });

    window.addEventListener("touchmove", (e) => {
      if (!isDragging) return;
      const touch = e.touches[0];
      const rect = wrapper.getBoundingClientRect();
      const centerX = rect.left + rect.width / 2;
      const centerY = rect.top + rect.height / 2;
      const angle = getAngle(centerX, centerY, touch.clientX, touch.clientY);
      currentRotation = angle - startAngle;

      velocity = currentRotation - lastAngle;
      lastAngle = currentRotation;

      dial.style.transform = `rotate(${currentRotation}deg)`;
      updateCardRotation();
    });

    window.addEventListener("touchend", () => {
      if (!isDragging) return;
      isDragging = false;
      animateInertia();
    });

    updateCardRotation();
  </script>
</body>

</html>
