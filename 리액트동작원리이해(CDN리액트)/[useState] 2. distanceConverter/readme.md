# useState

## **1. 들어가기전**

일반적으로 이벤트 리스너를 사용하면 모든 요소들(body 안에 내용이 바뀌기 때문)이 업데이트가 된다.

이때 react의 장점중 핵심이 모든 요소를 업데이트 시키지 않고 UI에서 바뀐 부분만 업데이트가 된다는 것이다.

<br>

## **2. reRender**
리액트에서 이벤트 리스너를 사용했을때 렌더를 다시 해줘야 ui가 업데이트 된다.(여기서 바뀐 ui만 업데이트가 된다.)

useState를 이용하면 리렌더 하지 않고(리렌더 효율 X) ui를 업데이트 할 수있다. 

```jsx
//useState 미사용시 아래 코드를 업데이트 마다 호출 해야한다.
ReactDOM.render(<App/>, renderTarget);
```

<br>

## **3. 배열선언?에 관한 정보**

useState를 사용할때 기본적인 문법에서 배열을 이용하여 선언한다. 이것은 리액트가 아니더라도 일반 자바스크립트에서 사용할 수 있다. ~~(이 생각은 못했네 ...)~~

배열을 사용해서 하는 이유는 코드가 짧아 져서 그런것 같다.

```jsx
//useState 사용시 기본 문법
const [counter, modifier] = React.useState(0); // [0,function]

//일반 js에서 사용하는 법 (useState 문법 원리?)
const x = [1,2];
const [A,B] = x;
console.log(A); // 1 === x[0]
console.log(B); // 2 === x[1]

//배열 없이 사용한다면?
const x = [1,2];
const A = x[0];
const B = x[1];
console.log(A); // 1
console.log(B); // 2
```

<br>

## **4. useState를 사용해보자!**
위에서 봤듯 useState를 콘솔에 찍어볼때 인수로 받은 값을 배열 첫번째요소로, 두번째 요소는 함수가 값으로 할당된다. 

```jsx
console.log(React.useState(0)); // [0,function]
```

첫번째 요소는 우리가 업데이트 시킬 값, 두번째는 리액트 언어에서 리렌더를 대신해 값을 업데이트 해주는 함수라고 이해하면 될것 같다.

>useState를 사용시 인수값을 변수로 사용했을때 의도치 않게 다른 값을 변경 시킬수 있으므로 함수로 사용하는것이 좋다...!