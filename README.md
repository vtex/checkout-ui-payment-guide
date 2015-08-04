# Guia de desenvolvimento de layout para meio de pagamento no _Smart Checkout_ VTEX

## Introdução
Este é um documento destinado aos integradores de novos meios de pagamento ao _Smart Checkout_ da VTEX. Além da integração _back-end_ com o _PCI Gateway_, é essencial que os integradores forneçam uma interface com o usuário que contenha a identidade visual do meio de pagamento a ser apresentada.

Oferecemos o código de um dos nossos meios de pagamentos já integrados para servir de base na contrução de novos meios.

## Como utilizar este repositório

### Estrutura

* `index.html`: HTML do checkout (não deve ser alterado)
* `payment.html`: HTML de exemplo do módulo de pagamento
* `payment.less`: estilo de exemplo do módulo de pagamento
* `img`: pasta das imagens utilizadas no pagamento
* `locale`: pasta dos arquivos de tradução
    * `pt-BR.json`: português do Brasil
    * `en-US.json`: inglês dos EUA
    * `es.json`: espanhol LATAM

### Desenvolvimento

Para começar a escrever seu código, você deve fazer um _fork_ do repositório. Após clonar o repositório na sua máquina, existem duas formas de rodar o projeto:

* __Com servidor local__: você pode utilizar o [http-server](https://www.npmjs.com/package/http-server) para rodar um simples servidor local;
* __Sem servidor local (não funciona no _Chrome_)__: basta abrir o arquivo `index.html` no navegador.

## Como projetar a solução de interface com o usuário

### Comunicação
A comunicação sobre o meio de pagamento é iniciada ao selecioná-la. É o momento em que o consumidor manifesta algum interesse em utilizá-la. Dessa maneira, é importante comunicar, resumidamente e de forma clara, como funciona e quais são as vantagens de se utilizar este meio. Dados de contato, sendo telefone ou e-mail, também podem ajudar o consumidor a resolver algum problema ou dúvida no momento da compra.

Os textos devem ser produzidos em três idiomas: português, inglês e espanhol. As imagens também podem ser alteradas para atender melhor cada idioma.

### Design e elementos de _UI_

#### Cores e imagens
A utilização de cores e imagens deve seguir a identidade visual do meio de pagamento, sem restrições. Idealmente, as imagens devem ser otimizadas e agrupadas em uma só, utilizando a técnica de css sprites.

#### Tipografia
Seguindo o padrão do _Bootstrap_, as fontes adotadas no _Smart Checkout_ são, nesta ordem: _Helvetica Neue, Helvetica, Arial, sans-serif_. Não é recomendado utilizar outras fontes para textos. Caso seja extremamente necessário, estas fontes devem fazer parte do pacote padrão do sistema operacional, já que não é possível importar novas fontes.

#### Links e scripts
É vetada a utilização de _links_ e _scripts_. Além de não ser essencial para o fechamento da compra, o uso de _links_ e _scripts_ pode distrair o consumidor e até levá-lo para fora do _checkout_. Dessa forma, o conteúdo deve ser apenas informativo e o único _call-to-action_ apresentado na tela deve ser o botão de Finalizar compra, já apresentado atualmente.

#### Responsividade
A interface desenvolvida deve atender os dispositivos:

* ___Desktop_ e _tablet_ horizontal (largura maior ou igual a 768px__). O container possui 462px de largura e altura que pode variar entre 200px e 330px, dependendo do conteúdo;
* ___Tablet_ vertical e _mobile_ (largura menor que 768px)__. O container possui 100% de largura, com margin de 30px e padding de 15px.

Outros _breakpoints_ podem ser adicionados livremente.

### Front-end

#### Bootstrap Framework
O código do _Smart Checkout_ é baseado nos padrões do _Bootstrap_ v2.3.2. Classes de _grid_, alinhamento e outras podem ser utilizadas para estruturar o código do HTML e do CSS.

#### CSS e LESS
O código do estilo pode ser escrito utilizando o pré-processador CSS, LESS.

Na escrita do código, é recomendado:

* Utilizar apenas classes como seletores;

E obrigatório:

* __Não__ utilizar seletores globais, que podem interferir na estrutura ou em outros elementos da página;
* __Não__ utilizar IDs como seletores;
* Utilizar no máximo dois seletores aninhados;
* Utilizar classes em inglês, com letras minúsculas e palavras separadas por hífen. Ex: “.my-payment-method”.
