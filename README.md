<br/>
<br/>
<br/>

<p align="center"><img src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/df3191d3-f245-4e4b-8eee-bf2e2562fd76" alt="Mogazoa" width="400" height="70"></p><br>
<br>

# Mogazoa - 음악, 식당, 영화, 강의, 여행지, 전자기기, 호텔, 와인, 옷, 앱 등 다양한 분야의 상품을 리뷰하는 플랫폼

- 개발 기간 : 2024.05.18 ~ 2024.06.27
- 배포 주소 : https://mogazoa4-20.vercel.app/

<br/>

**개발 모드로 실행하기**

```
git clone https://github.com/Mogazoa-team20/mogazoa.git

npm install

npm run dev
```

---

## ⚙️ TechStack

<div align="left">

<img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white">
<img src="https://img.shields.io/badge/TypeScript-3178c6?style=for-the-badge&logo=typescript&logoColor=white">
<img src="https://img.shields.io/badge/Sass-CC6699?style=for-the-badge&logo=sass&logoColor=white">
<img src="https://img.shields.io/badge/Tanstack-query?style=for-the-badge&logo=tanstackQuery&logoColor=white">
<img src='https://img.shields.io/badge/ESLint-4B3263?style=for-the-badge&logo=eslint&logoColor=white'>
<img src='https://img.shields.io/badge/React%20Hook%20Form-%23EC5990.svg?style=for-the-badge&logo=reacthookform&logoColor=white'>

<br/>

### Next.js

---

- 기획에 제시된 사이트 특성상 다수의 프로덕트 페이지가 존재하며, 해당 페이지 별 SEO가 중요할 것이라고 판단하여 `Next.js`를 도입
- 서버 컴포넌트를 활용해 서버사이드에서 동작할 로직을 다루고 클라이언트 단과 역할을 분리하여 사용하기 위해 `app router`를 사용
  - 인터랙션이 많은 페이지에서도 최대한 빠르게 화면을 렌더링하여 유저에게 최적의 경험을 선사할 수 있도록 함
  - 보여줄 필요가 없는 & 숨겨야 하는 로직을 다루기에 용이함
  - `Next.js`에서 `fetch API`에 제공하는 `revalidate` 기능을 활용
- 파일 시스템은 `colocation`을 활용해 페이지, 컴포넌트 내부에 연관성 있는 파일을 함께 관리함
  - 관련된 파일을 쉽고 빠르게 찾을 수 있어 수정 및 유지 보수 등 관리에 용이함

### Tanstack query

---

- 쿼리키를 기반으로 데이터를 캐싱
- useQuery는 특정 조건에서 자동으로 데이터를 가져오기 때문에 최신 정보를 유지하고 표시할 수 있다.
  - 새로운 쿼리 인스턴스가 마운트
  - 브라우저 창에 다시 포커스
  - 네트워크가 다시 연결
  - 미리 설정해 둔 refetch interval 시간이 지났을 때
- useSuspenseInfiniteQuery 훅을 통해 무한 스크롤과 suspense를 쉽게 구현할 수 있다.

### CSS module / Sass

---

- `CSS-in-JS` 같은 경우 런타임에 스타일시트를 생성하고 `DOM` 요소에 주입하게 되므로 서버 컴포넌트에서 사용하기 위해서는 별도 처리가 필요함
- `Next.js` 에서 서버 컴포넌트를 사용할 때 조금 더 권장하는 방식
- 컴포넌트 파일과 스타일 파일의 분리를 원했음
- 클래스 명 중복을 방지할 수 있고 변수, 중첩 규칙, 믹스인을 통해 확장된 기능을 사용할 수 있는 `CSS module`과 `Sass`를 채택함

### TypeScript

---

- 타입 지정을 통해 버그 발생을 예방하고, TSC를 통해 미리 에러를 찾아 대응할 수 있음
- 데이터 타입을 명시함으로써 협업 개발 환경을 좀 더 편리하게 함 (코드 작성에만 집중하고 별도로 각 데이터의 데이터 타입을 찾아볼 필요 없음)

