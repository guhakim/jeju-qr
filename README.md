[jeju-qr-final.html](https://github.com/user-attachments/files/26158692/jeju-qr-final.html)
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>혼저옵서예 — 제주어 굿즈 QR 프로토타입</title>

<style>
  :root {
    --jeju-stone: #3a3530;
    --jeju-sand: #f0ebe2;
    --jeju-sea: #2a6b7c;
    --jeju-sea-light: #4a9baf;
    --jeju-moss: #5a7a4a;
    --jeju-sunset: #c8603a;
    --jeju-cream: #faf7f2;
    --jeju-dark: #1e1c1a;
    --font-serif: 'Apple SD Gothic Neo', 'Malgun Gothic', 'Nanum Myeongjo', Georgia, serif;
    --font-sans: 'Apple SD Gothic Neo', 'Malgun Gothic', 'Nanum Gothic', sans-serif;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--jeju-cream);
    color: var(--jeju-stone);
    font-family: var(--font-sans);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── 랜딩 / 허브 페이지 ── */
  .hub {
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    padding: 0 1.5rem 4rem;
  }

  .hub-header {
    width: 100%;
    max-width: 480px;
    padding: 3rem 0 2rem;
    text-align: center;
    position: relative;
  }

  .wave-top {
    position: absolute;
    top: 0; left: 50%;
    transform: translateX(-50%);
    width: 120px;
    height: 4px;
    background: linear-gradient(90deg, var(--jeju-sea), var(--jeju-sea-light), var(--jeju-sea));
    border-radius: 2px;
  }

  .brand-tag {
    font-family: var(--font-sans);
    font-size: 10px;
    font-weight: 500;
    letter-spacing: 0.25em;
    color: var(--jeju-sea);
    text-transform: uppercase;
    margin-bottom: 1rem;
    margin-top: 1.5rem;
  }

  .hub-title {
    font-family: var(--font-serif);
    font-size: 2.4rem;
    font-weight: 700;
    color: var(--jeju-stone);
    line-height: 1.2;
    margin-bottom: 0.5rem;
  }

  .hub-subtitle {
    font-size: 13px;
    color: #7a756e;
    font-weight: 300;
    line-height: 1.7;
  }

  /* ── 상품 카드 그리드 ── */
  .product-grid {
    width: 100%;
    max-width: 480px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
    margin-top: 2rem;
  }

  .product-card {
    background: white;
    border-radius: 16px;
    padding: 1.4rem 1.2rem 1.2rem;
    cursor: pointer;
    border: 1.5px solid transparent;
    transition: all 0.22s ease;
    position: relative;
    overflow: hidden;
    text-align: center;
  }

  .product-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 3px;
    background: var(--card-color, var(--jeju-sea));
    border-radius: 16px 16px 0 0;
  }

  .product-card:hover {
    border-color: var(--card-color, var(--jeju-sea));
    transform: translateY(-3px);
    box-shadow: 0 12px 32px rgba(42, 107, 124, 0.12);
  }

  .product-card.sea { --card-color: var(--jeju-sea); }
  .product-card.moss { --card-color: var(--jeju-moss); }
  .product-card.sunset { --card-color: var(--jeju-sunset); }
  .product-card.stone { --card-color: var(--jeju-stone); }

  .card-emoji {
    font-size: 2rem;
    margin-bottom: 0.6rem;
    display: block;
  }

  .card-jeju {
    font-family: var(--font-serif);
    font-size: 1.3rem;
    font-weight: 700;
    color: var(--jeju-stone);
    margin-bottom: 3px;
  }

  .card-korean {
    font-size: 11px;
    color: #9a9590;
    margin-bottom: 0.8rem;
    font-weight: 300;
  }

  .card-cta {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    font-size: 11px;
    font-weight: 500;
    color: var(--card-color, var(--jeju-sea));
    background: color-mix(in srgb, var(--card-color, var(--jeju-sea)) 10%, transparent);
    padding: 5px 12px;
    border-radius: 20px;
    letter-spacing: 0.03em;
  }

  /* ── 안내 섹션 ── */
  .how-section {
    width: 100%;
    max-width: 480px;
    margin-top: 2.5rem;
    background: white;
    border-radius: 20px;
    padding: 1.5rem 1.5rem 1.2rem;
  }

  .how-title {
    font-size: 11px;
    font-weight: 500;
    letter-spacing: 0.2em;
    color: var(--jeju-sea);
    text-transform: uppercase;
    margin-bottom: 1.2rem;
  }

  .how-steps {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .how-step {
    display: flex;
    align-items: flex-start;
    gap: 12px;
  }

  .how-num {
    width: 26px; height: 26px;
    border-radius: 50%;
    background: var(--jeju-sea);
    color: white;
    font-size: 12px;
    font-weight: 500;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    margin-top: 1px;
  }

  .how-text strong {
    display: block;
    font-size: 13px;
    font-weight: 500;
    color: var(--jeju-stone);
    margin-bottom: 2px;
  }

  .how-text span {
    font-size: 12px;
    color: #9a9590;
    font-weight: 300;
    line-height: 1.5;
  }

  /* ── 상세 페이지 ── */
  .detail-page {
    display: none;
    min-height: 100vh;
    flex-direction: column;
    animation: fadeSlideUp 0.35s ease;
  }

  .detail-page.active {
    display: flex;
  }

  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .detail-hero {
    background: var(--jeju-stone);
    color: white;
    padding: 3.5rem 1.5rem 2.5rem;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .detail-hero::after {
    content: '';
    position: absolute;
    bottom: -1px; left: 0; right: 0;
    height: 30px;
    background: var(--jeju-cream);
    border-radius: 30px 30px 0 0;
  }

  .hero-product-tag {
    display: inline-block;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: rgba(255,255,255,0.5);
    text-transform: uppercase;
    margin-bottom: 1.5rem;
  }

  .hero-jeju-word {
    font-family: var(--font-serif);
    font-size: 3.5rem;
    font-weight: 700;
    line-height: 1;
    margin-bottom: 0.6rem;
    letter-spacing: -0.02em;
  }

  .hero-romanize {
    font-size: 13px;
    color: rgba(255,255,255,0.45);
    font-weight: 300;
    letter-spacing: 0.1em;
    margin-bottom: 1.2rem;
  }

  .hero-meaning {
    display: inline-block;
    background: rgba(255,255,255,0.12);
    border: 1px solid rgba(255,255,255,0.2);
    border-radius: 8px;
    padding: 8px 18px;
    font-size: 14px;
    font-weight: 400;
    color: rgba(255,255,255,0.88);
  }

  /* ── 콘텐츠 영역 ── */
  .detail-content {
    flex: 1;
    padding: 1.5rem;
    max-width: 480px;
    width: 100%;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    gap: 1.2rem;
  }

  /* 발음 카드 */
  .pronunciation-card {
    background: white;
    border-radius: 18px;
    padding: 1.4rem;
    border: 1.5px solid #e8e3dc;
  }

  .card-section-label {
    font-size: 10px;
    font-weight: 500;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--jeju-sea);
    margin-bottom: 1rem;
  }

  .pronunciation-display {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 1rem;
  }

  .pron-text {
    font-family: var(--font-serif);
    font-size: 1.8rem;
    font-weight: 600;
    color: var(--jeju-stone);
  }

  .play-btn {
    width: 52px; height: 52px;
    border-radius: 50%;
    background: var(--jeju-sea);
    color: white;
    border: none;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
    transition: all 0.2s;
    flex-shrink: 0;
  }

  .play-btn:hover {
    background: var(--jeju-sea-light);
    transform: scale(1.05);
  }

  .play-btn.playing {
    background: var(--jeju-sunset);
    animation: pulse 1s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { box-shadow: 0 0 0 0 rgba(200, 96, 58, 0.4); }
    50% { box-shadow: 0 0 0 10px rgba(200, 96, 58, 0); }
  }

  .speaker-info {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 12px;
    background: var(--jeju-sand);
    border-radius: 10px;
  }

  .speaker-avatar {
    width: 28px; height: 28px;
    border-radius: 50%;
    background: var(--jeju-stone);
    color: white;
    display: flex; align-items: center; justify-content: center;
    font-size: 14px;
  }

  .speaker-name {
    font-size: 12px;
    font-weight: 500;
    color: var(--jeju-stone);
  }

  .speaker-desc {
    font-size: 11px;
    color: #9a9590;
  }

  /* 사용 예시 카드 */
  .usage-card {
    background: white;
    border-radius: 18px;
    padding: 1.4rem;
    border: 1.5px solid #e8e3dc;
  }

  .usage-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .usage-item {
    background: var(--jeju-sand);
    border-radius: 12px;
    padding: 12px 14px;
  }

  .usage-jeju {
    font-family: var(--font-serif);
    font-size: 14px;
    font-weight: 600;
    color: var(--jeju-stone);
    margin-bottom: 4px;
  }

  .usage-korean {
    font-size: 12px;
    color: #7a756e;
    font-weight: 300;
    line-height: 1.5;
  }

  /* 관련 단어 */
  .related-card {
    background: white;
    border-radius: 18px;
    padding: 1.4rem;
    border: 1.5px solid #e8e3dc;
  }

  .related-chips {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 0.8rem;
  }

  .related-chip {
    background: var(--jeju-sand);
    border: 1px solid #d8d2c8;
    border-radius: 20px;
    padding: 6px 14px;
    font-size: 12px;
    color: var(--jeju-stone);
    cursor: pointer;
    transition: all 0.15s;
    font-family: var(--font-serif);
  }

  .related-chip:hover {
    background: var(--jeju-sea);
    color: white;
    border-color: var(--jeju-sea);
  }

  /* 공유 섹션 */
  .share-card {
    background: var(--jeju-stone);
    border-radius: 18px;
    padding: 1.4rem;
    text-align: center;
    color: white;
  }

  .share-label {
    font-size: 11px;
    letter-spacing: 0.15em;
    color: rgba(255,255,255,0.5);
    text-transform: uppercase;
    margin-bottom: 0.8rem;
  }

  .share-title {
    font-family: var(--font-serif);
    font-size: 1.1rem;
    font-weight: 600;
    margin-bottom: 0.4rem;
  }

  .share-sub {
    font-size: 12px;
    color: rgba(255,255,255,0.55);
    margin-bottom: 1.2rem;
    font-weight: 300;
  }

  .share-btns {
    display: flex;
    gap: 10px;
    justify-content: center;
  }

  .share-btn {
    flex: 1;
    max-width: 140px;
    padding: 10px;
    border-radius: 12px;
    border: 1px solid rgba(255,255,255,0.2);
    background: rgba(255,255,255,0.08);
    color: white;
    font-size: 12px;
    font-family: var(--font-sans);
    cursor: pointer;
    transition: all 0.2s;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 6px;
  }

  .share-btn:hover {
    background: rgba(255,255,255,0.16);
  }

  /* 시리즈 카드 */
  .series-card {
    background: white;
    border-radius: 18px;
    padding: 1.4rem;
    border: 1.5px solid #e8e3dc;
  }

  .series-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 8px;
    margin-top: 0.8rem;
  }

  .series-item {
    background: var(--jeju-sand);
    border-radius: 10px;
    padding: 10px 6px;
    text-align: center;
    cursor: pointer;
    transition: all 0.15s;
    border: 1.5px solid transparent;
  }

  .series-item:hover {
    border-color: var(--jeju-sea);
    background: color-mix(in srgb, var(--jeju-sea) 8%, white);
  }

  .series-word {
    font-family: var(--font-serif);
    font-size: 13px;
    font-weight: 600;
    color: var(--jeju-stone);
    margin-bottom: 2px;
  }

  .series-meaning {
    font-size: 10px;
    color: #9a9590;
    font-weight: 300;
  }

  /* 네비게이션 */
  .nav-bar {
    display: flex;
    align-items: center;
    padding: 1.2rem 1.5rem 0.5rem;
    max-width: 480px;
    width: 100%;
    margin: 0 auto;
  }

  .back-btn {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 13px;
    color: var(--jeju-sea);
    background: none;
    border: none;
    cursor: pointer;
    font-family: var(--font-sans);
    padding: 6px 0;
  }

  /* QR 시뮬레이터 */
  .qr-demo-card {
    background: white;
    border-radius: 18px;
    padding: 1.4rem;
    border: 1.5px solid #e8e3dc;
    text-align: center;
  }

  .qr-box {
    width: 100px; height: 100px;
    margin: 0.8rem auto;
    border: 2px solid var(--jeju-stone);
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 10px;
    color: #9a9590;
    background: var(--jeju-sand);
    position: relative;
    overflow: hidden;
  }

  .qr-grid {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    grid-template-rows: repeat(7, 1fr);
    width: 84px; height: 84px;
    gap: 1px;
  }

  .qr-cell {
    border-radius: 1px;
  }

  .qr-cell.b { background: var(--jeju-stone); }
  .qr-cell.w { background: var(--jeju-sand); }

  .qr-desc {
    font-size: 11px;
    color: #9a9590;
    font-weight: 300;
    margin-top: 0.5rem;
  }

  /* 탭 뷰 (시뮬레이터) */
  .tab-row {
    display: flex;
    gap: 6px;
    margin-bottom: 1.5rem;
  }

  .tab-btn {
    flex: 1;
    padding: 8px;
    border-radius: 10px;
    border: 1px solid #e8e3dc;
    background: white;
    font-size: 11px;
    color: #9a9590;
    cursor: pointer;
    font-family: var(--font-sans);
    transition: all 0.15s;
  }

  .tab-btn.active {
    background: var(--jeju-sea);
    color: white;
    border-color: var(--jeju-sea);
    font-weight: 500;
  }

  /* 반응 피드백 */
  .toast {
    position: fixed;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%) translateY(80px);
    background: var(--jeju-stone);
    color: white;
    padding: 10px 20px;
    border-radius: 20px;
    font-size: 13px;
    transition: transform 0.3s ease;
    z-index: 100;
    white-space: nowrap;
  }

  .toast.show {
    transform: translateX(-50%) translateY(0);
  }

  /* 스크롤바 */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: #d8d2c8; border-radius: 2px; }
