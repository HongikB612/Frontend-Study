## 📁Project Structure

```
│
├─ frontend-study
│     │
│     ├─ young0519 (dir)
│     │     │
│     │     ├─  모던자바스크립트(book)
│     │     │    ├─ week1
│     │     │    |    ├─ 주제.md
│     │     │    |    ├─ 콜백함수.md
│     │     │    |    ├─ ...
│     │     │    ├─ week2
│     │     │    ├─ ...
│     │     ├─  JS문제풀이
│     │     │    ├─ week1
│     │     │    |    ├─ 문제번호.md
│     │     │    |    ├─ ...
│     │     │    ├─ week2
│     │     │    ├─ ...
│     │     ├─ .. 이하동일
│     │
│     ├─ 본인 아이디 (dir)
│     │     │
│     │     ├─  .. 이하동일
│     │
│     ├─ .. 이하 동일
│
│
```

> 파일 이름은 상관없지만, 나머지 폴더 구조, 이름, 양식 같은 것은 지켜주세요 🙏
> 

## 🔒Rule

1. 일정 
    - 교내 카페 오프라인
    - 화요일 19:00 ~ 21:00 (2주당 1번)
2. 커뮤니케이션 툴
    - 급한 일정은 카톡
    - 디스코드 프론트엔드 방 활용하기 ❗

3. 스터디 방식

- 각자 커리큘럼에 맞춰 공부 및 간단히 정리 (요약 & 느낀점)
- 

## 👨‍💻 Process

1. 해당 레포지토리를 fork
2. **본인 id**로 된 **브랜치**를 생성 후 커밋
3. 레포지토리에 공부한 내용 push
4. 화요일 18:00 전까지 본인 id branch에 `Pull Request` 생성
5. TM에게 PR 날렸다고 말하기
6. 노션에도 동일하게 자료 생성

## 📄PR Guide

**Git 사용법**

1. B612 Frontend Git을 본인 깃허브 계정으로 **fork**하기
2. fork 한 레포를 **Clone**
→  `git clone [레포 클론 주소]`
3. `**git remote -v**`를 통해 먼저 연결된 **원격 저장소**를 확인
    - 보통 다음과 같이 되어 있을 것
        
        `origin  [https://github.com/young0519/Frontend-Study.git](https://github.com/young0519/Frontend-Study.git) (fetch)
        origin  [https://github.com/young0519/Frontend-Study.git](https://github.com/young0519/Frontend-Study.git) (push)`
        
    - `git remote add **upstream** [https://github.com/young0519/Frontend-Study.git](https://github.com/young0519/Frontend-Study.git)`
        
        를 입력하여 원격 저장소에 원본 저장소를 추가한다
        
    - 참고로 origin과 upstream은 변수명임. 여기에 원격 레포지토리 주소를 변수로써 저장한다는 뜻임
4. 매번 새로 들어올 때마다, `**git fetch upstream**`을 통해 원본 저장소와 내 포크한 레포를 동기화시켜주는 것이 좋다.
    - `fetch`는 이후에 `merge` 과정을 거쳐야 하는데, fetch+merge를 합친 명령어로 `pull`이 있다.
    - `**git pull upstream main`해서 원본 저장소의 main 레포지토리를 pull한다.**
    - 참고로 이 pull 과정을 안 했을시 이후에 merge conflict 등 다양한 문제가 발생할 수 있어서, 꼭 pull을 해주는게 좋다
5. 작업을 열심히 마무리하고선, `**git add [파일명]**`을 통해 변경사항이 들어있는 파일을 스테이징 아리아로 옮긴다.
    - `**git add .**`를 하면 모든 변경된 파일이 스테이징 아리아에 올라간다.
    - 대신 이때는 수동으로 필요없는 파일들은 지운다
6. `**git commit -m [커밋메시지]**`로 스테이징된 파일들을 로컬 레포지토리로 옮긴다
    - 커밋 메시지 컨벤션은 후술할 내용 참조
7. `**git push origin**`으로 원격 레포지토리에 푸시한다.
    - 참고로 이때 origin 뒤에 브랜치 이름을 붙인다면 해당 브랜치로 푸시된다
    - 예를 들어 `git push origin young0519`라 하면 young0519라는 브랜치로 푸시됨
    - **upstream**으로 푸시하지 않는다.
8. 이후에 github.com으로 가서, 변경사항을 확인한 후 `**Create Pull Request**`를 눌러 `**pull request**`를 생성해준다
9. merge conflict가 나는지 확인한 후에, submit 브랜치에 PR을 생성한다

**PR 이후**

매주 화요일마다 제(young0519)가 PR을 모두 체크한 뒤에, main으로 merge할 것 입니다. 만약 수정사항이 있으면 PR을 거절하고, 다시 PR을 보내달라고 요청할 것입니다. 이때 목요일까지 다시 수정해서 올려주시면 됩니다.

## 🔐Commit Rule

하단의 규칙을 최대한 적용해서 일관되게 작성해주세요.

1. 단위 기능 별로 커밋한다.
    - 너무 많은 커밋을 남기는 것은 좋지 않으나, 적당히 기능/수정 사항 별로 쪼개서 커밋을 남기는 게 좋다.
2. 커밋 메시지는 일관되게 영어로 작성한다.
    - 커밋 메시지 규칙은 하단을 참고해주세요.
3. 제목과 본문을 빈 행으로 구분한다
4. 제목을 50글자 내로 제한
5. 제목 첫 글자는 대문자로 작성
6. 제목 끝에 마침표 넣지 않기
7. 제목은 명령문으로 사용하며 과거형을 사용하지 않는다
8. 본문의 각 행은 72글자 내로 제한
9. 어떻게 보다는 무엇과 왜를 설명한다

+ Frontend Study 특별 규칙

- 매 주차 첫 커밋 시 `Study (언어) (주제) on (주차)` 로 커밋한다
    - 예: `Study HTML tag on week2`
- • PR의 제목 : `Study (언어) (주제) on (주차)` 로 작성한다

## **Commit 유형 방식**

- Feat : 새로운 기능의 추가
- Fix: 버그 수정
- Docs: 문서 수정
- Style: 스타일 관련 기능(코드 포맷팅, 세미콜론 누락, 코드 자체의 변경이 없는 경우)
- Refactor: 코드 리펙토링
- Test: 테스트 코트, 리펙토링 테스트 코드 추가
- Chore: 빌드 업무 수정, 패키지 매니저 수정(ex .gitignore 수정 같은 경우)
- Study: 과제 제출 (Frontend Study에만 있는 깃허브 명령어)

**예시**

```html
Docs: Update Readme
```

```html
Feat: Add Fibonacci function
```

```html
Fix: Fibonacci function to working with long long type

Now fibonacci function uses long long type, and if overflows happens function throws error
```

```html
Fix: Anagram_hash function returns invalid hash error

Now anagram_hash function returns valid hash, which is ordered by lexicographical order
```

```html
Style: Apply clang-format to main.cpp, use llvm format
```

```html
Refactor: Rename the cnt variable to testCount

Rename the variable with more descriptive name
```

```html
Refactor: remove unused import
```

```html
Study HTML tag on week2
```
