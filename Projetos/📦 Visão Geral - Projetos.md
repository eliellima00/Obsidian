#  Visão Geral - Projetos

```dataview
TABLE 
    descricao AS "Descrição",
    equipe AS "Equipe",
    status AS "Status",
    join(dependencias, ", ") AS "Dependências",
    join(regras, ", ") AS "Regras de Negócio"
FROM "Projetos"
WHERE file.name != "Visão Geral"
SORT status ASC
