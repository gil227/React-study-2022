# useState

## **구현**
1. useState의 함수를 이용해서 input 태그를 생성하고 각각 분, 시간을 입력할 수 있게 만든다.
2. value를 삼항연산자를 이용하여 flip시 반환하는 값을 바꿔준다.(이때 리셋 함수를 한번 호출 하여 값을 0으로 초기화한다.)
3. onFlip 함수를 생성하여서 disabled를 전환하여 활성화 input을 교체한다.

> useState 함수(두번째 배열요소 함수)를 이용할때 인수값으로 함수를 입력하여 의도치 않은 값의 변화를 방지 하고,  첫번째 인수에 매개변수를 입력시 값을 참조할 수 있다.

```jsx
const [minute, setMinute] = React.useState();

// current는 minute 값을 반환한다.
// 따라서 current + 1은 minute + 1와 같다.
React.useState((current) => current + 1)
```
