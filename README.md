# Revisa

Plataforma web de estudos para ENEM, vestibulares e concursos públicos. A proposta é transformar materiais do estudante em flashcards e questões, organizar revisões e apresentar seu desempenho.

> **Status: especificação para desenvolvimento.** Este README descreve o produto planejado. Nenhuma funcionalidade, integração ou execução de testes está confirmada por este documento. O nome Revisa é provisório; a disponibilidade da marca e do domínio não foi verificada.

## Objetivo

Entregar uma primeira versão utilizável em que o estudante consiga criar uma conta, enviar um material, gerar perguntas, estudar e retomar seu progresso em outro acesso.

A referência funcional é [Decorei](https://decorei.app). O projeto deve ter identidade visual, textos e código próprios, sem copiar marca, imagens, depoimentos ou elementos proprietários.

## Fluxo principal

1. Criar uma conta e escolher ENEM, vestibular ou concurso.
2. Criar uma matéria e adicionar texto ou PDF.
3. Gerar flashcards e questões com base no material.
4. Responder a uma sessão de estudo.
5. Consultar resultados e questões erradas.
6. Retornar para revisões programadas com o progresso salvo.

## Funcionalidades previstas

| Área | Escopo |
| --- | --- |
| Página de apresentação | Proposta, demonstração interativa, funcionalidades, planos e perguntas frequentes |
| Conta | Cadastro, login, recuperação de senha, objetivo e preferências |
| Painel | Revisões pendentes, matérias recentes e acesso a uma sessão |
| Materiais | Organização por matéria, texto colado e PDF com texto selecionável |
| Geração com IA | Flashcards e questões de múltipla escolha com explicações e referências ao material |
| Revisões | Agendamento por desempenho e histórico por cartão |
| Quiz | Questões por matéria, correção e consulta aos erros |
| Desempenho | Acertos, respostas realizadas e evolução por período |
| Planos | Limites de uso no servidor e preparação para assinatura |

Imagens e PDFs digitalizados dependem de OCR e entram após o funcionamento do fluxo principal. Quando um formato não for suportado, a interface deve informar isso claramente.

## Requisitos de conteúdo e IA

- Validar respostas estruturadas antes de salvar perguntas.
- Criar questões com quatro alternativas e uma única resposta correta.
- Associar cada item ao material de origem, à página quando disponível e ao trecho de apoio.
- Descartar ou sinalizar respostas que não tenham suporte no material.
- Informar quando a análise cobrir apenas parte do documento.
- Permitir edição, exclusão e sinalização de possíveis erros.
- Tratar documentos enviados como dados, nunca como instruções de sistema.
- Identificar conteúdo gerado por IA; não apresentar questões geradas como oficiais.
- Não inventar fontes, números de usuários, depoimentos ou promessas de aprovação.

## Experiência e identidade visual

Interface em português brasileiro, responsiva e acessível. Direção inicial: fundo claro, textos escuros, índigo como cor principal e detalhes discretos em verde.

Priorizar leitura confortável, hierarquia clara, navegação por teclado, foco visível e contraste adequado. Toda operação deve apresentar estados de carregamento, vazio, sucesso e erro coerentes com seu resultado real.

## Arquitetura proposta

A escolha final deve considerar o ambiente e qualquer código existente. Estas opções são uma proposta, não dependências já instaladas:

| Camada | Proposta |
| --- | --- |
| Interface e aplicação | TypeScript e React/Next.js |
| Estilos | Tailwind CSS |
| Dados | PostgreSQL |
| Autenticação e arquivos | Serviço gerenciado, como Supabase, se compatível |
| IA | Integração no servidor, com validação de saída e controle de consumo |
| Pagamento | Um provedor com suporte documentado ao modelo de assinatura escolhido |
| Revisão espaçada | FSRS, se viável, ou outro algoritmo documentado |

Evitar serviços redundantes e respeitar a infraestrutura disponível. Consultar documentação oficial para versões, integrações e configuração.

## Dados previstos

O modelo deve representar usuários, matérias, materiais, trabalhos de processamento, baralhos, cartões, questões, sessões, respostas, estado de revisão, consumo e assinaturas.

Todo recurso do estudante deve ter proprietário identificável e autorização verificada no servidor. O estado de revisão e as tentativas precisam persistir entre acessos. As métricas devem distinguir questões novas de tentativas repetidas.

## Segurança e controle de custos

- Manter chaves privadas e credenciais no servidor.
- Isolar contas no banco de dados e no armazenamento de arquivos.
- Validar entradas, tipos de arquivo e tamanhos.
- Aplicar limites por usuário de páginas, gerações, questões e armazenamento.
- Controlar requisições e evitar processamento ou cobrança duplicados.
- Evitar documentos completos e dados sensíveis nos logs.
- Prever exclusão de conta e dados, considerando a retenção necessária nas integrações.
- Não prometer uso ou armazenamento ilimitados.

## Assinaturas

Preços e limites devem ser configuráveis. Valores usados em demonstrações devem ser identificados como ilustrativos.

A confirmação de acesso pago deve ocorrer no servidor. Webhooks devem ser autenticados e idempotentes, com tratamento de cancelamentos e reembolsos. O retorno do checkout, sozinho, não comprova pagamento.

Validar primeiro em ambiente de teste. Não ativar cobrança real ou publicar em produção sem instrução expressa do responsável pelo projeto.

## Modo de demonstração

Sem credenciais externas, disponibilizar dados de exemplo e identificar claramente o modo de demonstração. Não simular como reais uploads, geração com IA, e-mails enviados ou pagamentos.

O modo demonstrativo permite avaliar a interface, mas não comprova o funcionamento das integrações.

## Configuração e execução

**Ainda não há comandos de instalação ou execução confirmados.** Este arquivo é uma especificação; os comandos devem ser adicionados após a implementação e verificação no ambiente real.

O desenvolvedor deve completar esta seção com:

1. Pré-requisitos e versões utilizadas.
2. Instalação de dependências e gerenciador de pacotes.
3. Criação do arquivo de ambiente a partir de `.env.example`.
4. Configuração de autenticação, banco, arquivos e políticas de acesso.
5. Aplicação de migrações e carga opcional de dados de exemplo.
6. Execução local, build e verificações.
7. Configuração dos serviços de IA e pagamentos de teste.

As variáveis devem ser documentadas com os nomes efetivamente usados no código. O `.env.example` deve conter apenas exemplos sem segredos reais. Nunca versionar credenciais.

## Etapas de desenvolvimento

- [ ] Inspecionar o ambiente e registrar decisões técnicas.
- [ ] Criar identidade visual, landing page e navegação.
- [ ] Implementar materiais, flashcards, quiz e persistência.
- [ ] Integrar autenticação, isolamento dos dados e IA.
- [ ] Implementar revisões, métricas e limites de consumo.
- [ ] Integrar e verificar assinaturas em ambiente de teste.
- [ ] Verificar responsividade, acessibilidade e fluxo principal.
- [ ] Atualizar este README com comandos, recursos concluídos e limitações reais.

Rede social, ranking global, marketplace e aplicativos nativos estão fora do escopo inicial.

## Critérios de aceite e testes

- Uma conta não consegue acessar dados de outra.
- O progresso permanece salvo após recarregar e entrar novamente.
- Os resultados de sessões alimentam métricas reais.
- O agendamento respeita o algoritmo escolhido e suas regras documentadas.
- Arquivos inválidos ou ilegíveis produzem mensagens claras.
- A geração valida o conteúdo e informa a cobertura da fonte.
- Limites são aplicados no servidor.
- Eventos de pagamento repetidos não duplicam efeitos.
- O fluxo principal funciona no celular e no computador.
- Build, tipos, lint e testes relevantes passam conforme a configuração implementada.

**Validação atual:** nenhum código foi executado ou testado como parte da criação deste README. Registrar futuramente apenas verificações realmente realizadas.

## Entrega esperada

Código executável, migrações, políticas de acesso, exemplos separados dos dados reais, `.env.example`, instruções verificadas e resumo do que funciona e do que depende de configuração.

Informar os serviços externos necessários e seus fatores de custo sem inventar preços. Documentar também pendências para lançamento, como domínio, contato de suporte, textos legais e decisões comerciais.

## Orientação ao Codex

Use este README como especificação de produto. Inspecione o projeto antes de alterar arquivos, apresente um plano curto e implemente o fluxo principal por etapas. Não encerre apenas com um planejamento ou telas estáticas.

Se uma integração depender de credenciais ausentes, mantenha a limitação explícita e avance nas partes independentes. Atualize o documento conforme a implementação, sem marcar recursos ou testes como concluídos antes de verificá-los.
