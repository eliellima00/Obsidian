```dataviewjs
dv.span("## Onboarding da Equipe")

let colaboradores = dv.pages('"Colaboradores/Colaboradores"')

for (let grupo of colaboradores.groupBy(c => c.equipe)) {
    dv.header(2, grupo.key)

    let html = "<div style='display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 16px;'>"

    for (let c of grupo.rows) {
        html += `
        <div style="border: 1px solid #ddd; border-radius: 12px; padding: 12px; text-align: center; background: #fafafa; box-shadow: 0 2px 6px rgba(0,0,0,0.1);">
            ${c.imagem ? `<img src='${c.imagem}' style="width:100px; height:100px; object-fit:cover; border-radius:50%; margin-bottom: 10px;" />` : ""}
            <h3 style="margin: 6px 0;">${c.name ?? "Sem nome"}</h3>
            <p><strong>Projetos:</strong> ${Array.isArray(c.projetos) ? c.projetos.join(", ") : (c.projetos ?? "-")}</p>
            <p><strong>Tecnologias:</strong> ${Array.isArray(c.tecnologias) ? c.tecnologias.join(", ") : (c.tecnologias ?? "-")}</p>
        </div>
        `
    }

    html += "</div>"
    dv.el("div", html)
}

```