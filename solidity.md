
Smart Contracts em Solidity
============================

##Introdução
* sadasdasdasdasdasdadsadasdasdasdasdasdasdsadasdasdasdasdasdasdasdadasdasdasdasd

##O Contrato
* Bloco de código fundamental na construção de aplicações em Ethereum
* Todas as variáveis e funções pertencem a um **contract**

Exemplo de declaração de um contrato:
>~~~go
>//Declaração do corpo do contrato
>contract Contrato{
>
>}
>~~~

###Pragma Version
* **Deve** estar na primeira linha 
* Indica a versão do compilador Solidity

Exemplo de declaração de Version Pragma

>~~~go
>version pragma solididty ^0.4.19
>
>contract Contrato{
>
>}
>~~~

##Variáveis

* **Variáveis de Estado** representam o estado do contrato e são gravadas permanentemente na block chain, é semelhante a campos de uma tabela em uma banco de dados
* **Tipos de Variáveis**
	* **bool**
		>~~~go 
		>//Define um booleano, podendo ser true ou false
		>bool ok = true;
		>~~~
	* **int**
		>~~~go
		>//Representam valores inteiros de 256bits positivos e negativos (limite de -2^256 à 2^256)
		>int256 inteiroDe256bits = 256;
		>int inteiroDe256BitsSimples = 256;
		>
		>//Representam valores inteiros de 128bits positivos e negativos (limite de -2^128 à 2^128)
		>int128 inteiroDe128bits = 128;
		>
		>//Representam valores inteiros de 64bits positivos e negativos (limite de -2^64 à 2^64)
		>int64 inteiroDe64bits = 64;
		>
		>//Representam valores inteiros de 32bits positivos e negativos (limite de -2^32 à 2^32)
		>int32 inteiroDe32bits = 32;
		>
		>//Representam valores inteiros de 16bits positivos e negativos (limite de -2^16 à 2^16)
		>int16 inteiroDe16bits = 16;
		>
		>//Representam valores inteiros de 8bits positivos e negativos (limite de -2^8 à 2^8)
		>int8 inteiroDe8bits = 8;
		>~~~
	* **uint**
		>~~~go
		>//Representam valores inteiros de 256bits positivos (limite de 0 à 2^256)
		>uint256 inteiroDe256bits = 256;
		>uint inteiroDe256BitsSimples = 256;
		>
		>//Representam valores inteiros de 128bits positivos (limite de 0 à 2^128)
		>uint128 inteiroDe128bits = 128;
		>
		>//Representam valores inteiros de 64bits positivos (limite de 0 à 2^64)
		>uint64 inteiroDe64bits = 64;
		>
		>//Representam valores inteiros de 32bits positivos (limite de 0 à 2^32)
		>uint32 inteiroDe32bits = 32;
		>
		>//Representam valores inteiros de 16bits positivos (limite de 0 à 2^16)
		>uint16 inteiroDe16bits = 16;
		>
		>//Representam valores inteiros de 8bits positivos (limite de 0 à 2^8)
		>uint8 inteiroDe8bits = 8;
		>~~~
	* **address**
		>~~~go
		>//Representa um endereço na blockchain, sendo esse um valor hexadecimal de 20bytes
		>address endereco = 0x627306090abaB3A6e1400e9345bC60c78a8BEf57;
		>~~~
	* **string**
		>~~~go
		>//Representa um texto UTF-8
		>string texto = "Texto";
		>~~~

###Operações Matemáticas

* Nada diferente das outras linguagens de programação, em solidity temos:

	* **Adição**
		>~~~go
		>int x = a + b; //Se int x = 5 + 5, então x = 10
		>~~~
	* **Subtração**
		>~~~go
		>int x = a - b; //Se int x = 6 - 3, então x = 3
		>~~~
	* **Multiplicação**
		>~~~go
		>int x = a * b; //Se int x = 6 * 7, então x = 42
		>~~~
	* **Divisão**
		>~~~go
		>int x = a / b; //Se int x = 48 / 12, então x = 4
		>~~~
	* **Módulo da Divisão**
		>~~~go
		>int x = a % b; //Se int x = 19 % 2, então x = 1
		>~~~
	* **Exponenciação**
		>~~~go
		>int x = a ** b; //Se int x = 5 ** 2, então x = 25
		>~~~
	* **Incremento**
		>~~~go
		>int x++; //O mesmo que x = x + 1
		>~~~
	* **Decremento**
		>~~~go
		>int x--; //O mesmo que x = x - 1
		>~~~

