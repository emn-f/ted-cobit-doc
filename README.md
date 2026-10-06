# TED COBIT — Projeto LaTeX (ABNT NBR com XeLaTeX)

Estrutura padronizada de escrita acadêmica em LaTeX baseada na classe `abntex2`, configurada com DevContainer, fontes TrueType (Arial) e extensão LaTeX Workshop para VS Code.

---

## 📁 Estrutura do Projeto

```text
ted-cobit/
├── .devcontainer/
│   ├── Dockerfile                           # Imagem Debian Bookworm + TeXLive + XeLaTeX + mscorefonts + agy
│   ├── devcontainer.json                     # Configuração do Dev Container, extensões e receitas de build
│   └── ted-cobit.code-workspace              # Workspace do VS Code
├── .vscode/
│   ├── extensions.json                       # Extensões recomendadas (LaTeX Workshop, LTeX, Python)
│   └── settings.json                         # Configuração e receitas de compilação XeLaTeX/latexmk
├── imagens/                                  # Figuras e diagramas inseridos no texto
│   └── .gitkeep
├── imagens-template/                         # Imagens institucionais fixas do cabeçalho
│   └── ucsal_logo.png
├── preambulo/
│   ├── configuracoes.tex                     # Margens (3-3-2-2), parágrafos, listings e estilos
│   └── pacotes.tex                           # fontspec (Arial), babel pt-br, amsmath, tabularx, etc.
├── secoes/                                   # Seções modulares do documento
│   ├── 00-resumo.tex                         # Resumo e Abstract
│   ├── 01-introducao.tex                     # Introdução e objetivos
│   ├── 02-referencial-teorico.tex            # Fundamentação teórica
│   ├── 03-metodologia.tex                    # Metodologia adotada
│   ├── 04-desenvolvimento.tex                # Desenvolvimento / análise
│   └── 05-conclusao.tex                      # Considerações finais
├── abntex2.cls                               # Classe base abntex2
├── abntex2abrev.sty                          # Módulo de abreviações abntex2
├── abntex2cite.sty                           # Módulo de citações abntex2
├── main.tex                                  # Documento mestre
├── referencias.bib                           # Base bibliográfica BibTeX (ABNT 6023)
├── requirements.txt                          # Dependências Python para scripts auxiliares
└── .gitignore                                # Filtro para binários e arquivos intermediários TeX
```

---

## 🚀 Como Executar

### Opção 1: VS Code com Dev Containers (Recomendado)

1. Abra a pasta no VS Code:
   ```bash
   code /home/holmes/dev/ted-cobit
   ```
2. Pressione `F1` (ou `Ctrl+Shift+P`) e selecione:
   > **Dev Containers: Reopen in Container**
3. O VS Code construirá o container com todas as fontes (Arial), pacotes TeXLive e ferramentas de compilação automaticamente.
4. Ao salvar qualquer arquivo `.tex`, o documento será compilado automaticamente via **LaTeX Workshop**.
5. Para visualizar o PDF lado a lado, clique no botão de preview no canto superior direito do editor ou use o atalho `Ctrl+Alt+V`.

---

## 🛠️ Receitas de Compilação Configuradas

O projeto está configurado para utilizar o motor **XeLaTeX** (necessário para carregamento nativo de fontes TrueType/OpenType como Arial):

1. **`latexmk (XeLaTeX) 🔃`** *(Padrão)*:
   - Executa `latexmk` com a flag `-xelatex`, gerenciando automaticamente múltiplas passagens e referências bibliográficas.
2. **`xelatex ➞ bibtex ➞ xelatex × 2`**:
   - Ciclo clássico sequencial para resolução de citações e referências cruzadas.

---

## 📦 Dependências Inclusas no Dev Container

- **Base**: `mcr.microsoft.com/devcontainers/python:3.13-bookworm`
- **Tipografia**: `ttf-mscorefonts-installer` (Arial, Times New Roman), `fonts-liberation`, `fonts-texgyre`.
- **TeXLive**:
  - `texlive-latex-base`
  - `texlive-latex-recommended`
  - `texlive-latex-extra`
  - `texlive-lang-portuguese`
  - `texlive-publishers`
  - `texlive-bibtex-extra`
  - `texlive-xetex`
  - `texlive-fonts-recommended`
  - `latexmk`
- **CLI**: Google Antigravity CLI (`agy`) pré-instalado em `/usr/local/bin`.
- **Extensões VS Code**:
  - `James-Yu.latex-workshop` (compilação e visualização de PDF)
  - `valentjn.vscode-ltex` (verificação gramatical e ortográfica em pt-BR)
  - `ms-python.python` & `ms-python.vscode-pylance` (suporte a scripts Python)
