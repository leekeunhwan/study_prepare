# 2018-10-23 Study Prepare

## OOP && FP

---

## OOP - Object Oriented Programming

객체지향 프로그래밍, 자바 혹은 자바스크립트를 접한 사람이라면<br>
누구나 한번 쯤은 들어봤을 법한 단어입니다.<br>

다음은 생활코딩에서 객체지향 프로그래밍에 대해 설명하는 텍스트중 일부입니다.<br>
`객체지향 프로그래밍은 좀 더 나은 프로그래밍을 만들기 위한 패러다임으로`<br>
`로직은 하나의 상태(state)와 행위(behave)로 이루어진 객체로 만드는 것이다.`<br>

로직은 하나의 상태와 행위를 갖는다는 핵심적인 단어가 잘 설명해주고 있습니다.<br>
사실 객체지향은 자바스크립트 보다 자바에서 그 의미가 큽니다.<br>

자바에서는 객체의 동작을 메소드라고 하며,<br>
여러개의 객체가 한 곳에서 유기적으로 맞물릴 수 있도록 하는 틀을 클래스라고 하고,<br>
그리고 그 클래스들을 서로 관련이 있는 것들끼리 묶어놓은 것을 패키지라고 합니다.<br>

개인적으로도 처음 자바를 배웠을 때, 자바스크립트를 배운다음 자바를 배웠기에<br>
이런 방식으로도 프로그래밍을 할 수 있구나..!<br>
자바스크립트보다 객체지향에 최적화 되어있구나라는 생각을 했었습니다.<br>

문득 `그럼 객체지향 프로그래밍을 하면 뭐가 좋지? 더 나은 프로그래밍을 만들기 위함이라는데 왜지?`<br>
와 같은 이런 생각이 들으실수도 있습니다.<br>
객체지향 프로그래밍과 관련된 책만해도 서점에 빽빽할 정도로 많고<br>
또한 사람들이 열광하고 찾는 이유를 이제 알아보겠습니다.<br>

흔히 객체지향이라고 하면 기계조립이라고 많이들 합니다.<br>
각자의 기계부품들을 조립하여 하나의 제품을 만든다는 철학을 객체 지향 프로그래밍이 갖고 있기 때문입니다.<br>
말로만 하면 잘 안와닿으실 것 같아서 예제로 코드를 보여드리겠습니다.<br>

```js
function SalaryCal(firstSalary, career, major, year) {
  this.firstSalary = firstSalary;
  this.career = career;
  this.major = major;
  this.year = year;
  this.calculator = function() {
    let hopeSalary;
    if ((career = true)) {
      hopeSalary = firstSalary + 700;
    }
    if (major == true) {
      hopeSalary = firstSalary + (firstSalary / 10) * 2 * year;
    } else {
      hopeSalary = firstSalary + (firstSalary / 10) * 1.5 * year;
    }
    alert(`당신의 ${year}차 연봉은 ${hopeSalary}만원 입니다.`);
  };
}

const juniorDevleoperAverage = new SalaryCal(2700, false, false, 10);
juniorDevleoperAverage.calculator();
```

간략하게 만든 연봉계산기입니다.<br>
눈치 빠른 분들은 눈치채셨을 수도 있는데 맞습니다!<br>
우리가 패스트캠퍼스에서 자바스크립트를 배울 때 공부했던 생성자입니다.<br>

자바스크립트 ES2015(ES6) 이전에는 Class 문법이 없었기에<br>
생성자 함수가 그 역할을 대신하곤 했었죠!<br>
new 라는 키워드를 사용하여 함수에 맞는 파라미터를 넣어주면 동작을 합니다.<br>

이게 왜 도대체 객체지향인지 모르시겠다는 분들을 위해 설명드리자면,<br>
위에서 객체지향에 대한 설명을 할 때<br>
`로직은 하나의 상태(state)와 행위(behave)로 이루어진 객체로 만드는 것`이라는 설명을 드렸습니다.<br>

