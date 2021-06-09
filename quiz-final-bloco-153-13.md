# Questão 01

---

## Habilidade cobrada na questão:

- Enumerar as quatro fases do ciclo de vida de um componente React - inicialização, montagem, atualização, desmontagem

---

## Enunciado

Em que ordem ocorrem os ciclos de vida de um componente React?

---

## Alternativas
### Alternativa A

Inicialização, atualização, desmontagem e montagem.

### Alternativa B

Inicialização, atualização, montagem e desmontagem.

### Alternativa C

Inicialização, montagem, atualização e desmontagem.

### Alternativa D

Montagem, atualização, inicialização e desmontagem.

### Alternativa E

Montagem, inicialização, atualização e desmontagem.

### Alternativa correta 
#### Alternativa C

---

## Resoluções
### Alternativa A

Essa alternativa está incorreta. A ordem correta é inicialização, montagem, atualização e desmontagem.

### Alternativa B

Essa alternativa está incorreta. A ordem correta é inicialização, montagem, atualização e desmontagem.

### Alternativa C

Essa alternativa está correta. A ordem correta é inicialização, montagem, atualização e desmontagem. Veja com detalhes o <a href="https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/">ciclo de vida de um componente React</a>.

### Alternativa D

Essa alternativa está incorreta. A ordem correta é inicialização, montagem, atualização e desmontagem.

### Alternativa E

Essa alternativa está incorreta. A ordem correta é inicialização, montagem, atualização e desmontagem.

---

# Questão 02

---

## Habilidade cobrada na questão:

- Enumerar as formas de disparar a atualização de um componente React - via atualização de props, estado ou com a função forceUpdate

---

## Enunciado

Quais são as formas de disparar a atualização de componente React?

---

## Alternativas
### Alternativa A

Via atualização de props, estado ou com a função forceUpdate().

### Alternativa B

Via componentDidMount()

### Alternativa C

Via componentDidUpdate()

### Alternativa D

Via component­Will­Unmount()

### Alternativa E

Via constructor(), render() e componentDidMount()

### Alternativa correta 
#### Alternativa A

---

## Resoluções
### Alternativa A

Essa alternativa está correta. Veja os 3 primeiros itens do ciclo de atualização do ciclo de via de um componente React <a href="https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/">aqui</a>.

### Alternativa B

Essa alternativa está incorreta porque componentDidMount() é a invocação logo após a primeira renderização de um componente React.

### Alternativa C

Essa alternativa está incorreta porque componentDidUpdate() é a invocação logo após qualquer atualização do compomente.

### Alternativa D

Essa alternativa está incorreta porque component­Will­Unmount() é a invocação realizada antes de um componente ser retirado do DOM.

### Alternativa E

Essa alternativa está incorreta porque constructor(), render() e componentDidMount() são as etapas de montagem de um componente.

---

# Questão 03

---

## Habilidade cobrada na questão:

- Utilizar a função `setState` de forma a garantir que um determinado código só é executado após o estado ser atualizado

---

## Enunciado

Neste exercício, é esperado que:
- apareça uma mensagem para o usuário abrir o console do navegador
- após o primeiro clique, uma nova mensagem aparece em consequência da atualização de estado
- do segundo clique em diante, um contador mostre a quantidade de cliques a cada atualização de estado
  
Qual alternativa modifica o código no local indicado, para que os passos acima funcionem corretamente?

```javascript
// App.js
import React from "react";

class ReactClass extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isUpdate: false,
      counter: 0,
    };
    this.handleClick = this.handleClick.bind(this);
    this.counterMessage = this.counterMessage.bind(this);
  }
  handleClick() {
    this.setState({
      isUpdate: true,
      counter: this.state.counter + 1,
    });
  }
  counterMessage(counter) {
    return (
      <div>
        <div>
          Esta mensagem somente deve aparecer quando o estado é atualizado.
          Se esta mensagem apareceu antes do click, algo esta errado no
          seu código.
        </div>
        <div>
          {`Quantidade de atualizações do estado: ${counter}`}
        </div>
      </div>
    )
  };
  render() {
    
    console.log(this.state);

    return (
      <div>
        <div>Abra o console do seu navegador</div>
        <div>
        { /* Altere seu código nesta linha para que ele funcione corretamente */}
        </div>
        <button onClick={ this.handleClick }>
          Clique aqui para atualizar o estado do componente
        </button>
      </div>
    );
  }
}

export default ReactClass;
```

