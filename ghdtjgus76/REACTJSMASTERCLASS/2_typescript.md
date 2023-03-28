***Definitely Typed***

*@types는 아주 큰 깃헙 레포지토리인데, 모든 유명한 npm 라이브러리를 가지고 있는 저장소이다.*

*여기서 라이브러리나 패키지의 type definition을 알려준다.*

*type definition은 styled-component의 소스 코드를 보고 typescript에게 해 줄 설명을 만들어 내는 것이다.*

***Typing the Props***

```jsx
// App.tsx
import styled from 'styled-components';
import Circle from './Circle';

const App = () => {
  return (
    <div>
      <Circle bgColor='teal' />
      <Circle bgColor='tomato' />
    </div>
  )
}

export default App;
```

```jsx
// Circle.tsx
import styled from "styled-components";

interface ContainerProps {
    bgColor: string;
}

const Container = styled.div<ContainerProps>`
    width: 200px;
    height: 200px;

    background-color: ${props => props.bgColor};

    border-radius: 100px;
`;

interface CircleProps {
    bgColor: string;
}

const Circle = ({ bgColor }: CircleProps) => {
    return (
        <Container bgColor={bgColor} />
    )
}

export default Circle;
```

*Prop Types를 이용하면 알맞은 prop이 전달되지 않으면, 브라우저의 콘솔에 경고 표시를 해준다.*

*다만, 이는 코드를 실행한 후에만 확인이 가능하다.*

*우리가 typescript를 사용하는 이유는 코드가 실행되기 전에 오류를 확인하기 위해서이다.*

*따라서 우리는 Prop Types 대신 다른 방법을 사용한다.*

*이때, interface라는 개념이 도입되는데, interface는 객체의 모양을 typescript에게 설명해주는 것이다.*

*interface를 사용하면 코드가 실행되기 전에 오류가 있는지 확인해준다.*

```tsx
import styled from "styled-components";

interface CircleProps {
    bgColor: string;
}

const Container = styled.div<CircleProps>`
    width: 200px;
    height: 200px;

    background-color: ${props => props.bgColor};

    border-radius: 100px;
`;

const Circle = ({ bgColor }: CircleProps) => {
    return (
        <Container bgColor={bgColor} />
    )
}

export default Circle;
```

*위와 같이 컴포넌트에 보내주는 props가 같을 경우, interface를 하나만 선언해서 타입을 넣어주어도 된다.*

***Optional Props***

```tsx
// App.tsx
import styled from 'styled-components';
import Circle from './Circle';

const App = () => {
  return (
    <div>
      <Circle bgColor='teal' borderColor='black' />
      <Circle bgColor='tomato' />
    </div>
  )
}

export default App;
```

```jsx
// Circle.tsx
import styled from "styled-components";

interface ContainerProps {
    bgColor: string;
    borderColor: string;
}

const Container = styled.div<ContainerProps>`
    width: 200px;
    height: 200px;

    background-color: ${props => props.bgColor};

    border-radius: 100px;

    border: 1px solid ${props => props.borderColor};
`;

interface CircleProps {
    bgColor: string;
    borderColor?: string;
}

const Circle = ({ bgColor, borderColor }: CircleProps) => {
    return (
        <Container bgColor={bgColor} borderColor={borderColor ?? 'blue'} />
    )
}

export default Circle;
```

*Circle 컴포넌트의 props에서 borderColor는 optional props이다.*

*styled component인 Container에서는 borderColor가 required인 상태이기 때문에, borderColor를 props로 받지 않은 경우에는 default 값을 지정해주도록 한다.*

*이때 ?? 연산자를 사용하는데, 이는 널 병합 연산자이다.* 

*위의 경우, borderColor가 값이 undefined/null이라면 ‘blue’가 지정이 되고, 그게 아니라면 borderColor 값을 가져오도록 하는 것이다.*

```tsx
import styled from 'styled-components';
import Circle from './Circle';

const App = () => {
  return (
    <div>
      <Circle bgColor='teal' borderColor='black' />
      <Circle text='hi' bgColor='tomato' />
    </div>
  )
}

export default App;
```

```tsx
import styled from "styled-components";

interface ContainerProps {
    bgColor: string;
    borderColor: string;
}

const Container = styled.div<ContainerProps>`
    width: 200px;
    height: 200px;

    background-color: ${props => props.bgColor};

    border-radius: 100px;

    border: 1px solid ${props => props.borderColor};
