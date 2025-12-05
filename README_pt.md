# Command Fuzzy Finder (cmd)

[![License: GPLv3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
![Bash Version](https://img.shields.io/badge/Bash-4.0%2B-brightgreen)
![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS-lightgrey)
![Multilingual](https://img.shields.io/badge/Multilingual-EN%20%7C%20PT-blue)

Uma ferramenta de linha de comando poderosa e intuitiva para busca fuzzy de comandos do PATH, escrita puramente em Bash sem dependências externas.

<p align="center">
  <img src="https://raw.githubusercontent.com/felipefacundes/cmd-fuzzy-finder/main/screenshot.png" alt="Demonstração do cmd" width="800">
</p>

## ✨ Características Principais

- 🔍 **Busca fuzzy em tempo real** - Encontre comandos enquanto digita
- 🎨 **Interface colorida e intuitiva** - Visualização clara e agradável
- ⚡ **Sem dependências externas** - Apenas Bash puro
- 🌍 **Suporte multilíngue** - Inglês e Português (detecta automaticamente)
- 📋 **Histórico de execuções** - Mantém registro dos comandos usados
- 🎯 **Navegação rápida** - Teclas direcionais para navegar
- 📁 **Múltiplos modos de uso** - Interativo, busca inicial e lista simples

## 🚀 Instalação

### Método Rápido (Recomendado)
```bash
# Baixe o script
curl -L -o cmd https://raw.githubusercontent.com/felipefacundes/cmd-fuzzy-finder/main/cmd

# Torne executável
chmod +x cmd

# Mova para o PATH (opcional, mas recomendado)
sudo mv cmd /usr/local/bin/
```

### Método Clone do Repositório
```bash
git clone https://github.com/felipefacundes/cmd-fuzzy-finder.git
cd cmd-fuzzy-finder
chmod +x cmd
sudo cp cmd /usr/local/bin/
```

### Instalação via Pacote (Futuro)
```bash
# Em breve disponível nos repositórios
```

## 📖 Uso

### Modo Interativo Completo
```bash
# Interface vazia para busca interativa
cmd

# Interface com termo de busca inicial
cmd snap
```

### Modo Lista Simples
```bash
# Lista não-interativa de comandos
cmd --list fire
cmd -l python
```

### Outros Modos
```bash
# Mostrar histórico de execuções
cmd --history
cmd -H

# Mostrar documentação completa
cmd --docs
cmd -d

# Mostrar ajuda
cmd --help
cmd -h
```

## 🎮 Atalhos e Navegação

| Tecla | Ação |
|-------|------|
| `↑ ↓` | Navegar entre comandos |
| `Enter` | Executar comando selecionado |
| `Backspace` | Apagar caractere da busca |
| `Ctrl+C` | Sair do programa |
| `Home` | Ir para primeiro resultado |
| `End` | Ir para último resultado |

## 🌍 Internacionalização

O script detecta automaticamente o idioma do sistema baseado na variável `$LANG`:

- **Português**: Ativado quando `LANG` contém `pt_` (ex: `pt_BR.UTF-8`)
- **Inglês**: Idioma padrão (fallback)

Para forçar um idioma específico:
```bash
# Forçar Português
LANG=pt_BR.UTF-8 cmd

# Forçar Inglês
LANG=en_US.UTF-8 cmd
```

## ⚙️ Configuração

### Variáveis de Configuração
As seguintes variáveis podem ser ajustadas no código:

```bash
# Número máximo de resultados exibidos
MAX_RESULTS=35

# Número de comandos visíveis na interface
SHOW_COUNT=10

# Arquivo de histórico
HISTORY_FILE="$HOME/.cmd_history"

# Tamanho máximo do histórico
HISTORY_MAX=1000
```

### Cores Personalizadas
O script usa códigos ANSI para cores. Você pode personalizar:

```bash
RED='\033[0;31m'      # Comando selecionado
GREEN='\033[0;32m'    # Texto destacado na busca
YELLOW='\033[1;33m'   # Texto de busca
BLUE='\033[0;34m'     # Contadores e informações
MAGENTA='\033[0;35m'  # Instruções
CYAN='\033[0;36m'     # Título
```

## 🔧 Como Funciona

### Algoritmo de Busca
1. **Coleta**: Obtém todos os comandos executáveis do PATH
2. **Indexação**: Remove duplicados e ordena alfabeticamente
3. **Filtragem**: Busca substring case-insensitive em tempo real
4. **Apresentação**: Exibe resultados com destaque para matches

### Fluxo do Programa
```
Início → Verifica modo → Coleta comandos → Loop principal
     ↓                            ↑
  Execução ← Seleção usuário ← Interface
```

## 📊 Performance

- **Inicialização**: < 0.1s (cache de comandos do PATH)
- **Busca**: Instantânea (filtragem em memória)
- **Memória**: < 5MB (depende do número de comandos no PATH)

## 🛠️ Desenvolvimento

### Estrutura do Código
```
cmd-fuzzy-finder/
├── cmd                    # Script principal
├── README.md             # Esta documentação
├── LICENSE               # Licença GPLv3
└── examples/             # Exemplos de uso
```

### Adicionando Novos Idiomas
Para adicionar suporte a um novo idioma:

1. Adicione uma nova condição na detecção de `$LANG`:
```bash
elif [[ "${LANG,,}" =~ es_ ]]; then
    # Mensagens em Espanhol
    MESSAGES=(
        [title]="=== Buscador Difuso de Comandos ==="
        # ... demais mensagens
    )
```

2. Traduza todas as chaves do array `MESSAGES`

### Testando
```bash
# Teste básico
./cmd --help

# Teste de funcionalidade
./cmd --list bash

# Teste de internacionalização
LANG=pt_BR.UTF-8 ./cmd
LANG=en_US.UTF-8 ./cmd
```

## 🤝 Contribuindo

Contribuições são bem-vindas! Por favor:

1. Fork o repositório
2. Crie uma branch para sua feature (`git checkout -b feature/incrivel`)
3. Commit suas mudanças (`git commit -am 'Adiciona feature incrível'`)
4. Push para a branch (`git push origin feature/incrivel`)
5. Abra um Pull Request

### Áreas para Contribuição
- ✅ Adicionar novos idiomas
- ✅ Melhorar performance
- ✅ Novas features
- ✅ Correção de bugs
- ✅ Melhor documentação

## 📝 Licença

Este projeto está licenciado sob a **GPLv3**. Veja o arquivo [LICENSE](LICENSE) para detalhes.

```
Copyright (C) 2024 Felipe Facundes

Este programa é software livre: você pode redistribuí-lo e/ou modificar
sob os termos da GNU General Public License conforme publicada pela
Free Software Foundation, seja versão 3 da Licença, ou
(a seu critério) qualquer versão posterior.
```

## 🙏 Créditos

- **Autor**: [Felipe Facundes](https://github.com/felipefacundes)
- **Inspiração**: Ferramentas como `fzf`, `rofi`, e `dmenu`
- **Contribuidores**: [Lista de contribuidores](https://github.com/felipefacundes/cmd-fuzzy-finder/graphs/contributors)

## 🐛 Reportando Bugs

Encontrou um bug? Por favor:

1. Verifique se já existe um issue aberto
2. Use o template de bug report
3. Inclua informações do sistema:
   ```bash
   echo "Sistema: $(uname -a)"
   echo "Bash: $(bash --version | head -1)"
   echo "PATH: $(echo $PATH | tr ':' '\n' | wc -l) diretórios"
   ```

## 🌟 Estrelas

Se você achou esta ferramenta útil, considere dar uma ⭐ no repositório!

## 📞 Suporte

- **Issues**: [GitHub Issues](https://github.com/felipefacundes/cmd-fuzzy-finder/issues)
- **Discussões**: [GitHub Discussions](https://github.com/felipefacundes/cmd-fuzzy-finder/discussions)
- **Email**: [felipe.facundes@gmail.com](mailto:felipe.facundes@gmail.com)

## 📈 Roadmap

- [ ] Suporte a plugins
- [ ] Cache persistente de comandos
- [ ] Integração com ZSH/Fish
- [ ] Interface TUI aprimorada
- [ ] Modo batch para scripts
- [ ] Mais idiomas (ES, FR, DE, etc.)

---

<p align="center">
  <em>Encontre comandos mais rápido, trabalhe de forma mais inteligente 🚀</em>
</p>