* Devido a alguns problemas de segurança com operações matemáticas em Solidity, é aconselhável o uso de uma biblioteca conhecida como SafeMath, desenvolvida pela OpenZepellin para realizar essas operações:
>~~~go
>pragma solidity ^0.4.18;
>
>/**
> * @title SafeMath256
> * @dev Math operations with safety checks that throw on error for uint256
> */
>library SafeMath256 {
>
>  /**
>  * @dev Multiplies two numbers, throws on overflow.
>  */
>  function mul(uint256 a, uint256 b) internal pure returns (uint256) {
>    if (a == 0) {
>      return 0;
>    }
>    uint256 c = a * b;
>    assert(c / a == b);
>    return c;
>  }
>
>  /**
>  * @dev Integer division of two numbers, truncating the quotient.
>  */
>  function div(uint256 a, uint256 b) internal pure returns (uint256) {
>    // assert(b > 0); // Solidity automatically throws when dividing by 0
>    uint256 c = a / b;
>    // assert(a == b * c + a % b); // There is no case in which this doesn't hold
>    return c;
>  }
>
>  /**
>  * @dev Substracts two numbers, throws on overflow (i.e. if subtrahend is greater >than minuend).
>  */
>  function sub(uint256 a, uint256 b) internal pure returns (uint256) {
>    assert(b <= a);
>    return a - b;
>  }
>
>  /**
>  * @dev Adds two numbers, throws on overflow.
>  */
>  function add(uint256 a, uint256 b) internal pure returns (uint256) {
>    uint256 c = a + b;
>    assert(c >= a);
>    return c;
>  }
>}
>~~~

###Conversão de Tipos

* Em solidity, às vezes é necessário fazer uma conversão explícita para um determinado tipo, da seguinte forma: 
	>~~~go 
	>//Declaração de dois inteiros 256bits
	>uint a = 5;
	>uint b = 6;
	>//Soma e conversão em um inteiro de 8bits
	>uint8 c = uint8(a + b);
	>~~~

##Structs

* Assim como em C, representam tipos de dados que encapsulam diversos atributos
* É declarado com a palavra reservada **struct** da seguinte forma:
>~~~go
>//Declaração de uma estrutura com dois campos
>struct Estrutura{
>	int dado1;
>	string dado2;
>}
>~~~

##Arrays

* Serve para agrupar dados em listas
* É declarado da seguinte forma:
	>~~~go
	>tipoDeDado[tamanhoDoArray] nomeDoArray;
	>~~~
* Existem dois tipos de arrays em solidity:
	* **fixed**: Com tamanho fixo
		>~~~go
		>//Declaração de um array com tamanho fixo
		>int[10] arrayDeInteirosComTamanhoDez;
		>~~~
	* **dynamic**: Com tamanho dinâmico
		>~~~go
		>//Declaração de um array com tamanho dinâmico
		>int[] arrayDeInteirosComTamanhoIlimitado;
		>~~~

###Operações em Arrays

* É possível fazer algumas operações nos arrays em Solidity, dentre elas temos: 

	* **Adicionar Elemento**
		>~~~go
		>//Declaração de um array dinâmico
		>int[] array;
		>
		>//Para se adicionar um elemento ao array, usa-se a função array.push(novoItem)
		>array.push(1);
		>array.push(2);
		>array.push(3);
		>~~~

##Mapeamentos

* É uma estrutura do tipo chave-valor que é capaz de armazenar e buscar valores, sendo usado e declarado da seguinte maneira
	>~~~go
	>//Declaração de um mapeamento de um endereço a um valor inteiro, onde o endereço único é a chave e o inteiro um valor relacionado a essa chave
	>mapping (address => int) public addressToInt;
	>
	>//Armazena na variável v o valor relacionado a chave 0x527306090abaC3A6e1400e9345bC60c78a8BEf57 no mapa addressToInt
	>int v = addressToInt[0x527306090abaC3A6e1400e9345bC60c78a8BEf57];
	>~~~

