<div align="center">
	<h1>starbucks</h1>
	<h3><a href="https://vermillion-rugelach-58bcab.netlify.app/" />💻사이트 이동하기💻</a></h3>
	<p>HTML, CSS, Emmit, Js Libraries 및 bundler를 활용하여 작업한 웹페이지입니다.</p>
</div>
<br/>
<div align="end">

</div>

<br/>

## 📌주요 기능
- 오픈 그래프 (Open Graph)
- youtube API
- 배너와 위로 가기 버튼
- 연도 생성
- 로그인 페이지

<br/>

## 🧩사용 기술
|기술|설명|
|---|---|
|![HTML](https://img.shields.io/badge/-HTML-F05032?style=flat-square&logo=html5&logoColor=ffffff)|HTML5 웹표준 준수|
|![CSS](https://img.shields.io/badge/-CSS-007ACC?style=flat-square&logo=css3)|반응형 처리 및 디자인|
|![JavaScript](https://img.shields.io/badge/-JavaScript-dc8d2d?style=flat-square&logo=javascript&logoColor=ffffff)|웹 요소의 제어 및 라이브러리 연동|
|![Swiper](https://img.shields.io/badge/Swiper-6332F6?logo=swiper&logoColor=white&style=flat-square) |슬라이더 구현|
|![GSAP](https://img.shields.io/badge/GSAP-88CE02?logo=greensock&logoColor=white&style=flat-square)|부드럽고 가벼운 애니메이션 구현|
|![Lodash](https://img.shields.io/badge/-lodash-3492FF0?style=flat-square&logo=cloudflare&logoColor=3492FF)|코드 간결화 및 효율성 고려|

<br/>

## ⌨코드 살펴보기

### 1. 오픈 그래프📱
<details>
	<summary><b>💛적용 구간 보기</b></summary>
	<table>
		<tr>
			<td> 콘텐츠 공유시 화면 </td>
		</tr>
		<tr>
			<td><img src="https://github.com/user-attachments/assets/557b93f7-2f0c-4bf3-ae8b-7ea61dcea029" alt="open graph view" /></td>
		</tr>
	</table>
</details>

```html
<meta property="og:type" content="콘텐츠 유형" />
<meta property="og:site_name" content="Starbucks" />
<meta property="og:title" content="콘텐츠 제목" />
<meta property="og:description" content="페이지 설명" />
<meta property="og:image" content="미리보기 이미지 url" />
<meta property="og:url" content="주소" />
```

> [!NOTE]  
> 웹 페이지의 메타데이터를 정의하는 프로토콜로, 사용자에게 미리보기를 제공함으로써
> 클릭하고자 하는 내용이 무엇인지 짐작할 수 있도록 합니다.

<br/>

### 2. Youtube Api🎞
<details>
	<summary><b>💛적용 구간 보기</b></summary>
	<table>
		<tr>
			<td>API 적용</td>
		</tr>
		<tr>
			<td><img src="https://github.com/user-attachments/assets/7ded9b17-65c6-43bb-ace0-11482c1b89e5" alt="youtube api" /></td>
		</tr>
	</table>
</details>

```javascript
var tag = document.createElement('script');

tag.src = "https://www.youtube.com/iframe_api";
var firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

function onYouTubeIframeAPIReady() {
	new YT.Player('player', {
		videoId: '최초 재생할 유튜브 영상 ID',
		playerVars: {
			autoplay: true,
			loop: true,
			playlist: '반복 재생할 유튜브 영상 ID 목록'
		},
		events: {
			onReady: function (event) {
				event.target.mute()
			}
		}
	});
}
```

> [!NOTE]    
> 해당 코드는 아래와 같은 단계로 페이지 내에 영상을 삽입하는 기능을 수행합니다.
> 
> 1. `document.createElement('script')`로 새로운 script 태그를 생성합니다.
> 1. `tag.src`로 API의 URL을 설정합니다.
> 1. `firstScriptTag`는 현재 문서의 첫 번째 script를 찾습니다.
> 1. `insertBefore()`는 생성한 script를 첫 번째 script 앞에 삽입, API를 로드합니다.
>
> 이후에는 `onYouTubeIframeAPIReady` 통해 비디오를 호출하고, 기타 필요한 기능을 제어합니다.

<br/>

### 3. 배너와 위로 가기 버튼🔝
<details>
	<summary><b>💛적용 구간 보기</b></summary>
	<table>
		<tr>
			<td>배너</td><td>위로 가기 버튼</td>
		</tr>
		<tr>
			<td><video src="https://github.com/user-attachments/assets/cff634bf-fb81-4b51-b90d-ab9d50070dca" alt="banner" /></td><td><video src="https://github.com/user-attachments/assets/eda9da4c-3568-40b4-a238-0ed869617b24" alt="top button" /></td>
		</tr>
	</table>
</details>

```javascript
const badgeEl = document.querySelector('header .badges');
const toTopEl = document.querySelector('#to-top');

window.addEventListener('scroll', _.throttle(function () {
  console.log(window.scrollY);
  if (window.scrollY > 500) {
    gsap.to(badgeEl, .6, {
      opacity: 0,
      display: 'none'
    });
    gsap.to(toTopEl, .2, {
      x: 0
    });
  } else {
    gsap.to(badgeEl, .6, {
      opacity: 1,
      display: 'block'
    });
        gsap.to(toTopEl, .2, {
          x: 100
        });
  }
}, 300));

toTopEl.addEventListener('click', function () {
  gsap.to(window, .7, {
    scrollTo: 0
  });
});
```

> [!NOTE]  
> GSAP와 Lodash의 `_.throttle`를 이용하여 배너와 위로 가기 버튼을 구현했습니다.
>
> `_.throttle`를 활용하여 가독성과 효율성을 높였습니다.
> 해당 함수는 지정된 시간 동안 함수를 한 번만 호출하도록 제한하기 때문에, 과도한 트래픽을 예방하여 성능 최적화에 도움이 됩니다.

<br/>
	
### 4. 연도 생성📅
<details>
	<summary><b>💛적용 구간 보기</b></summary>
	<table>
		<tr>
			<td>카피라이트의 연도 자동 업데이트</td>
		</tr>
		<tr>
			<td><img src="https://github.com/user-attachments/assets/67d220ff-4bd4-4aeb-b4c8-9aab9d2eec76" alt="count year" /></td>
		</tr>
	</table>
</details>

```javascript
	const thisYear = document.querySelector('.this-year');
  thisYear.textContent = new Date().getFullYear();
```

<br/>

![Footer](https://capsule-render.vercel.app/api?type=waving&color=5f6571&height=100&section=footer)