</style>
</head>
<body>
<div id="share-banner" style="
  position:fixed; top:0; left:0; right:0; z-index:9999;
  background:#2a6b7c; color:white;
  padding:10px 16px;
  display:flex; align-items:center; justify-content:space-between;
  font-family:'Apple SD Gothic Neo','Malgun Gothic',sans-serif;
  font-size:12px; gap:10px;
">
  <span>🪸 <strong>혼저옵서예</strong> — 제주어 굿즈 QR 프로토타입</span>
  <div style="display:flex;gap:8px;flex-shrink:0;">
    <button onclick="copyCurrentURL()" style="
      background:rgba(255,255,255,0.18); color:white; border:1px solid rgba(255,255,255,0.3);
      border-radius:8px; padding:5px 12px; font-size:11px; cursor:pointer; font-family:inherit;
    ">링크 복사</button>
    <button onclick="document.getElementById('share-banner').style.display='none'" style="
      background:none; color:rgba(255,255,255,0.6); border:none; font-size:16px; cursor:pointer; line-height:1;
    ">×</button>
  </div>
</div>
<div style="height:44px;"></div>

<script>
function copyCurrentURL() {
  navigator.clipboard.writeText(location.href).then(() => {
    const btn = document.querySelector('#share-banner button');
    btn.textContent = '복사됐어요 ✓';
    setTimeout(() => btn.textContent = '링크 복사', 2000);
  }).catch(() => {
    const ta = document.createElement('textarea');
    ta.value = location.href;
    document.body.appendChild(ta);
    ta.select(); document.execCommand('copy');
    document.body.removeChild(ta);
  });
}
</script>


