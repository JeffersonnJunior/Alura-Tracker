# Como Criar uma tabela

> ## 1 - Passo
> * ### Criar Entidade 
> * ### Camada para criação -  4-Domain/Domain/Entities

> ## 2 - Passo
> * ### Criar Dtos
> * ### Camada para criação -  3-Application/Application/DataTransferObjects

> ## 3 - Passo
> * ### Criar Mapeamento com o Banco de Dados
> * ### Camada para criação - 5-Infra/5.1-Data/Infra.Data/Mappings

> ## 4 - Passo
> * ### Criar Mapeamento com AutoMapper
>* ### Camada para criação 3-Application/Application/AutoMapper/AutoMapperProfileConfigurationMap.cs


> ## 5 - Passo
> * ### Criar Migration

```
Para Criar Uma Migration

Observações:
* Em Default Project colocar em 5-Infra/5.1-Data/Infra.Data
* 1 - Comando para criação da Migration
* 2 - Comando para execução da Migration no banco de dados

1- Add-Migration OQueElaFaz -Context DataBase

2- Update-Database

```
:smiley:

