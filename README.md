# My Joomla Gitignore
*[🇧🇷 Leia em Português](#-em-português) | [🇺🇸 Read in English](#-in-english)*

---

## 🇧🇷 Em Português

Arquivos `.gitignore` prontos para uso em projetos Joomla nas versões **3, 4, 5 e 6**. Estes arquivos ignoram os arquivos padrão do core e incluem um escopo otimizado para sistemas operacionais, IDEs e ferramentas de Inteligência Artificial / agentes de código.

### 📋 Versões Disponíveis

| Arquivo | Versão do Joomla | Descrição | Link Direto (Raw) |
|---|---|---|---|
| [joomla3.gitignore](joomla3.gitignore) | Joomla 3.x | Templates: Protostar, Beez3, Hathor, Isis | [Raw Link](https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla3.gitignore) |
| [joomla4.gitignore](joomla4.gitignore) | Joomla 4.x | Templates: Cassiopeia, Atum. Inclui API REST | [Raw Link](https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla4.gitignore) |
| [joomla5.gitignore](joomla5.gitignore) | Joomla 5.x | Atualizado com guidedtours, schemaorg, compat | [Raw Link](https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla5.gitignore) |
| [joomla6.gitignore](joomla6.gitignore) | Joomla 6.x | Versão mais recente (Joomla 6.1 Nyota) | [Raw Link](https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla6.gitignore) |

### 🚀 Como Usar

#### Opção 1: Download direto via terminal (Recomendado)

**No Linux, macOS ou Git Bash:**
```bash
# Para Joomla 6:
curl -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla6.gitignore

# Para Joomla 5:
curl -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla5.gitignore

# Para Joomla 4:
curl -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla4.gitignore

# Para Joomla 3:
curl -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla3.gitignore
```

**No Windows PowerShell:**
> [!TIP]
> No PowerShell do Windows, use `curl.exe` (com a extensão `.exe`) para chamar o binário nativo do curl e evitar conflito com o alias interno do PowerShell (`Invoke-WebRequest`).
```powershell
# Para Joomla 6:
curl.exe -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla6.gitignore

# Para Joomla 5:
curl.exe -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla5.gitignore

# Para Joomla 4:
curl.exe -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla4.gitignore

# Para Joomla 3:
curl.exe -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla3.gitignore
```

#### Opção 2: Cópia manual
1. Abra o arquivo correspondente à sua versão do Joomla.
2. Copie todo o conteúdo para um arquivo chamado `.gitignore` na raiz do projeto.
3. Certifique-se de salvar o arquivo em codificação **UTF-8 sem BOM**.

---

### ⚠️ Aplicando em Repositórios Existentes (Cuidado Importante)

Se o seu repositório já estava rastreando arquivos do core do Joomla antes de adicionar o `.gitignore`, apenas adicionar o arquivo não remove o que já está versionado.

Para desindexar os arquivos sem apagá-los do seu disco local, execute linha a linha no seu terminal:

```bash
git rm -r --cached .
git add .
git commit -m "chore: aplica novo .gitignore e limpa arquivos ignorados do indice"
```

> [!CAUTION]
> **ATENÇÃO AO FAZER PUSH EM PRODUÇÃO OU EQUIPES**:
> O comando `git rm -r --cached .` preserva os arquivos na sua máquina local, mas registra uma **remoção** no histórico do Git. 
> - Se você enviar (`git push`) esse commit para um servidor de produção ou outro colega rodar `git pull`, **o Git apagará do disco de produção todos os arquivos que deixaram de ser rastreados**, o que pode derrubar o site se o core não estiver instalado de outra forma.
> - **Recomendação**: Crie uma branch de teste e faça backup completo antes de aplicar essa limpeza em repositórios que já estejam em produção.

---

### 🪟 Dicas Específicas para Usuários Windows

1. **PowerShell vs `curl`**: No PowerShell clássico (5.1), o comando `curl` é um alias para `Invoke-WebRequest` e não aceita o parâmetro `-o`. Use sempre `curl.exe` ou `Invoke-WebRequest -Uri "URL" -OutFile ".gitignore"`.
2. **Separador de Comandos no Windows**: O PowerShell 5.1 não suporta o operador `&&` para encadear comandos. Execute os comandos separadamente em linhas distintas ou use ponto e vírgula (`;`).
3. **Maiúsculas vs Minúsculas (Case Sensitivity no Windows / NTFS)**:
   - O sistema de arquivos do Windows (NTFS) **ignora** maiúsculas e minúsculas (`index.php` = `INDEX.PHP`), mas os servidores de produção (Linux) são estritamente sensíveis ao caso (*case-sensitive*).
   - O `.gitignore` no Linux diferencia maiúsculas de minúsculas. Por isso, as regras deste repositório seguem rigorosamente a caixa padrão do core do Joomla (letras minúsculas, ex: `/administrator/templates/atum/`).
   - Se você renomear pastas ou arquivos alterando apenas a caixa no Windows, o Git local não detectará a mudança automaticamente. Use sempre `git mv -f NomeAntigo.php nomeantigo.php`.
   - Ao executar `git rm -r --cached .` no Windows, o `git add .` reindexará os arquivos com a caixa exata gravada no NTFS. Se o repositório remoto foi criado no Linux com caixas diferentes, isso pode registrar renames inesperados.
4. **Codificação UTF-8 SEM BOM**: Ao criar ou editar arquivos `.gitignore` ou extensões Joomla no Windows, certifique-se de salvar em **UTF-8 sem BOM** (no VS Code, selecione "UTF-8", nunca "UTF-8 with BOM"). Caracteres BOM causam erro fatal de *headers already sent* no PHP do Joomla.

---

### 📝 Observações Importantes

- **Segurança e Senhas**: Arquivos sensíveis como `/configuration.php`, `.env` e `.htpasswd` são sempre ignorados para evitar vazamento de credenciais e chaves no repositório.
- **Idiomas e Overrides**: As pastas `/language/`, `/administrator/language/` e suas subpastas de overrides (`overrides/*.ini`) **não são ignoradas**, garantindo o versionamento de traduções e novos pacotes de idioma (como `pt-BR`).
- **Extensões de Terceiros**: Apenas as extensões nativas do core do Joomla são ignoradas. Componentes, módulos e plugins desenvolvidos sob medida ou instalados de terceiros são rastreados automaticamente.
- **Overrides de Templates**: As pastas `html/` dos templates padrão do frontend e backend (`cassiopeia/html/`, `atum/html/`) **são rastreadas** no Joomla 4, 5 e 6, permitindo versionar suas customizações visuais.
- **Uploads e Mídia**: A pasta `/images/` é ignorada por padrão para evitar o armazenamento de uploads e mídias pesadas de usuários no histórico do Git.
- **Ferramentas de IA e IDEs**: Pastas e arquivos gerados por agentes de código e IDEs (como Antigravity, `.agents/`, `.agent`, `.gemini/`, `.antigravity/`, Cursor, Claude Code, Cline, Roo, Windsurf, Copilot, `.vscode/` e `.idea/`) vêm bloqueados por padrão.

### 📂 Exemplo do que é rastreado

Exemplos do que **será** rastreado pelo Git:
- `/templates/meu_template_customizado/`
- `/plugins/system/minha_extensao/`
- `/administrator/components/com_minha_extensao/`
- `/language/pt-BR/` (e demais pacotes de idioma)
- `/administrator/templates/atum/html/` (overrides do backend)
- `/templates/cassiopeia/html/` (overrides do frontend)

---

## 🇺🇸 In English

Ready-to-use `.gitignore` files for Joomla projects in versions **3, 4, 5, and 6**. These files ignore core files and provide an optimized scope for operating systems, IDEs, and AI coding agents.

### 📋 Available Versions

| File | Joomla Version | Description | Direct Raw Link |
|---|---|---|---|
| [joomla3.gitignore](joomla3.gitignore) | Joomla 3.x | Templates: Protostar, Beez3, Hathor, Isis | [Raw Link](https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla3.gitignore) |
| [joomla4.gitignore](joomla4.gitignore) | Joomla 4.x | Templates: Cassiopeia, Atum. Includes REST API | [Raw Link](https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla4.gitignore) |
| [joomla5.gitignore](joomla5.gitignore) | Joomla 5.x | Updated with guided tours, schema.org, compat | [Raw Link](https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla5.gitignore) |
| [joomla6.gitignore](joomla6.gitignore) | Joomla 6.x | Latest version (Joomla 6.1 Nyota) | [Raw Link](https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla6.gitignore) |

### 🚀 How to Use

#### Option 1: Direct terminal download (Recommended)

**On Linux, macOS, or Git Bash:**
```bash
# For Joomla 6:
curl -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla6.gitignore

# For Joomla 5:
curl -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla5.gitignore

# For Joomla 4:
curl -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla4.gitignore

# For Joomla 3:
curl -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla3.gitignore
```

**On Windows PowerShell:**
> [!TIP]
> In Windows PowerShell, use `curl.exe` (with the `.exe` extension) to call the native curl binary, avoiding conflicts with PowerShell's built-in alias (`Invoke-WebRequest`).
```powershell
# For Joomla 6:
curl.exe -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla6.gitignore

# For Joomla 5:
curl.exe -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla5.gitignore

# For Joomla 4:
curl.exe -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla4.gitignore

# For Joomla 3:
curl.exe -o .gitignore https://raw.githubusercontent.com/uzielweb/my-joomla-gitignore/main/joomla3.gitignore
```

#### Option 2: Manual copy
1. Open the file corresponding to your Joomla version.
2. Copy all content into a file named `.gitignore` at the project root.
3. Ensure the file is saved in **UTF-8 without BOM** encoding.

---

### ⚠️ Applying to Existing Repositories (Important Warning)

If your repository was already tracking Joomla core files prior to adding this `.gitignore`, simply adding the file will not un-track files that are already indexed.

To remove tracked files from Git without deleting them from your local disk, execute line by line in your terminal:

```bash
git rm -r --cached .
git add .
git commit -m "chore: apply new .gitignore and remove ignored files from index"
```

> [!CAUTION]
> **BE CAREFUL WHEN PUSHING TO PRODUCTION OR TEAMS**:
> The `git rm -r --cached .` command preserves files on your local machine, but records a **deletion** in Git history.
> - If you push this commit to a production server or a teammate runs `git pull`, **Git will physically delete all un-tracked files from their disk**, which can take down your live site.
> - **Recommendation**: Test this on a separate branch and take a full backup before applying index cleanup to production repositories.

---

### 🪟 Windows Specific Tips

1. **PowerShell vs `curl`**: In classic Windows PowerShell (5.1), `curl` is an alias for `Invoke-WebRequest` and will fail when using `-o`. Always use `curl.exe` or `Invoke-WebRequest -Uri "URL" -OutFile ".gitignore"`.
2. **Command Chaining on Windows**: PowerShell 5.1 does not support the `&&` operator. Run commands line by line or separate them with semicolons (`;`).
3. **Uppercase vs Lowercase (Case-Sensitivity on Windows / NTFS)**:
   - Windows filesystems (NTFS) are case-insensitive (`index.php` = `INDEX.PHP`), whereas Linux production servers are strictly case-sensitive.
   - `.gitignore` on Linux is case-sensitive, which is why all rules in this repository use exact Joomla core casing (lowercase, e.g., `/administrator/templates/atum/`).
   - If you rename a file changing only its case on Windows, Git won't notice it automatically. Always use `git mv -f OldName.php oldname.php`.
   - Running `git rm -r --cached .` on Windows causes `git add .` to reindex files matching current NTFS casing, which may produce unintended rename commits if the remote was created on Linux.
4. **UTF-8 without BOM Encoding**: When creating or editing files in Windows, ensure they are saved as **UTF-8 without BOM** (in VS Code, select "UTF-8", not "UTF-8 with BOM"). BOM characters cause fatal headers-already-sent errors in Joomla PHP.

---

### 📝 Important Notes

- **Security & Passwords**: Sensitive files such as `/configuration.php`, `.env`, and `.htpasswd` are always ignored to prevent leaking database credentials and secret keys into your repository.
- **Languages & Overrides**: The `/language/` and `/administrator/language/` folders (including `overrides/*.ini`) **are not ignored**, ensuring custom language packs (such as `pt-BR`, `es-ES`) and string overrides are tracked.
- **Third-party extensions**: Only standard core Joomla extensions are ignored. Any custom or third-party components, modules, and plugins you develop or install will be tracked automatically.
- **Template overrides**: Customizable `html/` folders inside default templates (`cassiopeia/html/`, `atum/html/`) **are tracked** on Joomla 4, 5, and 6, preserving your visual layout overrides.
- **Uploads & Media**: The `/images/` directory is ignored by default to keep heavy user uploads and media files out of the Git history.
- **AI Tools & IDEs**: Files and folders generated by coding agents and IDEs (such as Antigravity, `.agents/`, `.agent`, `.gemini/`, `.antigravity/`, Cursor, Claude Code, Cline, Roo, Windsurf, Copilot, `.vscode/` and `.idea/`) are locked down and ignored out of the box.

### 📂 What IS Tracked

Examples of what **will be** actively tracked by your Git repository:
- `/templates/my_custom_template/`
- `/plugins/system/my_super_plugin/`
- `/administrator/components/com_my_extension/`
- `/language/pt-BR/` (or any additional language pack)
- `/administrator/templates/atum/html/` (backend overrides)
- `/templates/cassiopeia/html/` (frontend overrides)

---

## 📄 Licença / License
Livre para uso. Contribuições são bem-vindas! / Free to use. Pull Requests are welcome!
