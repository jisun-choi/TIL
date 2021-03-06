## var vs. let vs. const

> var, let, const의 차이점
>
> 1. var는 함수 레벨 스코프이고 let, const는 블럭 레벨 스코프입니다.
> 2. var로 선언한 변수는 선언 전에 사용해도 에러가 나지 않지만 let, const는 에러가 발생합니다. (호이스팅)
> 3. var는 이미 선언되어있는 이름과 같은 이름으로 변수를 또 선언해도 에러가 나지 않지만 let, const는 이미 존재하는 변수와 같은 이름의 변수를 또 선언하면 에러가 납니다.
> 4. var, let은 변수 선언시 초기 값을 주지 않아도 되지만 const는 반드시 초기값을 할당해야 합니다.
> 5. var, let은 값을 다시 할당할 수 있지만 const는 한번 할당한 값은 변경할 수 없습니다(단, 객체 안에 프로퍼티가 변경되는 것까지 막지는 못합니다)

### 함수 레벨 스코프

- 함수 내에서 선언된 변수는 함수 내에서만 유효하고 외부에서 참조할 수 없음

### 블록 레벨 스코프

- 함수, if 문, for, while 문, try/catch 문등 코드 블록 내에서 선언된 변수는 코드 블록 내에서 유효하고 외부에서는 참조할 수 없음

[포이마웹](https://poiemaweb.com/es6-block-scope)
