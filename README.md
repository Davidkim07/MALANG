# MALANG
MALANG
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>서연 ❤️ 동현</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&family=Merriweather:wght@400;700&display=swap" rel="stylesheet" />
  <style>
    :root {
      --primary: #ff6b81;
      --accent: #ff4d6d;
      --bg: #f9f4f8;
      --card-bg: #ffffff;
      --text: #333333;
      --muted: #777777;
      --radius: 1rem;
      --transition: 0.3s ease;
    }
    * { box-sizing: border-box; margin:0; padding:0; }
    body { background: var(--bg); font-family: 'Poppins', sans-serif; color: var(--text); }
    header { background: var(--card-bg); padding: 1.5rem; text-align: center; font-family: 'Merriweather', serif; font-size: 2rem; color: var(--primary); border-bottom: 2px solid var(--primary); }
    nav { display: grid; grid-template-columns: repeat(auto-fit, minmax(120px,1fr)); gap: .5rem; padding: .5rem 1rem; }
    nav button { padding: .75rem; background: var(--primary); color: #fff; border: none; border-radius: var(--radius); font-family: 'Poppins', sans-serif; font-weight: 600; transition: background var(--transition), transform var(--transition); }
    nav button:hover { background: var(--accent); transform: translateY(-3px); }
    nav button:disabled { opacity: .5; cursor: not-allowed; }
    main { padding: 1rem; display: flex; flex-direction: column; align-items: center; gap: 1rem; }
    .card { width: 100%; max-width: 800px; background: var(--card-bg); border-radius: var(--radius); padding: 1.5rem; box-shadow: 0 4px 12px rgba(0,0,0,0.1); }
    .view { display: none; }
    .view.active { display: block; }
    ul { list-style: none; padding: 0; margin: 0; }
    li { padding: .5rem 0; border-bottom: 1px solid #eee; font-family: 'Poppins', sans-serif; }
    li.current { font-weight: 800; color: white; background: black; padding: 0.5rem; border-radius: .5rem; }
    #survey .emoji-btn { font-size: 2rem; background: transparent; border: none; cursor: pointer; margin: 0 .3rem; }
    #survey-input, #survey-thanks, #survey-entries, #btn-view-survey { display: none; }
    textarea { width: 100%; padding: .75rem; border: 1px solid #ccc; border-radius: .5rem; font-family: 'Poppins', sans-serif; }
    button.action { margin-top: .75rem; padding: .5rem 1rem; background: var(--primary); color: #fff; border: none; border-radius: .75rem; font-family: 'Poppins', sans-serif; font-weight: 600; cursor: pointer; transition: background var(--transition); }
    button.action:hover { background: var(--accent); }
    #day-counter p { font-family: 'Merriweather', serif; font-size: 1.25rem; text-align: center; }
  </style>
</head>
<body>
  <header>서연 ❤️ 동현</header>
  <nav>
    <button id="btn-plan-dong">동현 일정</button>
    <button id="btn-plan-seo">서연 일정</button>
    <button id="btn-rules">규칙 보기</button>
    <button id="btn-checkin" disabled>출석체크</button>
    <button id="btn-survey">설문조사</button>
  </nav>
  <main>
    <section id="day-counter" class="card">
      <p id="day-count">–</p>
    </section>
    <section id="plan-dong" class="view card">
      <h2>동현 일정</h2>
      <ul id="dong-schedule"></ul>
    </section>
    <section id="plan-seo" class="view card">
      <h2>서연 일정</h2>
      <ul id="seo-schedule"></ul>
    </section>
    <section id="rules" class="view card">
      <h2>💖 우리 사랑 지키는 규칙 💖</h2>
      <ul id="rules-content">
        <li>🫶 싸울 때 지켜야 할 것들</li>
        <li>나쁜 말 하지 않기 (내가 듣는다고 생각하고 말하기)</li>
        <li>“야”, “니”, “너” 같은 말 대신 이름 부르기</li>
        <li>존댓말 사용하기</li>
        <li>말 다 듣고 나서 말하기</li>
        <li>일이 벌어진 후 15분은 “알겠어”만 말하기</li>
        <li>싸움 회피 금지</li>
        <li>자존심보단 사랑, 인정은 쿨하게</li>
        <li>“헤어지자” 절대 금지</li>
        <li>화해 손 내밀면 받아주기</li>
        <li>싸움 후 “사랑해” 말하고 전화하기 💗</li>
        <li>밤샘 후 감사 표현</li>
        <li>피곤하면 휴식 필수</li>
        <li>이성 친구 사적 대화·만남 금지</li>
        <li>가벼운 미소 OK, 선 넘는 말엔 철벽</li>
        <li>몸 접촉 금지</li>
        <li>모든 일 보고하기</li>
        <li>스크린 쉐어 주3회</li>
        <li>의심 금지, 서로 믿어주기</li>
        <li>“싫어” 솔직하게 표현</li>
        <li>솔직함엔 감사, 화내지 않기</li>
        <li>시간 필요하면 하루 안으로 주기</li>
        <li>인맥 자랑 금지, 질투 적당히</li>
        <li>연락 꾸준, 예상 시간 공유</li>
        <li>표현 자주 하기!</li>
        <li>끝날 땐 브리핑</li>
        <li>사랑 잊지 않기 ❤️</li>
      </ul>
      <button id="btn-read-rules" class="action">규칙 다 읽었어요</button>
    </section>
    <section id="checkin" class="view card">
      <h2>출석체크</h2>
      <p id="checkin-status">아직 출석하지 않았습니다.</p>
      <button id="btn-do-checkin" class="action">출석 완료</button>
    </section>
    <section id="survey" class="view card">
      <h2>오늘 기분은 어떠신가요?</h2>
      <div id="emoji-buttons">
        <button class="emoji-btn">😄</button>
        <button class="emoji-btn">🙂</button>
        <button class="emoji-btn">😐</button>
        <button class="emoji-btn">🙁</button>
        <button class="emoji-btn">😢</button>
      </div>
      <div id="survey-input">
        <textarea id="survey-text" rows="3" placeholder="오늘 느낀 점을 적어보세요..."></textarea><br>
        <button id="btn-save-survey" class="action">저장하기</button>
      </div>
      <div id="survey-thanks">감사합니다! 😊</div>
      <button id="btn-view-survey" class="action">설문 결과 보기</button>
      <div id="survey-entries"></div>
    </section>
  </main>

  <script>
    // NAVIGATION
    const views = document.querySelectorAll('.view');
    const btnPlanDong = document.getElementById('btn-plan-dong');
    const btnPlanSeo = document.getElementById('btn-plan-seo');
    const btnRules = document.getElementById('btn-rules');
    const btnCheckin = document.getElementById('btn-checkin');
    const btnSurvey = document.getElementById('btn-survey');
    const btnReadRules = document.getElementById('btn-read-rules');
    const btnDoCheckin = document.getElementById('btn-do-checkin');
    const btnSaveSurvey = document.getElementById('btn-save-survey');
    const btnViewSurvey = document.getElementById('btn-view-survey');
    let rulesRead = false;
    let selectedEmoji = '';

    function showView(id) {
      views.forEach(v => v.id === id ? v.classList.add('active') : v.classList.remove('active'));
    }

    btnPlanDong.onclick = () => { showView('plan-dong'); renderSchedule(dongSchedules, 'dong-schedule', 'Asia/Seoul'); };
    btnPlanSeo.onclick = () => { showView('plan-seo'); renderSchedule(seoSchedules, 'seo-schedule', 'America/New_York'); };
    btnRules.onclick = () => showView('rules');
    btnCheckin.onclick = () => showView('checkin');
    btnSurvey.onclick = () => showView('survey');

    // DAY COUNTER
    function updateDayCount() {
      const now = new Date(new Date().toLocaleString('en-US',{timeZone:'Asia/Seoul'}));
      const start = new Date('2024-10-08T00:00:00+09:00');
      const diff = Math.floor((now - start)/(1000*60*60*24)) + 1;
      document.getElementById('day-count').textContent = `우리는 ${diff}일째 사귀었어`;
    }
    updateDayCount(); setInterval(updateDayCount,1000*60*60);

    // RULES & CHECKIN
    btnReadRules.onclick = () => {
      rulesRead = true;
      btnCheckin.disabled = false;
      alert('💪 규칙 모두 읽었습니다!');
    };
    btnDoCheckin.onclick = () => {
      if (!rulesRead) return alert('먼저 규칙을 읽어주세요!');
      document.getElementById('checkin-status').textContent = '출석 완료! 오늘도 함께 해요 💕';
    };

    // SURVEY
    document.querySelectorAll('#emoji-buttons .emoji-btn').forEach(btn => {
      btn.onclick = () => {
        selectedEmoji = btn.textContent;
        document.getElementById('survey-input').style.display = 'block';
      };
    });
    btnSaveSurvey.onclick = () => {
      const text = document.getElementById('survey-text').value;
      const div = document.createElement('div');
      div.innerHTML = `<strong>${selectedEmoji}</strong> ${text}<br><time>${new Date().toLocaleString()}</time>`;
      document.getElementById('survey-entries').appendChild(div);
      document.getElementById('survey-input').style.display = 'none';
      document.getElementById('survey-thanks').style.display = 'block';
      btnViewSurvey.style.display = 'inline-block';
    };
    btnViewSurvey.onclick = () => {
      const se = document.getElementById('survey-entries');
      se.style.display = se.style.display === 'block' ? 'none' : 'block';
    };

    // SCHEDULES DATA AND FUNCTIONS BELOW...
    function renderSchedule(scheduleData, elementId, timeZone) { const ul = document.getElementById(elementId); ul.innerHTML = ''; const now = new Date(new Date().toLocaleString('en-US', { timeZone })); const hour = now.getHours(); const day = now.getDay(); let tasks = []; if (elementId === 'dong-schedule') { tasks = scheduleData.default; } else if (elementId === 'seo-schedule') { if ([1, 3, 4].includes(day)) tasks = scheduleData.monWedThu; else if ([2, 5].includes(day)) tasks = scheduleData.tueFri; } tasks.forEach(item => { const li = document.createElement('li'); li.innerHTML = `<span class="${highlightTime(item.time, hour, timeZone) ? 'current' : ''}">${item.time} - ${item.text}</span>`; ul.appendChild(li); }); }
    const dongSchedules = {
      default: [
        { time: '7시', text: '일어나서 스트레칭 + 말랭이 문자' },
        { time: '7시 40분', text: '학교 갈 준비' },
        { time: '8시 20분', text: '서연이와 응원 연락' },
        { time: 'Key point', text: '공부 끝까지 포기하지 않기' },
        { time: '16시 30분', text: '학교 끝나고 문자 보내기' },
        { time: '17시', text: '전화하기 (피곤 시 패스)' },
        { time: '18시 50분', text: '밥먹고 학원 준비' },
        { time: '19시~22시', text: '학원 진도 & 연락' },
        { time: '22시~23시', text: '운동하기' },
        { time: '23시', text: '전화하기 (불독타임 제외)' },
        { time: '23시 20분~2시', text: '스터디 카페 공부' },
        { time: '2시~7시', text: '잠자기' }
      ],
      tuesday: [
        { time: '12시', text: '점심시간 연락' },
        { time: '16시 30분', text: '학교 끝나고 연락' },
        { time: '18시 50분', text: '수학 공부' },
        { time: '20시~21시', text: '식사 후 운동 준비' },
        { time: '21시~23시', text: '운동' },
        { time: '23시~1시', text: '스터디 카페 & 연락' },
        { time: '1시~7시', text: '취침' }
      ]
    };
    
    const seoSchedules = {
      monWedThu: [
        { time: '5시 40분', text: '기상 후 간단한 스트레칭 후 오빠한테 온 연락 확인하기' },
        { time: '6시', text: '전화하면서 학교 갈 준비하기' },
        { time: '6시 10분', text: '버스타고 학교 가기 (피곤하면 잠깐 눈 붙이거나 오빠랑 전화하기)' },
        { time: '6시 40분', text: '화장하고 아침 받기 (오빠랑 전화하기)' },
        { time: '7시 10분', text: '수업 시작 공부 집중하기' },
        { time: '8시', text: '오빠한테 짧게 연락하고 다음 교시 이동한다고 연락해주기' },
        { time: '9시', text: 'ROTC 가기 전에 잠깐 전화하기 (못할 수도 있으면 짧게 연락 남겨주기)' },
        { time: '9시 53분', text: '불독 때 (숙제, 시험 준비가 최우선) 없으면 오빠랑 연락하거나 이동해야 할 경우 연락 남겨주기' },
        { time: '11시 40분', text: '런치 (숙제, 시험 준비가 최우선) 없으면 밥 먹으면서 오빠랑 전화하기' },
        { time: '1시 15분', text: '6교시 이동할 때 연락할 수 있으면 연락해주고 (오빠 연락 확인하기)' },
        { time: '1시 20분', text: '7교시 마지막 교시 AP 수업 마지막으로 집중하기' },
        { time: '2시 10분', text: '수업 끝 버스 빠르게 가서 좋은 자리 앉기' },
        { time: '2시 30분', text: '오빠한테 학교 끝났다고 연락해주기 (눈을 붙이거나 집에 가서 할 것들 정리하기)' },
        { time: '2시 50분', text: '집 도착 연락 남겨주기' },
        { time: '3시', text: '옷 갈아입고 점심 먹기' },
        { time: '3시 30분', text: '낮잠 자기 (잠이 안 오면 일기를 쓰거나 어려운 숙제 끝내기)' },
        { time: '3시 40분', text: '집 앞에서 간단한 줄넘기 하기' },
        { time: '4시', text: '따뜻한 물로 샤워하기' },
        { time: '7시', text: '운동 1, 공부 1, 힐링 1 선택하여 하루 브리핑 하기' },
        { time: '11시', text: '전까지 모든 일을 끝내고 잠에 들 준비' },
      ],
    
      tueFri: [
        { time: '5시 40분', text: '기상 후 간단한 스트레칭 후 오빠한테 온 연락 확인하기' },
        { time: '6시', text: '전화하면서 학교 갈 준비하기' },
        { time: '6시 10분', text: '버스타고 학교 가기 (피곤하면 잠깐 눈 붙이거나 오빠랑 전화하기)' },
        { time: '6시 40분', text: '화장하고 아침 받기 (오빠랑 전화하기)' },
        { time: '7시 10분', text: '수업 시작 공부 집중하기' },
        { time: '8시', text: '오빠한테 짧게 연락하고 다음 교시 이동한다고 연락해주기' },
        { time: '9시', text: 'ROTC 가기 전에 잠깐 전화하기 (못할 수도 있으면 짧게 연락 남겨주기)' },
        { time: '9시 53분', text: '불독 때 (숙제, 시험 준비가 최우선) 없으면 오빠랑 연락하거나 이동해야 할 경우 연락 남겨주기' },
        { time: '11시 40분', text: '런치 (숙제, 시험 준비가 최우선) 없으면 밥 먹으면서 오빠랑 전화하기' },
        { time: '1시 15분', text: '6교시 이동할 때 연락할 수 있으면 연락해주고 (오빠 연락 확인하기)' },
        { time: '1시 20분', text: '7교시 마지막 교시 AP 수업 마지막으로 집중하기' },
        { time: '2시 10분', text: '수업 끝 버스 빠르게 가서 좋은 자리 앉기' },
        { time: '2시 30분', text: '오빠한테 학교 끝났다고 연락해주기 (눈을 붙이거나 집에 가서 할 것들 정리하기)' },
        { time: '2시 50분', text: '집 도착 연락 남겨주기' },
        { time: '3시', text: '옷 갈아입고 점심 먹기' },
        { time: '4시', text: '낮잠 자기' },
        { time: '6시 20분', text: '기상 후 교회 갈 준비하기' },
        { time: '6시 40분', text: '교회 가면서 전화로 서로 얼굴 보면서 하루 브리핑 해주기' },
        { time: '7시 20분', text: '오빠 학교 보내고 도착할 때까지 잠을 자거나 개인 활동' },
        { time: '10시', text: '교회 끝나고 오는 길에 폰 보지 않기 (잠을 자거나 엄마랑 말하기)' },
        { time: '10시 30분', text: '집에 와서 씻기' },
        { time: '11시', text: '마저 못 끝냈던 일 끝내기' },
        { time: '12시', text: '금요일 12시까지 잠에 들기' },
      ]
    };

    // 시간 강조 함수
    function highlightTime(itemTime, hour) {
      const currentMinutes = new Date().getMinutes(); // 현재 분

      if (itemTime.includes('~')) {
        const [startStr, endStr] = itemTime.split('~');
        const startHour = parseInt(startStr.replace(/[^0-9]/g, ''), 10);
        const endHour = parseInt(endStr.replace(/[^0-9]/g, ''), 10);
        
        if (startHour > endHour) return hour >= startHour || hour < endHour;
        return hour >= startHour && hour < endHour;
      } else {
        const startTime = parseInt(itemTime.split('시')[0].replace(/[^0-9]/g, ''), 10);

        if (startTime === 11) {
          // 11시 40분을 별도로 처리
          if (itemTime.includes('11시 40분')) {
            return hour === 11 && currentMinutes >= 40;
          } else {
            return hour === 11 && currentMinutes < 40;
          }
        } else {
          return itemTime.includes(`${hour}시`);
        }
      }
    }

    function renderSchedule(scheduleData, elementId, timeZone) {
      const ul = document.getElementById(elementId);
      ul.innerHTML = '';
      const now = new Date(new Date().toLocaleString('en-US', { timeZone }));
      const hour = now.getHours();
      const day = now.getDay();
      let tasks = [];

      if (elementId === 'dong-schedule') {
        tasks = dongSchedules.default;
      } else if (elementId === 'seo-schedule') {
        if ([1, 3, 4].includes(day)) tasks = seoSchedules.monWedThu;
        else if ([2, 5].includes(day)) tasks = seoSchedules.tueFri;
      }

      tasks.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.time} - ${item.text}`;
        if (highlightTime(item.time, hour)) li.classList.add('current');
        ul.appendChild(li);
      });
    }

    // Initial schedule
    renderSchedule(dongSchedules, 'dong-schedule', 'Asia/Seoul');
    renderSchedule(seoSchedules, 'seo-schedule', 'America/New_York');
  </script>
</body>
</html>