<!-- ══════════════════════════════════
     허브 페이지 (QR 스캔 후 첫 화면)
══════════════════════════════════ -->
<div class="hub" id="hub-page">
  <div class="hub-header">
    <div class="wave-top"></div>
    <p class="brand-tag">제주어 굿즈 · 디지털 아카이브</p>
    <h1 class="hub-title">혼저옵서예</h1>
    <p class="hub-subtitle">제주의 말을 만나는 곳<br>어떤 굿즈의 QR을 스캔하셨나요?</p>
  </div>

  <!-- 상품 선택 그리드 -->
  <div class="product-grid">
    <div class="product-card sea" onclick="openDetail('honjer')">
      <span class="card-emoji">🪸</span>
      <div class="card-jeju">혼저옵서예</div>
      <div class="card-korean">어서 오세요</div>
      <div class="card-cta">▶ 발음 듣기</div>
    </div>

    <div class="product-card moss" onclick="openDetail('yomang')">
      <span class="card-emoji">🌿</span>
      <div class="card-jeju">요망지다</div>
      <div class="card-korean">영리하고 야무지다</div>
      <div class="card-cta">▶ 발음 듣기</div>
    </div>

    <div class="product-card sunset" onclick="openDetail('omeomaebang')">
      <span class="card-emoji">🍊</span>
      <div class="card-jeju">어멍 아방</div>
      <div class="card-korean">어머니 아버지</div>
      <div class="card-cta">▶ 발음 듣기</div>
    </div>

    <div class="product-card stone" onclick="openDetail('sumang')">
      <span class="card-emoji">🌊</span>
      <div class="card-jeju">수고마씸</div>
      <div class="card-korean">수고하세요</div>
      <div class="card-cta">▶ 발음 듣기</div>
    </div>
  </div>

  <!-- 이용 안내 -->
  <div class="how-section">
    <p class="how-title">이용 방법</p>
    <div class="how-steps">
      <div class="how-step">
        <div class="how-num">1</div>
        <div class="how-text">
          <strong>굿즈의 QR 코드 스캔</strong>
          <span>엽서, 스티커, 달력 뒷면의 QR을<br>카메라 앱으로 찍어주세요</span>
        </div>
      </div>
      <div class="how-step">
        <div class="how-num">2</div>
        <div class="how-text">
          <strong>제주어 발음 & 해설 확인</strong>
          <span>원어민 발음 영상, 뜻풀이,<br>실제 사용 예시를 만나보세요</span>
        </div>
      </div>
      <div class="how-step">
        <div class="how-num">3</div>
        <div class="how-text">
          <strong>SNS에 공유하기</strong>
          <span>제주어의 매력을 친구에게도<br>알려주세요 🍊</span>
        </div>
      </div>
    </div>
  </div>
