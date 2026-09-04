# San Connect Japan — site

Landing page da San Connect Japan. HTML, CSS e JavaScript puros.
Sem build, sem npm, sem framework: é só subir os arquivos.

---

## ⚠️ ANTES DE PUBLICAR — leia isto

O site está com **dados de teste e conteúdo fictício**. Se for ao ar assim,
vai anunciar preços e depoimentos que não existem.

### 1. Contato (obrigatório)

Abrir `index.html` e editar o bloco `CONFIG`, logo no começo da tag `<script>`:

```js
const CONFIG = {
  whatsapp: '5544999665711',   // ← HOJE É O NÚMERO PESSOAL DO RICARDO
  ga4: '',                     // ex.: 'G-XXXXXXXXXX'
  metaPixel: '',               // ex.: '1234567890123456'
  endpoint: ''                 // opcional: URL do Formspree/Basin
};
```

O e-mail `joshuafguirado@gmail.com` também é de teste e aparece no rodapé.

### 2. Conteúdo inventado (trocar tudo)

| Onde | O que está lá | Situação |
|---|---|---|
| Rodapé | CNPJ 58.412.706/0001-93 | fictício |
| Quem somos | Cargos e bios das três sócias (Aichi, Shizuoka, Gunma) | fictício |
| Depoimentos | Os 8 depoimentos e seus autores | **reais** (enviados pela San Connect) |
| FAQ | Taxa de R$ 2.400 em duas parcelas | fictício |
| FAQ | Prazo de 4 a 8 meses | fictício |
| FAQ | Faixa salarial ¥1.100–¥1.500/h | fictício |
| FAQ | Faixa etária 18 a 45 anos | fictício |
| Card de conversa | As 4 mensagens do WhatsApp | fictício |
| Mapa | "18.500 km de distância" | conferir |
| Sócias | Retângulos rosa no lugar das fotos | faltam fotos |

**Confirmados** (vieram do perfil oficial): endereço, telefone fixo,
horário de atendimento, Instagram, Facebook e o slogan.

**Sem confirmação:** se a San Connect faz restituição de shakai hoken,
prova de vida e aposentadoria japonesa. Esses serviços foram removidos
do site até alguém confirmar.

### 3. Política de privacidade

`politica-privacidade.html` tem campos marcados em rosa (CNPJ, e-mail,
data, prazo de retenção). Preencher antes de publicar. O texto cobre o
que a LGPD exige, mas **não substitui revisão de advogado**.

### 4. Domínio

`robots.txt` e `sitemap.xml` estão com `SEUDOMINIO.com.br`. Trocar pelo
domínio real depois de conectar na Vercel.

---

## Subir na Vercel

1. Criar o repositório no GitHub com estes arquivos.
2. Em vercel.com → **Add New → Project** → importar o repositório.
3. **Não configurar nada**: Framework Preset = *Other*, sem build command,
   sem output directory. É site estático.
4. Deploy.

O `vercel.json` já cuida de cache dos assets por 1 ano, cabeçalhos de
segurança e URLs limpas (`/politica-privacidade` sem o `.html`).

Domínio próprio: Vercel → Settings → Domains.

---

## Estrutura

```
index.html                  página principal
politica-privacidade.html   documento legal
assets/
  fonts/                    Archivo Black + Montserrat em woff2 (SIL OFL)
  logo-*.png                logotipos
  simbolo-cor.svg           símbolo em vetor
  pattern-*.png             textura de sakura
  petala-*.png              pétalas da animação
  og.jpg                    imagem de compartilhamento
vercel.json / robots.txt / sitemap.xml
```

---

## Notas técnicas

**Fontes** são servidas localmente, sem Google Fonts — mais rápido e sem
enviar IP do visitante para terceiros (relevante para a LGPD). Licença SIL
Open Font License, hospedar é permitido.

**Japonês:** o botão PT / 日本語 troca cerca de 190 blocos de texto sem
recarregar a página, e a escolha fica salva. O dicionário está no objeto
`JA` dentro do script. Não há fonte japonesa embutida — o japonês usa a
fonte do sistema.

⚠️ Ao editar textos em português, lembre de atualizar a chave
correspondente no objeto `JA`, senão aquele trecho para de traduzir.
E cuidado: se um texto dividir o mesmo elemento com outro conteúdo
(um ícone, um horário), a tradução não encontra. Nesse caso, envolver
o texto num `<span>` próprio.

**Mapa-múndi:** os 4.934 pontos dos continentes foram gerados aqui a
partir da geometria real dos países e compactados num único `path`.
As rotas partem de Maringá para Aichi, Gunma e Shizuoka.

**Medição:** nada do Google ou da Meta é carregado enquanto os IDs
estiverem vazios. Já estão ligadas duas conversões — clique no WhatsApp
e envio do formulário — e o site captura `utm_source`, `gclid` e `fbclid`,
anexando a origem na mensagem que chega no WhatsApp.

**Acessibilidade:** todas as animações respeitam `prefers-reduced-motion`.
Em telas até 760px e em aparelhos sem mouse, os efeitos mais pesados são
desligados automaticamente.

---

## Ainda por fazer

- [ ] Fotos das sócias e de clientes reais no Japão
- [ ] Trocar todo o conteúdo fictício da tabela acima
- [ ] Confirmar shakai hoken / prova de vida / aposentadoria
- [ ] Preencher a política de privacidade e revisar com advogado
- [ ] Testar o Lighthouse mobile depois no ar
- [ ] Fonte japonesa sob demanda, se o público japonês for prioridade
