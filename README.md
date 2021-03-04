# Move it

Este projeto consiste de uma aplicação para ajudar quem fica muito tempo na sentado no PC.

A Tela inicial possui um timer, que a cada 25 minutos notifica o usuário para que ele pare um pouco e faça um exercício (desafio).

Caso ele complete o desafio, ele ganhará experiencia e irá avançar de nível, incentivando ele a fazer o exercício.

Não esqueça de ativar as notificações quando acessar o sistema.

## Tecnologias utilizadas

- NextJS
- Typescript
- Context API
- Vercel para deploy

## Link de produção

[Clique aqui para acessar o link de produção](https://moveit-beige.vercel.app)

# Context API

Contexto (context) é indicado para compartilhar dados que podem ser considerados “globais” para a árvore de componentes do React.

Por exemplo, suponha que temos dois temas na nossa aplicação:

```jsx
const themes = {
  light: {
    foreground: "#000000",
    background: "#eeeeee"
  },
  dark: {
    foreground: "#ffffff",
    background: "#222222"
  }
};
```

Para criar um contexto de temas, basta utilizarmos o `createContext`:

```jsx
const ThemeContext = React.createContext({});
```

Com isso, criamos um componente chamado `ThemeContext.Provider`. 

Para que nossa aplicação tenha acesso ao tema de maneira global, basta aninharmos esse componente na nossa aplicação com a prop `value`:

```jsx
function App() {
  return (
    <ThemeContext.Provider value={themes.dark}>
      <MinhaApp />
    </ThemeContext.Provider>
  );
}
```
E, dentro na nossa aplicação, para recuperar o valor do contexto, basta usarmos o hook `useContext`:

```jsx
function MinhaApp() {
  const theme = useContext(ThemeContext);
  return (
    <div style={{ background: theme.background, color: theme.foreground }}>
      I am styled by theme context!
    </div>
  );
}
```