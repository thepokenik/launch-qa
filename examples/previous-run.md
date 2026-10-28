# Caso anterior anonimizado / Anonymized earlier case

Este caso resume uma execução anterior ao lançamento da skill, baseada no prompt que inspirou `launch-qa`. Os resultados abaixo vêm do relatório consolidado e dos registros de uma jornada e de seu reteste em outro projeto; **não validam a versão atual da skill**. O nome do projeto, endereços, identificadores e dados de contas foram omitidos. Capturas e logs originais não são incluídos nesta versão pública.

This case summarizes an earlier run of the prompt that inspired `launch-qa`. It draws on a consolidated report and one persona's original and retest records; **it does not validate the current skill**. Project names, addresses, identifiers and account data have been removed. Original screenshots and logs are not included.

## Contexto e cobertura

Em 27–28 de outubro de 2026, cinco perfis simulados percorreram uma aplicação web em sessões Chromium isoladas, com backend e dados de teste locais. O relatório registra uma nova rodada após mudanças. Na jornada detalhada abaixo, a sessão de reteste foi reaberta com a mesma conta sintética; portanto, esse reteste não demonstra a condição de conta nova exigida pela revisão atual da skill.

O objetivo operacional era ativar um teste e registrar um primeiro serviço. O relatório informa que cadastro, confirmação de e-mail e criação de organização foram alcançados pelos cinco perfis após as mudanças, mas **a ativação e o primeiro serviço não foram verificados**: a configuração local de cobrança de teste estava indisponível e o catálogo retornava erro. Esses marcos intermediários não comprovam o sucesso operacional.

## Um achado: nome de organização vazio

- **Perfil:** breaker, em navegador real.
- **Antes:** depois de autenticar, abriu a criação de organização, informou dois espaços como nome e um identificador válido, e enviou o formulário. A organização foi criada e apareceu sem nome visível.
- **Esperado:** rejeitar um nome sem caracteres visíveis.
- **Impacto observado:** uma organização sem nome visível dificultava sua identificação. O relatório consolidado atribui o achado a um dos cinco perfis simulados; isso não é uma estimativa de prevalência.
- **Depois:** o registro do reteste relata que dois espaços foram rejeitados pela interface com uma mensagem de validação. O mesmo registro esclarece que a validação do servidor não foi testada diretamente nessa sessão.
- **Evidência original:** os registros de antes e depois referenciam capturas da organização sem nome e da rejeição. Elas permanecem no projeto de origem e não foram revisadas ou reproduzidas aqui.

O relatório consolidado também registra mudanças no formulário e no backend. A observação de interface acima comprova apenas o comportamento relatado no reteste, não todos os caminhos de validação. As mudanças pertenciam ao estado local de trabalho da época, sem release ou deploy comprovado.

## Para uma demonstração pública

Revisar o conteúdo das capturas originais, remover dados pessoais, endereços e identificadores e confirmar que podem ser compartilhadas. Sem essa revisão, use este resumo textual como relato histórico, sem apresentar imagens ou resultados adicionais. A execução completa da versão atual continua pendente.

