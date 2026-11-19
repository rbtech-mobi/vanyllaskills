# vanyllaskills

Especificações operacionais em Markdown para agentes de IA executarem fluxos de engenharia de release, conformidade LGPD e publicação de aplicativos na App Store e Google Play com validação de entrada, bloqueio de inferência e saída auditável.

## Estrutura do repositório

    .
    ├── auditoria-binario-pre-review
    ├── captura-de-telas-para-lojas
    ├── checklist-lojas-privacidade
    ├── conta-revisao-lojas
    ├── politica-dados-mobile
    ├── política-dados
    ├── release-notes-metadados
    └── README.md

## Catálogo de skills

### Conformidade, Privacidade e Lojas
* **`politica-dados-mobile`**: gera minuta técnica de Política de Privacidade para aplicativos iOS e Android (LGPD, Marco Civil da Internet, Resoluções ANPD e regras da Apple/Google), cobrindo permissões de hardware/SO, SDKs, Ads/ATT, IAP/antifraude, uso de IA e exclusão de conta in-app.
* **`política-dados`**: gera minuta técnica de Política de Privacidade para aplicações SaaS Web operando no Brasil, mapeando base legal por finalidade, matriz de Controlador/Operador/Subprocessadores e regras de retenção e descarte.
* **`checklist-lojas-privacidade`**: traduz o inventário técnico de dados e SDKs do aplicativo nas respostas exatas exigidas pelos formulários **App Privacy (Nutrition Labels)** da App Store Connect e **Data Safety** do Google Play Console.

### Engenharia de Release e Submissão
* **`auditoria-binario-pre-review`**: audita manifestos (`Info.plist`, `PrivacyInfo.xcprivacy`, `AndroidManifest.xml`), permissões sensíveis, `targetSdkVersion` e configurações de build antes do upload do `.ipa` ou `.aab`.
* **`captura-de-telas-para-lojas`**: gera comandos nativos via CLI (`adb` e `xcrun simctl`) para captura de screenshots e gravação de vídeos de tela com Demo Mode ativo e pós-processamento (`sips`/`ffmpeg`) nas resoluções exigidas pelas lojas.
* **`release-notes-metadados`**: converte `git log` e changelogs técnicos em notas de lançamento (*What's New*) e textos de ficha de loja dentro dos limites rígidos de caracteres e diretrizes editoriais da Apple e Google.
* **`conta-revisao-lojas`**: estrutura credenciais de demonstração, mecanismos de bypass de 2FA/OTP e roteiros de navegação para os revisores validarem áreas logadas, assinaturas e recursos restritos (*App Review Information* / *App Access*).

## Anatomia padrão das skills

Cada arquivo de skill segue uma máquina de estados determinística em 4 fases:

* **Fase 0 — Verificação de escopo:** valida pré-condições mínimas do ambiente ou produto antes de iniciar. Interrompe se faltar dado crítico.
* **Fase 1 — Mapeamento técnico:** questionário fechado por cláusula crítica. Proíbe inferência de finalidade, base legal, permissão ou configuração não declarada.
* **Fase 2 — Checklist de validação:** verificação cruzada antes da compilação da entrega. Bloqueia placeholders e frases genéricas.
* **Fase 3 — Formato de saída:** entrega estruturada em Markdown limpo pronto para uso operacional ou revisão jurídica.

## Regras globais de execução

1. **Zero inferência:** o agente nunca assume dados técnicos, legais ou operacionais ausentes. Na falta de informação, pergunta objetivamente antes de gerar saída.
2. **Bloqueio de texto genérico:** expressões vagas sem vínculo técnico ou normativo são descartadas.
3. **Escopo de minuta técnica:** entregas envolvendo LGPD e obrigações regulatórias são emitidas explicitamente como minutas técnicas para revisão jurídica formal.
4. **Formato de correção inline:** apontamentos pontuais de revisão seguem o padrão:

    <trecho analisado> // correção objetiva

## Como usar

1. Abra o arquivo da skill desejada neste repositório e clique em **Raw** para copiar o conteúdo puro.
2. Injete o texto no *System Prompt*, *Custom Instructions* ou arquivo de regras do seu agente/IDE.
3. Responda às verificações da **Fase 0** e ao mapeamento da **Fase 1** para liberar o artefato final da **Fase 3**.

## Adicionando uma nova skill

1. Crie um arquivo na raiz em `kebab-case` ASCII (sem acentos ou caracteres especiais).
2. Estruture o documento com as seções obrigatórias: **Descrição**, **Princípio operacional**, **Proibições**, **Fluxo obrigatório (Fases 0 a 3)**, **Estilo e formato de revisão** e **Referências técnicas**.
3. Abra um Pull Request validando a ausência de placeholders e consistência com o catálogo.
