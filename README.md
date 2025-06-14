# 인터넷 기초[04] 과제2 - 나만의 인공지능 서비스

## 개요
- 서비스 명 : <span style="background-color:rgb(182,0,80); color:white; padding: 2px 4px; border-radius: 3px;">혈액형 성격 분석 AIz</span>
- 서비스 설명 : 사용자로부터 **이름**, **생년월일**, **혈액형**을 입력받으면  
  <span style="background-color:rgb(182,0,80); color:white; padding: 2px 4px; border-radius: 3px;">혈액형 성격 분석 AIz</span>는 해당 혈액형을 기반으로  
  사용자의 오늘 기분, 성격 특징, 강점과 약점을 간결하고 긍정적으로 설명해준다.  
  마지막에는 희망을 주는 한 줄 격언을 덧붙여, 하루를 응원하는 메시지를 제공한다.
- 서비스 접속 주소 : [[https://github.com/belita04/duksung_fortune]


---

## 서비스 구성 요소 (1) - Gemini API
- 혈액형 성격 설명과 오늘의 기분 분석은 Google의 대형 언어 모델인 Gemini API를 통해 생성된다.
- 활용 모델 : [Gemini-2.0-flash](https://cloud.google.com/vertex-ai/generative-ai/docs/models/gemini/2-0-flash?hl=ko)
- 시스템 프롬프트 작성 전략
  - AI에게 60년 경력의 성격 분석 전문가라는 역할을 부여함.
  - 응답은 **150자 내외**로 제한하여 간결하게 전달.
  - 내용은 반드시 **긍정적으로**, 마지막에는 희망을 주는 **한 줄 격언**을 추가함.
  - 사용자로부터 이름, 생년월일, 혈액형을 받아 이를 기반으로 텍스트를 생성함.

---

## 서비스 구성 요소 (2) - 프론트엔드

- 전체 웹 페이지는 **HTML + CSS + JavaScript**로 구성되었으며, 정적 웹사이트로 GitHub Pages를 통해 배포됨.
- 입력 요소
  - 이름 (text)
  - 생년월일 (date)
  - 혈액형 (select)
- 버튼 클릭 시 JavaScript로 사용자 데이터를 백엔드에 POST 요청하여 응답을 받아 화면에 출력.
- 스타일은 [style.css](./style.css)로 별도 분리되었으며, 전체적으로 **노란색 계열 톤**과 부드러운 카드 UI로 꾸며짐.
- 이미지 디자인은 [OpenAI Sora](https://openai.com/sora)를 사용하여 직접 생성한 혈액형 관련 일러스트 사용.
  
<img src="./images/ABO.jpg" width="200px" height="200px" alt="혈액형 캐릭터 이미지"/>

---

## 서비스 구성 요소 (3) - 백엔드

- 백엔드는 Google Gemini API를 직접 호출하는 역할을 수행하며, Vercel의 서버리스 기능을 이용해 배포되었다.
- API 경로 :  
  [https://assign2-delta.vercel.app/api/duksungAI]
- 기능 설명:
  - 프론트엔드에서 전송한 JSON 데이터를 받아, `userName`, `userBirth`, `userBloodType` 정보를 기반으로 Gemini API에 요청을 생성.
  - 요청은 서버에서 환경변수로 저장된 Gemini API 키를 사용하여 안전하게 처리됨.
  - 응답 받은 성격 분석 결과를 JSON 형식으로 프론트엔드에 반환.

- 백엔드 코드 및 구현 내용:
[[https://github.com/belita04/duksung_fortune](https://github.com/belita04/duksung-foutune-api)]


---

## 사용 기술 스택
- Frontend: HTML5, CSS3, JavaScript (Vanilla JS)
- Backend: Vercel Serverless Function (Node.js 기반)
- AI 모델: Google Gemini 2.0 Flash
- 배포: GitHub Pages, Vercel

---

## 기대 효과 및 활용 가능성
- 혈액형이라는 가벼운 주제를 통해 사용자와 AI가 소통하는 경험 제공
- Gemini API를 통한 간단한 생성형 AI 서비스 구현 연습
- 학습용 프로젝트로, 사용자 입력 → 백엔드 API 호출 → AI 응답 생성 → 프론트에 표시되는 전 과정을 경험할 수 있음
