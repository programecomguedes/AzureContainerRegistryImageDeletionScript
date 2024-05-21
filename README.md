# Azure Container Registry Image Deletion Script

Script em Python com o objetivo deletar imagens de repositórios no Azure Container Registry deixando apenas os dois mais recentes.

## Descrição

O script utiliza a biblioteca `azure-containerregistry` e `azure-identity` para se autenticar e interagir com o Azure Container Registry. Ele lista todos os repositórios, filtra repositórios específicos, organiza as tags por data de atualização e deleta as tags antigas, mantendo apenas as duas mais recentes.

## Dependências

- `azure-containerregistry`
- `azure-identity`

Você pode instalar essas dependências usando o pip:

```bash
pip install azure-containerregistry azure-identity
```

Instale o cliente do Azure Container Registry:
```bash
pip install --pre azure-containerregistry
```

## Configuração

### Autenticação

Antes de executar o código, é necessário autenticar-se ao Portal Azure, para isso execute o seguinte comando no terminal:
```bash
az login
```

Em seguida pode iniciar o jupyer notebook:
```bash
jupyter notebook
```

### Endpoint

Você deve substituir `"CONTAINER_REGISTRY_NAME"` pelo nome do seu Container Registry no Azure.

### Filtros
Se tiver interesse em filtrar os repositórios por algum critério específico, altere os valores de `FILTER_ONE` e `FILTER_TWO` no `if` ou aplique o filtro conforme sua necessidade. 

## Funções

### `convertDateToGMT_3(data)`

Converte um objeto `datetime` para o fuso horário GMT-3.

### `orderTagsByLastUpdate(tags)`

Ordena uma lista de tags pela data de atualização, em ordem decrescente.

### `getTagsToDelete(tags)`

Retorna todos os itens em uma lista, exceto os dois primeiros. Se a lista tiver menos de três itens, retorna uma lista vazia.

### `deleteTag(repository_name, tag_name)`

Deleta uma tag específica de um repositório.


# Documentação Oficial
https://learn.microsoft.com/en-us/python/api/overview/azure/containerregistry-readme?view=azure-python#delete-manifest
