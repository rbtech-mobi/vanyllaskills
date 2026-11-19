# vanyllaskills

Especificações operacionais em Markdown para agentes de IA executarem tarefas técnicas e regulatórias com validação de entrada, bloqueio de inferência e saída auditável.

## Estrutura do repositório

    .
    ├── política-dados/       # Em migração para o padrão /skills/<nome>/SKILL.md
    └── README.md

> **Nota de padronização:** Novas skills devem seguir a árvore `/skills/<nome-em-kebab-case>/SKILL.md` (sem acentos ou caracteres especiais nos nomes de diretório) para evitar quebra de path em ambientes POSIX/CI.

## Anatomia de uma skill

Todo arquivo `SKILL.md` precisa definir obrigatoriamente:

* **Identificação:** nome em `kebab-case` (ex: `politica-uso-dados`).
* **Escopo:** critérios objetivos de quando acionar e quando ignorar a skill.
* **Restrições:** lista explícita do que o agente está proibido de assumir ou gerar.
* **Pipeline de execução:**
  * **Fase 0 (Pré-condições):** dados mínimos obrigatórios para iniciar.
  * **Fase 1 (Coleta):** perguntas fechadas ao usuário, sem inferência de contexto.
  * **Fase 2 (Validação):** checklist técnico antes da compilação do resultado.
  * **Fase 3 (Entrega):** schema e formato exato do documento final.
* **Referências:** base legal, norma técnica ou documentação oficial que sustenta as regras.

Diretórios auxiliares opcionais dentro da pasta da skill: `examples/` (casos de entrada válida e inválida) e `tests/`.

## Regras de execução

1. **Zero inferência:** não deduzir finalidade, base legal, prazo de retenção ou operadores/processadores de dados. Na ausência de dado, perguntar antes de sugerir.
2. **Proibição de texto genérico:** expressões vagas (ex: *"melhorar a experiência do usuário"*) são bloqueadas se não estiverem vinculadas a um dado específico e sua respectiva base legal.
3. **Aviso de escopo jurídico/fiscal:** qualquer saída envolvendo LGPD, contratos ou obrigações fiscais deve ser emitida explicitamente como **minuta técnica**, sem substituir revisão jurídica formal.
4. **Formato de revisão:** apontamentos de inconsistência seguem o padrão inline:

    <trecho analisado> // correção objetiva

## Como usar

1. Navegue até o diretório da skill desejada e abra o `SKILL.md` (ou clique em **Raw** para obter o texto puro).
2. Injete o conteúdo no *System Prompt*, *Custom Instructions* ou arquivo de regras do seu agente/IDE.
3. Forneça os parâmetros exigidos na **Fase 0** e responda ao questionário da **Fase 1** para liberar a entrega da **Fase 3**.

## Adicionando uma nova skill

1. Crie a estrutura base em `kebab-case` (ASCII):

    mkdir -p skills/nome-da-skill/examples
    touch skills/nome-da-skill/SKILL.md

2. Preencha o `SKILL.md` seguindo as seções descritas em **Anatomia de uma skill**.
3. Adicione ao menos um caso de uso válido e um inválido em `examples/`.
4. Abra um Pull Request descrevendo o escopo e a validação realizada.

## Skills disponíveis

* **`politica-uso-dados`** *(em estruturação em `política-dados/`)*: gera minuta de política de privacidade mapeada a partir da arquitetura e operação real do software. Cobre mapeamento de base legal por finalidade, matriz de responsabilidade (Controlador, Operador e Subprocessadores) e regras de retenção/descarte no encerramento de conta ou contrato.