### ESLint / husky / stylelint

---

- 협업 컨벤션을 지키고 발생할 수 있는 에러를 최소화/사전 방지 하기 위해 사용함

### react hook form

---

- 모달을 이용한 폼 제출이 많다.
- 폼 상태 관리를 최적화하여 불필요한 리렌더링을 최소화(`uncontrolled input`)
- 현재 입력 값, 에러 상태, 제출 상태를 쉽게 관리할 수 있고 폼 전체의 상태를 추적할 수 있다.
- 직관적이어서 가독성 높은 코드를 작성할 수 있다.

### next-auth

---

- 로그인 뿐 아니라 자체적으로 `oauth provider`를 제공해 간편 로그인을 보다 쉽게 구현할 수 있음
- 사용자 인증 및 세션 관리를 서버 측에서 처리할 수 있어 보안상 이점이 있음
- `next-auth`에서 제공하는 기능을 통해 사용자 인증 및 세션 관리를 손쉽게 처리 가능함

### react-cropper

---

- 제공된 UI 시안에서 모든 이미지의 비율이 1:1로 정해져있음
- 유저가 비율이 다른 이미지를 업로드할 경우, 유저가 노출하고자 했던 부분의 이미지가 아니거나 이미지 비율이 깨지는 등의 문제가 발생할 수 있음
- 최대한 유저가 의도한 대로 이미지를 업로드할 수 있도록 이미지 크롭 기능을 추가하기 위해 사용함

### cheerio

---

- 상품 상세 페이지에서 유저에게 상품 구매로 바로 이동할 수 있는 페이지를 제공해주고 싶었음
- 네이버는 `search API`를 지원하지만, 쿠팡은 별도로 지원하지 않음
- 프론트에서 크롤링을 돌리는 대신 `Next.js`에서 지원하는 `Serverless Functions`를 사용하기 위해 `node` 라이브러리 중 `HTML` 파싱을 도와주는 `cheerio`를 선택해 사용함

### uuid

---

- 토스트 컴포넌트 구현시 개별 토스트에 유니크한 `id`값을 부여하기 위해 사용

<br/>

## 🪡 Communication

<img src="https://img.shields.io/badge/visualstudiocode-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white">
<img src="https://img.shields.io/badge/Discord-5865f2?style=for-the-badge&logo=discord&logoColor=black">
<img src="https://img.shields.io/badge/Figma-f24e1e?style=for-the-badge&logo=figma&logoColor=black">
<img src="https://img.shields.io/badge/github-181717?style=for-the-badge&logo=github&logoColor=white">

</div>
<br>
<br/>
<br/>

## 👑 팀원 구성

