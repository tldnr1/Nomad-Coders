## Cloning-Chrome-App-With-VanillaJS

- html, css, js 의 관계?
    - 브라우저가 html을 열고  
        html이 css, js의 접착제 역할을 한다

- 변수 : __const__, __let__, var
    - const : 상수(constant), 변하지 않는 값 - __항상__
    - let : 변할 수 있는 값 - __가끔__
    - var : 사용 금지 (상수의 개념이 없음) - __네버__

- Booleans
    - true, false : '참, 거짓'이라는 값
    - null : '비어있다'라는 값
        - 절대 자연적으로 발생하지 않음
        - 인위적으로 variable 안에 어떤 것이 없다는 것을 확실히 하기 위해 사용됨
    - undefined : variable은 존재하나 값이 정해지지 않은 상태
        - null은 '비어있음' 값이 정해진 상태지만, undefined는 값이 정해지지 않은 상태임

### JavaScript 기본

- Array : 대괄호 [ ]을 이용하여 생성 + ;. 다른 언어들과 동일

- Objects : 중괄호 { }을 이용하여 생성 + ;. 파이썬과 비슷함
    ```
        const player = {
            name: "RnL",
            points: 10,
            weight: 70
        };
    ```
    - const는 player 자체에만 해당  
        즉, player.name을 변경하거나 player.height를 추가하는 동작은 오류가 아님!
    ```
        player.name = "RnL_"
        player.height = "174"
    ```
- Function : function 함수이름(매개변수) { } 의 형태로 생성. ;은 필요 없음
    - 객체(Objects)의 안과 밖에서 형태가 조금 다름
    ```
         function plus(a, b) {
             console.log(a + b);
         }

         const calc = {
             plus: function (a, b) {
                 console.log(a + b);
             }
         };
    ```

- Conditional : if, else if, else 로 사용. ;은 필요 없음

- 연산자 (대부분 동일, 헷갈린 것만 적어둠)
    - 일치(===) : 두 피연산자의 값과 타입이 모두 같은 경우 true를 반환
    - 조건(삼항) 연산자 : ' condition ? 참값 : 거짓값; ' 의 형태
    - typeof 연산자 : ' typeof 피연산자 ' 의 형태. 피연산자의 타입을 나타내는 문자열 반환

    https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Expressions_and_Operators

### JavaScript on the Browser

- document : html 파일을 저장해둔 것. js에서 document.title 처럼 사용해서 접근 가능
    - js로 html을 수정할 수 있다는 뜻!

- querySelector : 클래스 선택자, id 선택자 등을 이용해서 document에 접근 가능
    - 예시 - const h1 = document.querySelector('div.hello:first-child h1');

- addEventListener : 원하는 이벤트와 그에 대응하는 동작을 만들 수 있음
    - h1.addEventListener("clicked", handleTitleColor);  => h1을 클릭했을 때, handleTitleColor가 실행

- classList : 클래스 이름들을 담아두는 리스트. js와 css를 연동해서 쓸 때 사용
    - className = "" 와 같이 직접적으로 클래스 명을 변경하면 이전 클래스명이 지워짐  
            따라서 classList에 toggle, add, remove 등을 이용해서 기존 클래스를 유지
    ```
        function handleTitleClick() {
            h1.classList.toggle("clicked");

            /*  아래의 코드가 toggle과 동일함
            const clickedClass = "clicked";
            if (h1.classList.contains(clickedClass)) {
                h1.classList.remove(clickedClass);
            } else {
                h1.classList.add(clickedClass);
            } */
        }
    ```

### Login
- Form Submissions
    - form 내부에서 input이나 버튼을 사용하면 페이지가 새로고침이 된다.  
        이를 event.preventDefault(); 를 통해 막을 수 있다.
    ```
        function onLoginSubmit(event) {
            event.preventDefault();
            console.log(loginInput.value);
        }
    ```
    - event : 매개변수로 적은 event는 __js 함수가 반환하는 기본 매개변수__ 이다.  
            즉, addEventListener('click', clickFunction); 이라고 하면  
                clickFunction(event) 라는 함수의 event는 click에 해당하는 event를 받게된다!!
        ```
        [ 아래는 submit event 에 대한 예시 ]
        const loginInput = document.querySelector("#login-form input");

        function onLoginSubmit(event) {
            event.preventDefault();
            console.dir(event);
            console.log(loginInput.value);
        }

        loginForm.addEventListener("submit", onLoginSubmit);
        ```
        - 위 코드에서 console.dir(event) 를 보면 SubmitEvent 라고 뜨는 걸 볼 수 있다!

- classList 활용
    - css에서 hidden이라는 클래스 생성 후,  
        특정 태그에 hidden 클래스를 주면 그 태그를 숨길 수 있다!
        - 당연히 hidden 클래스는 display: none; 이 되어야 함

- 문자열 합치기 with `
    - "Hello " + username 은 ` 로 감싼 Hello ${username} 과 동일함
    ```
    [ 아래의 둘은 동일한 결과 ]
        "Hello " + username

        `Hello ${username}`
    ```

- __Web의 기본 저장소__
    - 개발자 도구(F12) -> Application -> Storage 로 가면 볼 수 있음
    - 다양한 것들이 많고, 각 저장소에 따라 사용 방법이 다르므로 공부 필요! (__API__ 등)
        - local storage는 (key, value) 의 형태로 저장  
            localStorage.setItem("username", "이름")

### Clock
- clock : getClock() 이용
    - getHours(), getMinutes(), getSeconds() 등

- setInterval, setTimeout
    - setInterval(function, ms) : ms 초 마다 function 실행
    - setTimeout(function, ms) : ms 초 뒤에 function 실행

- a.padStart(cnt, x) : cnt 보다 a가 짧으면 x를 모자란 만큼 a 앞에 붙여줌
    - e.g.  "Hello".padStart(7, "x") => xxHello

### Quotes and Background
- Math.random : 0 ~ 1 사이의 난수(float형)를 랜덤으로 생성.
    - Math.random(10) => 0 ~ 9.999... 사이의 수를 랜덤 생성
    - Math.floor 을 통해 내림을 이용해서 정수로 바꿈
        - Math.florr(Math.random(10)) : 0 ~ 9 사이의 정수

- __js를 이용해 html 태그 추가하기__
    - a.createElement(태그명) : a에 새로운 태그를 생성할 수 있음
    - a.appendChild(x) : a에 x를 추가할 수 있음
    ```
        const chosenImage = "0.jpeg";

        const bgImage = document.createElement("img");
        bgImage.src = `img/${chosenImage}`;

        document.body.appendChild(bgImage);
    ```

### To Do List
- list와 push
    - toDos.push(newToDo) 라고 하면 toDos라는 리스트에 newToDo를 추가할 수 있음

- __JSON.stringify()__
    - object, array 상관 없이 다 __JSON 문자열__ 로 바꿔줌