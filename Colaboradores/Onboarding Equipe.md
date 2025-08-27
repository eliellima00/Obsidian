```dataviewjs
// Pega todas as notas dentro da pasta Colaboradores
const pages = dv.pages('"Colaboradores"')
  // ignora subpastas
  .where(p => p.file.folder === "Colaboradores");

dv.container.innerHTML = `
  <div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 16px;">
    ${pages.map(p => {
      // usa imagem do frontmatter se existir, senão usa um placeholder
      const img = p.imagem ? p.imagem : "https://via.placeholder.com/80";
      return `
        <div style="border: 1px solid #ccc; border-radius: 12px; padding: 12px; text-align: center; box-shadow: 0 2px 6px rgba(0,0,0,0.1); background: white;">
          <img src="${img}" style="width:80px;height:80px;border-radius:50%;object-fit:cover;margin-bottom:8px;">
          <div style="font-weight: bold; margin-bottom: 4px;">${p.file.link}</div>
        </div>
      `;
    }).join("")}
  </div>
`;
```
