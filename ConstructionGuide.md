## Next.JS
https://nextjs.org/
`npx create-next-app@latest --empty`

OBS: não instalar o Tailwind por aqui, instalar manualmente conforme abaixo!

## Tailwind CSS
https://tailwindcss.com/docs/installation/framework-guides/nextjs

Passos:
2º `npm install tailwindcss @tailwindcss/postcss postcss`;

3º Criar arquivo `postcss.config.mjs` na raiz, e colocar o seguinte código:
```mjs
    const config = {
        plugins: {
            "@tailwindcss/postcss": {},
        },
    };
    export default config;
```

4º Criar arquivo ./src/app/`globals.css`, e colocar o seguinte código:
```css
    @import "tailwindcss";
```

5º importar o arquivo `globals.css` no topo do arquivo `layout.tsx`:
```tsx
    import './globals.css'
```

6º `npm run dev`;

## 