# NovelFlix — Plano técnico e produto V0

## Visão

OTT de microdramas com episódios verticais de curta duração, foco inicial em PWA/H5, catálogo editorial e monetização por desbloqueio de episódios ou assinatura.

## Decisão proposta

1. Manter atlashub-digital/novelflix como repositório original, não fork de um clone Netflix.
2. Fazer uma prova de conceito ISOLADA do MiniTV v1.0.0 (https://github.com/xuliang2024/minitv), licenciado MIT, sem copiar ainda a plataforma inteira para main.
3. Comparar custos e qualidade com um front-end Next.js próprio. Decidir arquitetura final a partir de testes verificáveis.
4. Reutilizar contratos e conceitos da GWD somente após revisão das versões e permissões; não acoplar bases de dados produtivas.

## Superfícies do produto MVP

| Superfície | Escopo MVP |
|---|---|
| Descobrir | Catálogo, categorias, destaques e série detalhada |
| Player 9:16 | HLS, controlo de episódio, próximas partes e legendas |
| Conta | Login, favoritos, continuar a assistir |
| Monetização | 3 episódios de amostra; entitlement para seguintes; no piloto, pagamento simulado |
| CMS | CRUD série/temporada/episódio; publicação programada e media com direitos verificados |
| Analytics | Início, conclusão, episódio seguinte, abandono, conversão e custo de transmissão |

## Arquitectura candidata

- PWA/H5 responsiva primeiro; apps Flutter apenas depois de validar retenção.
- API de catálogo e sessões com base PostgreSQL isolada.
- Ingestão/transcodificação HLS separadas do servidor web: avaliar Bunny Stream ou R2 + serviço de transcode; não enviar ficheiros grandes por Node.
- CDN com tokenização do playback; a API deve verificar a titularidade do acesso ANTES de emitir URLs de reprodução; expiração curta.
- ARO como futura fonte de verdade para checkout, pagamento, reembolso e entitlements, com idempotência.
- Quotas, auditoria, logs e observabilidade; testes de BOLA/IDOR, pagamentos e URLs com acesso vencido.
- Media e segredos sempre fora do GitHub. Conteúdo comercial só com direitos explícitos.

## Prova de conceito MiniTV

Preparar deployment segregado, com frontend H5, admin, FastAPI, PostgreSQL, Redis e BUNNY_MODE=fake; depois adicionar 1-2 vídeos originais de teste com CDN real. Usar valores de demonstração e autenticação de laboratório, nunca credenciais produtivas. Não executar scripts do upstream sem revisão.

Critérios de saída: (a) catálogo administrável; (b) reprodução 9:16 e troca automática; (c) 3 episódios gratuitos + desbloqueio do 4.º; (d) sessão e progresso; (e) limites de acesso; (f) custos de streaming aferidos; (g) testes do upstream e próprios passam.

## Fases

**Fase 0 — Auditoria:** dependências, licenças, riscos, saúde dos testes, disponibilidade de recursos na VPS.
**Fase 1 — UX:** definir design Atlas, mapa de ecrãs e adaptar dados de demonstração.
**Fase 2 — PoC:** subir MiniTV em laboratório isolado e confirmar os fluxos principais.
**Fase 3 — Produto:** escolher base final; implementar integração ARO, segurança e observabilidade.
**Fase 4 — Beta:** catálogo licenciado, testes de tráfego, analytics e monetização.

## Questões de decisão

- Fork operacional do MiniTV num laboratório separado ou importação seletiva de módulos MIT após PoC.
- Caminho comercial: assinatura vs desbloqueio de temporada vs crédito por episódio.
- Modelo de produção de conteúdos: direitos licenciados, originais próprios ou coproduções.
- Marca final: NovelFlix é nome de trabalho e requer verificação de disponibilidade.

## Fora do escopo imediato

Apps móveis publicadas, anúncios recompensados, royalties automáticos, IA geradora de novelas, infraestrutura de transcoding própria e DRM enterprise.
