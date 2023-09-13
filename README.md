<p align="center">
  <a href="https://portal.cin.ufpe.br/">
    <img src="https://i.imgur.com/w4LNDII.png" width=330 height=100>
  </a>

  <h3 align="center">Projeto de Banco de Dados - 23.1</h3>

  <p align="center">
    <i>This is a full database project, starting from conceptual and going all over to the physical implementation in Oracle, passing throught the logical phase. Its related to an Veterinary Clinic system.</i>
    <br>
    <br>
    <i>By: <a href="mailto:lfs@cin.ufpe.br">Lucas Florêncio</a>, <a href="mailto:lrbf@cin.ufpe.br">Luiz Roberto</a></i>
    <br>
    <br>
    <a href="https://github.com/luucaslfs/clinic-database-project#running-the-physical-project"><strong>Physical Project (Oracle)&raquo;</strong></a>
    <br>
    <br>
    <a href="https://github.com/luucaslfs/clinic-database-project#conceptual-project">Conceptual Project</a>
    &middot;
    <a href="https://github.com/luucaslfs/clinic-database-project#logical-project">Logical Project</a>
  </p>
</p>

# About

This project aims to design a database from side to side, starting from [scratch](./Conceptual/Scratch.md), producing an [EER diagram](./Conceptual/EER_Model.jpg), that would be [mapped to a relational database](./Logical/Relational_Mapping.md) to finally build the [physical Oracle project](./Physical/).

We are building an database for a Vet Clinic system that has[...]

<br>

# Conceptual Project

![EERModel](./Conceptual/EER_Model.jpg "EER Model of our Database")

<br>

# Logical Project

```
TUTOR (CPF, NOME, LOG, ESTADO, CIDADE)

NUM_TELEFONE (CPF, NUMERO)
CPF -> TUTOR(CPF)

ANIMAL (NOME, CPF, NASCIMENTO)
CPF -> TUTOR(CPF)

PRONTUARIO(IDP, HISTORICO, [CPF, NOME]!)
CPF, NOME -> ANIMAL(CPF, NOME)

VETERINARIO(CRVET, NOME, CRVETSUP)
CRVETSUP -> VETERINARIO(CRVET)

ATENDIMENTO (DATA, NOME, CPF, CRVET)
NOME, CPF -> ANIMAL(NOME)
CRVET -> VETERINARIO(CRVET)

RECEITA(IDR, DESCRITIVO, DATA!, NOME!, CPF!, CRVET!)
DATA, NOME, CPF, CRVET -> ATENDIMENTO(DATA, NOME, CPF, CRVET)

PROCEDIMENTO(IDP, DESCRICAO, DATA, MEDICACAO, RECOMENDACAO)

CLINICO(IDP, EXAME)
IDP -> PROCEDIMENTO(IDP)

DOMICILIAR(IDP, DATAVOLTA)
IDP -> PROCEDIMENTO(IDP)

EXECUTA(NOME, CPF, IDP, CRVET)
NOME, CPF -> ANIMAL(NOME, CPF)
IDP -> PROCEDIMENTO(IDP)
CRVET -> VETERINARIO(CRVET)
```
<br>

# Running the physical project

![SQL Live](./Physical/Preview.jpg "A preview of our physical model in Live SQL (Oracle)")

<br>

- We used LiveSQL tool from Oracle to host and run the DDL, DML and Procedures.
- [Here you can see information about running/testing the actual physical model of this database project.](./Physical/Physical_Model.md)
