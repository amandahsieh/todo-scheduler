FROM python:3.10-slim

# 安裝 Zsh、Git 和其他必要工具
RUN apt-get update && \
    apt-get install -y zsh git curl && \
    chsh -s $(which zsh) root && \
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" --unattended && \
    echo "plugins=(git)" >> ~/.zshrc && \
    sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="agnoster"/g' ~/.zshrc

WORKDIR /app

# 複製 requirements.txt 並安裝依賴
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 複製應用代碼
COPY . .