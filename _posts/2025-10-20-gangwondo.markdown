---
layout: post
title: 강원도 교육청 도서관
period: 2025.06 ~ 2025.09
date: 2025-10-20 14:38:23 +0900
category: portfolio
tags: [library]
role: 도서관 웹페이지 개발
team: 4명 (프론트엔드 2명, 백엔드 3명)
demo: https://lib.wonju.go.kr/portal/main
---

## 📋 프로젝트 개요

<div class="portfolio-section">
    <div class="portfolio-content">
    <ul>
        <li>강원도 교육청 도서관의 고도화 프로젝트입니다. </li>
        <li>이용자 홈페이지 및  CMS를 개발했습니다. </li>
        <li><a href="https://lib.gwe.go.kr/portal/main" target="_blank" rel="noreferrer">강원도 교육청 도서관 주소</a></li>
    </ul>
    </div>
    <div class="portfolio-image">
        <a href="https://lib.gwe.go.kr/portal/main" target="_blank" rel="noreferrer">
            <img src="/public/img/post/gangwondo/portal_main.png" alt="강원도 교육청 도서관 메인 페이지"/>
        </a>
        <a href="https://lib.gwe.go.kr/portal/main" target="_blank" rel="noreferrer">
            <div class="image-caption">강원도 교육청 도서관 메인 페이지</div>
        </a>
    </div>
</div>

---

## 🛠️ 사용 기술

### Backend

- **Language & Runtime**: Java 21
- **Framework**: Spring Boot, EGovFrame, JPA, QueryDSL, Mybatis
- **View Engine**: JSP + JSTL
- **Logging**: log4jdbc-log4j2 + Log4j2

### Frontend

- JavaScript, jQuery

### Database

- MariaDB
- Redis

---

## 🎯 주요 기능

<div class="portfolio-section">
    <div class="portfolio-content">
    <h3>1. 도서 관련 기능 제공</h3>
    <ul>
        <li>실시간 도서 검색</li>
        <li>희망도서 신청</li>
        <li>도서 예약</li>
        <li>도서 상세 정보 제공</li>
    </ul>

    <h3>2. 문화/행사</h3>
    <ul>
        <li>문화/행사 등록 및 수정 기능 제공</li>
        <li>신청자 관리 기능</li>
        <li>이용자에게 문화/행사 신청 기능 제공</li>
    </ul>

    <h3>3. 사용자 관리</h3>
    <ul>
        <li>회원가입/로그인</li>
        <li>개인정보 관리</li>
        <li>대출 현황 확인</li>
    </ul>

    <h3>4. CMS</h3>
    <ul>
        <li>배너, 팝업 등 홈페이지 관리 기능</li>
        <li>게시판 관련 기능</li>
        <li>문화/행사 관리 기능</li>
    </ul>

</div>
    <div class="portfolio-image">
        <div class="image-group">
            <img src="/public/img/post/gangwondo/search.png" alt="검색">
            <div class="image-caption">검색 페이지</div>
        </div>
        <div class="image-group">
            <img src="/public/img/post/gangwondo/cms_main.png" alt="CMS 메인 페이지">
            <div class="image-caption">CMS 메인 페이지</div>
        </div>
    </div>
</div>

---

## 💡내 역할

- 유저의 관심도서 기능을 위한 DB 설계 및 개발
- 회원 관련 외부 API 연동 및 기능 개발
- 게시판
  - 게시글 조회 속도 개선 (1~1.5s -> 79ms)
  - 커스텀 컬럼 기능 개선 및 추가 
- 회원 로그인 및 정보 수정 이력 로그 저장 
  - 이후에 위 활동 외에 추가로 회원 활동 이력 로그를 저장해야할 일이 생길 경우를 대비해서 어노테이션과 AOP로 해당 기능을 구현함  

```
@GuestOnly
@PostMapping("/user/login")
@UserActivity("LOGIN") // 사용하기 쉽게 하기 위한 어노테이션
public String login(Model model, @PathVariable String homepagePathName, @PathVariable Long menuSn
```

```
 @Pointcut("@annotation(egovframework.apex.homepage.user.annotation.GuestOnly)")
public void checkGuestOnly() {
}

@Before("checkGuestOnly()")
public void guestOnlyBeforeMethod() throws IOException {
```

- 서고자료신청 모듈 개발 

---

## 🚀 트러블 슈팅

### 📦 본인인증 후 인증 실패 오류(방화벽 이슈)
#### ⚠️ 문제 상황
> 본인 인증 완료 후, 인증 결과 값을 받아야 하는 서버가 응답을 받지 못하는 상황이 발생.
>
> 고객사의 보안 정책으로 인해 URL 길이 제한으로 응답 값을 받지 못하는 상황.
>
> 따라서 고객사에서 GET으로 데이터를 받지 말고 POST로 받으라는 답변을 받음.
#### ✅ 해결 방법
1. 본인인증사에 POST로 데이터를 달라고 요청 -> POST로 보내주고 있지만, 특정 브라우저(크롬)의 경우에는 GET으로 밖에 데이터를 못 보내준다고 함
2. 해당 답변을 메일로 받은 뒤 고객사에 전달 
3. GET URL 길이 제한 해제 

### 📦 FileCountLimitExceededException

#### ⚠️ 문제 상황

> 페이로드의 데이터 수가 51개 이상일 경우 해당 예외 발생.
> 
> 톰캣 9.0.106 패치에서  CVE-2025-48988 취약점으로 인해 parts 수 제한하는 maxPartCount 설정이 추가됐고, 9.0.107 버전부터는 최대 50개까지 받을 수 있도록 기본 값이 셋팅돼 있음.

#### ✅ 해결방법

> conf/server.xml의 maxPartCount 를 100으로 늘려주어서 해결

```
<Connector port="8080" protocol="HTTP/1.1"
   connectionTimeout="20000"
   maxPartCount="100" # 이 부분 설정 추가
   redirectPort="8443" />
```

---

## 📸 프로젝트 스크린샷

<div class="screenshot-grid">
<div class="screenshot-item">
        <img src="/public/img/post/gangwondo/gnecc_main.png" alt="중앙도서관 메인 페이지 1">
        <div class="image-caption">메인 페이지</div>
    </div>
    <div class="screenshot-item">
        <img src="/public/img/post/gangwondo/join.png" alt="회원가입 페이지">
        <div class="image-caption">회원가입 페이지</div>
    </div>
    <div class="screenshot-item">
        <img src="/public/img/post/gangwondo/board1.png" alt="게시판">
        <div class="image-caption">게시판</div>
    </div>
    <div class="screenshot-item">
        <img src="/public/img/post/gangwondo/cms_menu.png" alt="cms 메뉴 관리">
        <div class="image-caption">메뉴 관리</div>
    </div>
    <div class="screenshot-item">
        <img src="/public/img/post/gangwondo/banner.png" alt="배너관리">
        <div class="image-caption">배너 관리</div>
    </div>
    <div class="screenshot-item">
        <img src="/public/img/post/gangwondo/locker.png" alt="사물함">
        <div class="image-caption">사물함 관리</div>
    </div>
</div>
