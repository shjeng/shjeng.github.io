---
layout: post
title: 정선군립 도서관
period: 2024.03 ~ 2024.07
date: 2020-01-12 19:20:23 +0900
category: portfolio
tags: [웹개발, React, Node.js, MongoDB]
role: 프론트엔드 개발
team: 4명 (프론트엔드 2명, 백엔드 2명)
github: https://github.com/username/jeongseon-library
demo: https://jeongseon-library.com
---

## 📋 프로젝트 개요

<div class="portfolio-section">
<div class="portfolio-content">
<ul>
    <li>정선군립 도서관의 웹사이트 신규 구축 개발 프로젝트입니다.</li>
    <li>도서 검색, 대출/반납, 예약 서비스 등 도서관의 핵심 기능을 온라인으로 제공합니다.</li>
    <li>해당 프로젝트를 진행하면서 CMS 초기 버전을 구축했습니다.</li>
</ul>
</div>
<div class="portfolio-image">
    <a href="https://lib.jeongseon.go.kr/main" target="_blank">
        <img src="/public/img/post/06/jeongseon_main.png" alt="정선군립 도서관 메인 페이지"/>
    </a>
    <a href="https://lib.jeongseon.go.kr/main" target="_blank">
        <div class="image-caption">정선군립 도서관 메인 페이지</div>
    </a>
</div>
</div>

---
## 🛠️ 사용 기술

<div class="technology-stack">
  <div class="stack-column">
    <h3>Backend</h3>
    <ul>
      <li><strong>Language</strong>: Java 21</li>
      <li><strong>Framework</strong>: Spring Boot 2.7.18, Spring MVC, EGovFrame, Mybatis</li>
      <li><strong>View Engine</strong>: JSP + JSTL</li>
      <li><strong>Logging</strong>: log4jdbc-log4j2 + Log4j2</li>
    </ul>
  </div>
  <div class="stack-column">
    <h3>Frontend</h3>
    <ul>
      <li>JavaScript, jQuery</li>
    </ul>
    <h3>Database</h3>
    <ul>
      <li>MariaDB</li>
    </ul>
  </div>
</div>

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
            <img src="/public/img/post/06/jeongseon_intro_search.png" alt="인트로 검색">
            <div class="image-caption">인트로 검색 페이지</div>
        </div>
        <div class="image-group">
            <img src="/public/img/post/06/jeongseon_culture_list.png" alt="문화행사 목록 이미지">
            <div class="image-caption">문화행사 목록</div>
        </div>
        <div class="image-group">
            <img src="/public/img/post/06/jeongseon_intro_search.png" alt="도서 검색 및 관리 시스템">
            <div class="image-caption">도서 검색 및 관리 시스템</div>
        </div>
    </div>
</div>

---

## 💡내 역할

- 유저의 관심도서 기능을 위한 DB 설계 및 개발
- 회원 관련 외부 API 연동 및 기능 개발 
- 전역 예외처리
- 게시판 기능 개발
- 홈페이지 관리를 위한 CMS 초기 버전
- ALPAS API 연동(도서관련 기능)

---

## 🌲 성장 경험


### 📌 협업과 유지보수를 고려한 개발 습관의 변화

혼자 공부하던 시절에는 변수명이나 메서드명을 깊이 고민하지 않았고, 로그도 거의 남기지 않았습니다.  
이러한 습관은 실제 프로젝트와 운영 환경에서 다음과 같은 문제를 일으켰습니다:

- 운영 서버에서 **알라딘 API 오류** 발생 → 전체 **책 검색 기능 마비**
- 하지만 **로그가 남지 않아 원인 파악에 큰 시간 소요**
- 협업 시 **의미 없는 변수명**으로 인해 코드 이해에 어려움 발생
- 시간이 지나면서 **자신이 짠 코드조차 이해하기 어려운 상황**이 생김

이러한 경험을 통해 개발 습관을 다음과 같이 개선하게 되었습니다.

#### 🔄 개선 방향

- 변수와 메서드명을 지을 때 **의미 있고 명확한 이름을 고민**
- 로그는 **과하다 싶을 정도로 상세히 기록**
- 이후 **불필요한 로그는 정리**하는 방식으로 유지 관리
- 향후에는 **공식 코드 컨벤션 문서화 및 공유** 계획도 수립

이러한 개선을 통해 협업과 유지보수가 쉬운 코드를 작성하는 데 더 큰 가치를 두게 되었으며,  
운영 안정성 또한 크게 향상시킬 수 있었습니다.


