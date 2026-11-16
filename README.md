## 문제1의 DB
- 자격증의 취득일시를 추가하였습니다.
- 취업신청내역의 신청일시와 취업확정내역의 취업확정일시를 추가하였습니다.
- 구직자에 이름, 전화번호를 추가하였습니다.
- 대학교의 취업자 수는 취업확정내역이 업데이트될때 Trigger를 사용해서 자동으로 업데이트합니다.
- 기업의 희망 구직자 수는 취업신청내역 업데이트시 Trigger를 사용해서 자동으로 업데이트합니다.

```mermaid
erDiagram
  기업 {
    String 회사명 PK
    String 산업분야
    int 희망_구직자_수 
    String 신청_기간
    int 초봉
  }
  구직자 {
    String 주민등록번호 PK
    String 이름
    String 전화번호
    String 대학명 FK
    String 전공_분야
    decimal(3,2) 대학_학점
    int 토익_성적
    int 희망_연봉
  }
  자격증_취득내역 {
    String 주민등록번호 PK, FK
    String 자격증_이름 PK
    date 취득일시
  }
  구직자_취업신청내역 {
    int 신청번호 PK
    String 주민등록번호 FK
    String 회사명 FK
    date 신청일시
  }
  취업확정 {
    int 신청번호 PK, FK
    date 취업확정일시
  }
  대학교 {
    String 대학명 PK
    String 주소
    String 대학설명
    int 취업자_수  
  }

  구직자 ||--o{ 구직자_취업신청내역 : "n"
  기업 ||--o{ 구직자_취업신청내역 : "m"
  자격증_취득내역 o{--|| 구직자 : "자격증 취득"
  구직자 o{--o| 대학교 : "출신대학"
  구직자_취업신청내역 ||--o| 취업확정 : "특수화"
  
```


## 문제2의 DB
- 상행, 하행선이 존재하며 상행선은 정류장 목록의 순서 속성의 오름차순대로, 하행선은 내림차순대로 운행한다고 가정하였습니다.
- 정류장 A->B, B->A 운행할 때 방향에 따라 소요시간이 다를 수 있다고 가정하였습니다.
- 그날 노선에 배치된 버스는 상행, 하행을 왕복하며 운행한다고 가정하였습니다.

```mermaid
erDiagram
  버스_노선 {
    int 버스_번호 PK
    String 배차_간격 
    String 구분
    String 회사명 FK
  }
  정류장_목록 {
    int 정류장_식별id PK
    String 이름
  }
  노선도_구성 {
    int 버스_번호 PK, FK
    int 정류장_식별id PK, FK
    int 하행선_다음정류장_식별id FK
    int 상행선_다음정류장_식별id FK
    int 운행순서
  }
  인접정류장_소요시간 {
    int 출발정류장_식별id PK, FK
    int 도착정류장_식별id PK, FK
    int 분단위_소요시간
  }
  버스_회사 {
    String 회사명 PK
    String 전화번호
    String 주소
    String 대표이사명
  }
  차량 {
    int 차량_번호 PK
    String 회사명 FK
    String 모델
    date 출시연도
  }
  날짜별_노선배치 {
    int 차량_번호 PK, FK
    int 버스_번호 PK, FK
    date 배치일시 PK
  }
  버스기사 {
    String 주민등록번호 PK
    int 근무연수
    int 연봉
  }
  버스기사_운행정보 {
    String 주민등록번호 PK, FK
    String 버스_번호 PK, FK
    date 운행일시 PK
  }
```




