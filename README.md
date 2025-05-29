Repositório criado para a prova prática.

## Etapas que consegui concluir:

### Etapa 1: Repositório GitHub
Criei o repositório `Prova_Devops` e clonei localmente.

### Etapa 2: Projeto FastAPI
Implementei uma API  com três endpoints:
- `/`: retorna mensagem "Hello World"
- `/square/{x}`: retorna o quadrado de um número
- `/double/{x}`: retorna o dobro de um número

Corrigi o erro do cálculo do quadrado no endpoint `/square/{x}` e fiz testes com `pytest`.

### Etapa 3: Commits semânticos
Usei mensagens de commit seguindo o padrão semântico, exemplo:  
`fix: corrigido cálculo do quadrado em /square`

### Etapa 4: Docker
Criei um `Dockerfile` e `requirements.txt` para gerar a imagem da aplicação.

### Etapa 5: GitHub Actions (CI/CD)
Configurei o workflow para:
- Executar os testes
- Fazer build da imagem
- Fazer push para o DockerHub

Adicionei as secrets `DOCKER_USERNAME` e `DOCKER_PASSWORD` no repositório.

### Etapa 6: Kubernetes com Kustomize
Criei os manifests:
- `deployment.yaml`
- `service.yaml`
- `kustomization.yaml`

Todos na pasta `k8s/base`.

### Etapa 7: Cluster com Kind
Configurei um cluster local com 3 nós usando Kind (1 control-plane e 2 workers).

### Etapa 8: ArgoCD
Instalei o ArgoCD no cluster, consegui acessar via port-forward e fiz login usando o secret inicial.

### Etapa 9: Criação do App no ArgoCD
Criei a aplicação no ArgoCD apontando para meu repositório e a pasta `k8s/base`.

### Etapa 10: Erro ao tentar sincronizar
Quando tentei sincronizar a aplicação no ArgoCD, apareceu o seguinte erro:

Unable to create application: application spec for fastapi-app is invalid: InvalidSpecError: Unable to generate manifests in k8s/base: rpc error: code = Unknown desc = repository contains out-of-bounds symlinks. file: venv/bin/python3


**Pelo que entendi, o problema foi porque subi a pasta `venv` no repositório sem querer, e ela acabou indo parar na pasta de configuração do ArgoCD.** Isso gerou o erro de segurança ao tentar processar o `kustomization.yaml`.

Apesar de não ter conseguido concluir a etapa da sincronização no ArgoCD, consegui avançar bastante no projeto. Acho que com mais um tempinho eu corrigiria esse erro e finalizaria o deploy.

