# Benchmark GitHub — NovelFlix

Investigação realizada em 2026-11-07. Dados e licenças podem mudar; validar sempre no commit utilizado.

| Repositório | Situação / stack | Licença identificada | Decisão |
|---|---|---|---|
| [xuliang2024/minitv](https://github.com/xuliang2024/minitv) | Microdramas verticais; H5 React, Flutter, FastAPI, PostgreSQL, Redis, Bunny Stream, Stripe; testes | MIT | Candidato principal de PoC |
| [jason-liu22/netflix-clone-react-typescript](https://github.com/jason-liu22/netflix-clone-react-typescript) | React/TS com interface TMDB, código atualizado pela última vez em 2024 | Sem LICENSE encontrado no root/tree | Referência visual apenas |
| [burakorkmez/mern-netflix-clone](https://github.com/burakorkmez/mern-netflix-clone) | Tutorial MERN, TMDB, auth e trailers | Sem LICENSE encontrado | Não copiar para produto |
| [spring-cloud/spring-cloud-netflix](https://github.com/spring-cloud/spring-cloud-netflix) | Ferramentas Java para microserviços, NÃO streaming de vídeo | Apache-2.0 | Fora do escopo |
| [sadmann7/netflx-web](https://github.com/sadmann7/netflx-web) | Next.js 13, Prisma, NextAuth, Stripe; código de 2024 | Sem LICENSE encontrado | Referência de UX / subscrição |
| [AnuragKun/StreamFlix](https://github.com/AnuragKun/StreamFlix) | Java Spring/Kafka/S3/HLS; stack pesada para MVP | Sem LICENSE encontrado | Referência arquitetural, não base |
| [alokp0274/streamflix](https://github.com/alokp0274/streamflix) | React/TS, HLS real, PWA, catálogo mockado e testes smoke | Verificar licença de cada ativo/dependência; repositório declara MIT | Referência de player e PWA |

## Notas sobre MiniTV

- O mantenedor declarou o repositório público congelado em 2026-11-05; atualizações passam a ser privadas. Exigirá manutenção própria.
- Existem diretórios backend/tests (dezenas de testes), frontends Web/H5/Admin e app Flutter; isso NÃO substitui auditoria ou teste real do deploy.
- Foi identificada a API de desbloqueio, a chamada H5 e o componente UnlockSheet. Documentação de outubro que dizia não haver frontend para moedas está desatualizada nesse ponto.
- Alguns benefícios publicitados na plataforma, como downloads e ausência de anúncios, são descritos em documentação histórica como incompletos ou não implementados; conferir código e interface antes de vender.
- Para a Atlas será necessário adaptar Bunny/Stripe, modelo de pagamentos ARO, português-BR, design, segurança, conteúdo e conformidade.
- A licença MIT permite aproveitamento comercial preservando os avisos legais e auditando dependências, recursos visuais e media.

## Critério decisivo

Não escolher por estrelas ou semelhança com a Netflix. Escolher por operação funcional: catálogo próprio, HLS vertical, progressão, restrição por episódio, pagamentos e custos.
