# launch-qa

A reusable launch QA skill that simulates five first-time user journeys, captures friction, prioritizes issues, and verifies fixes in a real browser.

Use esta skill antes do lançamento ou após mudanças na experiência inicial de uma aplicação web. Ela acompanha a jornada da página de entrada até um primeiro resultado de valor verificável, reúne evidências e prioriza problemas pelo número de perfis simulados afetados. Correções são feitas somente quando solicitadas e quando há acesso ao código; uma auditoria por si só não altera o produto.

## Perfis

- **Impatient user:** lê superficialmente, escolhe o primeiro botão plausível e abandona no primeiro erro.
- **Skeptical user:** procura preços, termos e privacidade antes de se cadastrar.
- **Mobile user:** usa viewport de 375 px e emulação de conexão lenta 3G, quando disponível.
- **Non-native English speaker:** interpreta as instruções literalmente, sem presumir conhecimento que a interface não fornece.
- **Breaker:** experimenta entradas inválidas, navegação para trás e cliques duplos dentro dos limites do ambiente de teste.

## Requisitos

- Acesso à aplicação e, para correções, ao código correspondente; instruções e permissões para iniciar ou acessar o ambiente.
- Um navegador real controlável pelo agente, com sessões isoladas e, quando disponíveis, captura de tela, viewport configurável e emulação de rede.
- Uma URL de entrada, um critério verificável de primeiro sucesso e contas ou dados de teste necessários. Prefira ambientes e dados de teste para operações com efeitos externos.
- Subagentes são opcionais: podem executar as jornadas quando estiverem disponíveis e forem solicitados ou autorizados. Sem eles, o agente executa jornadas separadas.

## Instalação e uso

Copie o diretório deste repositório para o diretório de skills do seu agente, com o nome `launch-qa`. No Codex, o caminho habitual é `~/.codex/skills/launch-qa/`; o arquivo `SKILL.md` deve ficar diretamente dentro dele. Por exemplo, a partir do diretório que contém este repositório, no macOS ou Linux:

```sh
mkdir -p ~/.codex/skills
cp -R ./launch-qa ~/.codex/skills/launch-qa
```

No PowerShell, a partir do mesmo diretório:

```powershell
New-Item -ItemType Directory -Force "$HOME\.codex\skills" | Out-Null
Copy-Item -Recurse .\launch-qa "$HOME\.codex\skills\launch-qa"
```

Se já existir uma skill nesse destino, revise-a antes de substituir seus arquivos. Reinicie ou recarregue o agente se necessário para descobrir a skill. Invoque-a pelo nome em uma solicitação, por exemplo:

```text
Use $launch-qa para auditar https://example.com em um ambiente de teste.
O primeiro sucesso é criar um projeto de teste e vê-lo listado no painel.
Registre os problemas e as evidências; não altere o produto.
```

Para incluir correções, peça explicitamente que o agente corrija os problemas confirmados e repita as jornadas. Forneça acesso, contas e dados de teste quando forem necessários e não puderem ser obtidos do projeto.

## Limitações

Os perfis são simulações: sua contagem não é uma amostra estatística e não substitui pesquisa com pessoas reais. As capacidades de navegador, captura, emulação, modelos e delegação dependem do ambiente. Condições indisponíveis e jornadas bloqueadas devem ser relatadas; uma correção só é considerada verificada após observação ou teste posterior. Evite dados sensíveis desnecessários nas evidências.
