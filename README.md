```mermaid
erDiagram
  기업 {
    String 회사명 PK
    String 산업분야
    int 희망_구직자_수 
    date 신청_기간
    int 초봉
  }
  구직자 {
    String 주민등록번호 PK
    String 대학명 FK
    String 전공_분야
    nuumber(3,2) 대학_학점
    int 토익_성적
    int 희망_연봉
  }
  자격증_취득내역 {
    String 주민등록번호 PK, FK
    String 자격증_이름 PK, FK
    date 취득일시
  }
  구직자_취업신청내역 {
    String 주민등록번호 PK, FK
    String 회사명 PK, FK
    date 신청일시
  }
  취업확정_구직자 {
    String 주민등록번호 PK, FK
    String 회사명 PK, FK
    date 신청일시
  }
  대학교 {
    String 대학명 PK
    String 주소
    String 대학설명
    int 취업자_수
  }

  구직자 ||--o{ 구직자_취업신청내역 : "신청한다"
  회사 ||--o{ 구직자_취업신청내역 : "신청을 받는다"
```