재미를 위해 파라미터를 여러개를 넣어서 만들었지만<br>
주로 만드는 함수 생성자를 보여드리면 아래와 같습니다.<br>

```js
function count() {
  // 하나의 상태
  var count = 1;

  return function() {
    // 하나의 행위
    console.log(count++);
  };
}

var count = count();
count(); //outputs 1
count(); // 2
count(); // 3
```

하나의 상태와 하나의 행위로 이루어진 함수죠..!<br>

<b>[잠깐!]</b><br>

혹시 함수니까 객체가 아니지 않냐고 생각하셨다면<br>
잊지 마시라고 함정문구로 글을 써봤는데요!<br>
함수도 자바스크립트에서는 객체입니다.<br>
그 것도 일급객체죠!!<br>
(모르시겠는 분은 지금 당장 => https://helloworldjavascript.net/pages/180-object.html)<br>

그렇기에 생성자 함수를 이용해서 부품들을 만들고,<br>
부품들을 잘 조립해서 제품을 만드는 것을 자바스크립트에서의<br>
객체지향 프로그래밍이라고 할 수 있습니다.<br>

지금은 자잘한 연봉계산기지만,<br>
저기에 조금 더 추가적으로 기능을 만들고,<br>
많은 생성자들을 만들어 DB 에 저장하고,<br>
HTML 과 CSS 를 이용하여 UI 를 만든다면<br>
회사에서 연봉관련해서 사용할 수 있는 CMS 가 되는 것이죠!<br>

정말 간단한 것들이 모여서 제품이 되는 것..!<br>
그 것이 바로 객체지향 프로그래밍의 핵심입니다.<br>

객쳬지향 프로그래밍을 한다면, 개발환경과 개발을 해온 습관이 다르더라도,<br>
하나의 로직에 하나의 상태와 하나의 행동이라는 규칙대로 프로그래밍을 하게되어<br>
개발의 생산력이라던가 불필요한 충돌을 없앨 수 있어 다양한 이점을 취할 수 있습니다.<br>

객체지향 프로그래밍이 좋다구요?<br>
근데 요즘에는 객체지향 프로그래밍보다<br>
많은 사람들이 함수지향 프로그래밍 혹은 컴포넌트지향 프로그래밍을 공부하고자 합니다.<br>
그 것들은 무엇일까요?<br>
무엇이기에 열광하는지 간단한 실습을 하고 알아보겠습니다.<br>
질문은 틈틈히 중간중간 혹은 슬랙, 정말 민망하면 개인톡으로 해주세요!<br>

// 쉬기 전에 할일이 있죠!<br>
// 2 인 1 조로 자바스크립트를 이용하여<br>
// 객체 지향 코드 만들기<br>
// ex) 간단해도 좋고 복잡해도 좋습니다.<br>
// 실습시간 15 분<br>
// repl => https://repl.it/@leekeunhwan/Lets-Make-OOP-Code<br>

<br>
<br>

## FP - Functional Programming

뜨거운 감자죠..!!<br>
유인동이라는 분이 우리나라에서 유명해진 것도 FP 덕분이라고 해도 과언이 아닌데요!<br>
한 번 알아보겠습니다.<br>

함수형 프로그래밍에 대해서 알기 위해서는 순수/비순수 함수를 확실히 알고 계셔야 합니다.<br>
쉽게 전달해드리고자 최대한 의미전달만 해보자면,<br>
함수의 호출결과가 100 번이고 1000 번이고 의도하고 예상한대로 결과가 변함없이 나오면 순수 함수이고,<br>
함수의 호출결과가 매번 자신의 예상과 다르고 값이 계속 바뀐다면 비순수 함수입니다.<br>
말로는 감이 안오시죠?<br>
그렇다면 당신은 개발자입니다. (제발.. 뻘소리.. 그만..)<br>

```js
// 순수 함수

function plus(x, y) {
  return x + y;
}

function minus(x, y) {
  return x - y;
}

function multiply(x, y) {
  return x * y;
}

function divide(x, y) {
  return x / y;
}

plus(3, 6); // 9
minus(7, 3); // 4
multiply(9, 9); // 81
divide(9, 3); // 3
```

사칙연산을 함수로 나타낸 것인데요!<br>
x,y 에 어떤 값을 넣어도 계산대로 변함없이 결과가 나옵니다.<br>
그렇기에 순수함수입니다!<br>
반대로 비순수함수는 다음과 같습니다.<br>

```js
// 비순수 함수

function notPure() {
  return Math.random();
}

notPure(); // 0.5692133417515535
notPure(); // 0.9116145140200496
notPure(); // 0.13970568165883535
```

예측을 할 수 없고 여러번 수행해도 결과가 매번 달라지죠..!<br>
(예상해서 맞추셨다거나 결과가 같게 나왔다면.. 로또사거나 병원가보시는 것을 추천드립니다.)<br>
위와 같은 함수를 비순수함수라고 합니다.<br>

함수형 프로그래밍에 이게 뭐가 중요하냐구요!<br>
함수형 프로그래밍은 순수 함수를 작성하는 것입니다.<br>
숨겨진 입력이나 출력을 최대한 제거하여 가능한 한 우리 코드의 대부분이<br>
단지 입력과 출력의 관계를 기술하게끔 하는 것을 의미합니다.<br>
어떤 동작을 실행하게 하기 위해 엄격하게 통제를 하겠다는 것이 포인트입니다.<br>

다시한번 정리해서 말씀드리자면<br>
입력과 출력만을 담당하게 하여 엄격하게 통제함으로,<br>
우리는 가능한 모든 곳에서 부작용(에러)를 제거하고,<br>
제거할 수 없는 경우는 철저하게 대응할 수 있는 프로그래밍을 하겠다는 것이<br>
함수형 프로그래밍의 핵심 철학입니다.<br>

함수형 프로그래밍이나 객체지향 프로그래밍이나 궁극적인 목표는 같다는 것을 볼 수 있습니다.<br>
다만 방법이 다를 뿐이지, 더 나은 프로그램을 만들기 위함은 같습니다.<br>

객체지향 프로그래밍은 객체에 의존도를 두는 대신<br>
함수형 프로그래밍은 객체끼리의 의존도를 없애고 가능하면 객체 안의 함수도 순수하게 실행한 명령만 하게끔<br>
프로그래밍을 하는 것입니다.<br>
(무상태 (no state) 프로그래밍이라고 볼 수 있습니다. - 상태(state)는 의도치 않게 동작을 하게끔 유발하는 원인이 될 수 있기 때문입니다.)<br>

자 이제 개념에 대해서는 충분히 설명드렸으니 코드를 봐볼까요?<br>

```js
// 예시 1

function doubleNumbers(numbers) {
  const doubled = [];
  const l = numbers.lenth;
  for (let i = 0; i < l; i++) {
    doubled.push(numbers[i] * 2);
  }
  return doubled;
}
doubleNumbers([1, 2, 3]); // [2, 4, 6]
```

```js
// 예시 2

function doubleNumbersMap(numbers) {
  return numbers.map(n => n * 2);
}
doubleNumbersMap([1, 2, 3]); // [2, 4, 6]
```

어디선가 많이 봤죠..!<br>
이 것도 또한 패스트캠퍼스 스쿨 과정에서 배운<br>
자바스크립트 map 문법입니다.<br>
예시 1 의 코드를 예시 2 에서 map 을 사용하여<br>
코드를 확 줄였죠!<br>
물론 1 번도 함수형 프로그래밍이라고 말할 수 있습니다.<br>
(효율적이지는 않지만..)<br>

기존의 값이 불변이면사, 입력값에 따라 의도하는 대로 결과가<br>
여러번을 수행해도 같게 나오게끔 하는 것이 포인트입니다.<br>

```js
function SalaryCal(firstSalary, career, major, year) {
  this.firstSalary = firstSalary;
  this.career = career;
  this.major = major;
  this.year = year;
  this.calculator = function() {
    let hopeSalary;
    if ((career = true)) {
      hopeSalary = firstSalary + 700;
    }
    if (major == true) {
      hopeSalary = firstSalary + (firstSalary / 10) * 2 * year;
    } else {
      hopeSalary = firstSalary + (firstSalary / 10) * 1.5 * year;
    }
    alert(`당신의 ${year}차 연봉은 ${hopeSalary}만원 입니다.`);
  };
}

const juniorDevleoperAverage = new SalaryCal(2700, false, false, 10);
juniorDevleoperAverage.calculator();
```

여기서 한번 다시 등장하는 제가 짠 객체지향 프로그래밍 예시 코드인데요!<br>
다시보니 함수형 프로그래밍이라고 해도 어긋나는 것은 없네요!<br>
입력값에 따라서 출력되는 결과가 예상대로 같게 나오니까요!<br>

우리가 앞으로 함수형 프로그래밍을 공부하게 되는 것들은 물론 이런 예제 코드와는 많이 다릅니다.<br>
오히려 이런 코드가 많이 나오겠죠..! (underscore 지옥..)<br>

```js
var users = [
  { id: 1, name: "ID", age: 32 },
  { id: 2, name: "HA", age: 25 },
  { id: 3, name: "BJ", age: 32 },
  { id: 4, name: "PJ", age: 28 },
  { id: 5, name: "JE", age: 27 },
  { id: 6, name: "JM", age: 32 },
  { id: 7, name: "HI", age: 24 }
];

/* 일반적 사용 */
_.go(
  users,
  function(users) {
    return _.filter(users, function(u) {
      return u.age < 30;
    });
  },
  function(users) {
    return _.pluck(users, "name");
  },
  console.log
);
// ["HA", "PJ", "JE", "HI"]

/* 부분 적용 */
_.go(
  users,
  _.partial(_.filter, _, function(u) {
    return u.age < 30;
  }),
  _.partial(_.pluck, _, "name"),
  console.log
);
// ["HA", "PJ", "JE", "HI"]

/* 부분 커링이 된다면 */
_.go(
  users,
  _.filter(function(u) {
    return u.age < 30;
  }),
  _.pluck("name"),
  console.log
);
// ["HA", "PJ", "JE", "HI"]

/* Underscore.js 체인 */
und
  .chain(users)
  .filter(function(u) {
    return u.age < 30;
  })
  .pluck("name")
  .tap(console.log);
// ["HA", "PJ", "JE", "HI"]
```

이 코드를 보여드리는 이유는 절대 겁먹지 마시라고 보여드리는 겁니다..!<br>
백엔드 코드가 이렇게 많이 생기기도 했고,<br>
이 기회에 낯선 코드도 보면서 빠르게 친숙해지는 능력도 기르시기바라면서<br>
이제 백문이 불여일견!<br>
함수형 프로그래밍이 될지 단순 함수를 정의하는 것일지 모르겠지만<br>
한 번 만들어보죠!<br>
스타트!!<br>

// 2 인 1 조로 자바스크립트를 이용하여<br>
// 함수형 코드 만들기<br>
// ex) 간단해도 좋고 복잡해도 좋습니다.<br>
// 실습시간 15 분<br>
// repl => https://repl.it/@leekeunhwan/Lets-Make-FOP-Code<br>

이상입니다!

<br>
<br>

# 참고 자료

> https://medium.com/@jooyunghan/%ED%95%A8%EC%88%98%ED%98%95-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-fab4e960d263

> https://opentutorials.org/course/743/6553

> https://www.zerocho.com/category/JavaScript/post/573c2acf91575c17008ad2fc
