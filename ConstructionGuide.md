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

## Configurar `@theme` do Tailwind no arquivo `globals.css`;

instalar a extensão `Poscss Language Support`;

```css
@theme {
    /** propriedade para só aceitar as cores que estão definidas aqui em @theme! */
    --color-*: initial;

    --color-white: white;
    --color-blue: #6F9DE2;
    --color-purple: #9871F3;
    --color-gradient: 90deg, #4B7FCD 0%, #8A61EA 100%;

    --color-danger: #F05D6C;

    --color-gray-100: #DAE4F2;
    --color-gray-200: #C8D0DA;
    --color-gray-300: #95A1B1;
    --color-gray-400: #6F7D90;
    --color-gray-500: #2A313C;
    --color-gray-600: #21252C;
    --color-gray-700: #191D24;
    --color-gray-800: #13161B;
    --color-gray-900: #0F1216;

    --font-heading: var(--font-oxanium);
    --font-sans: var(--font-montserrat);

}
```

Importar as fontes no arquivo `layout.tsx`:
No arquivo `globals.css` importe `import { Montserrat, Oxanium } from "next/font/google";` no topo.

```css
const oxanium = Oxanium({
	weight: ['500', '600'],
	subsets: ['latin'],
  variable: '--font-oxanium',
})

const montserrat = Montserrat({
	weight: ['400', '600'],
	subsets: ['latin'],
	variable: '--font-montserrat',
})
```

No mesmo arquivo, na tag <html> acrencenta a "className={`${oxanium.variable} ${montserrat.variable}`}"

EX:
```tsx
return (
    <html lang="en" className={`${oxanium.variable} ${montserrat.variable}`}>
      <body className="bg-gray-900 text-white">{children}</body>
    </html>
  );
```

## Instalar biblioteca de Icones

`npm i lucide-react`

## Biome (linter e format) - organiza o código, da mesma forma, seguindo uma formatação, e escrevendo o código da mesma forma até o fim. *OPCIONAL

1º `npm i @biomejs/biome -D`;

2º baixar a extensão do VSCode do `Biome`;

https://biomejs.dev/guides/getting-started/

3º rodar para iniciar as configurações `npx @biomejs/biome init`;

4º e adicionar no arquivo `biome.json`:
```json
    "formatter": {
        "enabled": true,
        "indentStyle": "space",
        "indentWidth": 2,
        "lineWidth": 80
	},
```
5º E,
```json
    "javascript": {
        "formatter": {
            "quoteStyle": "single",
            "trailingCommas": "es5",
            "semicolons": "asNeeded"
        }
	}
```

https://biomejs.dev/reference/vscode/

6º E, no ">json" `Open Workspaces Settings` do VSCode, adicionar:
```json
{
    "[javascript]": {
        "editor.defaultFormatter": "biomejs.biome"
    },
    "[typescript]": {
        "editor.defaultFormatter": "biomejs.biome"
    },
    "[typescriptreact]": {
        "editor.defaultFormatter": "biomejs.biome"
    },
    "editor.codeActionsOnSave": {
        "source.organizeImports.biome": "explicit"
    },
    "editor.formatOnSave": true
}
```

7º Agora é só ir salvalndo (CTRL + S) de arquivo em arquivo!