</div>


<!-- ══════════════════════════════════
     상세 페이지 1 — 혼저옵서예
══════════════════════════════════ -->
<div class="detail-page" id="detail-honjer">
  <div class="nav-bar">
    <button class="back-btn" onclick="goBack()">← 목록으로</button>
  </div>

  <div class="detail-hero" style="background: var(--jeju-sea);">
    <p class="hero-product-tag">엽서 시리즈 No.01 · 제주어 인사말</p>
    <div class="hero-jeju-word">혼저옵서예</div>
    <div class="hero-romanize">hon-jeo-op-seo-ye</div>
    <div class="hero-meaning">어서 오세요 · 환영합니다</div>
  </div>

  <div class="detail-content">

    <!-- 발음 카드 -->
    <div class="pronunciation-card">
      <div class="card-section-label">원어민 발음</div>
      <div class="pronunciation-display">
        <div class="pron-text">혼저옵서예</div>
        <button class="play-btn" id="play-honjer" onclick="togglePlay('honjer')">▶</button>
      </div>
      <div class="speaker-info">
        <div class="speaker-avatar">👵</div>
        <div>
          <div class="speaker-name">고순덕 할망 (76세)</div>
          <div class="speaker-desc">제주시 조천읍 · 평생 제주어 사용자</div>
        </div>
      </div>
    </div>

    <!-- 사용 예시 -->
    <div class="usage-card">
      <div class="card-section-label">실제 사용 예시</div>
      <div class="usage-list">
        <div class="usage-item">
          <div class="usage-jeju">혼저옵서예, 들어옵서!</div>
          <div class="usage-korean">어서 오세요, 들어오세요!</div>
        </div>
        <div class="usage-item">
          <div class="usage-jeju">혼저옵서예 — 제주에 오신 걸 환영합니다</div>
          <div class="usage-korean">제주 관광지 입구 표지판에서 자주 볼 수 있는 표현</div>
        </div>
        <div class="usage-item">
          <div class="usage-jeju">아이고, 혼저옵서예!</div>
          <div class="usage-korean">아이고, 잘 오셨어요! (반가운 인사)</div>
        </div>
      </div>
    </div>

    <!-- 단어 유래 -->
    <div class="usage-card">
      <div class="card-section-label">단어 이야기</div>
      <p style="font-size:13px; color:#7a756e; line-height:1.8; font-weight:300;">
        <strong style="color:var(--jeju-stone); font-weight:500;">혼저</strong>는 "어서"를, <strong style="color:var(--jeju-stone); font-weight:500;">옵서예</strong>는 "오십시오"를 뜻하는 제주어입니다. 육지의 "어서 오세요"에 해당하며, 제주의 환대 문화를 담은 대표적인 인사말이에요. 제주 공항, 식당, 관광지 등 어디서나 들을 수 있어요.
      </p>
    </div>

    <!-- 관련 단어 -->
    <div class="related-card">
      <div class="card-section-label">비슷한 제주어 인사</div>
      <div class="related-chips">
        <div class="related-chip" onclick="openDetail('honjer')">잘 왕 봅서</div>
        <div class="related-chip" onclick="showToast('준비 중이에요! 🍊')">안녕하우꽈</div>
        <div class="related-chip" onclick="showToast('준비 중이에요! 🍊')">잘 갑서예</div>
        <div class="related-chip" onclick="showToast('준비 중이에요! 🍊')">또 옵서예</div>
      </div>
    </div>

    <!-- QR 안내 -->
    <div class="qr-demo-card">
      <div class="card-section-label">이 페이지의 QR 코드</div>
      <div class="qr-box">
        <div class="qr-grid" id="qr-honjer"></div>
      </div>
      <div class="qr-desc">굿즈에 인쇄된 QR을 스캔하면<br>이 페이지로 바로 연결돼요</div>
    </div>

    <!-- 시리즈 -->
    <div class="series-card">
      <div class="card-section-label">다른 제주어 굿즈 보기</div>
      <div class="series-grid">
        <div class="series-item" onclick="openDetail('yomang')">
          <div class="series-word">요망지다</div>
          <div class="series-meaning">영리하다</div>
        </div>
        <div class="series-item" onclick="openDetail('omeomaebang')">
          <div class="series-word">어멍아방</div>
          <div class="series-meaning">부모님</div>
        </div>
        <div class="series-item" onclick="openDetail('sumang')">
          <div class="series-word">수고마씸</div>
          <div class="series-meaning">수고해요</div>
        </div>
      </div>
    </div>

    <!-- 공유 -->
    <div class="share-card">
      <div class="share-label">제주어 알리기</div>
      <div class="share-title">이 단어가 마음에 드셨나요?</div>
      <div class="share-sub">친구에게도 제주어의 매력을 알려주세요</div>
      <div class="share-btns">
        <button class="share-btn" onclick="showToast('링크가 복사됐어요! 🔗')">🔗 링크 복사</button>
        <button class="share-btn" onclick="showToast('인스타 공유 준비 중 🍊')">📸 인스타 공유</button>
      </div>
    </div>

  </div>
