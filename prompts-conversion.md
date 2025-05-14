#조회 화면 컨버전 소스 생성 프롬프트

### 작업지시
원본 소스인 (원본소스)파일을 아래 내용 고려해서 컨버전해줘.
- 똑같이 생긴 화면을 만드는 것이 목표가 아님. 
- 기존 스타일링은 버리고 ui의 스타일링과 레이아웃은 (결과참조)를 베이스로 재구성할 것.
- 컨버전 시 필수로 반영할 요소들은 검색조건, 조회결과 테이블 컬럼정의 등 데이터와 화면의 기능적인 요소이며
이를 목록화하여 결과물 참조 파일인 (결과참조)와 화면 구성과 유사하게 만들 것.
- (결과참조)에서 레퍼런스하고 있는 파일을 컨텍스트로 활용해서 사용하고 있는 컴포넌트를 재활용하는 것을 고려할 것.
- 커스텀 ui컴포넌트는 이 경로(react-plus-admin/apps/web/src/components/) 하위에 있음. 추가 생성이 필요한 경우에는 요청자에게 확인 받을 것.
- (라우터파일참조)라우터 파일은 이 파일을 참조.
- 라우팅 url은 (라우터url참조) 로 설정해줘.


### 참조 변수
(원본소스) >>> 원본소스
(결과참조) >>> 최종 컨버전 결과 생성 시 참조할 파일
(라우터파일참조) >>> 라우터 생성 시 참조 파일
(라우터url참조) >>> 라우팅 URL 문자열


### 작업 후 생성된 파일 경로 설정
아래 경로 하위에 생성할 것.
- 라우터파일: react-plus-admin/apps/web/src/routes/
- 화면: react-plus-admin/apps/web/src/features/


### 컴포넌트 구조화 지침
1. 메인 컴포넌트는 최소한의 상태 관리와 레이아웃 구성만 담당
2. 검색 조건 영역은 별도의 컴포넌트로 분리
   - 검색 조건 별 레이아웃은 다음 경로 하위 컴포넌트 활용 고려. react-plus-admin/apps/web/src/components/form
   - 검색 조건 별 입력 컴포넌트는 다음 경로 하위 컴포넌트 활용 고려. react-plus-admin/apps/web/src/components/fields
    - radio > radio-group-field.tsx 사용 
    - ckeckbox > checkbox-group-field.tsx 사용
    - 상품분류 셀렉터 > product-category-select.tsx 사용
    - 날짜 기간 설정 > date-range-picker.tsx 사용
    - only숫자 인풋 > number-field.tsx 사용
   - 공통으로 사용되는 필터 로직은 hooks로 분리
3. 조회 결과 영역은 별도의 컴포넌트로 분리
   - 테이블 컬럼 정의는 별도 파일로 분리
   - 테이블 관련 로직은 hooks로 분리
4. 공통 컴포넌트 재활용
   - (결과참조)에서 사용 중인 컴포넌트 우선 사용
   - 필요한 경우 새로운 공통 컴포넌트 생성 요청

### 파일 구조 예시
```
features/
  ├── products/
  │   └── prd-ship-mgr-list/
  │       ├── index.tsx                    # 메인 컴포넌트
  │       ├── types/                       # 타입 정의
  │       ├── api/                         # API 연동
  │       ├── hooks/                       # 커스텀 훅
  │       └── ui/                          # UI 컴포넌트
  │           ├── prd-ship-mgr-list-filter.tsx          # 검색 조건 컴포넌트
  │           ├── prd-ship-mgr-list-index.tsx           # 조회 결과 컴포넌트
  │           └── prd-ship-mgr-list-columns.tsx         # 테이블 컬럼 정의
```



