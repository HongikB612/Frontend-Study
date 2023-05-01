<h2>Section 2. JavaScript 응용</h2>

---
<details>
<summary>Truthy & Falsy</summary>
<div markdown="1">

```jsx
  let a = "";

  if(a){
  	console.log("TRUE");
  } else{
  	console.log("FALSE");
  }  // 빈 문자열을 조건문에 넣으면 거짓으로 인식
```

| TRUTHY | FALSY |
|---|---|
| “비어 있지 않은 문자열” | undefined |
| [ ]  // 빈 배열	| null / NaN |
| { }  // 객체 리터럴 | 0	|
| 숫자(Infinity 포함) | “ “  // 빈 문자열 |

```jsx
const getName = (person) =>{
	if(!person){  // undefined & null 모두 falsy라 조건문에 활용 가능
		return "객체가 아닙니다";
	}
	return person.name;
};

let person;
const name = getName(person);
console.log(name);
```

</div>
</details>

---

<details>
<summary>삼항 연산자</summary>
<div markdown="1">

```jsx
// 주어진 숫자가 양수인지 음수인지 판별하는 함수
let a = 3;

if(a>=0){
	console.log("양수");
} else{
	console.log("음수");
}  // 이 조건식을 한줄로 표현하는 게 삼항연산자

// 조건문?true:false
a>=0 ? console.log("양수") : console.log("음수");
```

```jsx
// 주어진 숫자가 양수인지 음수인지 판별하는 함수
let a = 3;

if(a>=0){
	console.log("양수");
} else{
	console.log("음수");
}  // 이 조건식을 한줄로 표현하는 게 삼항연산자

// 조건문?true:false
a>=0 ? console.log("양수") : console.log("음수");
```

```jsx
// trusy와 falsy 이용하기
// 주어진 값이 null이거나 undefined가 아닌지 판단하는 함수
let a;

const result = a ? true : false;
console.log(result);
```

```jsx
// trusy와 falsy 이용하기
// 주어진 값이 null이거나 undefined가 아닌지 판단하는 함수
let a;

const result = a ? true : false;
console.log(result);
```
</div>
</details>

---

<details>
<summary>단락회로 평가</summary>
<div markdown="1">

```jsx
// 논리연산자의 연산 순서를 이용(오른쪽 -> 왼쪽)
const getName = (person) => {
	if(!person){
		return "객체가 아닙니다";
	}
	return person.name;
};

---

const getName = (person) => {
	return person && person.name;
};  // person이 falsy이기 때문에 AND 연산자에서 뒤에 오는 값 고려할 필요 X

let person;
const name = getName(person);
console.log(name);
```

```jsx
const getName = (person) => {
	const name = person && person.name;  // 둘 다 trusy -> name 반환
	return name || "객체가 아닙니다";  // name이 trusy라 이름 반환
};

let person = {name: "조은정"};
const name = getName(person);
console.log(name);  // 조은정
```

</div>
</details>

---

<details>
<summary>조건문 Upgrade</summary>
<div markdown="1">

```jsx
// 전달받은 음식이 한식인지 확인하는 코드
function isKoreanFood(food){
	if(food==="불고기" || food==="비빔밥" || food==="떡볶이"){
		return true;
}
	return false;
}

---

function isKoreanFood(food){
	if(["불고기", "떡볶이", "비빔밥"].includes(food)){
		return true;
	}
	return false;
}

const food1 = isKoreanFood("불고기");  // true
const food2 = isKoreanFood("파스타");  // false
```

```jsx
// 전달받은 음식이 한식인지 확인하는 코드
function isKoreanFood(food){
	if(food==="불고기" || food==="비빔밥" || food==="떡볶이"){
		return true;
	}
	return false;
}

---

function isKoreanFood(food){
	if(["불고기", "떡볶이", "비빔밥"].includes(food)){
		return true;
	}
	return false;
}

const food1 = isKoreanFood("불고기");  // true
const food2 = isKoreanFood("파스타");  // false
```

</div>
</details>

---

<details>
<summary>비 구조화 할당</summary>
<div markdown="1">

```jsx
let arr = ["one", "two", "three"];

let one = arr[0];
let two = arr[1];
let three = arr[2];

console.log(one, two, three);  // one, two, three
```

```jsx
let arr = ["one", "two", "three"];

let one = arr[0];
let two = arr[1];
let three = arr[2];

console.log(one, two, three);  // one, two, three
```

```jsx
let arr = ["one", "two", "three"];

let one = arr[0];
let two = arr[1];
let three = arr[2];

console.log(one, two, three);  // one, two, three
```

```jsx
let arr = ["one", "two", "three"];

let one = arr[0];
let two = arr[1];
let three = arr[2];

console.log(one, two, three);  // one, two, three
```

</div>
</details>

---

<details>
<summary>spread 연산자</summary>
<div markdown="1">

```jsx
const cookie = {
	base: "cookie",
	madeIn: "korea"
};

const chocochipCookie = {
	base: "cookie",
	madeIn: "korea",
  toping: "chocochip"
};

const blueberryCookie = {
	base: "cookie",
	madeIn: "korea",
	toping: "blueberry"
};

const strawberryCookie = {
	base: "cookie",
	madeIn: "korea",
	toping: "strawberry"
};
```

```jsx
// 위 코드를 spread 사용해 간편하게 바꾸기
const cookie = {
	base: "cookie",
	madeIn: "korea"
};

const chocochipCookie = {
	...cookie,
  toping: "chocochip"
};

const blueberryCookie = {
	...cookie,
	toping: "blueberry"
};

const strawberryCookie = {
	...cookie,
	toping: "strawberry"
};
```

```jsx
// 위 코드를 spread 사용해 간편하게 바꾸기
const cookie = {
	base: "cookie",
	madeIn: "korea"
};

const chocochipCookie = {
	...cookie,
  toping: "chocochip"
};

const blueberryCookie = {
	...cookie,
	toping: "blueberry"
};

const strawberryCookie = {
	...cookie,
	toping: "strawberry"
};
```

</div>
</details>

---