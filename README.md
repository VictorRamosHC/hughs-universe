# Hugo's Universe

Um hub de portfólio WebGL inspirado em um sistema solar: cada planeta é um projeto navegável. A cena usa Three.js via CDN, portanto não exige Node, bundler ou etapa de build.

## Abrir localmente

Servidores estáticos evitam restrições de `fetch` ao carregar `planets.json`:

```powershell
python -m http.server 8080
```

Abra `http://localhost:8080`. Arraste para orbitar, use scroll/pinch para aproximar, clique em um mundo para abrir o dossiê e pressione `Esc` para voltar à visão geral.

## Adicionar um planeta

`planets.json` é a única fonte de verdade. Acrescente uma entrada seguindo este formato:

```json
{
  "id": "meu-projeto",
  "name": "MEU PROJETO",
  "description": "Uma descrição curta e humana.",
  "orbitRadius": 450,
  "size": 7,
  "color": "#00e5ad",
  "textureType": "matrix",
  "status": "EM DEV",
  "repoUrl": "https://github.com/usuario/repositorio",
  "techStack": ["JavaScript", "WebGL"]
}
```

As órbitas são normalizadas visualmente pelo `main.js` para manter uma cena legível; o valor no JSON continua sendo a escala semântica do catálogo. `textureType` aceita hoje `glitch-metal`, `data`, `matrix`, `book` e `engine`, e determina o acabamento luminoso do planeta.

## Performance e acessibilidade

- Desktop: 52 mil partículas; telas compactas/touch: 30 mil.
- Pixel ratio limitado e bloom reduzido no mobile.
- Planetas usam geometria enxuta e materiais procedurais; o foco de câmera evita dependências extras.
- Sem WebGL, a aplicação revela automaticamente uma lista 2D de links diretos.
- Os dossiês são diálogos HTML, acessíveis por teclado; `Esc` retorna ao sistema.

## GitHub Pages

O workflow em `.github/workflows/deploy-pages.yml` publica o conteúdo da raiz a cada push na `main`. No repositório, em **Settings → Pages**, selecione **GitHub Actions** como fonte. O endereço esperado é:

`https://victorramoshc.github.io/hughs-universe/`

## Experiência

Você entra em uma câmera silenciosa, cercada por poeira estelar e sinais neon. O núcleo CAPRI pulsa no centro como um terminal astronômico. Ao selecionar um mundo, as órbitas congelam, a câmera se aproxima e o dossiê do projeto surge. A navegação externa só acontece ao escolher **VISITAR MUNDO** — o universo nunca remove o controle de quem o explora.

## Captura de demonstração

Abra a versão publicada, selecione um planeta e faça uma captura da transição/modal. Salve-a em `assets/` como `navigation-demo.gif` ou `navigation-demo.png` e inclua-a aqui antes de divulgar o projeto.
