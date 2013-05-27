SeatJs Developer Style Guide
===
---
Coding Convention
---
  - 기본적으로는 [Felix's Node.js Style](http://nodeguide.com/style.html)을 따릅니다.
  - callback 함수의 첫 번째 argument는 err
  - callback을 arguement로 넘여야 한다면, 맨 마지막에 표시

    ```
    listen.on('event', function(err, data, callback)){ ...
    ```
  - data나 callback은 구조를 comment에서 설명

    ```
    /**
     * 특정 페이지를 작업중 페이지로 추가한다.
     * @param page { name: ..., id: ...}
     * @param user
     * @param callback (err, 추가성공여부 true/false)
     * @return {*}
     */
    exports.update = function(page, user) {
      if (page.id == undefined) {
        throw new WorkingPageError("page id doesn't exits!");
      }
    ```
  - private method는 "_"로 시작

    ```
    var _go = function(){...}
    ```

  - js file로 클래스를 구분(file명은 소문자)

    ```
    예) Worker Class는 => project_home/lib/worker.js
    ```
  - commit log
     - 첫줄은 50자 정도의 요약
     - 부연설명이 더 필요한 경우,
         - 한 줄을 띄고
         - 그 다음에 부연설명 본문을 작성
         - 한 줄의 너비는 80자
  - 줄바꿈은 LF만 사용
  
    ```
    git config core.autocrlf input
    ```
  - trailing white spece는 제거
  
    ```
    git config apply.whitespace fix
    ```

Achitechture
---
   - Language: Javascript
   - Platform: [node.js](http://nodejs.org)
   - Web Framework: [express](http://expressjs.com/)
   - Template Engine: [jade](http://jade-lang.com/)
   - UI toolkit: [Bootstrap](http://twitter.github.com/bootstrap/)

Documentation & Comments
---
  - [Comments Sample](https://github.com/visionmedia/mocha/blob/master/lib/mocha.js)
  - 기본문서 포맷: markdown, plain text

Test
---
  - [Mocha](http://visionmedia.github.io/mocha/)를 사용
  - Write and Run
     - write: ./test 디렉터리에 작성
     - run: mocha  -u tdd  -R spec
  - Travis CI
       - [Sameple Project](http://travis-ci.org/doortts/node-test-samples)
 
Development Environment
---
  - Default Encoding Type: UTF8
  - Folder 구성
  
    ```
    seatjs
        ./docs      <- 각종 문서들, spec들
        ./lib       <- 직접 작성한 라이브러리
        ./lib_ext   <- 직접 가져온 외부 모듈
        ./locales   <- locale message files
        ./node_module
        ./test      <- test 코드
    ```


Loggin Level
------------
     info : 1,
     warn : 2,
     debug: 3,
     error: 4
