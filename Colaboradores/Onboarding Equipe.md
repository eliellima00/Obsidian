

```dataviewjs
const pages = dv.pages('"Colaboradores/Colaboradores"')
  .where(p => p.file.folder === "Colaboradores/Colaboradores");

dv.container.innerHTML = `
  <div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 20px;">
    ${pages.map(p => {
      const img = p.imagem ? p.imagem : "https://via.placeholder.com/100";
      const equipe = p.equipe ? `<p><strong>Equipe:</strong> ${p.equipe}</p>` : "";
      const projetos = (p.projetos && p.projetos.length > 0) 
        ? `<p><strong>Projetos:</strong> ${p.projetos.map(x => x).join(", ")}</p>` 
        : "";
      const tecnologias = (p.tecnologias && p.tecnologias.length > 0) 
        ? `<p><strong>Tecnologias:</strong> ${p.tecnologias.map(x => x).join(", ")}</p>` 
        : "";

      return `
        <a href="${p.file.path}" style="text-decoration: none; color: inherit;">
          <div style="border: 1px solid #ccc; border-radius: 12px; padding: 16px; text-align: center; 
                      box-shadow: 0 2px 6px rgba(0,0,0,0.1); background: white; transition: transform 0.2s;">
            <img src="${img}" style="width:100px;height:100px;border-radius:50%;object-fit:cover;margin-bottom:12px;">
            <div style="font-size: 18px; font-weight: bold; margin-bottom: 8px;">${p.name ?? p.file.name}</div>
            <div style="text-align: left; font-size: 14px; line-height: 1.4;">
              ${equipe}
              ${projetos}
              ${tecnologias}
            </div>
          </div>
        </a>
      `;
    }).join("")}
  </div>
`;
```
