# TED COBIT — Artigo no Padrão SBC / UCSAL (com referências ABNT)

Estrutura padronizada de escrita de artigos acadêmicos baseada no modelo oficial da **Sociedade Brasileira de Computação (SBC)** disponibilizado pela **UCSAL** (`ucsal-template.sty`), integrado ao DevContainer e mantendo o sistema de citações e referências ABNT (`abntex2cite` / `referencias.bib`).

---

## 📁 Estrutura do Projeto

```text
ted-cobit/
├── .devcontainer/
│   ├── Dockerfile                           # Imagem Debian Bookworm + TeXLive + agy CLI
│   ├── devcontainer.json                     # Configurações do container, extensões e receitas de build
│   └── ted-cobit.code-workspace              # Workspace do VS Code
├── .vscode/
│   ├── extensions.json                       # Extensões recomendadas (LaTeX Workshop, LTeX, Python)
│   └── settings.json                         # Receitas de compilação (pdfLaTeX e XeLaTeX)
├── imagens/                                  # Figuras e diagramas inseridos no texto
│   ├── fig1.jpg                              # Imagem de exemplo do template
│   ├── fig2.jpg                              # Imagem de exemplo do template
│   └── table.jpg                             # Exemplo de tabela em imagem
├── preambulo/
│   ├── configuracoes.tex                     # Ajustes complementares (listings, hypersetup, tabelas)
│   └── pacotes.tex                           # ucsal-template, caption2, hyperref, amsmath, abntex2cite
├── secoes/                                   # Seções modulares do documento
│   ├── 00-resumo.tex                         # Abstract e Resumo (SBC)
│   ├── 01-introducao.tex                     # Introdução e objetivos
│   ├── 02-referencial-teorico.tex            # Fundamentação teórica (COBIT 2019 / Governança de TI)
│   ├── 03-metodologia.tex                    # Metodologia
│   ├── 04-desenvolvimento.tex                # Desenvolvimento / análise
│   └── 05-conclusao.tex                      # Considerações finais
├── caption2.sty                              # Estilização de legendas SBC (Helvetica 10pt)
├── ucsal-template.sty                        # Estilo oficial SBC/UCSAL (margens, tipografia Times 12pt, cabeçalho)
├── sbc.bst                                   # Estilo bibliográfico nativo SBC (opcional)
├── abntex2cite.sty                           # Módulo de citações ABNT mantido do projeto
├── abntex2abrev.sty                          # Módulo de abreviações ABNT
├── main.tex                                  # Documento mestre (\documentclass[12pt]{article})
├── referencias.bib                           # Base bibliográfica BibTeX (COBIT 2019 / ISACA)
├── requirements.txt                          # Dependências Python para scripts de suporte
└── .gitignore                                # Filtro para arquivos auxiliares TeX
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
3. O ambiente carrega todas as ferramentas de compilação automaticamente.
4. Ao salvar qualquer arquivo `.tex`, o documento será compilado automaticamente via **LaTeX Workshop**.
5. Para visualizar o PDF lado a lado, clique no botão de preview no canto superior direito do editor ou use o atalho `Ctrl+Alt+V`.

---

## 🛠️ Receitas de Compilação Configuradas

O projeto inclui receitas para **pdfLaTeX** (motor nativo do modelo SBC) e **XeLaTeX**:

1. **`latexmk (pdfLaTeX) 🔃`** *(Padrão)*:
   - Executa `latexmk -pdf`, otimizado para o padrão SBC com tipografia Times New Roman nativa.
2. **`pdflatex ➞ bibtex ➞ pdflatex × 2`**:
   - Ciclo sequencial clássico de compilação.
3. **`latexmk (XeLaTeX) 🔃`**:
   - Compilação via XeTeX.
4. **`xelatex ➞ bibtex ➞ xelatex × 2`**:
   - Ciclo sequencial via XeTeX.

---

## 📚 Citações e Referências (ABNT)

As citações seguem a configuração do projeto atual via `abntex2cite`:
- Citação indireta: `\cite{weill2004governance}` -> `(WEILL; ROSS, 2006)`
- Citação textual: `\citeonline{isaca2019framework}` -> `ISACA (2018)`
- Arquivo de referências: `referencias.bib`
