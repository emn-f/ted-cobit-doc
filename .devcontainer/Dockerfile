FROM mcr.microsoft.com/devcontainers/python:3.13-bookworm

# Habilitar contrib e non-free para a instalação dos mscorefonts (fonte Arial)
RUN sed -i 's/Components: main/Components: main contrib non-free/g' /etc/apt/sources.list.d/debian.sources 2>/dev/null || true \
    && if [ -f /etc/apt/sources.list ]; then sed -i 's/main/main contrib non-free/g' /etc/apt/sources.list; fi

# Instalar dependências do LaTeX (incluindo XeLaTeX, estilo ABNT e fonte Arial)
RUN echo "ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true" | debconf-set-selections \
    && apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
       curl \
       ca-certificates \
       wget \
       cabextract \
       fontconfig \
       fonts-liberation \
       fonts-croscore \
       fonts-texgyre \
       ttf-mscorefonts-installer \
       texlive-latex-base \
       texlive-latex-recommended \
       texlive-latex-extra \
       texlive-lang-portuguese \
       texlive-publishers \
       texlive-bibtex-extra \
       texlive-xetex \
       texlive-fonts-recommended \
       latexmk \
    && fc-cache -f \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Instalar o Google Antigravity CLI (agy)
RUN curl -fsSL https://antigravity.google/cli/install.sh | bash -s -- --dir /usr/local/bin

# Criar diretório de configuração do Gemini com permissões corretas para o usuário vscode
RUN mkdir -p /home/vscode/.gemini && chown -R vscode:vscode /home/vscode/.gemini
