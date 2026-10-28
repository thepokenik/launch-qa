# Validação em uma landing local / Validation on a local landing page

Em 28 de outubro de 2026, a revisão da `launch-qa` com SHA-256 `85FBE7F45582D8016109D994D4CA2F90B8238A8E1442A8B2AB52978237761408` foi aplicada a uma landing em ambiente local. O nome do produto e os caminhos de evidências privadas foram omitidos. Este resumo se baseia no relatório da execução; capturas e logs não estão incluídos.

On October 28, 2026, the revision of `launch-qa` identified by the SHA-256 above was applied to a locally served landing page. The product name and private evidence paths are omitted. This summary is based on the execution report; screenshots and logs are not included.

## Escopo e resultado

O primeiro sucesso acordado era sair da página inicial, encontrar um guia e abrir uma seção útil para decidir onde sair. Os cinco perfis simulados alcançaram esse critério. O guia fornecia orientações gerais; escolher um estabelecimento específico não foi testado.

As jornadas começaram em sessões isoladas. O ambiente relatado foi Windows, Microsoft Edge 156.0.4314.50 em modo headless, Node 24.20.0 e Playwright CLI 0.1.22. O perfil móvel usou viewport de 375×812 e emulação de rede configurada via CDP: 400 ms de latência e 500 Kibit/s em cada direção. Isso é uma aproximação, não uma medição de rede física.

| Perfil | Resultado relatado | Limite de cobertura |
|---|---|---|
| Impaciente | Abriu o guia e uma seção de bares e restaurantes. | O CTA mais destacado não foi explorado nesse perfil. |
| Cético | Consultou informações sobre preço, localizou termos e privacidade e abriu uma seção do guia. | Não abriu os documentos externos. |
| Mobile | Abriu uma seção do guia com viewport e rede emulados. | Não representa um dispositivo ou conexão física. |
| Leitura literal | Abriu uma seção do guia. | O perfil foi adaptado para interface em português; não houve participante humano. |
| Breaker | Testou rota inválida, voltar e cliques duplos e abriu uma seção do guia. | Não havia campo de texto para testar entradas inválidas. |

Não houve defeitos de produto confirmados nos percursos. Uma possível dificuldade com vocabulário foi registrada como hipótese, sem incompreensão reproduzida. Em uma solicitação posterior de correções, não se identificou defeito confirmado aplicável; nenhuma correção foi feita e nenhuma jornada foi repetida. Essa decisão exercitou o limite de escopo da skill, mas não valida sua implementação e verificação de correções reais.

Não foram testados conteúdo legal externo, produção, cadastro, aplicativo nativo ou escolha de um estabelecimento. Os resultados são simulações, não prevalência de usuários nem avaliação de prontidão para lançamento.

## Evidências e reprodução

O relatório original registra passos, snapshots, capturas e metadados. Os 95 arquivos do manifesto foram conferidos por tamanho e SHA-256 nesta preparação, sem divergências; isso verifica a integridade dos arquivos, não repete os testes. Nenhuma captura foi adicionada aqui: antes de compartilhá-las, revise seu conteúdo e remova informações privadas.

Esta execução sustenta a aplicação da revisão atual à auditoria descrita, neste ambiente e escopo. Abandono no primeiro erro de produto, priorização de defeitos compartilhados e correções com reteste ainda não foram exercitados empiricamente.