---

## Alternativas
### Alternativa A

```javascript
{ counterMessage(state.counter) }
```

### Alternativa B

```javascript
{ counterMessage(this.state.counter) }
```

### Alternativa C

```javascript
{ this.counterMessage(this.state.counter) }
```

### Alternativa D

```javascript
{ this.state.isUpdate && counterMessage(this.state.counter) }
```

### Alternativa E

```javascript
{ this.state.isUpdate && this.counterMessage(this.state.counter) }
```

### Alternativa correta 
#### Alternativa E

---

## Resoluções
### Alternativa A

Essa alternativa está incorreta porque a função e o estado não foram chamados corretamente. É preciso o termo `this.`. Sem o `this.`, vai apresentar o seguinte erro na tela:
Failed to compile
src/App.js
  Line 41:11:  'counterMessage' is not defined  no-undef
  Line 41:26:  'state' is not defined           no-undef

### Alternativa B

Essa alternativa está incorreta porque a função e o estado não foram chamados corretamente. É preciso o termo `this.`. Sem o `this.`, vai apresentar o seguinte erro na tela:
Failed to compile
src/App.js
  Line 41:11:  'counterMessage' is not defined  no-undef
  Line 41:26:  'state' is not defined           no-undef

### Alternativa C

Essa alternativa está incorreta. O contador irá funcionar corretamente, mas o esperado aqui é que o contador apareça somente após o primeiro clique.

### Alternativa D

Essa alternativa está incorreta porque o `counterMessage(this.state.counter)` foi chamado de forma errada, gerando o seguinte erro:
Failed to compile
src/App.js
  Line 44:34:  'counterMessage' is not defined  no-undef

Search for the keywords to learn more about each error.

 O correto seria `this.counterMessage(this.state.counter)`.

### Alternativa E

Essa alternativa está correta. O `this.state.isUpdate` tem seu estado inicial como `false`. Isto oculta o componente `this.counterMessage(this.state.counter)`. O clique no botão atualiza o estado do `this.state.isUpdate` de `false` para `true`. Esta atualização no estado passa a mostrar o `this.counterMessage(this.state.counter)` na tela. E deste ponto em diante, a cada clique no botão, a função `handleClick` é chamada. Esta chamada faz uma atualização no estado do `this.state.counter`, fazendo o incremento. Esta atualização gera uma nova renderização, gerando o efeito do contador.

---

# Questão 04

---

## Habilidade cobrada na questão:

- Utilizar o `spread operator` para passar um array de props para um componente

---

## Enunciado

Preencha corretamente a lacuna do código a seguir para que o código aceite a passagem de 1 ou mais argumentos de `detailAllPerson`.
``` javascript

class ReactClass extends React.Component {
  render() {
    const person1 = {
      firstName: "João",
      lastName: "da Silva",
      age: 18,
      car: "Fusca",
    };

    const person2 = {
      primeiroNome: "Maria",
      ultimoNome: "Almeira",
      idade: 21,
      hobby: "Bike",
    };

    const detailPerson = (person) => {
      const details = Object.entries(person);
      return details.map((properties) => <li>{properties[0]}: {properties[1]}</li>);
    };

    const detailAllPerson = (_________________________) => {
      let all = [_________________________];
      let all2 = [];
      all.map((person) => {
        all2.push(detailPerson(person));
      });
      return all2;
    };

    console.log(detailAllPerson(person1, person2));

    console.log(person1, person2);

    return (
      <div>
        <ul>
          { detailAllPerson(person1, person2) }
        </ul>
      </div>
    );
  }
}

export default ReactClass;
```

---

## Alternativas
### Alternativa A

...allPerson / ...allPerson

### Alternativa B

allPerson / allPerson

### Alternativa C

[allPerson] / [allPerson]

### Alternativa D

{allPerson} / {allPerson}

### Alternativa E

[...allPerson] / [...allPerson]

