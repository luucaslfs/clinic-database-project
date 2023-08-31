```
tutor (*CPF*, Nome, Log, Estado, Cidade)

Num_telefone (*CPF, numero*)
CPF -> Tutor(CPF)

Animal (*ID, CPFDono*, Dnascimento, Nome)
CPFDono -> Tutor(CPF)

Prontuario(*ID*, Histórico, [ID_animal, CPFDono]!)
ID_animal, CPFDono -> Animal(ID, CPFDono)

Veterinario(*CRVet*, nome, CRVetSup{obrigatório?})
CRVetSup -> Veterinario(CRVet)

Atendimento (*Data, IDAnimal, CRVet*)
IDAnimal -> Animal(ID)
CRVet -> Veterinario(CRVet)

Receita(*ID*, descritivo, [Data, IDAnimal, CRVet]!)
Data, IDAnimal, CRVet -> Atendimento(Data, IDAnimal, CRVet)

Procedimento(*ID*, Desc, Data, Medicação)

Clínico(*ID*, Exame)
ID -> Procedimento(ID)

Domiciliar(*ID*, DataVolta, Recomendação)
ID -> Procedimento(ID)

Executa(*IDAnimal, IDProcedimento, CRVet*)
IDAnimal -> Animal(ID)
IDProcedimento -> Procedimento(ID)
CRVet -> Veterinario(CRVet)
```
