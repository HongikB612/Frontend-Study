***Styled components***

```jsx
import styled from 'styled-components';

const Father = styled.div`
  display: flex;
`;

const BoxOne = styled.div`
  background-color: teal;

  width: 100px;
  height: 100px;
`;

const BoxTwo = styled.div`
  background-color: tomato;

  width: 100px;
  height: 100px;
`;

const Text = styled.h1`
  color: white;
`;

function App() {
  return (
    <Father>
      <BoxOne>
        <Text>Hello</Text>
      </BoxOne>
      <BoxTwo />
    </Father>
  );
}

export default App;
```

*백틱 사이에 들어가는 코드들은 css 코드여야 한다.*

***Adapting and Extending***

```jsx
import styled from 'styled-components';

const Father = styled.div`
  display: flex;
`;

const Box = styled.div`
  background-color: ${(props) => props.bgColor};

  width: 100px;
  height: 100px;
`;

function App() {
  return (
    <Father>
      <Box bgColor='teal' />
      <Box bgColor='tomato' />
    </Father>
  );
}

export default App;
```

*위와 같이 props로 속성을 전달해주면 동적으로 원하는 속성을 적용해줄 수 있다.*

```jsx
import styled from 'styled-components';

const Father = styled.div`
  display: flex;
`;

const Box = styled.div`
  background-color: ${(props) => props.bgColor};

  width: 100px;
  height: 100px;
`;

const Circle = styled(Box)`
  border-radius: 50px;
`;

function App() {
  return (
    <Father>
      <Box bgColor='teal' />
      <Circle bgColor='tomato' />
    </Father>
  );
}

export default App;
```

*위 코드에서 Circle 컴포넌트는 Box의 모든 속성들을 들고 온 다음 Circle에 추가적으로 적은 코드를 추가해서 컴포넌트를 만들어주는 것이다.*

*즉, 여기서 확장은 기존 컴포넌트의 모든 속성을 들고 와서 전부 복붙하고 새로운 속성까지 더해주는 것을 말한다.*

***As and Attrs***

```jsx
import styled from 'styled-components';

const Father = styled.div`
  display: flex;
`;

const Btn = styled.button`
  color: white;
  background-color: tomato;

  border: 0;
  border-radius: 15px;
`;

function App() {
  return (
    <Father>
      <Btn>Log in</Btn>
      <Btn as='a'>Log in</Btn>
    </Father>
  );
}

export default App;
```

*위와 같이 html 태그를 변경하고 싶은 경우에는 as 키워드를 사용해주면 된다.*

```jsx
import styled from 'styled-components';

const Father = styled.div`
  display: flex;
`;

const Input = styled.input.attrs({ required: true, minLength: 10 })`
  background-color: tomato;
`;

function App() {
  return (
    <Father>
      <Input />
    </Father>
  );
}

export default App;
```

*위와 같이 html 태그 속성을 styled component를 사용해서 지정해줄 수도 있다.*

***Animations and Pseudo Selectors***

```jsx
import styled, { keyframes } from "styled-components";

const Wrapper = styled.div`
  display: flex;
`;

const rotation = keyframes`
  0% {
    transform: rotate(0deg);
    
    border-radius: 0px;
  }
  50% {
    border-radius: 100px;
  }
  100% {
    transform: rotate(360deg);

    border-radius: 0px;
  }
`;

const Box = styled.div`
  width: 200px;
  height: 200px;
  
  background-color: tomato;

  animation: ${rotation} 5s linear infinite;
`;

const App = () => {
  return (
    <Wrapper>
      <Box />
    </Wrapper>
  )
}

export default App;
```

*위와 같이 keyframes를 사용해주면 애니메이션을 넣을 수 있다.*

```jsx
import styled, { keyframes } from "styled-components";

const Wrapper = styled.div`
  display: flex;
`;

const rotation = keyframes`
  0% {
    transform: rotate(0deg);
    
    border-radius: 0px;
  }
  50% {
    border-radius: 100px;
  }
  100% {
    transform: rotate(360deg);

    border-radius: 0px;
  }
`;

const Box = styled.div`
  width: 200px;
  height: 200px;
  
  background-color: tomato;

  animation: ${rotation} 3s linear infinite;

  display: flex;
  justify-content: center;
  align-items: center;

  span {
    font-size: 36px;

    &:hover {
      font-size: 50px;
    }

    &:active {
      opacity: 0;
    }
  }
`;

const App = () => {
  return (
    <Wrapper>
      <Box>
        <span>@</span>
      </Box>
    </Wrapper>
  )
}

export default App;
```

*위와 같이 컴포넌트 내부 html 태그에 접근할 수도 있고, & 선택자(pseudo selector)를 활용해서 hover와 같은 기능들에 대한 속성을 지정해줄 수도 있다.*

```jsx
import styled, { keyframes } from "styled-components";

const Wrapper = styled.div`
  display: flex;
`;

const rotation = keyframes`
  0% {
    transform: rotate(0deg);
    
    border-radius: 0px;
  }
  50% {
    border-radius: 100px;
  }
  100% {
    transform: rotate(360deg);

    border-radius: 0px;
  }
`;

const Box = styled.div`
  width: 200px;
  height: 200px;
  
  background-color: tomato;

  animation: ${rotation} 3s linear infinite;

  display: flex;
  justify-content: center;
  align-items: center;

  ${Emoji} {
    &:hover {
      font-size: 50px;
    }

    &:active {
      opacity: 0;
    }
  }
`;

const Emoji = styled.span`
  font-size: 36px;
`;

const App = () => {
  return (
    <Wrapper>
      <Box>
        <Emoji>@</Emoji>
      </Box>
    </Wrapper>
  )
}

export default App;
```

*Emoji 컴포넌트의 html 태그가 무엇이든 간에 해당 코드는 잘 작동하는 것을 볼 수 있다.*

***Themes***

```jsx
// index.js
import React from 'react';
import ReactDOM from 'react-dom/client';
import { ThemeProvider } from 'styled-components';
import App from './App';

const darkTheme = {
  textColor: 'whitesmoke',
  backgroundColor: '#111'
}

const lightTheme = {
  textColor: '#111',
  backgroundColor: 'whitesmoke'
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <ThemeProvider theme={lightTheme}>
      <App />
    </ThemeProvider>
  </React.StrictMode>
);
```

```jsx
// App.js
import styled from "styled-components";

const Wrapper = styled.div`
  display: flex;
  justify-content: center;
  align-items: center;

  width: 100vw;
  height: 100vh;

  background-color: ${props => props.theme.backgroundColor};
`;

const Title = styled.h1`
  color: ${props => props.theme.textColor};
`;

const App = () => {
  return (
    <Wrapper>
      <Title>Hello</Title>
    </Wrapper>
  )
}

export default App;
```

*theme은 기본적으로 모든 색상들을 가지고 있는 object이다.*

*App 컴포넌트의 경우, ThemeProvider의 내부에 있기 때문에 props를 이용해서 theme에 적어놓은 속성들에 접근할 수 있다.*