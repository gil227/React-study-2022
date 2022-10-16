# props, memo

<br>

## 1. props
props는 부모컴포넌트가 자식 컴포넌트에게 값(프로퍼티)을 전달 할때 쓰인다. 한가지 컴포넌트를 사용할때 특정 부분만 다른경우 사용하여 구현한다. 인수로는 모든 값을 받을수있다.(원시값, 객체, 함수 등등..)

```jsx
function Btn({props}){
    return(
        <span>{props.data}</span>
    )
}

function App(){
    return(
        <div>
            <Btn data="btn" />
        </div>
    )
}

//축약 방법
function Btn2({data}){
    return(
        <span>{data}</span>
    )
}
```

<br>

## 2. props와 useState 사용
props의 값으로 함수를 받을수도 있으며 이때 useState의 setter함수를 보내서 값을 변경 하는것도 가능하다.

>이때 자식 컴포넌트에 쓰는 프로퍼티로 onClick을 써도 props이다.(이벤트 핸들러X) 따라서 부모 컴퍼넌트에 매개변수를 사용하여 이벤트핸들러는 따로 달아야한다.

```jsx
function Btn({data,change}){
    console.log(arguments);// [{ data:btn, f ChangeValue() },{}]
    return(
        //따로 onClick 핸들러를 달아야한다.
        <button onClick={change}>{data}</button>
    )
}

function App(){
    const [value,setValue] = React.useState("btn");
    const ChangeValue = () => setValue("NotBtn")
    
    return(
        <div>
            <Btn data={value} change={ChangeValue} />
        </div>
    )
}
```

<br>

## 3. memo
리액트는 props를 사용할때 컴포넌트를 다시 렌더를 한다. 하지만 변하지 않는 부분도 렌더를 하기때문에 성능 향상을 위해서 memo를 사용하여 변하지 않는 부분을 제외할 수 있다.

```jsx
function Btn({data,change}){
    return(
        <button onClick={change}>{data}</button>
    )
}

//memo
const MemoBtn = React.memo(Btn);

function App(){
    const [value,setValue] = React.useState("btn");
    const ChangeValue = () => setValue("NotBtn");
    
    return(
        <div>
            {/* 컴포넌트 이름 교체(메모 담은 이름) */}
            <MemoBtn data={value} change={ChangeValue} />
            <MemoBtn data="imBtn"/>
        </div>
    )
}
```

>컴포넌트를 메모의 인수값으로 받아서 담아준 변수 이름으로 교체 한다.(```React.memo(컴포넌트명)```) 이렇게 하면 변하지 않는것을 제외하고 렌더를 실행한다.