</div>


<!-- ══════════════════════════════════
     상세 페이지 2 — 요망지다
══════════════════════════════════ -->
<div class="detail-page" id="detail-yomang">
  <div class="nav-bar">
    <button class="back-btn" onclick="goBack()">← 목록으로</button>
  </div>

  <div class="detail-hero" style="background: var(--jeju-moss);">
    <p class="hero-product-tag">스티커 시리즈 No.03 · 제주어 감성 표현</p>
    <div class="hero-jeju-word">요망지다</div>
    <div class="hero-romanize">yo-mang-ji-da</div>
    <div class="hero-meaning">영리하고 야무지다 · 똑똑하다</div>
  </div>

  <div class="detail-content">

    <div class="pronunciation-card">
      <div class="card-section-label">원어민 발음</div>
      <div class="pronunciation-display">
        <div class="pron-text">요망지다</div>
        <button class="play-btn" id="play-yomang" onclick="togglePlay('yomang')">▶</button>
      </div>
      <div class="speaker-info">
        <div class="speaker-avatar">👴</div>
        <div>
          <div class="speaker-name">강길수 하르방 (71세)</div>
          <div class="speaker-desc">서귀포시 표선면 · 제주어 보존 활동가</div>
        </div>
      </div>
    </div>

    <div class="usage-card">
      <div class="card-section-label">실제 사용 예시</div>
      <div class="usage-list">
        <div class="usage-item">
          <div class="usage-jeju">경 요망지민 크멍 성공하크라!</div>
          <div class="usage-korean">그렇게 야무지면 크면 성공하겠다!</div>
        </div>
        <div class="usage-item">
          <div class="usage-jeju">저 아이 참 요망져.</div>
          <div class="usage-korean">저 아이 참 영리해. (칭찬의 말)</div>
        </div>
        <div class="usage-item">
          <div class="usage-jeju">요망진 우리 딸</div>
          <div class="usage-korean">영리한 우리 딸 — 부모가 자녀 칭찬할 때 자주 씀</div>
        </div>
      </div>
    </div>

    <div class="usage-card">
      <div class="card-section-label">단어 이야기</div>
      <p style="font-size:13px; color:#7a756e; line-height:1.8; font-weight:300;">
        <strong style="color:var(--jeju-stone); font-weight:500;">요망지다</strong>는 제주어에서 "영리하다", "야무지다", "재치있다"를 한꺼번에 담은 표현이에요. 육지어의 "야무지다"와 비슷하지만 제주에서는 특히 아이를 칭찬할 때 즐겨 쓰는 말이에요. 긍정적인 뉘앙스가 강하고, 쓸수록 정감이 넘쳐요.
      </p>
    </div>

    <div class="related-card">
      <div class="card-section-label">비슷한 제주어 칭찬말</div>
      <div class="related-chips">
        <div class="related-chip" onclick="showToast('준비 중이에요! 🍊')">착헌 아이</div>
        <div class="related-chip" onclick="showToast('준비 중이에요! 🍊')">영특하다</div>
        <div class="related-chip" onclick="showToast('준비 중이에요! 🍊')">정들다</div>
      </div>
    </div>

    <div class="series-card">
      <div class="card-section-label">다른 제주어 굿즈 보기</div>
      <div class="series-grid">
        <div class="series-item" onclick="openDetail('honjer')">
          <div class="series-word">혼저옵서</div>
          <div class="series-meaning">어서오세요</div>
        </div>
        <div class="series-item" onclick="openDetail('omeomaebang')">
          <div class="series-word">어멍아방</div>
          <div class="series-meaning">부모님</div>
        </div>
        <div class="series-item" onclick="openDetail('sumang')">
          <div class="series-word">수고마씸</div>
          <div class="series-meaning">수고해요</div>
        </div>
      </div>
    </div>

    <div class="share-card">
      <div class="share-label">제주어 알리기</div>
      <div class="share-title">"요망지다"를 아는 사람 몇 명?</div>
      <div class="share-sub">친구에게 제주어 칭찬 한마디 보내보세요</div>
      <div class="share-btns">
        <button class="share-btn" onclick="showToast('링크가 복사됐어요! 🔗')">🔗 링크 복사</button>
        <button class="share-btn" onclick="showToast('카카오 공유 준비 중 🍊')">💬 카카오 공유</button>
      </div>
    </div>

  </div>