##Functions

* Permitem encapsular a lógica do contrato
* Por convenção, os parâmetros das funções devem iniciar com um *underline*
* A declaração de uma função em Solidity é algo como:
	>~~~go
	>//Declaração de uma função
	>function fazAlgo(int _param1, string _param2){
	>	//Faz algo com _param1 e _ param2	
	>}
	>~~~
* Para se usar esta função, basta chamá-la passando os parâmetros corretamente
	>~~~go
	>//Declaração de uma função
	>fazAlgo(10, "UmaString");
	>~~~

###Retorno das funções

* Para retornar valores em uma função deve-se declarar o tipo de retorno com a palavra **returns** seguido do tipo de retorno e ao fim do método retornar o dado correspondente com a palavra **return**, como por exemplo:
	>~~~go
	>//Função que retorna um uint
	>function fazAlgo(int a) returns(uint){
	>	uint b;
	>	//Faz algo com a e b
	>	return b;
	>}
	>~~~
* É possível em solidity retornar vários valores em uma única função da seguinte forma:
	>~~~go
	>//Função que retorna um int e um uint
	>function fazAlgo(int a) returns(int, uint){
	>	uint b;
	>	//Faz algo com a e b
	>	return (a, b);
	>}
	>~~~
* Para receber os dados desse retorno basta:
	>~~~go
	>//Função que retorna um int e um uint
	>int v1;
	>uint v2;
	>
	>//Copia os retornos da função fazAlgo para as variáveis v1 e v2
	>(v1,v2) = fazAlgo(5);
	>~~~
* Caso você não queira receber algum dos retornos basta deixar o campo referente a esse retorno indesejado vazio:
	>~~~go
	>//Função que retorna um int e um uint
	>int v1;
	>uint v2;
	>
	>//Copia o primeiro retorno da função fazAlgo para a variável v1
	>(v1,) = fazAlgo(5);
	>//Copia o segundo retorno da função fazAlgo para a variável v2
	>(,v2) = fazAlgo(5);
	>~~~

###Funções Construtoras

* São funções opcionais que têm o mesmo nome do contrato e são executadas apenas uma vez, na primeira criação do contrato
	>~~~go
	>//Declaração do contrato
	>contract Contrato{
	>	
	>	function Contrato(){
	>		//Faz algo na primeira criação do contrato
	>	}
	>}
	>~~~

##Modificadores de Acesso

* Modificadores de acesso permitem observar onde uma função é visível dentro do projeto, este é aplicado em atributos e funções do contrato
* Em atributos eles são definidos logo após o tipo de dados
	>~~~go
	>int public inteiroPublico
	>~~~
* Em funções eles são definidos logo após o tipo de dados
	>~~~go
	>function nomeDaFuncao() public {
	>	
	>}
	>~~~
* Os modificadores de acesso em solidity são:
	* **Default(vazio)**: Público
		>~~~go
		>//Exemplo de Atributo sem modificador de acesso (public por padrão)
		>int public _nomeDoInt;
		>
		>//Exemplo de função sem modificador de acesso (public por padrão)
		>function nomeDaFuncao() {
		>	
		>}
		>~~~
	* **Public**: Permite que a função ou atributo sejam acessador por qualquer um que o chame
		>~~~go
		>//Exemplo de Atributo public
		>int public _nomeDoInt;
		>
		>//Exemplo de função public
		>function nomeDaFuncao() public {
		>	
		>}
		>~~~
	* **Private**: Só pode ser acessado dentro do próprio contrato
		* Por convenção atributos e funções privadas devem ser iniciadas com um *undeline* _
		>~~~go
		>//Exemplo de Atributo private
		>int private _nomeDoInt;
		>
		>//Exemplo de função privada
		>function _nomeDaFuncao() private {
		>	
		>}
		>~~~
	* **Internal**: Apenas para dentro do contrato e para contratos que herdam esse atributo
		>~~~go
		>//Exemplo de Atributo internal
		>int internal nomeDoInt;
		>
		>//Exemplo de função internal
		>function nomeDaFuncao() internal {
		>	
		>}
		>~~~
	* **External**: Só pode ser acessado por todos os contratos, assim como o public, mas não pode ser usado no contrato em que foi declarado
		>~~~go
		>//Exemplo de Atributo external
		>int external nomeDoInt;
		>
		>//Exemplo de função external
		>function nomeDaFuncao() external {
		>	
		>}
		>~~~
