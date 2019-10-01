---
title: Criando Merge Requests
subtitle: Guia de como criar corretamente um merge request para o projeto no gitlab
comments: false
date: 2019-08-29
---
Os _merge requests_ são como você integra alterações separadas que você fez em uma _branch_ do projeto.

1. Antes de começar, você já deveria ter passado pelo guia de [Como contribuir?](https://pluggedcomputing.gitlab.io/post/contribuitions/making_changes/).
2. Vá para o projeto em que deseja mesclar suas alterações e clique em **Merge requests**.
3. Clique em **New merge request** no lado direito da tela.
4. A partir daí, você tem a opção de selecionar a branch de origem e a de destino com o qual deseja comparar. A branch de destino deve ser sempre a _'develop'_.
![merge request exemple](https://docs.gitlab.com/ee/gitlab-basics/img/merge_request_select_branch.png)
5. Quando estiver pronto, clique no botão **Compare branches and continue**.
6. Adicione, um título e uma descrição. Selecione, um usuário para revisar seu _merge request_,  o marco atual e um rótulos de merge request à sua solicitação de mesclagem.
![merge request exemple](https://docs.gitlab.com/ee/gitlab-basics/img/merge_request_page.png)
7. Quando estiver pronto, clique no botão **Submit merge request**.

Sua solicitação de mesclagem estará pronta para ser analisada, aprovada e mesclada

### Referência
* How to create a merge request. Disponivel em: <https://docs.gitlab.com/ee/gitlab-basics/add-merge-request.html>