</div>


<!-- ══════════════════════════════════
     상세 페이지 3 — 어멍 아방
══════════════════════════════════ -->
<div class="detail-page" id="detail-omeomaebang">
  <div class="nav-bar">
    <button class="back-btn" onclick="goBack()">← 목록으로</button>
  </div>

  <div class="detail-hero" style="background: var(--jeju-sunset);">
    <p class="hero-product-tag">달력 시리즈 5월 · 가정의 달 특별판</p>
    <div class="hero-jeju-word">어멍 아방</div>
    <div class="hero-romanize">eo-meong · a-bang</div>
    <div class="hero-meaning">어머니 · 아버지</div>
  </div>

  <div class="detail-content">

    <div class="pronunciation-card">
      <div class="card-section-label">원어민 발음</div>
      <div class="pronunciation-display">
        <div class="pron-text">어멍 / 아방</div>
        <button class="play-btn" id="play-omeomaebang" onclick="togglePlay('omeomaebang')">▶</button>
      </div>
      <div class="speaker-info">
        <div class="speaker-avatar">👵</div>
        <div>
          <div class="speaker-name">오말순 할망 (82세)</div>
          <div class="speaker-desc">제주시 한림읍 · 제주 토박이 3대째</div>
        </div>
      </div>
    </div>

    <div class="usage-card">
      <div class="card-section-label">실제 사용 예시</div>
      <div class="usage-list">
        <div class="usage-item">
          <div class="usage-jeju">어멍, 밥 먹었수과?</div>
          <div class="usage-korean">어머니, 밥 드셨어요?</div>
        </div>
        <div class="usage-item">
          <div class="usage-jeju">아방, 어디 감수과?</div>
          <div class="usage-korean">아버지, 어디 가세요?</div>
        </div>
        <div class="usage-item">
          <div class="usage-jeju">우리 어멍 아방 보고 싶어라</div>
          <div class="usage-korean">우리 부모님이 보고 싶어라</div>
        </div>
      </div>
    </div>

    <div class="usage-card">
      <div class="card-section-label">단어 이야기</div>
      <p style="font-size:13px; color:#7a756e; line-height:1.8; font-weight:300;">
        <strong style="color:var(--jeju-stone); font-weight:500;">어멍</strong>(어머니)과 <strong style="color:var(--jeju-stone); font-weight:500;">아방</strong>(아버지)은 제주어에서 가족을 부르는 가장 기본적인 말이에요. 육지의 "엄마·아빠"처럼 친근하게 쓰여요. 제주 사람들이 자신의 부모를 부를 때 지금도 자연스럽게 쓰는, 살아있는 제주어예요.
      </p>
    </div>

    <div class="series-card">
      <div class="card-section-label">다른 제주어 굿즈 보기</div>
      <div class="series-grid">
        <div class="series-item" onclick="openDetail('honjer')">
          <div class="series-word">혼저옵서</div>
          <div class="series-meaning">어서오세요</div>
        </div>
        <div class="series-item" onclick="openDetail('yomang')">
          <div class="series-word">요망지다</div>
          <div class="series-meaning">영리하다</div>
        </div>
        <div class="series-item" onclick="openDetail('sumang')">
          <div class="series-word">수고마씸</div>
          <div class="series-meaning">수고해요</div>
        </div>
      </div>
    </div>

    <div class="share-card">
      <div class="share-label">부모님께 제주어로</div>
      <div class="share-title">어멍 아방께 이 페이지를</div>
      <div class="share-sub">가정의 달, 제주어로 마음을 전해보세요 🍊</div>
      <div class="share-btns">
        <button class="share-btn" onclick="showToast('링크가 복사됐어요! 🔗')">🔗 링크 복사</button>
        <button class="share-btn" onclick="showToast('문자 공유 준비 중 🍊')">📱 문자 보내기</button>
      </div>
    </div>

  </div>