##Modificadores Especiais para Funções

* Além dos modificadores de acesso padrão, temos alguns modificadores especiais para funções, dentre eles:

	* **view**: Esse modificador só pode ser usado em funções que não alteram o estado do contrato, isto é, não altera ou escreve qualquer coisa, e é usada da seguinte maneira:
		>~~~go
		>
		>string hello = "Hello";
		>
		>function sayHello() public view returns(string) {
		>	return hello;
		>}
		>~~~
	* **pure**: Esse modificador é utilizado em funções que nem ao menos lêem dados do contrato, utilizando apenas informações dos seus parâmetros ao ser executada, como por exemplo:
		>~~~go
		>function sum(int _n1, int _n2) public pure returns(int) {
		>	return _n1 + _n2;
		>}
		>~~~

##Funções Modificadoras

* São semi funções que são usadas para modificar o comportamento de uma função
* São normalmente usadas para fazer verificações require
* Utilizam a palavra reservada **modifier** na declaração
* Devem em seu final retormar a execução da função que modificaram pelo *undeline* (_)
* Podem ou não receber parâmetros
* São exemplos de funções modificadoras:
>~~~go
>//Modificador que verifica se _x é maior que _y
>modifier maiorQue(int _x,int _y){
>	//Faz a verificação
>	require(_x > _y);
>	//Continua a execução da função que o chamou
>	_;		
>}
>
>//Pode ser usado da seguinte maneira, validando que o _a deve ser maior que _b
>function soma(int _a, int _b) maiorQue(_a, _b) returns(int){
>	return _a + _b;
>}
>~~~

##Criptografia

* Solidity nos permite criptografar dados através de algumas funções, dentre elas temos por padrão:

	* **Keccak256**: Uma versão interna do solidity do SHA3 que permite transformar uma string em um número hexadecimal de 256 bits através de uma função hash
		>~~~go
		>kekkak256("um dado"); //91e9af6584bc1298db65ba17c83e4d0e1026d91a77db38d25563988e195f885f
		>
		>kekkak256("outro dado"); //4a1d0ca044077c7e50b4d7231b9b92ce0ba0158c12440082c3ba27d79ceacad0
		>~~~
	* **sha256**: Calcula o SHA256 de uma string
		>~~~go
		>sha256("um dado"); //6ca6f5327a6ea0b7985c96314cb6a4dd0610935806951316748f7c5e0d770f8a
		>
		>sha256("outro dado"); //939e67215c963d9c2d756b9deaf5ddffb5a53bcfc502eaa2b73253e093548173
		>~~~
	* **ripemd160**: Calcula o RIPEMD-160 de uma string, retornando uma hash de 20bytes 
		>~~~go
		>ripemd160("um dado"); //664ed11fe205dde0a7c4546f744a2c8ba2732be2
		>
		>ripemd160("outro dado"); //50c7c5d52f2dcbd08b46cc6467320b16acb4ee00
		>~~~

##Eventos

* Eventos em solidity é uma das formas que o contrato tem para comunicarem algo que ocorreu na Blockchain para o DApp, cuja o qual pode ouvir eventos do seu contrato e tomar decisões baseadas nisso.

* Eventos são declarados pela palavra reservada **event** da seguinte forma:
	>~~~go
	>event nomeDoEvento(int param1, string param2);
	>~~~
* E são disparados dentro de funções do contrato da seguinte forma:
	>~~~go 
	>function nomeDaFuncao(int _arg1, string _arg2) public {
	>	//Faz algo com os argumentos
	> 	//Dispara o evento
	>	nomeDoEvento(_arg1, _arg2);
	>}
	>~~~
* Ao disparar o evento, este será ouvido pela DApp, onde uma implementação em javascript seria:
	>~~~js
	>Contract.nomeDoEvento(function(error, result) {
	>	/*Faz Algo com result e error*/
	>});
	>~~~

##Variáveis e Funções Especiais

