# Site Academia RF Team

Página única, sem build e sem dependências. Abrir `index.html` direto no navegador ou subir a pasta inteira em qualquer hospedagem estática (GitHub Pages, Hostinger, Netlify).

```
Site/
├── index.html      página completa (HTML + CSS + JS embutidos)
├── assets/         imagens tratadas e o brasão
└── LEIA-ME.md      este arquivo
```

Peso total: 2,9 MB, sendo 76 KB de HTML. Sem framework, sem node_modules.

---

## Identidade

Paleta tirada do brasão real da academia, pixel a pixel:

| Token | Cor | Uso |
|---|---|---|
| `--yellow` | `#FBE10A` | cor principal, CTAs, números, destaques |
| `--red` | `#E8262C` | acento pontual (herdado das barras do brasão) |
| `--steel` | `#333136` | cinza do octógono do brasão |
| `--ink` | `#0A0A0B` | fundo |
| `--bone` | `#F2F2EE` | texto |

Tipografia: **Anton** nos títulos (condensada, cara de cartaz de luta) e **Inter** no corpo.

O brasão em `assets/logo.webp` foi extraído do card de horários, teve o fundo removido, foi ampliado 6x e teve as cores reancoradas nos quatro tons originais do desenho. É o logo da academia, não uma releitura: nada foi redesenhado.

---

## Tratamento das imagens

Todas as fotos passaram pelo mesmo processo: contraste local, nitidez por máscara de desfoque e ganho de saturação e brilho. **Nenhum conteúdo foi alterado, adicionado ou removido de nenhuma foto.**

A foto do Mestre Rivelino no topo foi recortada do fundo do card original por segmentação (modelo `isnet-general-use`), teve o vazamento de fundo entre o braço e o tronco removido por cor, e ganha um esmaecimento na base para não terminar num corte reto.

---

## De onde veio cada informação

Nada no site foi estimado ou inventado. Cada dado tem fonte publicada:

| Afirmação no site | Fonte |
|---|---|
| Academia desde 2000, Rua Belém 273, modalidades, telefone | Perfil `@academia_rfteam` e card de horários do cliente |
| Rivelino ensina desde 1995; formou Francimar "Bodão" | A Gazeta do Acre, out/2012 |
| Campeão Mundial CBJJE 2019, master 4 peso médio faixa preta | ge Globo, 29/07/2019 |
| Prata no Mundial 2016, master 3 | globoesporte, retrospectiva 26/12/2016 |
| Faixa preta 5º grau pelo Mestre Luiz Neto; seminário anual | Página da RF Team no Facebook |
| Responsável técnico Rivelino Pereira de Souza | FJJRO, agremiação nº 44 |
| Seminário do Jacaré em Rio Branco, 2015 | ge Globo, 13/07/2015 |
| Frase "Para chegar onde cheguei..." | ac24horas, 09/08/2019 |
| Alissandro: ouro 2015 (até 88,3 kg), bronze 2011 | ge Globo, 28/07/2015 |
| Alissandro: bronze no Mundial 2025, vitória sobre Ary Lobo | ge Globo, 28/11/2025 |
| Carlos Rafael: ouro No-Gi e bronze GI no Floripa Fall Open | ge Globo, 18/05/2026 |
| João Pedro: +40 medalhas, 2 ouros AJP, 4 na Copa Acre Pódio | ge Globo 07/04/2026 e ContilNet 08/02/2026 |
| Khevyn Francys no Mundial 2025 | ge Globo, 26/11/2025 |
| Lima Neto: 4 ouros na Copa América; Lua Branca; Adriano Moraes | Notícias da Hora, 08/06/2026 |
| Combate pelo Bem: 200+ atendidos, 70 inscritos, 30 atletas a RO | ContilNet, dez/2023 |
| Edson Lopes, Débora Sales, Júnior Lavor, Dennison Pinheiro | globoesporte, retrospectiva 2016 |
| Bruno Almeida no BRTL | A Gazeta, 26/12/2024 |

As fotos dos atletas vêm dessas mesmas reportagens, creditadas a "Arquivo pessoal" e "Divulgação/RF Team", ou seja, material da própria academia e dos próprios atletas.

**Correção aplicada:** o card informa Karatê às 20h. Conforme sua observação, o site publica **19h**.

---

## Antes de publicar, confirmar com a academia

Cinco pontos que não consegui verificar em fonte pública e que escrevi da forma mais conservadora possível:

1. **Horário de funcionamento** na barra do topo e no rodapé ("segunda a sexta, 7h30 às 21h"). Foi deduzido da primeira e da última turma da grade.
2. **Aula experimental sem kimono** (FAQ). É a prática comum, mas é política da casa.
3. **Idade mínima do Jiu Kids.** O site cita os 7 anos apenas para o projeto social, que é o dado publicado. A turma kids da academia ficou sem idade declarada de propósito.
4. **Mensalidade.** O FAQ manda para o WhatsApp em vez de citar valor, já que não tenho a tabela.
5. **Uso das fotos dos atletas.** Vale um aviso aos retratados, e o ideal é substituir pelos originais da academia, que terão mais resolução que as versões publicadas pela imprensa.

---

## Publicação

| | |
|---|---|
| Domínio | `academiarfteam.online` (registrado na Hostinger em 18/09/2026) |
| Repositório | `andersonlsbraga/rf-team-site`, público |
| Hospedagem | GitHub Pages, branch `main`, raiz |
| Build | concluído, conteúdo servido e conferido pelo CDN do Pages |

O arquivo `CNAME` já fixa o domínio, então qualquer `git push` para `main` republica o site sozinho.

### DNS que falta apontar na Hostinger

Em **Domínios > academiarfteam.online > DNS / Nameservers**, apagar os registros `A` e `CNAME` de parking e criar:

| Tipo | Nome | Valor | TTL |
|---|---|---|---|
| A | `@` | `185.199.108.153` | 3600 |
| A | `@` | `185.199.109.153` | 3600 |
| A | `@` | `185.199.110.153` | 3600 |
| A | `@` | `185.199.111.153` | 3600 |
| CNAME | `www` | `andersonlsbraga.github.io.` | 3600 |

Depois de propagar, ligar o **Enforce HTTPS** no repositório. Se o certificado ficar com `https_certificate` nulo por mais de uma hora, o pedido travou: remover e recolocar o domínio custom resolve.

---

## Checagens já feitas

- Sem rolagem horizontal de 320px a 1920px
- Console limpo, nenhuma requisição falhando
- Menu mobile abre, fecha e atualiza `aria-expanded`
- Todas as 22 imagens carregam, todas com `alt`
- Sem JavaScript, a seção de medalhistas continua mostrando os 8 cards e as 9 conquistas
- `prefers-reduced-motion` para os carrosséis, os contadores e as animações de entrada
- Um `<h1>`, HTML sem tags abertas, dados estruturados `SportsActivityLocation`
- Tabela de horários vira lista de cartões no celular, sem rolagem lateral