</div>


<!-- ══════════════════════════════════
     상세 페이지 4 — 수고마씸
══════════════════════════════════ -->
<div class="detail-page" id="detail-sumang">
  <div class="nav-bar">
    <button class="back-btn" onclick="goBack()">← 목록으로</button>
  </div>

  <div class="detail-hero" style="background: var(--jeju-stone);">
    <p class="hero-product-tag">노트 시리즈 · 일상 제주어</p>
    <div class="hero-jeju-word">수고마씸</div>
    <div class="hero-romanize">su-go-ma-ssim</div>
    <div class="hero-meaning">수고하세요 · 고생하십니다</div>
  </div>

  <div class="detail-content">

    <div class="pronunciation-card">
      <div class="card-section-label">원어민 발음</div>
      <div class="pronunciation-display">
        <div class="pron-text">수고마씸</div>
        <button class="play-btn" id="play-sumang" onclick="togglePlay('sumang')">▶</button>
      </div>
      <div class="speaker-info">
        <div class="speaker-avatar">👴</div>
        <div>
          <div class="speaker-name">현봉길 하르방 (68세)</div>
          <div class="speaker-desc">제주시 구좌읍 · 해녀 남편·어부</div>
        </div>
      </div>
    </div>

    <div class="usage-card">
      <div class="card-section-label">실제 사용 예시</div>
      <div class="usage-list">
        <div class="usage-item">
          <div class="usage-jeju">오늘도 수고마씸!</div>
          <div class="usage-korean">오늘도 수고하세요! (출근하는 이웃에게)</div>
        </div>
        <div class="usage-item">
          <div class="usage-jeju">경 일하민 몸 상합니다. 수고마씸.</div>
          <div class="usage-korean">그렇게 일하면 몸 상합니다. 고생하세요.</div>
        </div>
        <div class="usage-item">
          <div class="usage-jeju">수고마씸, 또 봅서예.</div>
          <div class="usage-korean">수고하세요, 또 만나요.</div>
        </div>
      </div>
    </div>

    <div class="usage-card">
      <div class="card-section-label">단어 이야기</div>
      <p style="font-size:13px; color:#7a756e; line-height:1.8; font-weight:300;">
        <strong style="color:var(--jeju-stone); font-weight:500;">수고마씸</strong>은 "수고하세요"의 제주어 표현이에요. "마씸"은 존칭을 나타내는 제주 고유의 어미로, 어른을 공경하는 제주 문화가 담겨 있어요. 일하는 사람에게 건네는 따뜻한 응원의 말로, 제주의 공동체 정신을 잘 보여주는 표현이에요.
      </p>
    </div>

    <div class="series-card">
      <div class="card-section-label">다른 제주어 굿즈 보기</div>
      <div class="series-grid">
        <div class="series-item" onclick="openDetail('honjer')">
          <div class="series-word">혼저옵서</div>
          <div class="series-meaning">어서오세요</div>
        </div>
        <div class="series-item" onclick="openDetail('yomang')">
          <div class="series-word">요망지다</div>
          <div class="series-meaning">영리하다</div>
        </div>
        <div class="series-item" onclick="openDetail('omeomaebang')">
          <div class="series-word">어멍아방</div>
          <div class="series-meaning">부모님</div>
        </div>
      </div>
    </div>

    <div class="share-card">
      <div class="share-label">오늘의 제주어</div>
      <div class="share-title">동료에게 수고마씸!</div>
      <div class="share-sub">제주어로 오늘 하루 응원 한마디 보내보세요</div>
      <div class="share-btns">
        <button class="share-btn" onclick="showToast('링크가 복사됐어요! 🔗')">🔗 링크 복사</button>
        <button class="share-btn" onclick="showToast('카카오 공유 준비 중 🍊')">💬 카카오 공유</button>
      </div>
    </div>

  </div>