* Em solidity temos algumas variáveis e funções especiais que estão disponíveis para o uso, elas são:
	>
	* **block.blockhash(uint blockNumber)**: Devolve a hash do bloco dado seu número
		* Funciona apenas para 256 blocos mais recentes, excluindo os atuais
	* **block.coinbase**: Devolve o endereço do atual minerador do bloco
	* **block.difficulty**: Devolve a dificuldade do bloco atual
	* **block.gasLimit**: Devolve o gas limit do bloco atual
	* **block.number**: Devolve o número do bloco atual
	* **block.timestamp**: Devolve o timestamp em segundos do bloco atual
		* Um alias para esse é usar a função _now()_
	* **gasLeft()**: Retorna a quantidade de gás restante
		* substituto para o _msg.gas_ depreciado na versão 0.4.21
	* **block.number**: Devolve
	>
	* **msg.data**: Devolve todos os dados da chamada ao contrato
	* **msg.sender**: Devolve o endereço do remetente que enviou a mensagem
	* **msg.sig**: Devolve os primeiros quatro bytes dos dados de chamada
	* **msg.value**: Devolve o número em wei enviado com a mensagem
	>
	* **tx.gasprice**: Devolve o preço do gás da transação
	* **tx.origin**: Devolve o endereço do remetente da transação 

##Prevenção de erros

* Solidity tem algumas funções que permitem lançar erros e impedir inconsistências no bloco, estas são:
	* **require**: Lança um erro caso a condição não seja atendida, é utilizada normalmente no início das funções para validar entradas ou componentes externos, um exemplo de uso é:
	>~~~go 
	>function nomeDaFuncao(int _arg1, int _arg2) public {
	>	//Requer que o _arg1 e _arg2 sejam diferentes
	>	require(_arg1 != _arg2);
	>	//Faz algo se os argumentos forem válidos	
	>}
	>~~~
	* **assert**: Lança um erro caso a condição não seja atendida, é utilizada normalmente no meio  das funções para validar possíveis problemas internos em tempo de execução
	>~~~go 
	>function nomeDaFuncao(int _arg1, int _arg2) public {
	>	//Faz algo se os argumentos	
	>	assert(_arg1 > 0);
	> 	//Continua fazendo algo se o _arg1 for válido
	>}
	>~~~

##Herança

* Em solidity existe a possibilidade de Herança entre contratos, onde um contrato é capaz de receber atributos e funções de outro
* A herança é definida com o uso da palavra reservada **is** da seguinte forma:
	>~~~go
	>contract ContratoAprendiz{
	>	//Atributos e funções
	>}
	>
	>contract ContratoMestre is ContratoAprendiz{
	>	//Atributos e funções do ContratoMestre e do ContratoAprendiz
	>}
	>~~~
* Também é possível ter herança múltipla utilizando o _vírgula_ (,) como separador
	>~~~go
	>contract ContratoAprendiz{
	>	//Atributos e funções
	>}
	>
	>contract ContratoProfessor{
	>	//Atributos e funções
	>}
	>
	>contract ContratoMestre is ContratoAprendiz, ContratoProfessor{
	>	//Atributos e funções do ContratoMestre, do ContratoAprendiz e do ContratoProfessor
	>}
	>~~~

##Interfaces

* Uma interface contém as informações sobre as funções que contém, permitindo usar assim apenas a interface com o endereço do contrato que a implementa, ao invés de criar um contrato totalmente novo
* As interfaces são declaradas como contratos que possuem funções que tem apenas corpo, mas sem implementação, da seguinte maneira
	>~~~go
	>//A declaração de uma interface é como a de um contrato
	>contract UmaInterface{
	>	//As funções possuem apenas corpo porém a implementação pode estar em outro local
	>	function umaFuncaoDaInterface(int _n1, int _n2) public returns(int);
	>}
* Para chamar uma interface, basta instanciá-la passando o endereço do contrato da interface como parâmetro do construtor
	>~~~go
	>//A declaração de uma interface é como a de um contrato
	>contract UsaInterface{
	>	//Declaração da interface passando seu endereço	
	>	UmaInterface inter = UmaInterface(0xf17f52151EbEF6C7334FAD080c5704D77216b732)	
	>	//Usando a função implementada nessa interface:
	>	int x = inter.umaFuncaoDaInterface(1,2);
	>}