### Alternativa correta 
#### Alternativa A

---

## Resoluções
### Alternativa A

Essa alternativa está correta porque esta forma é a correta para passar uma quantidade flexível de argumento nesta callback.

### Alternativa B

Essa alternativa está incorreta porque desta forma `detailAllPerson` irá aceitar apenas o primeiro argumento e vai desprezar os demais, pelo uso incorreto do `spread operator`.

### Alternativa C

Essa alternativa está incorreta porque para que `detailAllPerson` seja flexível para a quantidade de argumentos que serão passados, é necessário passar os argumentos da callback via `spread operator`. Neste caso, o react ira consolar o erro: `TypeError: undefined is not a function`.

### Alternativa D

Essa alternativa está incorreta porque desta forma `detailAllPerson` nenhum argumento será passado, pelo uso incorreto do  `spread operator`.

### Alternativa E

Essa alternativa está incorreta porque para que `detailAllPerson` seja flexível para a quantidade de argumentos que serão passados, é necessário passar os argumentos da callback via `spread operator`. Neste caso, o react ira consolar o erro: `TypeError: undefined is not a function`.

---

# Questão 05

---

## Habilidade cobrada na questão:

- Enumerar as propriedades que o `Route` pode transmitir para os componentes que renderiza - `history`, que contém o histórico de navegação, `match`, para receber parâmetros por URL e location

---

## Enunciado

Defina as propriedades do `Route` e suas respectivas funções:

---

## Alternativas
### Alternativa A

A propriedade `history` passa o histórico de alterações da props do componente.

### Alternativa B

A passagem de parâmetro para componente através da pros é feita com a propriedade `match`.

### Alternativa C

O `this.props.match.url` é quem recebe parâmetros para o componente filho enviados através da URL.

### Alternativa D

O componente `route` é responsável por passar as propriedades `history`, `match` e `location`.

### Alternativa E

A props é passada para o componente filho através do `component`, por uma callback que recebe a props como parâmetro.

### Alternativa correta 
#### Alternativa D

---

## Resoluções
### Alternativa A

Essa alternativa está incorreta porque a propriedade `history` passa o histórico de navegação para o componente.

### Alternativa B

Essa alternativa está incorreta porque o `match` faz passagem de parâmetro para componente através da URL.

### Alternativa C

Essa alternativa está incorreta porque o `this.props.match.url` não é a propriedade correta. A propriedade correta é `this.props.match.params`.

### Alternativa D

Essa alternativa está correta porque o componente `route` passa as propriedades `history`, `match` e `location` para o componente filho.

### Alternativa E

Essa alternativa está incorreta porque a props é passada para o componente filho através do `render`, por uma callback que recebe a props como parâmetro.

---

# Questão 06

---

## Habilidade cobrada na questão:

- Passar, via URL de um componente associado a uma rota com `Route`, parâmetros para ele, através da sintaxe `this.props.match.params.chave`

---

## Enunciado

Dentro do componente `Route` do `App.js`, como deve ser construído o `render`, para que o componente Children.js renderize: `Nome: João - Id 123`

``` javascript
// App.js
import React, { Component } from 'react';
import { BrowserRouter, Route, Switch } from 'react-router-dom';
import Children from './Children';

  class App extends Component {
    render() {
      return (
        <BrowserRouter>
          <Switch>
            <Route 
              exact
              path="/name/:id"
              // ESCREVA SEU CÓDIGO AQUI
            />
            <div>passar parâmetro na URL /name/123</div>
          </Switch>
        </BrowserRouter>
      );
    }
  }

  export default App;
  ```
``` javascript
// Children.js
import React, { Component } from "react";

class Children extends Component {
  render() {
    const { id } = this.props.match.params;
    const { name } = this.props;
    return (
      <div>
        {`Nome: ${name} - Id ${id}`}
      </div>
    );
  }
}

export default Children;
```

---

## Alternativas
### Alternativa A

render={ () => <Children {props} name="João" /> }

### Alternativa B

render={ (props) => <Children {props} name="João" /> }

### Alternativa C

render={ (props) => <Children name="João" /> }

### Alternativa D

render={ () => <Children {...props} name="João" /> }