</div>

<!-- 토스트 메시지 -->
<div class="toast" id="toast"></div>

<script>
  // ── 페이지 전환 ──
  function openDetail(id) {
    document.getElementById('hub-page').style.display = 'none';
    const all = document.querySelectorAll('.detail-page');
    all.forEach(p => p.classList.remove('active'));
    const target = document.getElementById('detail-' + id);
    if (target) {
      target.classList.add('active');
      window.scrollTo(0, 0);
    }
    renderQR(id);
  }

  function goBack() {
    document.querySelectorAll('.detail-page').forEach(p => p.classList.remove('active'));
    document.getElementById('hub-page').style.display = 'flex';
    window.scrollTo(0, 0);
    stopAllPlay();
  }

  // ── 재생 시뮬레이션 ──
  let playTimer = null;

  function togglePlay(id) {
    const btn = document.getElementById('play-' + id);
    if (!btn) return;
    if (btn.classList.contains('playing')) {
      stopAllPlay();
      return;
    }
    stopAllPlay();
    btn.classList.add('playing');
    btn.textContent = '■';
    showToast('🎵 제주 할망·하르방의 목소리로 들어보세요!');
    playTimer = setTimeout(() => {
      stopAllPlay();
    }, 3500);
  }

  function stopAllPlay() {
    if (playTimer) clearTimeout(playTimer);
    document.querySelectorAll('.play-btn').forEach(b => {
      b.classList.remove('playing');
      b.textContent = '▶';
    });
  }

  // ── 토스트 ──
  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.classList.add('show');
    setTimeout(() => t.classList.remove('show'), 2400);
  }

  // ── QR 패턴 렌더링 ──
  const qrPatterns = {
    honjer:      'BBBBBBBWBWWWWBWBBBBBBBWBWWWWBWBWBWBWBWBWBWWWWWBWBWWWWWBWBWBWBWBWBWWWWWBWBWWWWWBWBWBWBWBWWWBWWWBWBWBWBWBWBWWWWBWBBBBBBBWBWWWWBWBBBBBBB',
    yomang:      'BBBBBBBWBWWWWBWBBBBBBBWBWWWWBWBWBWWBWWWBWWBWWWWWBWBWWBWWWBWWWWWBWBWWWBWBWWWBWWWBWBWWWWBWBWWBWBWWWWWBWBBBBBBBWBWWWWBWBBBBBBB',
    omeomaebang: 'BBBBBBBWBWBWWBWBBBBBBBWBWWWWBWBWBWWWBWWWBWBWWWWWBWBWWWWWBWBWBWWBWBWWWBWWWBWBWWWWBWBWWBWWBWBWWWWWBWBBBBBBBWBWWWWBWBBBBBBB',
    sumang:      'BBBBBBBWBWWWWBWBBBBBBBWBWWWWBWBWBWWWBWWBWWBWWWWWBWBWWWWWBWBWBWWWBWWBWBWWWBWBWWWWBWWBWWBWBWWWWWBWBBBBBBBWBWWWWBWBBBBBBB'
  };

  function renderQR(id) {
    const el = document.getElementById('qr-' + id);
    if (!el) return;
    el.innerHTML = '';
    const pattern = (qrPatterns[id] || qrPatterns.honjer).padEnd(49, 'W');
    for (let i = 0; i < 49; i++) {
      const cell = document.createElement('div');
      cell.className = 'qr-cell ' + (pattern[i] === 'B' ? 'b' : 'w');
      el.appendChild(cell);
    }
  }

  // ── 초기 렌더 ──
  renderQR('honjer');
</script>
</body>
</html>
