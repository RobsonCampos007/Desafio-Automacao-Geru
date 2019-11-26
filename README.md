# Desafio-Automacao-Geru
O desafio de Empréstimo é sobre testes automatizados para api. Imagine que você tem uma API que é a solução para os cenários abaixo, crie alguns testes automatizados para essa API.
Cenário: Criar empréstimo
	Dado que o client possue todos os dados necessários para criação do empréstimo
         E possue um token válido para se comunicar com o serviço
      Quando envio todos os dados para o serviço de criação de empréstimo
	Então o serviço deve criar o empréstimo com sucesso

Cenário: Consultar empréstimo
      Dado que o client tem um empréstimo criado
	 E possue um token válido para se comunicar com o serviço
      Quando o client consultar o serviço de empréstimo informando o ID do empréstimo
         Então o serviço deve me retornar as informações do empréstimo criado

Cenário: Usuário informa e-mail ou senha inválido
     Dado que usuário possua conta cadastrada 
     Quando o usuário acessar o menu Minha Conta 
     Então o sistema exibe a tela Acesse Sua Conta 
         E eu preencho o campo E-mail 
         E eu preencho o campo Senha inválida 
         E eu clico no botão Entrar 
     Então o sistema exibe a mensagem “Usuário ou senha incorretos”

Cenário: Usuário esqueceu sua senha de acesso
      Dado que usuário possua conta cadastrada 
      Quando o usuário acessar o menu Minha Conta 
      Então o sistema exibe a tela Acesse Sua Conta 
          E usuário clicar no link esqueci minha senha 
      Então o sistema exibe a tela redefinir senha 
          E usuário preencher o campo E-mail 
          E clicar no botão enviar e-mail verificação 
       Então o sistema exibe a mensagem “Um e-mail com as instruções de como redefinir a sua senha foi enviado para você.”

Cenário: Usuário cadastra a senha
      Dado que usuário nã possua conta cadastrada 
      Quando usuário acessar o link do e-mail 
      Então o sistema exibe a tela para cadastrar senha 
          E preencher o campo senha 
          E preencher o campo conformar senha 
          E flegar no cmapo Li e aceito os termos 
      Então o sistema habilita o botão cadastrar senha

Cenário: Acesso a última interação do fluxo de solicitação 
       Dado que sua último interação foi em preencher cadastro 
          E possua conta cadastrada 
      Quando usuário esteja na tela minha conta 
          E preencher o campo e-mail 
          E preencher o campo senha 
      Então o sistema habilita o botão entrar 
          E clicar no botão entrar 
          E o sistema acesso a tela preencher cadastro

Dados da API:
#informações: Gerar token
	Endpoint= www.urlficticia.com.br/api/v1/token
	
	Headers= 
		Content-Type: application/json
	Body =
		username: String
		password: String
	Response =
		Token: b2c6f757eb9d49f4b2dace3aab9b1566


#informações: Criar empréstimo
	Endpoint= www.urlficticia.com.br/api/v1/emprestimos
	
	Headers
		Content-Type: application/json
		Authorization: Bearer <token>
	Body =
		id: Number
		nome: String
		cpf: String
		vl_emprestimo: String
		nr_parcelas: String
		vl_parcelas: String


#informações: Consultar empréstimo
	Endpoint= www.urlficticia.com.br/api/v1/emprestimos/<id>

	Headers=
		Content-Type: application/json
		Authorization: Bearer <token>
	Response
		id-emprestimo: String
		status: String

#informações: Usuário informa e-mail ou senha inválido
	Endpoint= www.urlficticia.com.br/api/v1/emprestimos/<id>

	Headers= 
		Content-Type: application/json
	Body =
		username: String
		password: String
	Response =
		{status 401: "Usuário ou senha incorretos"}

#informações: Usuário esqueceu sua senha de acesso
	Endpoint= www.urlficticia.com.br/api/v1/emprestimos/<id>

	Headers= 
		Content-Type: application/json
	Body =
		username: String
                reset-password-controller: String
	Response =
		{status ggg: "Um e-mail com as instruções de como redefinir a sua senha foi enviado para você."}

#informações: Usuário cadastra a senha
	Endpoint= www.urlficticia.com.br/api/v1/emprestimos/<id>

	Headers= 
		Content-Type: application/json
	Body =
		password: String
		confirm-password: String
	Response =
		{status 200: "Senha Cadastrada com Sucesso"}

#informações: Acesso a última interação do fluxo de solicitação 
        Endpoint= www.urlficticia.com.br/api/v1/token
	
	Headers= 
		Content-Type: application/json
	Body =
		username: String
		password: String
	Response =
		last-section: String





