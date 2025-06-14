# 개인 이력 포트폴리오 웹사이트

데이터 분석가를 꿈꾸는 김재영입니다.
이 페이지는 웹스크립트프로그래밍 학기말 과제로 제작한 개인 포트폴리오 사이트입니다.

별도의 템플릿 없이 HTML, CSS, JavaScript를 사용하여 직접 구현해보며 웹 개발의 기본기를 다졌습니다.

# 홈페이지 주소
- **https://Dumbbell04.github.io/**

# GitHub 저장소
- **https://github.com/Dumbbell04/Dumbbell04**

---

# 추가 기능 상세 설명

과제 평가 기준의 추가 점수를 위해, 아래와 같이 총 7개의 이력서 관련 기능을 구현했습니다.

# 1) 기능 제목: 태그(Tag) 기반 프로젝트 필터링
- **설명**: 프로젝트 목록을 `#AI`, `#데이터분석` 등 기술 스택 태그를 기준으로 필터링하여 보여주는 기능입니다. 사용자는 관심 있는 기술 태그를 클릭하여 관련 프로젝트만 쉽게 모아볼 수 있습니다.
- **코드 위치**:
    - `index.html`의 'Projects' 섹션 내 `.tag-filter` 및 각 프로젝트의 `data-tags` 속성
    - `index.html`의 `<script>` 태그 내 '태그 필터링' 로직
- **코드 설명**: 각 프로젝트 아이템에 `data-tags`로 기술 스택 정보를 문자열로 저장합니다. 태그 버튼 클릭 시, JavaScript는 해당 태그 문자열이 프로젝트의 `data-tags`에 포함(`includes()`)되어 있는지 여부를 확인하여, 일치하는 프로젝트만 화면에 표시(`display: 'block'`)하고 나머지는 숨깁니다.

# 2) 기능 제목: 상세 정보 모달(Modal) 창
- **설명**: 'My Skills' 및 'Awards & Certifications' 섹션의 각 항목을 클릭하면, 페이지를 이동하지 않고도 화면 위에 해당 항목의 상세 설명을 보여주는 팝업 창 기능입니다.
- **코드 위치**:
    - `index.html`의 `.info-item` 클래스 및 `data-title`, `data-description` 속성
    - `index.html`의 `#info-modal` HTML 구조 및 관련 JavaScript 로직
- **코드 설명**: 설명이 필요한 항목들에 `.info-item` 공통 클래스와 `data-title`, `data-description` 속성을 부여합니다. JavaScript는 `.info-item`의 클릭 이벤트를 감지하여, 해당 요소의 `data-*` 속성 값을 읽어와 모달 창의 내용을 채운 뒤 화면에 표시합니다.

# 3) 기능 제목: 동적 방명록 기능
- **설명**: 방문자가 닉네임과 메시지를 남길 수 있는 방명록 기능입니다. '남기기' 버튼 클릭 시, 입력된 내용이 페이지에 실시간으로 추가됩니다. (단, 정적 페이지의 한계로 새로고침 시 내용은 초기화됩니다.)
- **코드 위치**:
    - `index.html`의 'Guestbook' 섹션 내 `<form>` 및 `<ul>` 구조
    - `index.html`의 `<script>` 태그 내 '방명록' 로직
- **코드 설명**: `form`의 `submit` 이벤트를 가로채(`event.preventDefault()`) 페이지 새로고침을 막습니다. `document.createElement()`를 사용하여 새로운 목록(`<li>`) 요소를 생성하고, 입력받은 닉네임, 메시지, 그리고 `new Date()`로 구한 현재 시간을 내용으로 채웁니다. 마지막으로 `prepend()`를 이용해 생성된 요소를 목록의 맨 위에 추가하여 실시간으로 반영합니다.

# 4) 기능 제목: 타이핑 애니메이션 효과
- **설명**: 페이지에 처음 접속했을 때, 프로필 섹션의 H1 제목이 마치 타자기로 치는 것처럼 한 글자씩 동적으로 나타나는 시각적 효과입니다.
- **코드 위치**:
    - `index.html`의 `<script>` 태그 내 '타이핑 애니메이션 기능' 로직
    - `style.css`의 `h1.typing::after` 및 `@keyframes blink-caret`
