

```dataviewjs
const pages = dv.pages('"Colaboradores/Colaboradores"')
  .where(p => p.file.folder === "Colaboradores/Colaboradores");

dv.container.innerHTML = `
  <div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 16px; hover: ">
    ${pages.map(p => {
      const img = p.imagem ? p.imagem : "https://via.placeholder.com/80";
      return `
        <a href="${p.file.path}" 
           style="text-decoration: none; color: inherit;">
          <div style="border: 1px solid #ccc; border-radius: 12px; padding: 12px; text-align: center; box-shadow: 0 2px 6px rgba(0,0,0,0.1); background: white; transition: transform 0.2s;">
            <img src="${img}" style="width:80px;height:80px;border-radius:50%;object-fit:cover;margin-bottom:8px;">
            <div style="font-weight: bold; margin-bottom: 4px;">${p.name ?? p.file.name}</div>
          </div>
        </a>
      `;
    }).join("")}
  </div>
`;
```
