# curso-http-https
Resumo sobre o que é e como funciona HTTP e HTTPS


# HTTP
O HTTP é um protocolo de comunicação para a  web. Protocolo, nesse contexto, tem o sentido de definiçao, normas e regras de comunicação. 
Essa comunicação que estamos falando se trata da comunicação web, na qual utilizamos um navegador(browser) como o Chrome, Firefox, Opera entre outros. Mas quem são os agentes que participam dessa comunicação? Nesse caso, para a comunicação ocorrer  precisamos de um cliente e um servidor. O cliente é quem inicia essa comunicação, ele enviará um pedido - uma requisição - solicitando alguma coisa ou enviando alguma informação, e o servidor irá processar aquela informação e devolver uma resposta. E toda essa troca de mensagens é feita seguindo as normas do protocolo HTTP.

Navegador -> requisição(envio de dados) -> Servidor

![image](https://user-images.githubusercontent.com/90730406/208314917-5891714e-0b92-423c-90f6-6f49d2b551d3.png)


É importante frisarmos que as mensagens trocadas no HTTP são apenas em texto puro e que ele é indepente de tecnologias específicas ou linguagens de programação. O nosso celular por exemplo, o tempo todo usa o HTTP para enviar requisições através de aplicativos.


# HTTPS
Como o HTTP só trafega texto puro e também não utiliza nenhum tipo de criptografia, isso acaba o deixando inseguro, pois, ao enviarmos dados na requisição como um email e senha por exemplo, estamos enviando o texto puro para o servidor, visível para qualquer um que esteja mal intencionado. Por isso temos o HTTPS, que é o HTTP + uma camada de segurança(SSL/TLS).


O HTTPS funciona a a partir de um certificado digital, que é como se fosse uma identidade e é emitido por uma entidade certificadora(CA - Certificate Authority), cuja função é garantir que os certificados que estão sendo utilizados podem ser confiados. Ao acessarmos um site que trafega utilizando o HTTPS podemos clicar no ícone do cadeado e obter informações sobre o certificado utilizado.

![image](https://user-images.githubusercontent.com/90730406/208315001-dd990240-4129-4b77-96e5-295da6a223ca.png)

Cada certificado possui uma chave pública que irá criptografar os dados que o navegador enviar para o servidor. O servidor tem uma chave privada que só ele conhece e que consegue descriptografar os dados que foram criptografados com a chave pública para ler a requisição.

![image](https://user-images.githubusercontent.com/90730406/208315227-4d223db4-f551-44fc-851f-5551dbb08022.png)


Os tipos de criptografia
Quando a comunicação que é feita diretamente utilizando a chave pública do cliente e a chave privada do servidor chamamos de criptografia assimétrica. Essa comunicação é um pouco lenta, pois para cada requisição é necessário criptografar os dados com a chave pública e descriptografar os dados com a chave privada. 

Por outro lado, temos a criptografia simétrica, que usa a mesma chave para cifrar e decifrar os dados. No entanto, isso não seria tão seguro, não é mesmo?

Por isso, o HTTPS usa uma combinação dos dois tipo de criptografia. Inicialmente, a comunicação começa com a criptografia assimétrica, mas depois de iniciada o cliente gera uma chave simétrica ao vivo só para ele e o servidor com o qual está se comunicando naquele momento. Essa chave exclusiva (e simétrica) é então enviada para o servidor utilizando a criptografia assimétrica (chave privada e pública) e então é utilizada para o restante da comunicação.

# Endereços
O endereço é uma URL e é como localizamos uma página na internet. A URL começa com o protocolo, seguido pelo domínio.

Os elementos de um endereço são:

Ex: https://www.google.com.br

- https - protocolo
- google - domínio, uma referência ao IP do servidor.
	- .com - sub-domínio
	- .br - raiz

Cada endereço tem o seu IP e o DNS (Domain Name System ou servidor de domínios) fornece o IP de um nome de domínio, ou seja, realiza a tradução do nome de um domínio para o endereço de IP. 

Exemplo: Ao acessarmos o endereço google.com o DNS busca o IP correspondente, no caso 142.251.132.46.


# Portas
Uma porta é como um ponto de comunicação com um servidor e o servidor pode ter várias portas abertas. Por isso, podemos informar a porta ao realizar uma requisição para especificar qual porta queremos buscar no servidor e, caso não informarmos, o servidor irá buscar a porta padrão.

Ex: http://www.teste.com.br:81

A porta padrão para o HTTP é 80 e para o HTTPS a porta padrão é 443. Ou seja, mesmo que não digitamos essas portas ao buscar por um endereço na internet, elas estão lá.

Obs: Vários protocolos definem a sua porta padrão, como por exemplo o FTP que usa 21 ou SSH que usa 22.

# Recursos
Além do protocolo e domínio o endereço também pode especificar um recurso, que é algo concreto que queremos acessar, como um documento, uma foto ou qualquer outra coisa. 
![image](https://user-images.githubusercontent.com/90730406/208314636-65b29e3e-9997-40e5-9d58-fd28a6e830ff.png)

# Modelo Requisição e Resposta

O protocolo HTTP segue o modelo de requisição-resposta, onde o cliente inicia a comunicação realizando a requisição e o servidor gera a resposta. Para que o servidor gere essa resposta a requisição precisa ter todas as informações necessárias, o que também a faz ser sempre independente de outras requisições.

Além disso, não é possível guardar o estado(informações) dessas requisições, o que é uma característica do HTTP que chamamos de Stateless. Quando realizamos uma requisição, o HTTP não sabe sobre outras requisições e informações que foram enviadas em momentos anteriores, ele conhece somente sobre aquela requisição que está sendo enviada naquele momento.

Com isso, vamos pensar no cenário onde realizamos o login em um site. Após logarmos, faz sentido em cada página que formos acessar termos que enviar novamente os dados de email e senha na requisição? Isso seria muito trabalhoso. Para que isso não ocorra, o servidor gera uma identificação e passa ela para o navegador guardá-la e enviá-la nas próximas requisições, ou seja, uma sessão, que é um tempo que o cliente permanece ativo no sistema. Essa sessão irá guardar os cookies http, que são um pequeno arquivo de texto normalmente criado pela aplicação web, para guardar algumas informações sobre o usuário no navegador, não necessariamente sobre login.

![image](https://user-images.githubusercontent.com/90730406/208315663-6cf3ba88-9d33-40fe-b207-81331e6406ee.png)


Um cookie fica associado ao domínio que foi salvo (podemos ter um cookie para www.google.com.br, e outro para https://www.microsoft.com/pt-br e para vários outros sites) e pode ser manipulado e até apagado pelo navegador. Um site ou web app pode ter vários cookies e acessando as configurações do navegador conseguimos visualizar os cookies salvos.


# Métodos HTTP
O protocolo HTTP define um conjunto de métodos de requisição responsáveis por indicar a ação a ser executada para um dado recurso. 

Ou seja, podemos indicar qual será a ação realizada ao acessarmos um determinado domínio e recurso. Esses métodos são:

- GET - Receber, acessar dados
- POST - Submeter dados
- DELETE - remover um recurso
- PUT/PATCH - Atualizar um recurso

Os métodos GET e POST são os mais utilizados no desenvolvimento web.

# Respostas HTTP
As respostas HTTP possuem um código, e o código da resposta dá uma dica ao cliente se a requisição foi um sucesso ou não e qual foi o problema em caso de falha. Esses códigos são os Status Code no HTTP, que são categorizados por suas iniciais:

- 2XX - Successful
- 3XX - Redirection
- 4XX - Client error responses
- 5XX - Server error responses

A tabela completa de mensagens HTTP pode ser vista em: https://www.w3schools.com/tags/ref_httpmessages.asp.

# Web Services
O Web Service é uma aplicação que atua como um serviço, e que não necessariamente utiliza um browser para as requisições.

Eles disponibilizam uma funcionalidade na web, através do protocolo HTTP. As funcionalidades variam muito e dependem muito da empresa e do negócio dela. O Google e Facebook por exemplo, possuem muitos Web Services para acessar um usuário, ver os posts dele, interesses, etc. Muitas vezes esses serviços são pagos.

A grande diferença de um Web Service é que os dados não vêm no formato HTML, e sim em algum formato independente da visualização, como XML ou JSON. Com isso, a comunicação entre sistemas é muito mais simples. Com um Web service pode-se trocar informações entre sistemas sem precisar recolher informações detalhadas sobre o funcionamento de cada um. Eles auxiliam na ligação de qualquer tipo de sistema, independentemente de plataforma (Windows, Linux, etc.) ou linguagens de programação (Java, Javascript, PHP, etc.) utilizadas.

# REST
Rest significa  Representational State Transfer que, em português, é “Transferência de Estado Representacional”. É um conjunto de princípios de arquitetura para estabelecer a a comunicação entre aplicações na arquitetura na Web. Ele define a união da URI/URL com os métodos HTTP para determinarem a ação:

- http://usuarios.com/usuario + GET (retorna todos os usuários)
- http://usuarios.com/usuario + POST (adiciona um usuário)
- http://usuarios.com/usuario/1 + PUT/PATCH (atualiza o usuário 1)
- http://usuarios.com/usuario/1 + DELETE (deleta o usuário 1)

Por ser um conjunto de princípios, fica nas mãos do desenvolvedor o compromisso de seguir as definições do REST.

O REST também define a utilização de cabeçalhos na requisição para especificar a representação dos dados (JSON/XML...).

# SOAP 
SOAP significa "simple object access protoco" ou "protocolo de acesso a objetos simples" e é utilizado para comunicação entre aplicações desenvolvidas em diferentes linguagens e plataformas. Ele é um protocolo oficial mantido pela World Wide Web Consortium (W3C) e também se baseia no HTTP, com a diferença de que as suas mensagem são baseadas em XML.

O SOAP define uma série de regras que podem acabar deixando a aplicação um pouco mais lenta.

A principal diferença entre SOAP e REST é que SOAP é um protocolo e REST, não. Normalmente, uma API será baseada em REST ou SOAP, dependendo do caso de uso e das preferências do desenvolvedor. Já os Web Services em sua grande maioria utilizam o SOAP.

# HTTP2
O HTTP é um protocolo que surgiu em meados dos anos 1980/90, e com a chegada do mundo mobile e de novas tecnologias foi necessária uma mudança para otimização desse protocolo.

Em 2015 surgiu a versão 2 do protocolo HTTP, que traz diversas tecnologias para otimizar, dar segurança e diminuir o tamanho das requisições. 
Por padrão, no protocolo HTTP versão 1.1 não é necessário o uso da camada de segurança TSL/SSL, mas no HTTP/2 o uso de HTTPS é obrigatório, devido a quantidade de dados críticos que trafegamos na Web, como senhas e dados bancários.


As principais diferenças entre o HTTP 1.1 e  HTTP/2 são:
- Utilização padrão do GZIP, que "comprime" as respostas das requisições.
- Os headers(cabeçalhos) das requisições e respostas passam a ser binários e são comprimidos usando um algoritmo chamado HPACK para diminuir o volume de dados trafegados;
- Adição da camada TLS, que criptografa os dados das requisições fornecendo maior segurança;
- Utilização dos cabeçalhos/headers statefull: A partir do HTTP2 não precisamos mais repetir os cabeçalhos que já enviamos em uma requisição anterior. Quando fazemos uma requisição para um recurso X onde teríamos os cabeçalhos exatamente iguais aos da requisição anterior, nós não precisamos enviar novamente esses dados. Será necessário alterar o cabeçalho apenas quando enviarmos ou solicitarmos novos dados, e nesse caso enviamos apenas os cabeçalhos que são diferentes.
