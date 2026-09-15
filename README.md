# Navegacao-App

Aplicativo desenvolvido em **Flutter e Dart** para praticar a navegação entre telas, passagem de dados, retorno de informações entre páginas e utilização de rotas no `Navigator`.

A aplicação funciona como um catálogo de produtos, permitindo visualizar os produtos, acessar seus detalhes e cadastrar novos produtos.

## Versão Base — V.0.0

### Objetivo

Criar uma aplicação básica de catálogo utilizando múltiplas telas e navegação entre elas.

### O que a base fazia

A tela principal apresentava uma lista de produtos com nome, preço e um ícone. Ao selecionar um produto, o aplicativo utilizava o `Navigator` para abrir uma tela de detalhes, passando o objeto `Produto` como argumento.

Também existia uma tela para cadastro de produtos, permitindo adicionar um novo produto e retornar o resultado para a tela principal.

A navegação utilizava `Navigator` para abrir e retornar entre as telas, e a tela principal utilizava `setState()` para atualizar a lista quando um novo produto era recebido.

### Resultado

A versão base permitia navegar pelo catálogo, visualizar detalhes dos produtos e retornar informações entre as telas.

---

## Exercício 01 — V.0.0.1

### Objetivo

Criar uma terceira tela chamada `AddProductScreen` com um formulário para cadastrar novos produtos e adicioná-los à lista ao retornar.

### O que mudou

Foi criada a tela:

lib/screens/add_product_screen.dart

Nela foi implementado um formulário para receber as informações de um novo produto.

Na HomeScreen, foi criada a função:

_abrirCadastro()

responsável por abrir a tela de cadastro, aguardar o produto retornado e adicioná-lo à lista _produtos através de setState().

A navegação também passou a ser utilizada para retornar o objeto Produto da tela de cadastro para a tela principal.

### Resultado

O usuário passou a poder cadastrar novos produtos. Depois de retornar para a tela inicial, o produto recebido é adicionado ao catálogo e uma mensagem de sucesso é exibida com SnackBar.

---

## Exercício 02 — V.0.0.2

### Objetivo

Exibir uma caixa de diálogo (AlertDialog) solicitando confirmação antes de voltar para a tela anterior.

### O que mudou

Foi adicionada uma confirmação antes de executar o Navigator.pop() em uma das telas de navegação.

O AlertDialog apresenta as opções para o usuário cancelar ou confirmar a ação de voltar.

Somente após a confirmação o Navigator.pop() é executado, permitindo retornar à tela anterior.

### Resultado

O usuário passou a receber uma confirmação antes de sair da tela, evitando retornos acidentais.

---

### Exercício 03 — V.0.0.3

### Objetivo

Refatorar a navegação do aplicativo para utilizar rotas nomeadas.

### O que mudou

O MaterialApp passou a possuir rotas configuradas na propriedade:

routes:

A tela de cadastro foi registrada como:

'/cadastro'

Para abrir essa tela, passou a ser utilizado:

Navigator.pushNamed(
  context,
  '/cadastro',
);

A tela de detalhes utiliza uma rota dinâmica chamada:

'/detalhes'

Por utilizar um produto específico, os dados são enviados através de:

arguments: produto

e recuperados no onGenerateRoute por meio de:

final produto = settings.arguments as Produto;

Com isso, a aplicação deixou de depender somente de MaterialPageRoute diretamente nos pontos de navegação e passou a utilizar um sistema centralizado de rotas.

### Resultado

A navegação ficou mais organizada e padronizada, utilizando rotas nomeadas para acessar as telas de cadastro e detalhes, mantendo também a passagem de objetos Produto entre as telas.

---

### Histórico de Versões
- Versão	Exercício	Alteração principal
- V.0.0	Base	Catálogo, detalhes e navegação entre telas
- V.0.0.1	Exercício 01	Criação da AddProductScreen e cadastro de produtos
- V.0.0.2	Exercício 02	AlertDialog para confirmação antes de voltar
- V.0.0.3	Exercício 03	Utilização de rotas nomeadas com routes e pushNamed

---

### Estrutura Final
lib/
├── main.dart
├── models/
│   └── produto.dart
└── screens/
    ├── detail_screen.dart
    └── add_product_screen.dart

---

### Tecnologias Utilizadas
- Flutter
- Dart
- Git
- GitHub
