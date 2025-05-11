+++
date = '2025-05-11T10:26:05+02:00'
draft = true
title = 'OIDC vs Workload Identity Federation com Vault e GCP'
tags = ['vault','oidc','wif','gpc','cloud']
+++
Recentemente começamos a implementar uma solução de segurança um pouco mais robusta ao invés do velho modelo de _service account_ em _god-mode_ (uma conta com acesso total a tudo), onde vamos implementar um modelo baseado em **least privileged access**. Juntamente com essa decisão, tivemos que decidir o que exatamente iriamos usar, OIDC^1^ ou WIF^2^ (_Workload Identity Federation_).

Então resolvi destrinchar o que significa adotar cada um desses modelos, o que está por trás deles e seus principais conceitos. No meio disso tudo, vou tentar demonstrar como implementar ambos usando **Hashicorp Vault** no _Google Cloud_.

## O Problema 🧨

Lembro quando trabalhava numa grande empresa de eCommerce no Rio de Janeiro (remotamente) e sempre que alguém novo chegava no time nosso _onboarding_ era entregar uma cópia do arquivo do Keepass^3^ para a pessoa com a senha do arquivo. A grosso modo, essa é uma implementação mais segura e rudimentar dos _password managers_ (gerenciadores de senhas) modernos como Lastpass, 1Password, etc.  

Imagina o problema se uma dessas pessoas fosse hackeada e esse arquivo vazasse. Um conjunto de usuários e senhas com altos privilégios estariam nas mãos dos hackers e os danos poderiam ser devastadores.  

Hoje em dia já não temos mais (ou pelo menos espero que não) arquivos do Keepass por aí com todas as senhas da ++infraestrutura++, mas o problema existe de outra forma: **_service account_ em _god-mode_**.  

Basicamente, por conveniência, os administradores de sistemas criam uma (ou duas: produção e dev) _service account_ com privilégios de **admin** e essa conta é então usada em todos os _pipelines_ de infraestrutura. Os danos seriam igualmente devastadores caso as credencias dessa conta caiam em mãos erradas.

## As diferentes soluções 🩺

Hoje me dia temos ambientes predominantemente em Cloud e normalmente os provedores tentam nos ajudar ao oferecer soluções para autenticação e autorização. Ainda assim é possível que escolhamos a pior alternativa, por exemplo, as _service accounts_ com muito privilégio e alto risco em caso de vazamento das credenciais (chave, _client id_ e _secret id_).

Dentre as diversas soluções possíveis temos algumas que se destacam como o **OIDC** e o **Workload Identity Federation**. Cada um tem seus casos de uso e é isso que vamos investigar nesse post.

### OIDC

Antes de entender o OIDC, precisamos entender o _framework_ por trás dele: o **OAuth 2.0**. Provavelmente você já está acostumado com esses fluxos, só não tinha relacionado o nome à pessoa ;). É possível que você esteja se perguntando: "OIDC e OAuth 2.0 são para autenticação entre aplicativos e as redes sociais, o que raios isso tem a ver com Cloud?". Calma padawan, já explico, mas primeiro vamos entender os conceitos importantes para podermos continuar a jornada.

#### Conceitos-chave


### Workload Identity Federation

## Vault como OIDC Provider

## Vault com WIF

## Referencias
[1: OIDC](https://openid.net/developers/specs/)  
[2: Workload Identity Federation](https://cloud.google.com/iam/docs/workload-identity-federation)  
[3: Keepass](https://keepass.info/)  
