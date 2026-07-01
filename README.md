 <div align="center">


<img src="https://github.com/SOPRO-equipe1/.github/blob/main/profile/logo.png" alt="SOPRO Logo" width="250">



# 🌬️ Soprinho — O assistente virtual do projeto 

Nas exuberantes e místicas terras da Indonésia, em meio à vibrante natureza das Ilhas de Java,  
nasceu um leãozinho muito especial chamado **Soprinho**.

Diferente dos outros leões da savana que usavam seus rugidos para impor medo,  
o maior desejo de Soprinho sempre foi encontrar uma forma de aproximar as pessoas.

Ele percebeu que o mundo estava cheio de corações cheios de sentimentos, mas com grandes dificuldades de comunicação.  
Foi então que ele descobriu o seu verdadeiro propósito: ser uma ponte de carinho, clareza e empatia.

Com seu sopro suave e sua capa acolhedora, ele transforma mensagens complexas e jargões difíceis em palavras simples, cheias de afeto e fáceis de entender.

Mas para manter toda essa energia positiva, paciência e doçura no coração, o Soprinho tem um pequeno segredo:  
ele se abastece puramente com o melhor café de Java!  
É o calor de uma boa xícara que dá a ele o foco necessário para ouvir com atenção e responder sempre com um sorriso e um abraço em forma de palavras.

---
---

## Mascote


<!-- COLOQUE O SEU GIF AQUI -->
<img src="https://github.com/SOPRO-equipe1/chatbot-doc/blob/main/chatjava.png" alt="SOPRO Logo" width="400">


---

## 🛠️ Tecnologias utilizadas

O motor de inteligência e a API de comunicação do Soprinho foram integrados utilizando o seguinte ecossistema backend:

 **Java 17** & **Spring Boot**: Estrutura base da aplicação.
 **Spring RestClient**: Utilizado para realizar chamadas HTTP assíncronas e robustas para a API remota.
 **Ollama OSS**: Infraestrutura de LLM (Large Language Model) utilizada para processar os prompts utilizando o modelo `gpt-oss:120b`.
 **Spring Data JPA / PostgreSQL**: Camada de persistência que gerencia e busca o banco de conhecimentos estruturado.
 **Gson (Google)**: Biblioteca para o tratamento e parsing seguro do JSON bruto retornado pela API.

---

## 🧠 Como o Soprinho funciona?

O fluxo de atendimento do Soprinho foi desenhado pensando em **segurança de escopo** e **alta disponibilidade**:

### 1. Engenharia de prompt e escopo rígido
O assistente opera sob uma persona estrita definida via `System Prompt` dentro de `ConhecimentoService.java`:
 **Acolhimento:** Comunica-se de forma humanizada, usando parágrafos limpos e emojis sutis (como 😊, ✨, 💙).
 **Proibição de markdown:** Ele foi instruído a nunca gerar textos com asteriscos (`**texto**`) ou outras marcações estruturais, mantendo a leitura fluida[cite: 1].
 **Tradução de jargões:** Termos complexos ou nomes de componentes técnicos vindos do banco de dados são traduzidos automaticamente para linguagem popular (ex: *"medidor que sente o ar passar"* em vez de nomes de sensores industriais).  
 **Foco Total no Sopro:** Se o usuário tentar desviar o assunto para temas gerais (como receitas ou programação), o Soprinho relembra com carinho que ele é o assistente do SOPRO.

###  Filtro de contexto dinâmico
Antes de enviar a pergunta para a IA, o serviço consulta o repositório cadastrado. O sistema filtra os tópicos e metadados mais relevantes compatíveis com a dúvida do usuário, alimentando o modelo apenas com fatos reais do projeto.

###  Sistema de contingência local (Fallback)
Se a API do Ollama estiver fora do ar ou instável, o código intercepta a exceção e ativa uma **busca por palavras-chave local**[cite: 1]. Caso encontre uma correspondência exata nos metadados ou títulos cadastrados, ele entrega o conteúdo diretamente do banco de dados, garantindo que o usuário nunca fique sem resposta durante o **Demo Day**

---

 </div>
## 📂 Estrutura do Código Principal

A lógica está concentrada no arquivo `ConhecimentoService.java`, que gerencia:
 `sussurrarParaIA(String mensagemUsuario)`: Valida os dados, injeta as diretrizes de segurança, consome o endpoint do Ollama e trata o retorno.
 `filtrarContextoRelevante(...)`: Garante que a IA só saiba o que está cadastrado na nossa base real.
 `gerarRespostaDeContingenciaLocal(...)`: O mecanismo de segurança para manter o assistente funcionando offline ou em picos de instabilidade.

---

> ✨ **Nota do Projeto:** O assistente e os módulos do projeto SOPRO estão em fase ativa de validação para o Demo Day!
