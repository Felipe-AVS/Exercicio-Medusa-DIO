# Teste de autenticação com Medusa e DVWA

## Objetivo

Neste laboratório, utilizei o Kali Linux e a ferramenta Medusa para testar a segurança do formulário de login do DVWA em um ambiente controlado.

O objetivo foi compreender como tentativas automatizadas de autenticação funcionam e identificar os riscos do uso de credenciais fracas.

## Comando utilizado

```bash
medusa -h 192.168.56.101 -U users.txt -P pass.txt -M http \
-m PAGE:'/dvwa/login.php' \
-m FORM:'username=^USER^&password=^PASS^&Login=Login' \
-m 'FAIL=Login Failed' -t 6
```

O comando configura o endereço do alvo, os arquivos com usuários e senhas, o módulo HTTP, a página de login, os campos do formulário e o indicador de falha na autenticação.

## Resultado obtido

Durante o teste, a ferramenta Medusa identificou credenciais válidas para acessar o DVWA:

- **Usuário:** `admin`
- **Senha:** `password`

Após utilizar essas credenciais, consegui acessar a aplicação. O resultado demonstra como o uso de senhas fracas pode comprometer a segurança de um sistema quando não existem controles suficientes contra tentativas automatizadas de autenticação.

## Análise e medidas de segurança

Com esse teste, observei a importância de adotar medidas para dificultar ataques de força bruta, como:

- Utilizar senhas fortes e exclusivas.
- Implementar limites de tentativas de login e atrasos progressivos.
- Registrar e monitorar tentativas de autenticação malsucedidas.
- Implementar autenticação multifator (MFA), quando disponível.
- Evitar mensagens de erro que facilitem a identificação de contas válidas.
- Manter a aplicação e seus componentes atualizados.

## Conclusão

A prática demonstrou como uma ferramenta de auditoria pode identificar credenciais fracas em uma aplicação vulnerável. Também reforçou a importância de testar os mecanismos de autenticação em ambientes autorizados e aplicar medidas preventivas para reduzir o risco de acesso indevido.

O laboratório foi realizado com finalidade educacional, utilizando o DVWA em ambiente controlado.
