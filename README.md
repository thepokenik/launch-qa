# launch-qa

[Português](#português) · [English](#english)

## Português

`launch-qa` orienta um agente a auditar cinco jornadas simuladas de primeiro uso, da entrada de uma aplicação web até um primeiro resultado de valor verificável. As jornadas usam um navegador real, registram evidências e agrupam atritos por prioridade. Quando solicitado e com acesso ao código, o agente também pode corrigir problemas confirmados e verificar as alterações.

### Perfis simulados

- **Impaciente:** escolhe rapidamente a primeira opção plausível e abandona no primeiro erro.
- **Cético:** procura preços, termos e privacidade antes de tentar o objetivo.
- **Mobile:** usa viewport de 375 px e emulação de 3G lento, quando disponível.
- **Falante não nativo de inglês:** interpreta as instruções literalmente, sem presumir conhecimento ausente da interface.
- **Breaker:** experimenta entradas inválidas, voltar e cliques duplos dentro dos limites do ambiente de teste.

Cada jornada começa isolada e usa o mesmo critério de sucesso. A contagem de perfis afetados descreve apenas as simulações que chegaram ao passo em questão; não estima prevalência entre usuários reais.

### Requisitos

- Um agente que aceite skills, acesso a um navegador real controlável e sessões isoladas; a lógica da skill não exige Playwright. Capturas, viewport e emulação de rede dependem da ferramenta disponível.
- URL de entrada, acesso autorizado, dados e contas de teste quando necessários e um primeiro sucesso observável. Para correções, acesso ao código. Evite efeitos externos em produção.
- Para o caminho com `playwright-cli` abaixo: Node.js 20 ou superior, npm e Git. Instale o navegador solicitado pela ferramenta se necessário.

### Instalação

Requer Node.js 22.20 ou superior e Git para o instalador de skills. A skill é distribuída diretamente pelo GitHub; não exige publicar um pacote próprio no npm.

Instalação interativa (escolha o agente e a skill):

```sh
npx skills add thepokenik/launch-qa
```

Para instalar somente a `launch-qa` no Codex, disponível em todos os projetos:

```sh
npx skills add thepokenik/launch-qa --skill launch-qa --agent codex --global
```

Para instalar apenas no projeto atual, execute o comando na pasta desse projeto e remova `--global`. No PowerShell, use `npx.cmd` se a política de execução bloquear `npx.ps1`.

Confira as skills disponíveis antes de instalar:

```sh
npx skills add thepokenik/launch-qa --list
```

Depois da instalação global, confira com `npx skills list --global` e reinicie o Codex para carregar a skill. Para atualizar, use `npx skills update --global`; esse comando verifica as skills globais instaladas. A instalação pelo nome do repositório acompanha sua branch padrão.

A descoberta da skill foi verificada com `--list` tanto na pasta local quanto no repositório GitHub. Isso valida o reconhecimento do pacote, não uma auditoria nem a instalação completa no ambiente de cada usuário. Consulte a [documentação do instalador](https://github.com/vercel-labs/skills/blob/main/docs/commands.md).

### Navegador opcional: playwright-cli

A instalação acima fornece as instruções da auditoria. É necessário também um navegador real controlável, com sessões isoladas. Se o agente já tiver uma ferramenta compatível, use-a. Para configurar o caminho com Playwright CLI:

```sh
npm install -g @playwright/cli@0.1.22
playwright-cli install --skills=agents -g
playwright-cli --version
```

Revise uma instalação existente antes de substituí-la. O comando do Playwright instala sua skill global em `~/.agents/skills/playwright-cli`; instale o navegador solicitado pela ferramenta se necessário. A disponibilidade de navegadores e dependências do sistema varia conforme o ambiente. Consulte a [instalação do Playwright CLI](https://github.com/microsoft/playwright/blob/main/docs/src/getting-started-cli.md) e a [instalação da skill Playwright](https://playwright.dev/agent-cli/skills).

### Exemplos de solicitação

Somente auditoria (substitua os campos pelo seu ambiente de teste):

```text
Use $launch-qa e $playwright-cli para auditar <URL_DE_TESTE>.
O primeiro sucesso é criar um projeto de teste e vê-lo no painel.
Use somente os dados e a conta de teste fornecidos. Registre evidências e
priorize os atritos; não altere o produto.
```

Auditoria com correções:

```text
Use $launch-qa e $playwright-cli para auditar <URL_DE_TESTE>.
O primeiro sucesso é criar um projeto de teste e vê-lo no painel.
O código está neste repositório. Use somente dados e conta de teste;
corrija os problemas confirmados dentro do escopo e verifique cada correção,
repetindo as jornadas afetadas conforme necessário. Relate o que não foi retestado.
```

### Entregas, evidências e limites

O resultado inclui desfecho e cobertura dos cinco perfis, achados agrupados com passos para reproduzir, esperado e observado, impacto, gravidade, estado e evidências disponíveis. As prioridades consideram quantos perfis chegaram ao passo e observaram o problema; bloqueios graves são destacados. Se houver correções solicitadas, o relatório distingue antes, depois, itens não retestados e resultados pendentes. Veja a [validação em landing local](examples/local-landing-validation.md) e o [caso anterior anonimizado](examples/previous-run.md).

Perfis simulados não substituem QA, acessibilidade especializada ou pesquisa com pessoas reais. Evidências podem conter dados sensíveis e devem ser revisadas antes de compartilhar. Sem navegador, acesso ou condições necessárias, a jornada é bloqueada ou parcial; leitura de código não equivale a teste no navegador.

O prompt que inspirou a skill foi usado anteriormente em outro projeto com `playwright-cli`; esse caso não valida a versão revisada. A revisão atual foi executada em uma landing local no Windows, com Node 24.20.0, Playwright CLI 0.1.22 e Edge 156 headless: cinco perfis atingiram o critério de sucesso definido. O escopo e os limites estão na [validação](examples/local-landing-validation.md). Não houve defeitos confirmados, portanto a implementação de correções e seus retestes não foram exercitados. Outros sistemas, agentes, navegadores e ferramentas de automação não foram testados para esta revisão.

### Licença

[MIT](LICENSE).

## English

`launch-qa` guides an agent through five simulated first-time journeys, from a web app's entry point to a verifiable first success. It uses a real browser, records evidence and prioritizes friction. When requested and given code access, the agent can also fix confirmed issues and verify the changes.

### Simulated personas

- **Impatient:** skims, chooses the first plausible option and abandons at the first error.
- **Skeptical:** looks for pricing, terms and privacy before attempting the goal.
- **Mobile:** uses a 375 px viewport and slow 3G emulation when available.
- **Non-native English speaker:** interprets instructions literally without assuming knowledge absent from the interface.
- **Breaker:** tries invalid input, back navigation and double clicks within the test environment's limits.

Each journey starts isolated and uses the same success criterion. Affected-persona counts describe only simulated journeys that reached the step; they do not estimate real-user prevalence.

### Requirements and installation

The core skill needs a compatible agent, access to a controllable real browser with isolated sessions, an authorized test URL, a measurable first success, and any necessary test accounts or data. Code access is needed for fixes. Avoid external effects in production. Playwright is optional for the core workflow; screenshots, viewport and network emulation depend on the chosen tool.

Install Node.js 22.20+ and Git, then run:

```sh
npx skills add thepokenik/launch-qa --skill launch-qa --agent codex --global
```

Omit `--global` to install in the current project. Use `npx.cmd` in PowerShell if execution policy blocks `npx.ps1`. Verify discovery with `npx skills add thepokenik/launch-qa --list`, inspect global installs with `npx skills list --global`, and restart Codex. The repository's default branch is used. Local and GitHub discovery were verified; a full install in each user's environment was not. See the [installer reference](https://github.com/vercel-labs/skills/blob/main/docs/commands.md).

Browser tooling is separate. If needed, follow the [optional Playwright setup above](#navegador-opcional-playwright-cli), which pins the CLI to `0.1.22`. Review existing installations before replacing them.

### Example prompts

Audit only:

```text
Use $launch-qa and $playwright-cli to audit <TEST_URL>.
First success is creating a test project and seeing it on the dashboard.
Use only the supplied test account and data. Record evidence and prioritize
friction; do not change the product.
```

Audit and fixes:

```text
Use $launch-qa and $playwright-cli to audit <TEST_URL>.
First success is creating a test project and seeing it on the dashboard.
The code is in this repository. Use only test data and the test account;
fix confirmed in-scope problems and verify each fix, repeating affected
journeys as needed. Report what was not retested.
```

### Deliverables and limitations

Expect outcomes and coverage for all five personas, grouped findings with reproduction steps, expected and observed behavior, impact, severity, status and available evidence. Priorities account for the personas that reached and observed each issue, with severe blockers highlighted. When fixes are requested, results distinguish before, after, not rerun and unresolved. See the [local landing validation](examples/local-landing-validation.md) and [anonymized earlier case](examples/previous-run.md).

Simulations do not replace QA, specialist accessibility evaluation or research with real people. Review evidence for sensitive data before sharing. Missing browser access or capabilities means blocked or partial coverage; source inspection is not a browser test.

The prompt that inspired the skill was previously used with `playwright-cli` on another project; that case does not validate the revision. The current revision was run against a local landing page on Windows with Node 24.20.0, Playwright CLI 0.1.22 and headless Edge 156: all five personas reached the defined success criterion. See the [validation](examples/local-landing-validation.md) for scope and limitations. No product defects were confirmed, so implementing and retesting fixes was not exercised. Other operating systems, agents, browsers and automation tools have not been tested for this revision.

### License

[MIT](LICENSE).
