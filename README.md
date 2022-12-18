# curso-http-https
Resumo sobre o que é e como funciona HTTP e HTTPS


# HTTP
O HTTP é um protocolo de comunicação para a  web. Protocolo, nesse contexto, tem o sentido de definiçao, normas e regras de comunicação. 
Essa comunicação que estamos falando se trata da comunicação web, na qual utilizamos um navegador(browser) como o Chrome, Firefox, Opera entre outros. Mas quem são os agentes que participam dessa comunicação? Nesse caso, para a comunicação ocorrer  precisamos de um cliente e um servidor. O cliente é quem inicia essa comunicação, ele enviará um pedido - uma requisição - solicitando alguma coisa ou enviando alguma informação, e o servidor irá processar aquela informação e devolver uma resposta. E toda essa troca de mensagens é feita seguindo as normas do protocolo HTTP.

Navegador -> requisição(envio de dados) -> Servidor

É importante frisarmos que as mensagens trocadas no HTTP são apenas em texto puro e que ele é indepente de tecnologias específicas ou linguagens de programação. O nosso celular por exemplo, o tempo todo usa o HTTP para enviar requisições através de aplicativos.


# HTTPS
Como o HTTP só trafega texto puro e também não utiliza nenhum tipo de criptografia, isso acaba o deixando inseguro, pois, ao enviarmos dados na requisição como um email e senha por exemplo, estamos enviando o texto puro para o servidor, visível para qualquer um que esteja mal intencionado. Por isso temos o HTTPS, que é o HTTP + uma camada de segurança(SSL/TLS).


O HTTPS funciona a a partir de um certificado digital, que é como se fosse uma identidade e é emitido por uma entidade certificadora(CA - Certificate Authority), cuja função é garantir que os certificados que estão sendo utilizados podem ser confiados. Cada certificado possui uma chave pública que irá criptografar os dados que o navegador enviar para o servidor. O servidor tem uma chave privada que só ele conhece e que consegue descriptografar os dados que foram criptografados com a chave pública para ler a requisição.

Os tipos de criptografia
Quando a comunicação que é feita diretamente utilizando a chave pública do cliente e a chave privada do servidor chamamos de criptografia assimétrica. Essa comunicação é um pouco lenta, pois para cada requisição é necessário criptografar os dados com a chave pública e descriptografar os dados com a chave privada. 

Por outro lado, temos a criptografia simétrica, que usa a mesma chave para cifrar e decifrar os dados. No entanto, isso não seria tão seguro, não é mesmo?

Por isso, o HTTPS usa uma combinação dos dois tipo de criptografia. Inicialmente, a comunicação começa com a criptografia assimétrica, mas depois de iniciada o cliente gera uma chave simétrica ao vivo só para ele e o servidor com o qual está se comunicando naquele momento. Essa chave exclusiva (e simétrica) é então enviada para o servidor utilizando a criptografia assimétrica (chave privada e pública) e então é utilizada para o restante da comunicação.

# Endereços
Os elementos de um endereço
https://www.google.com.br

- https - protocolo
- google - domínio, uma referência ao IP do servidor.
	- .com - sub-domínio
	- .br - raiz

O endereço é como localizamos uma página na internet. Cada endereço tem o seu IP e o DNS (Domain Name System ou servidor de domínios) fornece o IP de um nome de domínio, ou seja, realiza a tradução do nome de um domínio para o endereço de IP. 

Exemplo: Ao acessarmos o endereço google.com o DNS busca o IP correspondente, no caso 142.251.132.46.
