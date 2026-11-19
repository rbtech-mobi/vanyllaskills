Cada skill é um procedimento completo, não um prompt genérico. Uma skill só é considerada completa quando mapeia operação real, valida entradas e entrega saída auditável.

Estrutura
/skills
  /politica-uso-dados
    SKILL.md
    examples/
    tests/
  /contrato-controlador-operador
    SKILL.md
  /retencao-e-eliminacao
    SKILL.md
README.md
CONTRIBUTING.md
Padrão de skill completa
Toda skill em /skills/<nome>/SKILL.md deve conter:

Nome: kebab-case. Ex: politica-uso-dados
Descrição: quando usar, quando não usar.
Princípio: por que template genérico falha.
Proibido: o que a skill não pode fazer.
Fluxo obrigatório:
Fase 0 - Verificação: dados mínimos para iniciar.
Fase 1 - Questionário: perguntas fechadas, sem inferência.
Fase 2 - Validação: checklist antes de entregar.
Fase 3 - Saída: formato exato da entrega.
Tom: formal, direto, técnico.
Saída: formato, seções, exemplo de tabela.
Referências: base legal, fonte.
Arquivo mínimo: SKILL.md. Opcional: examples/, tests/.

Regras
Não inferir. Não assumir finalidade, base legal, prazo, processador.
Perguntar antes de sugerir.
Sem frase genérica. Sem "melhorar serviço" sem especificar dado e base.
Saída marcada como minuta técnica quando envolver jurídico, fiscal ou LGPD. Não substitui advogado.
Formato de correção: <texto> linha analisada, // correção. Sem parágrafo longo sobre premissa errada.
Copy limpo, mínimo, funcional. Sem "não é X, é Y". Sem estética de IA.
Como usar
git clone https://github.com/seu-usuario/skills.git
Escolher skill em /skills/<nome>/SKILL.md
Copiar conteúdo para o agente ou referenciar como instrução
Responder Fase 0 e Fase 1
Receber entrega da Fase 3
Como criar nova skill
mkdir -p skills/nova-skill/examples
touch skills/nova-skill/SKILL.md
Preencher SKILL.md conforme padrão. Adicionar 1 exemplo válido e 1 inválido em examples/. Abrir PR.

Primeira skill
politica-uso-dados: gera política de privacidade a partir da operação real. Inclui 3 cláusulas críticas: base legal específica por finalidade, controlador x operador + processadores, retenção e destino no cancelamento / exclusão / fim de contrato.
Licença
MIT. Ver LICENSE.

Contribuição
Ver CONTRIBUTING.md. PRs exigem checklist de validação preenchido.