##Importação de contratos
* É possível organizar melhor os contratos e mantê-los em arquivos separados, adicionando eles apenas quando forem necessários.
* A forma de se chamar contratos existentes em arquivos externos é com a palavra reservada **import**:
	>~~~go
	>import "../algumaPastaNumDiretório/arquivoSoldity.sol";
	>~~~

##Armazenamento e Memória

* Em Solidity, existem dois lugares onde você pode guardar as variáveis - na storage (armazenamento) e na memory (memória)

* A **Storage** refere-se às variáveis guardadas eternamente na blockchain
* A **Memory** refere-se às variáveis temporárias que são apagadas entre as chamadas
* Por padrão o estado das variáveis está implícito, ou seja, caso uma variável seja declarada no corpo do contrato será uma do tipo storage, e uma que esteja declarada dentro de uma função será memory
* Mas existirão momentos em que será necessário utilizar essas palavras dentro de funções, principalmente quando se está lidando com **structs** ou **arrays**
* Nesse contexto uma storage será um ponteiro para a estrutura/array e fará alterações reais, enquanto a memory fará uma cópia da estrutura/array para ser usada na função
* Um exemplo em código é:
	>~~~go
	>struct Estrutura {
	>	string id;
    >	string nome;
	>}
	>
	>function manipulaEstruturaStorage(Estrutura storage estrutura) public {
	>	//Faz algo com o ponteiro para Estrutura	
	>}
	>
	>function manipulaEstruturaMemory(Estrutura memory estrutura) public {
	>	//Faz algo com a cópia da Estrutura	
	>}
	>~~~

##Contratos Ownable

* Prática que permite definir uma função como proprietária, isto é, apenas o dono do contrato pode utilizá-la
* Uma implementação é a biblioteca Ownable da OpenZepellin:
	>~~~go
	>/**
	> * @title Ownable
	> * @dev Um contrato Ownable tem um endereço de dono, e fornece funções básicas de autorização,
	> * que simplificam a implementação de "permissões de usuário".
	> */
	>contract Ownable {
	>  	address public owner;
	>  	event OwnershipTransferred(address indexed previousOwner, address indexed newOwner);
	>
	>  	/**
	>  	* @dev O construtor Ownable define o `owner` (dono) original do contrato como o sender da conta
	>  	*/
	>  	function Ownable() public {
	>    	owner = msg.sender;
	>  	}
	>
	>  	/**
	>	* @dev Lança um erro se chamado por outra conta que não seja o dono.
	>	*/
	>	modifier onlyOwner() {
	>		require(msg.sender == owner);
	>    	_;
	>  	}
	>
	>	/**
	>  	* @dev Permite que o atual dono transfira o controle do contrato para um novo dono.
	>  	* @param newOwner O endereço de transferência para o novo dono.
	>	*/
	>  	function transferOwnership(address newOwner) public onlyOwner {
	>    	require(newOwner != address(0));
	>    	OwnershipTransferred(owner, newOwner);
	>    	owner = newOwner;
	>  	}
	>}
	>~~~
* O modificador **onlyOwner** do contrato acima permite que apenas o proprietário do bloco consiga utilizar essa função

##Gas

* O Gas é o combustível utilizado pelas DApps Ethereum
* Toda vez que se utiliza uma função de algum contrato Ethereum, deve-se pagar uma taxa conhecida como **gas**
* O gas pode ser comprado com Ether, a moeda do Ethereum
* O valor dessa taxa é calculado com base na complexidade da lógica da função, onde cada operação individual tem um custo em gas, baseado no esforço computacional para executá-la. Desta forma o valor a ser pago com gas é a somatória desses valores
* Por causa disso, otimizar código em Solidity tem uma importância sem igual em Solidity
* O gás foi necessário pois os criadores da Ethereum queriam ter certeza de que a rede não seria prejudicada por funções que contenham laços infinitos e esgotar todos os recursos computacionais
* Esse tipo de cobrança faz apenas sentido no Ethereum e outras blockchains, mas existem casos em que essa cobrança seria desnecessária

###Formas de Economizar gas

* Utilizar tamanhos menores de variáveis como **int32**, **int64** não faz diferença para os custos em gás, a não ser que se esteja em uma **struct**
* Agrupar tipos iguais nas estruturas também facilita na economização de gas

