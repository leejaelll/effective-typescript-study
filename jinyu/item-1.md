# 아이템 1 - 타입스크립트와 자바스크립트의 관계 이해하기

타입스크립트는 자바스크립트의 상위 집합(superset)입니다. 타입스크립트는 자바스크립트와 굉장히 밀접한 관계에 있기 때문에, 서로 어떻게 연관되어 있는지 제대로 이해하는 것이 중요합니다.

타입스크립트는 자바스크립트의 상위 집합이라는 것이 어떤 의미일까요? 모든 자바스크립트 프로그램이 타입스크립트라는 명제는 참이지만, 그 반대는 성립하지 않습니다.

이는 타입스크립트가 타입을 명시하는 추가적인 문법을 가지기 때문입니다.

### 타입스크립트 타입 시스템은 자바스크립트의 런타임 동작을 '모델링'합니다.

처음에 책을 읽고 자바스크립트의 런타임 동작을 '모델링' 한다는 것이 어떤 의미인지 감이 안왔어요.

책에서는제시한 예제와 함께 설명해요.

```ts
const x = 2 + '3'; // 정상, string 타입입니다.
const y = '2' + 3; // 정상, string 타입입니다.
```

위의 코드는 자바, C와 같은 다른 언어였다면 런타임 오류가 될 만한 코드입니다. 하지만 타입스크립트의 타입 체커는 정상으로 인식하며 두 줄 모두 문자열 "23"이 되는 자바스크립트 런타임 동작으로 모델링됩니다.

저는 모델링한다는 것은 "타입스크립트가 자바스크립트의 동작을 모방한다." 이해했어요.

결국 타입스크립트는 타입을 체크하는 컴파일 과정을 거친 후 자바스크립트로 런타임 될테니까요.

하지만 타입스크립트를 사용하면 자바스크립트 런타임 오류가 발생하지 않는 코드인데도, 아래의 예제와 같이 타입 체커를 해줘요.

```ts
const a = null + 7; // 자바스크립트에서는 a값이 7이 됩니다.
// TypeScript Error: '+' 연산자를 ... 형식에 적용할 수 없습니다.

const b = [] + 12; // 자바스크립트에서는 b값이 '12'가 됩니다.
// TypeScript Error: '+' 연산자를 ... 형식에 적용할 수 없습니다.

alert('Hello', 'TypeScript'); // "Hello" 경고를 표시합니다.
// TypeScript Error: 0-1개의 인수가 필요한데 2개를 가져왔습니다.
```

### 타입스크립트를 쓰는 이유

- 자바스크립트 코드를 타입스크립트로 마이그레이션하기 쉽다.
- 런타임에 오류를 발생시킬 코드를 미리 찾아낸다.
- 개발자의 생산성 향상