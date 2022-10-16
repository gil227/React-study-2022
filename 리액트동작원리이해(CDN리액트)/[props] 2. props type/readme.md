# Props type
props type js를 이용하여(cdn사용) props로 받은 매개변수들의 타입 힌트를 주고 올바른 타입이 아닐시 에러를 띄우게 해준다.

```js
<script src="https://unpkg.com/prop-types@15.7.2/prop-types.js"></script>
```

리액트에서는 모든 타입을 받아 전달 할수 있기 때문에 올바른지 아닌지 체크를 하기 어려워 props type을 이용하여 보다 정확한 값을 할당할 수 있게 된다.

```jsx
//객체 리터럴 형식으로 사용
Btn.propTypes = {
    //isRequired 사용시 에디트에서 하이라이트로 표시 해준다(웹스톰)
    textData:PropTypes.number.isRequired,
    sizeScale:PropTypes.bool
};
```