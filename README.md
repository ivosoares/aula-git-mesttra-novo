# Apostila: Introdução ao Git e GitHub

## Índice
1. [Introdução](#introdução)
2. [O que é Git?](#o-que-é-git)
3. [O que é GitHub?](#o-que-é-github)
4. [Instalação e Configuração](#instalação-e-configuração)
5. [Conceitos Fundamentais](#conceitos-fundamentais)
6. [Comandos Básicos do Git](#comandos-básicos-do-git)
7. [Trabalhando com GitHub](#trabalhando-com-github)
8. [Fluxo de Trabalho Básico](#fluxo-de-trabalho-básico)
9. [Branches (Ramificações)](#branches-ramificações)
10. [Colaboração em Equipe](#colaboração-em-equipe)
11. [Boas Práticas](#boas-práticas)
12. [Exercício Prático](#exercício-prático)
13. [Comandos de Emergência](#comandos-de-emergência)
14. [Glossário](#glossário)

---

## Introdução

### Por que aprender Git e GitHub?

Imagine que você está escrevendo um trabalho importante no Word. Você salva várias versões:

```
trabalho_v1.docx
trabalho_v2.docx
trabalho_v2_final.docx
trabalho_v2_final_agora_vai.docx
trabalho_v2_final_definitivo.docx
```

**Problemas:**
- ❌ Muitos arquivos duplicados
- ❌ Difícil saber o que mudou em cada versão
- ❌ Impossível trabalhar em equipe sem conflitos
- ❌ Risco de perder tudo

**Solução: Git!**

Com Git você tem:
- ✅ Uma única pasta com seu projeto
- ✅ Histórico completo de todas as alterações
- ✅ Possibilidade de voltar no tempo
- ✅ Trabalho em equipe organizado
- ✅ Backup seguro na nuvem (GitHub)

### Cenários Reais de Uso

**1. Desenvolvedor Solo:**
- Controle de versões do projeto
- Backup automático
- Histórico de mudanças

**2. Equipe de Desenvolvimento:**
- Vários desenvolvedores no mesmo projeto
- Cada um trabalha em funcionalidades diferentes
- Integração organizada do código

**3. Projetos Open Source:**
- Qualquer pessoa pode contribuir
- Histórico transparente
- Revisão de código

---

## O que é Git?

### Definição

**Git** é um **sistema de controle de versão distribuído** criado por Linus Torvalds em 2005.

### Em palavras simples

Git é como uma **máquina do tempo** para seu código:
- Salva "fotos" (commits) do seu projeto ao longo do tempo
- Permite voltar a qualquer versão anterior
- Mostra exatamente o que foi alterado
- Permite criar linhas alternativas de desenvolvimento (branches)

### Analogia: Git como um Caderno de Notas

Imagine um caderno onde você:
1. **Escreve** suas anotações (código)
2. **Tira fotos** das páginas importantes (commit)
3. Pode **voltar** e ver qualquer foto antiga
4. Pode criar **cadernos paralelos** para temas diferentes (branches)
5. Pode **juntar** anotações de diferentes cadernos (merge)

### Características Principais

**1. Distribuído**
- Cada desenvolvedor tem uma cópia completa do histórico
- Não depende de servidor central para funcionar

**2. Rápido**
- Operações locais são muito rápidas
- Commits, branches e merges são instantâneos

**3. Seguro**
- Impossível perder código commitado
- Histórico imutável e rastreável

---

## O que é GitHub?

### Definição

**GitHub** é uma **plataforma online** para hospedar repositórios Git. É como o "Google Drive" do código.

### Git vs GitHub

| Git | GitHub |
|-----|--------|
| Software local (no seu PC) | Site na internet |
| Sistema de versionamento | Hospedagem de repositórios |
| Funciona offline | Precisa de internet |
| Gratuito e open source | Gratuito com recursos pagos |

### Analogia

```
Git = Microsoft Word (programa)
GitHub = Google Drive (armazenamento online)
```

Você usa o **Git** (programa) para gerenciar versões localmente.
Você usa o **GitHub** (site) para:
- Fazer backup na nuvem
- Compartilhar com outros
- Colaborar em equipe

### Recursos do GitHub

- 📦 **Repositórios**: Armazenamento de código
- 👥 **Colaboração**: Issues, Pull Requests
- 📊 **Gerenciamento**: Projects, Milestones
- 🔒 **Controle de Acesso**: Público/Privado
- 📚 **Documentação**: README, Wiki
- 🚀 **CI/CD**: GitHub Actions

---

## Instalação e Configuração

### 1. Instalar o Git

**Windows:**
1. Acesse: https://git-scm.com/download/win
2. Baixe e instale o instalador
3. Durante instalação, use opções padrão
4. Marque "Git Bash" e "Git GUI"

**Mac:**
```bash
# Usando Homebrew
brew install git
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get update
sudo apt-get install git
```

### 2. Verificar Instalação

Abra o terminal (Git Bash no Windows) e digite:

```bash
git --version
```

Deve aparecer algo como: `git version 2.40.0`

### 3. Configuração Inicial

**Configure seu nome e email (OBRIGATÓRIO):**

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu.email@exemplo.com"
```

**Por exemplo:**
```bash
git config --global user.name "João Silva"
git config --global user.email "joao.silva@email.com"
```

**⚠️ IMPORTANTE:** Use o **mesmo email** que você vai usar no GitHub!

### 4. Verificar Configuração

```bash
git config --list
```

Deve mostrar suas configurações.

### 5. Configurações Opcionais (mas recomendadas)

```bash
# Editor padrão (VS Code)
git config --global core.editor "code --wait"

# Cores no terminal
git config --global color.ui true

# Nome da branch padrão
git config --global init.defaultBranch main
```

---

## Conceitos Fundamentais

### 1. Repositório (Repository)

**O que é?** Uma pasta que contém seu projeto + histórico Git.

```
meu-projeto/
├── .git/           ← Pasta oculta com histórico
├── index.html
├── style.css
└── script.js
```

**Tipos:**
- **Repositório Local**: No seu computador
- **Repositório Remoto**: No GitHub (na nuvem)

### 2. Commit

**O que é?** Um "checkpoint" ou "foto" do seu projeto em um momento específico.

**Analogia:** Salvar jogo em um videogame.

Cada commit tem:
- **Hash**: Identificador único (ex: `a3b2c1d`)
- **Autor**: Quem fez
- **Data**: Quando foi feito
- **Mensagem**: Descrição do que mudou
- **Snapshot**: Estado completo dos arquivos

### 3. Working Directory, Staging Area e Repository

**Fluxo de trabalho Git:**

```
Working Directory  →  Staging Area  →  Repository
   (modificado)      (git add)       (git commit)
      📝                  📋               📦
```

**1. Working Directory (Diretório de Trabalho)**
- Seus arquivos normais
- Onde você edita o código

**2. Staging Area (Área de Preparação)**
- "Caixa de preparação"
- Arquivos prontos para commit
- Use `git add` para colocar aqui

**3. Repository (Repositório)**
- Histórico de commits
- Versões salvas permanentemente

**Exemplo prático:**
```bash
# 1. Você edita arquivo.txt (Working Directory)
# 2. Adiciona à staging area
git add arquivo.txt

# 3. Faz commit (salva no repositório)
git commit -m "Adiciona arquivo.txt"
```

### 4. Branch (Ramificação)

**O que é?** Uma linha paralela de desenvolvimento.

**Analogia:** Universos paralelos do seu projeto.

```
main:     A -- B -- C -- D
                   \
feature:            E -- F
```

**Por que usar?**
- Desenvolver novas funcionalidades sem afetar o código principal
- Experimentar ideias
- Trabalhar em equipe sem conflitos

### 5. Merge (Junção)

**O que é?** Juntar duas branches.

```
main:     A -- B -- C ------- M
                   \         /
feature:            D -- E --
```

### 6. Clone

**O que é?** Copiar repositório remoto para seu computador.

```
GitHub (remoto)  →  clone  →  Seu PC (local)
```

### 7. Push e Pull

**Push**: Enviar commits locais para o remoto (GitHub)
```
Seu PC  →  push  →  GitHub
```

**Pull**: Baixar commits do remoto para local
```
GitHub  →  pull  →  Seu PC
```

---

## Comandos Básicos do Git

### 1. Inicializar Repositório

**Criar novo repositório Git:**
```bash
git init
```

Isso cria a pasta oculta `.git` no diretório atual.

### 2. Verificar Status

**Ver estado dos arquivos:**
```bash
git status
```

Mostra:
- Arquivos modificados
- Arquivos na staging area
- Arquivos não rastreados

### 3. Adicionar Arquivos (Staging)

**Adicionar arquivo específico:**
```bash
git add arquivo.txt
```

**Adicionar todos os arquivos:**
```bash
git add .
```

**Adicionar arquivos por tipo:**
```bash
git add *.html    # Todos os HTML
git add *.css     # Todos os CSS
```

### 4. Fazer Commit

**Commit com mensagem:**
```bash
git commit -m "Mensagem descritiva"
```

**Boas mensagens:**
```bash
git commit -m "Adiciona página de login"
git commit -m "Corrige bug no formulário"
git commit -m "Atualiza estilo do header"
```

**Más mensagens:**
```bash
git commit -m "mudanças"
git commit -m "alterações"
git commit -m "commit"
```

### 5. Ver Histórico

**Histórico completo:**
```bash
git log
```

**Histórico resumido:**
```bash
git log --oneline
```

**Histórico gráfico:**
```bash
git log --oneline --graph --all
```

### 6. Ver Diferenças

**Ver o que foi modificado:**
```bash
git diff
```

**Ver diferenças de arquivo específico:**
```bash
git diff arquivo.txt
```

### 7. Desfazer Alterações

**Descartar mudanças no working directory:**
```bash
git restore arquivo.txt
```

**Remover arquivo da staging area:**
```bash
git restore --staged arquivo.txt
```

**Voltar para commit anterior (CUIDADO!):**
```bash
git reset --hard HEAD~1
```

---

## Trabalhando com GitHub

### 1. Criar Conta no GitHub

1. Acesse: https://github.com
2. Clique em "Sign up"
3. Preencha: username, email, senha
4. Verifique email
5. Complete perfil

### 2. Criar Repositório no GitHub

**Via Site:**
1. Clique em "New repository"
2. Nome do repositório: `meu-projeto`
3. Descrição (opcional)
4. Escolha: Public ou Private
5. ✅ Marque "Add README"
6. Clique em "Create repository"

### 3. Conectar Repositório Local ao GitHub

**Cenário 1: Repositório já existe localmente**

```bash
# Adicionar repositório remoto
git remote add origin https://github.com/seu-usuario/meu-projeto.git

# Verificar
git remote -v

# Enviar código
git push -u origin main
```

**Cenário 2: Clonar repositório existente**

```bash
git clone https://github.com/seu-usuario/meu-projeto.git
cd meu-projeto
```

### 4. Push (Enviar código)

```bash
# Enviar commits para GitHub
git push origin main
```

Na primeira vez:
```bash
git push -u origin main
```

O `-u` cria um "atalho", depois pode usar só:
```bash
git push
```

### 5. Pull (Baixar atualizações)

```bash
# Baixar e integrar mudanças
git pull origin main
```

Ou simplesmente:
```bash
git pull
```

### 6. Autenticação

**Token de Acesso Pessoal (recomendado):**

1. GitHub → Settings → Developer settings
2. Personal access tokens → Tokens (classic)
3. Generate new token
4. Marque: `repo` (Full control)
5. Copie o token (guarde em lugar seguro!)
6. Use como senha ao fazer push

**Ou use GitHub CLI:**
```bash
gh auth login
```

---

## Fluxo de Trabalho Básico

### Workflow Diário

```bash
# 1. Atualizar código local
git pull

# 2. Fazer alterações nos arquivos
# (editar, criar, deletar arquivos)

# 3. Ver o que mudou
git status

# 4. Adicionar arquivos
git add .

# 5. Fazer commit
git commit -m "Descrição das mudanças"

# 6. Enviar para GitHub
git push
```

### Exemplo Completo Passo a Passo

**Situação:** Criar projeto biblioteca e enviar para GitHub

```bash
# Criar pasta do projeto
mkdir biblioteca
cd biblioteca

# Inicializar Git
git init

# Criar arquivo HTML
echo "<h1>Biblioteca</h1>" > index.html

# Ver status
git status
# Mostra: index.html não rastreado

# Adicionar à staging area
git add index.html

# Ver status novamente
git status
# Mostra: index.html pronto para commit

# Fazer commit
git commit -m "Adiciona página inicial"

# Ver histórico
git log --oneline

# Criar repositório no GitHub (via site)
# Copiar URL: https://github.com/usuario/biblioteca.git

# Conectar com remoto
git remote add origin https://github.com/usuario/biblioteca.git

# Enviar código
git push -u origin main
```

---

## Branches (Ramificações)

### Por que usar Branches?

**Cenário:** Você está desenvolvendo uma nova funcionalidade, mas precisa corrigir um bug urgente no código que está em produção.

**Sem branches:** 😰
- Precisa desfazer todas as mudanças
- Perder trabalho
- Bagunça

**Com branches:** 😎
- Cria branch para funcionalidade nova
- Volta para main
- Corrige bug
- Depois volta para funcionalidade

### Comandos de Branch

**Listar branches:**
```bash
git branch
```

**Criar nova branch:**
```bash
git branch nome-da-branch
```

**Trocar de branch:**
```bash
git checkout nome-da-branch
```

**Criar e trocar (atalho):**
```bash
git checkout -b nome-da-branch
```

**Deletar branch:**
```bash
git branch -d nome-da-branch
```

### Exemplo Prático

```bash
# Listar branches atuais
git branch
# * main

# Criar branch para nova funcionalidade
git checkout -b feature-login

# Fazer alterações
echo "Login page" > login.html
git add login.html
git commit -m "Adiciona página de login"

# Voltar para main
git checkout main

# Ver que login.html não existe aqui!
ls

# Voltar para feature-login
git checkout feature-login

# login.html existe aqui!
ls
```

### Merge (Juntar Branches)

**Quando estiver pronto, junte a branch na main:**

```bash
# Ir para a branch de destino (main)
git checkout main

# Juntar branch feature
git merge feature-login

# Deletar branch após merge (opcional)
git branch -d feature-login
```

### Fluxo Completo com Branches

```bash
# 1. Criar branch para nova feature
git checkout -b feature-carrinho

# 2. Desenvolver
# ... fazer mudanças ...
git add .
git commit -m "Adiciona carrinho de compras"

# 3. Voltar para main
git checkout main

# 4. Atualizar main
git pull

# 5. Fazer merge
git merge feature-carrinho

# 6. Enviar para GitHub
git push

# 7. Deletar branch local
git branch -d feature-carrinho
```

---

## Colaboração em Equipe

### 1. Fork

**O que é?** Copiar repositório de outra pessoa para sua conta.

**Quando usar:** Contribuir para projetos open source.

**Como fazer:**
1. Vá no repositório no GitHub
2. Clique em "Fork" (canto superior direito)
3. Clone seu fork para seu PC

### 2. Pull Request

**O que é?** Pedido para adicionar suas mudanças ao repositório original.

**Fluxo:**
```
1. Fork do repositório
2. Clone para seu PC
3. Crie branch
4. Faça mudanças
5. Push para seu fork
6. Abra Pull Request no GitHub
7. Aguarda revisão e aprovação
```

**Criar Pull Request:**
1. Vá no GitHub, no seu fork
2. Clique em "Pull Request"
3. Escreva título e descrição
4. Clique em "Create Pull Request"

### 3. Issues

**O que são?** Sistema de rastreamento de bugs e tarefas.

**Criar Issue:**
1. Vá no repositório
2. Clique em "Issues"
3. "New Issue"
4. Descreva o problema ou sugestão

### 4. Colaboradores

**Adicionar colaborador:**
1. Settings do repositório
2. Collaborators
3. Add people
4. Digite username

---

## Boas Práticas

### 1. Commits

✅ **Faça commits pequenos e frequentes**
```bash
# Bom
git commit -m "Adiciona botão de login"
git commit -m "Estiliza botão de login"
git commit -m "Adiciona validação do formulário"

# Ruim
git commit -m "Faz várias coisas no projeto"
```

✅ **Mensagens descritivas**
```bash
# Bom
git commit -m "Corrige bug no cálculo de desconto"
git commit -m "Adiciona animação no menu hambúrguer"

# Ruim
git commit -m "fix"
git commit -m "mudanças"
```

✅ **Use verbos no imperativo**
```bash
# Bom
"Adiciona", "Remove", "Atualiza", "Corrige"

# Evite
"Adicionado", "Removido", "Adicionando"
```

### 2. Branches

✅ **Nomes descritivos**
```bash
# Bom
feature-login
bugfix-header
hotfix-payment

# Ruim
teste
branch1
nova-branch
```

✅ **Convenções de nomenclatura:**
- `feature/` - Nova funcionalidade
- `bugfix/` - Correção de bug
- `hotfix/` - Correção urgente
- `docs/` - Documentação

Exemplos:
```bash
feature/carrinho-compras
bugfix/formulario-validacao
hotfix/falha-pagamento
```

### 3. .gitignore

**O que é?** Arquivo que lista o que NÃO deve ser versionado.

**Criar .gitignore:**
```bash
# No raiz do projeto
touch .gitignore
```

**Exemplo de .gitignore:**
```
# Node modules
node_modules/

# Logs
*.log

# Variáveis de ambiente
.env

# IDE
.vscode/
.idea/

# Sistema operacional
.DS_Store
Thumbs.db

# Build
dist/
build/
```

### 4. README.md

**O que é?** Arquivo de documentação do projeto.

**Estrutura básica:**
```markdown
# Nome do Projeto

Descrição breve do que o projeto faz.

## Tecnologias

- HTML5
- CSS3
- JavaScript
- Bootstrap

## Como executar

1. Clone o repositório
2. Abra index.html no navegador

## Autor

Seu Nome - [GitHub](https://github.com/seu-usuario)
```

---

## Exercício Prático

### 🎯 Objetivo

Criar o projeto da Biblioteca, versionar com Git e hospedar no GitHub.

### 📋 Passo a Passo

#### Parte 1: Configuração Inicial

1. **Verifique se Git está instalado**
```bash
git --version
```

2. **Configure seu nome e email (se ainda não fez)**
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

3. **Crie conta no GitHub** (se ainda não tem)
- Acesse https://github.com
- Faça cadastro

#### Parte 2: Criando Repositório Local

4. **Navegue até a pasta do projeto biblioteca**
```bash
cd caminho/para/biblioteca
```

5. **Inicialize Git**
```bash
git init
```

6. **Verifique status**
```bash
git status
```

7. **Crie arquivo .gitignore**
```bash
echo "node_modules/" > .gitignore
```

8. **Adicione todos os arquivos**
```bash
git add .
```

9. **Faça primeiro commit**
```bash
git commit -m "Commit inicial - estrutura do projeto biblioteca"
```

10. **Veja o histórico**
```bash
git log --oneline
```

#### Parte 3: Conectando com GitHub

11. **Crie repositório no GitHub**
- Vá em github.com
- Clique em "New repository"
- Nome: `biblioteca-sistema`
- Public
- NÃO marque "Initialize with README"
- Create repository

12. **Copie a URL do repositório**
```
https://github.com/seu-usuario/biblioteca-sistema.git
```

13. **Conecte repositório local ao remoto**
```bash
git remote add origin https://github.com/seu-usuario/biblioteca-sistema.git
```

14. **Verifique conexão**
```bash
git remote -v
```

15. **Envie código para GitHub**
```bash
git branch -M main
git push -u origin main
```

16. **Atualize página do GitHub e veja seu código lá!**

#### Parte 4: Trabalhando com Branches

17. **Crie branch para nova funcionalidade**
```bash
git checkout -b feature-cadastro-autores
```

18. **Faça alterações** (crie arquivos de autores)

19. **Adicione e commite**
```bash
git add .
git commit -m "Adiciona CRUD de autores"
```

20. **Envie branch para GitHub**
```bash
git push origin feature-cadastro-autores
```

21. **Volte para main**
```bash
git checkout main
```

22. **Faça merge**
```bash
git merge feature-cadastro-autores
```

23. **Envie main atualizada**
```bash
git push
```

#### Parte 5: Simulando Trabalho em Equipe

24. **Faça alteração direto no GitHub** (simula colega)
- Vá no arquivo index.html no GitHub
- Clique no lápis (editar)
- Faça uma mudança
- Commit changes

25. **No seu PC, puxe as alterações**
```bash
git pull
```

26. **Veja que seu código local foi atualizado!**

### ✅ Checklist do Exercício

- [ ] Git configurado com nome e email
- [ ] Repositório inicializado localmente
- [ ] Primeiro commit realizado
- [ ] Repositório criado no GitHub
- [ ] Código enviado para GitHub
- [ ] Branch criada e usada
- [ ] Merge realizado
- [ ] Pull executado com sucesso
- [ ] Código visível no GitHub

---

## Comandos de Emergência

### 😱 "Comitei arquivo errado!"

**Desfazer último commit (mantém alterações):**
```bash
git reset --soft HEAD~1
```

### 😱 "Quero descartar todas as mudanças!"

```bash
git restore .
```

### 😱 "Commitei na branch errada!"

```bash
# Criar branch nova com os commits
git branch nome-correto

# Voltar main para antes dos commits
git reset --hard origin/main
```

### 😱 "Conflito no merge!"

```bash
# Ver arquivos com conflito
git status

# Abrir arquivo, resolver conflitos manualmente
# Procure por: <<<<<<, ======, >>>>>>

# Depois de resolver:
git add arquivo-resolvido.txt
git commit -m "Resolve conflitos"
```

### 😱 "Esqueci de criar branch!"

```bash
# Criar branch levando as mudanças
git stash
git checkout -b nova-branch
git stash pop
```

### 😱 "Quero ver código de commit antigo"

```bash
# Ver histórico
git log --oneline

# Voltar temporariamente
git checkout hash-do-commit

# Voltar para presente
git checkout main
```

---

## Glossário

| Termo | Significado |
|-------|-------------|
| **Repository** | Pasta com projeto + histórico Git |
| **Commit** | Snapshot/foto do projeto |
| **Branch** | Linha paralela de desenvolvimento |
| **Merge** | Juntar branches |
| **Clone** | Copiar repositório remoto |
| **Fork** | Copiar repositório de outra pessoa |
| **Push** | Enviar commits para remoto |
| **Pull** | Baixar commits do remoto |
| **Remote** | Repositório na nuvem (GitHub) |
| **Origin** | Nome padrão do remoto |
| **Main/Master** | Branch principal |
| **HEAD** | Referência ao commit atual |
| **Staging Area** | Área de preparação para commit |
| **Working Directory** | Seus arquivos atuais |
| **Hash** | Identificador único do commit |
| **.git** | Pasta oculta com dados do Git |
| **.gitignore** | Lista de arquivos ignorados |
| **README** | Documentação do projeto |

---

## Comandos Essenciais - Resumo

### Configuração
```bash
git config --global user.name "Nome"
git config --global user.email "email"
git config --list
```

### Básico
```bash
git init                    # Inicializar repositório
git status                  # Ver status
git add arquivo.txt         # Adicionar arquivo
git add .                   # Adicionar todos
git commit -m "mensagem"    # Fazer commit
git log                     # Ver histórico
git log --oneline          # Histórico resumido
```

### Remoto
```bash
git remote add origin URL   # Conectar com remoto
git remote -v              # Ver remotos
git push origin main       # Enviar
git pull origin main       # Baixar
git clone URL              # Clonar
```

### Branches
```bash
git branch                 # Listar branches
git branch nome           # Criar branch
git checkout nome         # Trocar branch
git checkout -b nome      # Criar e trocar
git merge nome            # Juntar branch
git branch -d nome        # Deletar branch
```

### Desfazer
```bash
git restore arquivo       # Descartar mudanças
git restore --staged      # Remover da staging
git reset --soft HEAD~1   # Desfazer commit
```

---

## Recursos Úteis

### Documentação
- **Git Oficial**: https://git-scm.com/doc
- **GitHub Docs**: https://docs.github.com
- **Git Book**: https://git-scm.com/book/pt-br/v2

### Ferramentas
- **GitHub Desktop**: Interface gráfica para Git
- **GitKraken**: Cliente Git visual
- **VS Code**: Git integrado

### Prática
- **Learn Git Branching**: https://learngitbranching.js.org/
- **GitHub Skills**: https://skills.github.com/

### Cheat Sheets
- **GitHub Cheat Sheet**: https://education.github.com/git-cheat-sheet-education.pdf

---

## Próximos Passos

Depois de dominar o básico, explore:

1. **GitHub Actions** - Automação e CI/CD
2. **GitHub Pages** - Hospedar sites estáticos
3. **Git Rebase** - Reescrever histórico
4. **Git Cherry-pick** - Aplicar commits específicos
5. **Git Submodules** - Repositórios dentro de repositórios
6. **Git Hooks** - Automação local

---

## Dicas Finais

### ✅ Faça
- Commit frequentemente
- Use mensagens descritivas
- Crie branches para features
- Sincronize com frequência (pull/push)
- Use .gitignore
- Documente no README

### ❌ Evite
- Commitar arquivos grandes (vídeos, binários)
- Commitar senhas ou tokens
- Trabalhar direto na main
- Fazer commits gigantes
- Esquecer de fazer pull antes de push

---

## Conclusão

**Parabéns!** 🎉

Você aprendeu os fundamentos de Git e GitHub! Agora você pode:
- ✅ Versionar seus projetos
- ✅ Trabalhar em equipe
- ✅ Manter backup na nuvem
- ✅ Contribuir para projetos open source

**Lembre-se:** Git pode parecer confuso no início, mas com prática fica natural. Não tenha medo de errar - é impossível perder código commitado!

**Continue praticando!** Quanto mais você usar, mais confortável vai ficar.

**Bons commits! # aula-git-mesttra
