## Cloning-Chrome-App-With-VanillaJS

- html, css, js 의 관계?
    - 브라우저가 html을 열고  
        html이 css, js의 접착제 역할을 한다

- 변수 : __const__, __let__, var
    - const : 상수(constant), 변하지 않는 값
    - let : 변할 수 있는 값
    - var : 사용 금지 (상수의 개념이 없음)

- Booleans
    - true, false : '참, 거짓'이라는 값
    - null : '비어있다'라는 값
        - 절대 자연적으로 발생하지 않음
        - 인위적으로 variable 안에 어떤 것이 없다는 것을 확실히 하기 위해 사용됨
    - undefined : variable은 존재하나 값이 정해지지 않은 상태
        - null은 '비어있음' 값이 정해진 상태지만, undefined는 값이 정해지지 않은 상태임

### JavaScript 자료구조 기본

- Array : 대괄호 [ ]을 이용하여 생성. 다른 언어들과 동일

- Objects : 중괄호 { }을 이용하여 생성. 파이썬과 비슷함
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