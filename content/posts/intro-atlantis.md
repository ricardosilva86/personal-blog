+++
date = '2025-09-04T13:40:42+02:00'
draft = true
title = 'Automatizando Terraform com GitOps: Um guia para iniciantes com Atlantis'
+++

Embora muitos de nós já tenhamos nos livrado de rodar `terraform apply` localmente, infelizmente outros ainda não encontraram uma forma de se livrar desse karma. Seja por falta de conhecimento ("as vezes o indivíduo está nas drogas"), seja por restrições de orçamento (Terraform Cloud custa algo em torno de $0.10USD/recurso gerenciado 🤑). Qualquer que seja desses problemas, vou tentar te ajudar a resolver isso e sair dessa vida miserável 😅.  

A forma mais simples e barata que vou te apresentar é usando o [Atlantis](https://www.runatlantis.io/).

> Atlantis é uma ferramenta para colaboração entre colegas de time [...]  
> A principal funcionalidade do Atlantis é permitir/possibilitar que desenvolvedores  
> possam executar `plan` e `apply` diretamente do Pull Request.  
> Assim dando visibilidade e controle sobre a infraestrutura como código.  
> Link para o post [aqui](https://www.runatlantis.io/blog/2017/introducing-atlantis.html)  

Atlantis brilha em cenários com muitos devs/devops/platform engineers trabalhando sobre a mesma base de código e com um volume de mudanças onde os colaboradores acabam "pisando" nos dedos uns dos outros, ou seja, num ambiente dinâmico de qualquer empresa minimamente estruturada nos dias de Cloud, é essa a realidade.

Soluções comuns são pipelines de CI/CD como Gitlab ou Github Actions, que geralmente não são baratos em casos de times um pouco maiores. Gitlab custa algo em torno de 29 trumps por dev no time no plano mais básico e o GitHub vai custar algo em torno de 21 trumps por dev. Sim, eu sei que ambos tem free tier, mas geralmente é bem capenga e capado, ou seja, poucos minutos de CI/CD e faltando features essenciais. Se você está em um time onde há alguma ferramenta de CI/CD já implementada, acredito que esse post será mais instrutivo do que prático do ponto de vista de mudar a ferramenta de CD de IaC -- não faz sentido mudar para o Atlantis se seu time já tem uma solução pronta e em uso.

Bom, vamos ao que interessa, "Atlantis ao resgate!"