`;

interface CircleProps {
    bgColor: string;
    borderColor?: string;
    text?: string;
}

const Circle = ({ bgColor, borderColor, text='hello' }: CircleProps) => {
    return (
        <Container bgColor={bgColor} borderColor={borderColor ?? 'blue'}>{text}</Container>
    )
}

export default Circle;
```

*위와 같이 props의 default 값 정해주는 방법도 있다.*

***state***

```jsx
import { useState } from "react";
import styled from "styled-components";

interface ContainerProps {
    bgColor: string;
    borderColor: string;
}

const Container = styled.div<ContainerProps>`
    width: 200px;
    height: 200px;

    background-color: ${props => props.bgColor};

    border-radius: 100px;

    border: 1px solid ${props => props.borderColor};
`;

interface CircleProps {
    bgColor: string;
    borderColor?: string;
    text?: string;
}

const Circle = ({ bgColor, borderColor, text='hello' }: CircleProps) => {
    const [counter, setCounter] = useState(1);
    
    return (
        <Container bgColor={bgColor} borderColor={borderColor ?? 'blue'}>{text}</Container>
    )
}

export default Circle;
```

*typescript는 state의 초기값을 바탕으로 타입을 추론한다.*

```jsx
import { useState } from "react";
import styled from "styled-components";

interface ContainerProps {
    bgColor: string;
    borderColor: string;
}

const Container = styled.div<ContainerProps>`
    width: 200px;
    height: 200px;

    background-color: ${props => props.bgColor};

    border-radius: 100px;

    border: 1px solid ${props => props.borderColor};
`;

interface CircleProps {
    bgColor: string;
    borderColor?: string;
    text?: string;
}

const Circle = ({ bgColor, borderColor, text='hello' }: CircleProps) => {
    const [value, setValue] = useState<number|string>(1);

    setValue('hi');
    setValue(2);

    return (
        <Container bgColor={bgColor} borderColor={borderColor ?? 'blue'}>{text}</Container>
    )
}

export default Circle;
```

*위와 같이 number 또는 string 타입으로 state의 타입을 지정해줄 수도 있다.*

***Forms***

```tsx
import styled from 'styled-components';
import { useState } from 'react';

const App = () => {
  const [username, setUsername] = useState('');

  const onChange = (event: React.FormEvent<HTMLInputElement>) => {
    const {
      currentTarget: { value }
    } = event;

    setUsername(value);  // setUsername(event.currentTarget.value);
  }

  const onSubmit = (event: React.FormEvent<HTMLFormElement>) => {
    event.preventDefault();

    console.log(`hello ${username}`);
  }

  return (
    <div>
      <form onSubmit={onSubmit}>
        <input 
          value={username} 
          type='text' 
          placeholder='username' 
          onChange={onChange}
        />
        <button type='submit'>Log in</button>
      </form>
    </div>
  )
}

export default App;
```

***Themes***

```jsx
// styled.d.ts
import 'styled-components';

declare module 'styled-components' {
  export interface DefaultTheme {
    textColor: string;
    bgColor: string;
    btnColor: string;
  }
}
```

```jsx
// theme.ts
import { DefaultTheme } from "styled-components";

export const lightTheme: DefaultTheme = {
    bgColor: 'white',
    textColor: 'black',
    btnColor: 'tomato'
}

export const darkTheme: DefaultTheme = {
    bgColor: 'black',
    textColor: 'white',
    btnColor: 'teal'
}
```

```jsx
// index.tsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import { ThemeProvider } from 'styled-components';
import App from './App';
import { darkTheme, lightTheme } from './theme';

const root = ReactDOM.createRoot(document.getElementById('root') as HTMLElement);
root.render(
  <React.StrictMode>
    <ThemeProvider theme={darkTheme}>
      <App />
    </ThemeProvider>
  </React.StrictMode>
);
```

```jsx
// App.tsx
import styled from 'styled-components';

const Container = styled.div`
  background-color: ${props => props.theme.bgColor};
`;
const H1 = styled.h1`
  color: ${props => props.theme.textColor};
`;

const App = () => {
  return (
    <div>
      <Container>
        <H1>Hello</H1>
      </Container>
    </div>
  )
}

export default App;
```