### Alternativa E

render={ (props) => <Children {...props} name="João" /> }

### Alternativa correta 
#### Alternativa E

---

## Resoluções
### Alternativa A

Essa alternativa está incorreta porque faltou a passagem da props como argumento da callback e dentro do componente `<Children />`  faltou o `spread` da props dentro do objeto. 

### Alternativa B

Essa alternativa está incorreta porque dentro do componente `<Children />` faltou o `spread` da props dentro do objeto. 

### Alternativa C

Essa alternativa está incorreta porque dentro do componente `<Children />` faltou o {...props}.

### Alternativa D

Essa alternativa está incorreta porque faltou a passagem da props como argumento da callback.

### Alternativa E

Essa alternativa está correta. Perceba que, no código:
```javascript
render={ (props) => <Children {...props} name="João" /> }
```
A propriedade render recebe uma callback que, por sua vez, repassa as props recebidas por parâmetro para o componente Children.

---

# Questão 07

---

## Habilidade cobrada na questão:

- Utilizar o `Browser Router` e o `Route`, do `React Router`

---

## Enunciado

Sobre a biblioteca `react-router-dom` e seus componentes, podemos afirmar

---

## Alternativas
### Alternativa A

O `BrowserRouter` é o componente que encapsula a sua aplicação, de forma que isso evita a passagem de informações indesejadas ao componente.

### Alternativa B

O `Route` importa o componente a ser roteado para dentro do componente `Switch`.

### Alternativa C

A sintaxe `<BrowserRouter path="/about" component={About} />` define que a URL "/about" vai renderizar o componente `About`.

### Alternativa D

O `<BrowserRouter path="/about" component={About} />` define uma correspondência entre caminhos da URL. O componente `About` será renderizado se a URL for `/about` ou `/about/me`.

### Alternativa E

Há um meio de definir a correspondência exata no Route: `<Route exact path="/about" component={About} />`.

### Alternativa correta 
#### Alternativa E

---

## Resoluções
### Alternativa A

Essa alternativa está incorreta porque o `BrowserRouter` é o componente que encapsula a sua aplicação, de forma a te possibilitar fazer uso de navegação.

### Alternativa B

Essa alternativa está incorreta porque o `Route` estabelece o mapeamento entre o caminho de URL declarado com o componente.

### Alternativa C

Essa alternativa está incorreta porque O `BrowserRouter` é o componente que encapsula a sua aplicação, de forma que isso evita a passagem de informações indesejadas ao componente. O `Route` define uma correspondência entre caminhos da URL. A sintaxe `<Route path="/about" component={About} />` define que a URL "/about" vai renderizar o componente `About`. A correção da alternativa é trocar o `BrowserRouter` pelo `Route`

### Alternativa D

Essa alternativa está incorreta. Trocando o `BrowserRouter` por `Route` torna a alternativa verdadeira

### Alternativa E

Essa alternativa está correta porque esta sintaxe define uma rota exata para renderizar o componente. No exemplo `<Route exact path="/about" component={About} />`, o componente `About` vai ser renderizado para a URL "/about", mas não para a URL "/about/me" 

---

# Questão 08

---

## Habilidade cobrada na questão:

- Utilizar o `Link` do `React Router`

---

## Enunciado

Qual componente React tem comportamento parecido com o atributo HTML anchor link (`<a>`)?

---

## Alternativas
### Alternativa A

BrowserRouter

### Alternativa B

Link

### Alternativa C

Redirect

### Alternativa D

Route

### Alternativa E

Switch

### Alternativa correta 
#### Alternativa B

---

## Resoluções
### Alternativa A

Essa alternativa está incorreta porque BrowserRouter é o componente que encapsula a sua aplicação, de forma a te possibilitar fazer uso de navegação.

### Alternativa B

Essa alternativa está correta porque Link é o componente a ser usado no lugar de elementos com a tag `<a>`, de forma a disponibilizar navegação por URL na sua aplicação.

### Alternativa C

Essa alternativa está incorreta porque Redirect é um componente que permite ativamente levar quem usa a aplicação para diferentes locais dela.

### Alternativa D

Essa alternativa está incorreta porque Route associa um componente com o caminho da URL.

