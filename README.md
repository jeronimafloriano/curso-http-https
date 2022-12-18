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


O HTTPS funciona a a partir de um certificado digital, que é como se fosse uma identidade e é emitido por uma entidade certificadora(CA - Certificate Authority), cuja função é garantir que os certificados que estão sendo utilizados podem ser confiados. Ao acessarmos um site que trafega utilizando o HTTPS podemos clicar no ícone do certificado e obter informações sobre o mesmo.

![image](https://user-images.githubusercontent.com/90730406/208315001-dd990240-4129-4b77-96e5-295da6a223ca.png)

Cada certificado possui uma chave pública que irá criptografar os dados que o navegador enviar para o servidor. O servidor tem uma chave privada que só ele conhece e que consegue descriptografar os dados que foram criptografados com a chave pública para ler a requisição.



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

