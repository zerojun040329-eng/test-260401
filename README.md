```mermaid
erDiagram
  회사 {
    String 회사명 PK
    String 산업분야
    int 희망_구직자_수
    date 신청_기간
    int 초봉
  }
  구직자 {
    String 주민등록번호 PK
    String 전공_분야
    nuumber(3,2) 대학_학점
    int 토익_성적
  }
  자격증 {
    String 주민등록번호 PK, FK
    String 자격증_이름
  }
```