| <img src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/7afc9ffd-05e9-4f75-a5c7-ca806268a876" width="150" height="150"/> | <img src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/6555fe97-b8b0-46d5-a412-5eeb37af0990" width="150" height="150"/> | <img src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/f9ccc488-4301-46b7-81b8-4ffb667e9a39" width="150" height="150"/> | <img src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/fa25bf75-d4bd-43e8-8b58-9f19249462af" width="150" height="150"/> | <img src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/47a3385d-fb21-4115-9893-36f066ffaa38" width="150" height="150"/> |
| :----------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------: |
|                                      FE : 길수진 <br/> [@suzinxix](https://github.com/suzinxix)                                      |                                        FE : 박유빈 <br/> [@yb3143](https://github.com/yb3143)                                        |                                     FE : 박준영 <br/> [@zoonyoung](https://github.com/zoonyoung)                                     |                                        FE : 유아름 <br/> [@aoooec](https://github.com/aoooec)                                        |                                       FE : 이진우 <br/> [@yeeZinu](https://github.com/yeeZinu)                                       |

<br>

## 🌸길수진

#### 비개발 분야

- 프로젝트 초기 세팅
- 템플릿 추가

#### 개발 분야

- 메인 페이지, 상품 추가 모달
- GNB/공통 드롭다운/프로덕트 카드 컴포넌트

## 🌻박유빈

#### 비개발 분야

- 전체 일정 관리
- README 작성

#### 개발 분야

- 비교하기 페이지
- 공통 칩 컴포넌트

## 🍀박준영

#### 비개발 분야

- 전체 컨벤션 및 룰 문서화
- 회의록 작성

#### 개발 분야

- 상품 상세 페이지, 리뷰 추가 모달
- 공통 모달/인풋 컴포넌트, 상품 리스트(쿠팡/네이버) 컴포넌트

## 🌷유아름 (팀장)

#### 비개발 분야

- 발표
- 일정 관리, 기록 보조

#### 개발 분야

- 로그인/회원가입/간편회원가입/에러/404 페이지
- 공통 유저 아이템/토스트 컴포넌트

## 🌼이진우

#### 비개발 분야

- 레포지토리 생성
- 프로젝트 배포
- 웹 후크 연결

#### 개발 분야

- 유저 페이지, 프로필 수정/팔로우/팔로잉 모달
- 공통 버튼/상품 통계 카드 컴포넌트

<br>

## 💻 프로젝트 내용

### 로그인 & 회원가입 페이지

<img width="1680" alt="로그인 페이지" src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/b028d0c7-8d26-4f2c-9c6a-2df8342a7cca">
<img width="1680" alt="회원가입 페이지" src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/ccf7ca62-aaf0-4d09-89de-224d0e42325a">

- Cookie로 AccessToken을 저장하고 인증하여 로그인과 회원가입을 할 수 있습니다.

### 홈페이지

<img width="1680" alt="홈페이지" src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/b4c0aca7-f762-4077-956e-a93a574daa90">

- 카테고리를 선택하지 않았거나 검색어가 없을 경우에는 “지금 핫한 상품 Top 6” 와 “별점이 높은 상품” 을 볼 수 있습니다.
- 메인 페이지에서 불러오는 데이터는 실시간으로 자주 바뀌지 않는 데이터라고 판단했습니다.
- 이러한 특성에 맞춘 서버 컴포넌트 선택하여 초기 로딩 속도를 크게 향상시켰습니다.

### 상품 상세 페이지

<img width="1680" alt="상품 상세 페이지" src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/a0397c26-a363-45ed-a5dc-8af4c5bad7af">

- 상품에 대한 정보를 확인할 수 있습니다. (이미지, 이름, 카테고리 등)
- 상품 상세 화면 링크를 카카오톡으로 공유하거나 클립보드에 복사할 수 있습니다.
- 비교하기, 상품 리뷰, 상품 찜 등 여러 기능들을 사용할 수 있습니다.

### 비교하기

<img width="1680" alt="비교하기 페이지" src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/3353055c-b99a-421d-9520-2106dc562dc4">

- 상품 입력창을 통해 비교 상품을 수정하거나 제거할 수 있습니다.
- 이미 비교 등록했던 상품이 있다면 입력창에 상품이 입력된 채로 보여집니다.
- 상품 입력창에 상품명을 입력하면 입력값과 관련된 상품 목록이 보여집니다. 보여진 상품 목록에서 상품을 클릭하여 비교 상품을 등록할 수 있습니다.

### 유저 프로필 화면

<img width="1680" alt="내 정보 페이지" src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/485ab762-0523-4d3d-9488-71060b382b6a">
<img width="1680" alt="유저 페이지" src="https://github.com/Mogazoa-team20/mogazoa/assets/96522163/d7e7d888-c640-43f3-8a73-61425733fb20">

- 나와 다른 유저의 프로필을 확인할 수 있습니다. <br/>
- 유저 닉네임, 프로필 이미지, 팔로워 수, 팔로잉 수, 프로필 소개를 확인할 수 있습니다.