- **코드 설명**: JavaScript의 `setInterval` 함수를 이용해 정해진 시간(150ms)마다 제목 문자열의 글자를 하나씩 가져와 H1 태그의 내용에 추가합니다. 모든 글자가 표시되면 `clearInterval`로 반복을 중단합니다. CSS에서는 `::after` 가상 요소를 이용해 텍스트 끝에 깜빡이는 커서를 구현하여 사실감을 더했습니다.

# 5) 기능 제목: 맨 위로 가기(Scroll to Top) 버튼
- **설명**: 사용자가 페이지를 일정량(200px) 이상 스크롤하면 화면 오른쪽 하단에 나타나는 버튼입니다. 클릭 시 페이지 최상단으로 부드럽게 이동시켜 사용자 편의성을 높입니다.
- **코드 위치**:
    - `index.html`의 `#to-top-btn` 버튼 및 관련 JavaScript 로직
    - `style.css`의 `#to-top-btn` 스타일
- **코드 설명**: JavaScript의 `window.addEventListener('scroll', ...)`를 사용해 스크롤 위치(`window.scrollY`)를 실시간으로 감지합니다. 스크롤 위치가 200px을 넘으면 버튼에 `.show` 클래스를 추가하여 화면에 표시하고, 그 이하면 제거하여 숨깁니다. 버튼 클릭 시에는 `window.scrollTo({ top: 0, behavior: 'smooth' })`를 실행하여 부드러운 스크롤 효과를 구현합니다.

# 6) 기능 제목: 이력서 인쇄 및 PDF 저장 기능
- **설명**: 화면 우측 상단의 버튼을 클릭하여 현재 보고 있는 웹페이지를 그대로 인쇄하거나 PDF 파일로 저장할 수 있는 기능입니다.
- **코드 위치**:
    - `index.html`의 `#print-btn` 버튼 및 관련 JavaScript 로직
    - `style.css`의 `#print-btn` 스타일
- **코드 설명**: 버튼에 `click` 이벤트를 설정하고, 클릭 시 JavaScript의 `window.print()` 내장 함수를 실행시켜 브라우저의 기본 인쇄 대화상자를 호출합니다.

# 7) 기능 제목: 모바일 반응형 디자인
- **설명**: PC 화면뿐만 아니라 태블릿, 스마트폰 등 다양한 크기의 화면에서 웹사이트의 레이아웃이 깨지지 않고 최적화된 형태로 보이도록 디자인했습니다.
- **코드 위치**:
    - `index.html`의 `<head>` 태그 내 `<meta name="viewport" ...>`
    - `style.css`의 맨 아래 `@media (max-width: 768px)` 블록
- **코드 설명**: `meta` 태그로 모바일 기기에서 페이지의 너비와 배율을 설정합니다. CSS의 `@media` 쿼리를 사용하여 화면 가로 크기가 768px 이하일 때, 모바일 환경에 맞는 별도의 스타일(폰트 크기 축소, 요소 세로 배치 등)이 적용되도록 하여 반응형 레이아웃을 구현했습니다.

# 8) 기능 제목: 스크롤 애니메이션
- **설명**: 페이지를 스크롤할 때, 각 섹션이 아래에서 위로 부드럽게 나타나는 애니메이션 효과입니다. 사용자에게 동적인 경험을 제공하고 콘텐츠에 대한 집중도를 높입니다.
- **코드 위치**:
    - `index.html`의 각 `<section>`에 적용된 `.fade-in-section` 클래스
    - `index.html`의 `<script>` 태그 내 '스크롤 애니메이션 기능' 로직
    - `style.css`의 `.fade-in-section` 및 `.visible` 클래스 스타일
- **코드 설명**: 최신 `IntersectionObserver` API를 사용하여, 각 섹션 요소가 화면(viewport)에 10% 이상 보이면 `.visible` 클래스를 추가합니다. CSS에서는 `.fade-in-section`을 기본적으로 투명하고(`opacity: 0`) 아래에 위치(`transform: translateY(30px)`)시킨 후, `.visible` 클래스가 추가되면 `transition` 효과를 통해 부드럽게 제자리로 나타나도록 구현했습니다. 한번 나타난 요소는 `observer.unobserve()`를 통해 더 이상 관찰하지 않아 성능을 최적화했습니다.