### Alternativa E

Essa alternativa está incorreta porque Switch é usado para encapsular um conjunto de rotas que você definiu via Route.

---

# Questão 09

---

## Habilidade cobrada na questão:

- Utilizar o `Switch` do `React Router`

---

## Enunciado

Descreva o componente `Switch` e sua aplicação.

---

## Alternativas
### Alternativa A

O componente Switch é usado para desativar um conjunto de rotas que você definiu via `Browser Router`.

### Alternativa B

Dada a URL atual da aplicação, o Switch procura a melhor correspondência entre seu caminho definido na prop path do componente e a URL atual da aplicação.

### Alternativa C

O encapsulamento de rotas é feito conforme a estrutura abaixo:
```javascript
<Route>
  <Switch exact path="/about" component={About}>about</Switch>
</Route>
```

### Alternativa D

O uso do Switch possibilita que mais de um componente seja renderizado, pela correspondência da URL

### Alternativa E

Os dois componentes filhos de um `Switch` são: `Route` e/ou `Redirect`

### Alternativa correta 
#### Alternativa E

---

## Resoluções
### Alternativa A

Essa alternativa está incorreta porque o componente Switch é usado para `encapsular` um conjunto de rotas que você definiu via `Route`.

### Alternativa B

Essa alternativa está incorreta porque dada a URL atual da aplicação, o Switch procura o primeiro Route que possuir correspondência entre seu caminho definido na prop path do componente e a URL atual da aplicação.

### Alternativa C

Essa alternativa está incorreta porque o Route é encapsulado pelo Switch. Na alternativa, os componentes estão invertidos:
O encapsulamento de rotas é feito conforme a estrutura abaixo:
```javascript
<Switch>
  <Route exact path="/about" component={About}>about</Route>
</Switch>
```

### Alternativa D

Essa alternativa está incorreta porque o Switch faz justamente o inverso, ou seja, apenas o primeiro filho que corresponder ao local atual será renderizado.

### Alternativa E

Essa alternativa está correta porque todos os filhos de um `Switch` devem ser `Route` ou `Redirect`.

---

# Questão 10

---

## Habilidade cobrada na questão:

- Utilizar o `Redirect` do `React Router`

---

## Enunciado

Descreva o uso do `Redirect`.

---

## Alternativas
### Alternativa A

O `Redirect` é um componente que renderiza vários componentes através da correspondência exata de várias URL's.

### Alternativa B

O `Redirect` é um componente que é inadequado para autenticação e acesso de informações sensíveis.

### Alternativa C

O `Redirect` é um componente que pode ser usado juntamente com ternários para renderizar outros componentes condicionalmente.

### Alternativa D

O `Redirect` é um componente que deve ser usado fora de um `Switch` para funcionar corretamente

### Alternativa E

O `Redirect` é um componente que deve ser usado dentro de um `Switch` para funcionar corretamente

### Alternativa correta 
#### Alternativa C

---

## Resoluções
### Alternativa A

Essa alternativa está incorreta porque correspondência exata ocorre com apenas uma única URL. O `Redirect` é um componente que permite ativamente levar quem usa a aplicação para diferentes locais dela.

### Alternativa B

Essa alternativa está incorreta porque `Redirect` é um componente que permite ativamente levar quem usa a aplicação para diferentes locais dela. Por exemplo, é possível acessar informações sensíveis (tipo conta bancária) de uma aplicação se ela já estiver autenticada; caso contrário, ela é redirecionada para uma página de login.

### Alternativa C

Essa alternativa está correta. Veja um exemplo desta utilização neste link: https://reactrouter.com/web/api/Redirect.

### Alternativa D

Essa alternativa está incorreta porque não há restrição em usar o `Redirect` dentro ou fora do `Switch`. Usar dentro do `Switch` é recomendado para evitar possíveis problemas de renderização na ocorrência de correspondências de rota.

### Alternativa E

Essa alternativa está incorreta porque não há restrição em usar o `Redirect` dentro ou fora do `Switch`. Usar dentro do `Switch` é recomendado para evitar possíveis problemas de renderização na ocorrência de correspondências de rota.

---
