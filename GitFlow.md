# Fluxo de trabalho com Git e Pull Requests

Este repositório utiliza um fluxo Git simplificado para manter a documentação do sistema de psicólogos organizada, revisada e com histórico de alterações.

## 1. Branch principal

- `main`: contém a versão oficial e revisada da documentação.
- Não faça commits diretamente na `main`. Toda alteração deve entrar por meio de um Pull Request (PR), salvo uma exceção combinada por toda a equipe.

## 2. Nome das branches

Crie uma branch por tarefa ou conjunto pequeno de alterações relacionadas. Use nomes curtos, em minúsculas, sem acentos e com hífens.

Padrões recomendados:

- `docs/documento` — criação ou atualização de documentos.
- `diagram/diagrama` — criação ou alteração de diagramas.
- `fix/descricao` — correções de erros ou inconsistências.
- `refactor/descricao` — reorganização de pastas ou nomes sem mudança conceitual.

Exemplos:

- `docs/requisitos-funcionais`
- `diagram/casos-de-uso`
- `diagram/modelo-entidade-relacionamento`
- `fix/links-do-readme`
- `refactor/estrutura-de-pastas`

Prefira uma branch por tarefa, e não uma branch permanente por integrante. Assim, cada PR fica focado e fácil de revisar.

## 3. Fluxo de trabalho

### Passo 1 — Atualize a `main`

```bash
git switch main
git pull origin main
```

### Passo 2 — Crie uma branch

```bash
git switch -c 'docs'/'requisitos-funcionais'
```

Substitua o nome pelo da sua tarefa seguindo o padrão acima.

### Passo 3 — Faça as alterações

- Salve os arquivos na pasta correspondente ao assunto.
- Use nomes consistentes e descritivos.
- Quando possível, mantenha o arquivo-fonte editável do diagrama ou documento junto do PDF final.
- Atualize o `README.md` se adicionar, remover ou renomear documentos e links.
- Não inclua dados reais ou identificáveis de pacientes; use exemplos fictícios.

### Passo 4 — Revise e registre as alterações

```bash
git status
git diff --stat
git add .
git commit -m "docs: adiciona requisitos funcionais"
```

Adicione apenas os arquivos relacionados à tarefa. Se houver vários arquivos relacionados, informe os caminhos correspondentes no `git add`.

Sugestões de mensagens de commit:

- `docs: adiciona regras de negócio`
- `diagram: cria diagrama de casos de uso`
- `fix: corrige links da documentação`
- `refactor: reorganiza pastas de modelagem`

### Passo 5 — Envie a branch

```bash
git push -u origin docs/requisitos-funcionais
```
Substitua o nome pela sua branch

### Passo 6 — Abra um Pull Request

No GitHub, abra um PR da sua branch para `main`. O PR deve conter:

- **Título:** claro e específico, por exemplo `docs: adiciona requisitos funcionais`.
- **Resumo:** o que foi criado ou alterado e por quê.
- **Arquivos afetados:** informe os caminhos dos documentos modificados.
- **Checklist:** confirme que revisou o PDF, os nomes, a pasta de destino e os links relacionados.
- **Revisor:** solicite a revisão de pelo menos um outro integrante.

### Passo 7 — Revisão e merge

O revisor deve conferir se:

- Os arquivos estão nas pastas corretas e têm nomes consistentes.
- O conteúdo está legível e coerente com os requisitos e documentos relacionados.
- Os PDFs abrem corretamente e correspondem à versão final pretendida.
- O `README.md` e outros links foram atualizados quando necessário.
- Não foram incluídos dados pessoais ou informações confidenciais.

Se forem solicitadas mudanças, faça-as na mesma branch, crie novos commits e envie-os. Após a aprovação, faça o merge do PR para `main`. Depois do merge, a branch pode ser excluída.

## 4. Como identificar os arquivos alterados

O GitHub mostra os arquivos e caminhos alterados na aba **Files changed** do PR. No resumo do PR, liste os caminhos principais, por exemplo:

```text
02-requisitos/requisitos-funcionais.pdf
README.md
```

Não é necessário colocar o caminho inteiro no título do PR; deixe o título curto e registre os caminhos no corpo do PR.

## 5. Se duas pessoas alterarem a mesma documentação

Antes de começar, atualize sua branch a partir da `main`. Se alguém já estiver trabalhando no mesmo arquivo, conversem para definir quem fará a alteração principal ou dividam o trabalho em tarefas que não se sobreponham. Evitem manter cópias concorrentes do mesmo documento.

Se houver conflito, resolvam-no em conjunto, confiram o conteúdo final e só então concluam o PR.

## 6. Regras resumidas

1. `main` deve permanecer revisada e utilizável.
2. Não faça commit direto na `main`.
3. Crie uma branch por tarefa.
4. Mantenha cada PR pequeno e focado.
5. Todo PR deve ser revisado por outro integrante antes do merge.
6. Atualize o `README.md` quando os caminhos ou documentos referenciados mudarem.
7. Mantenha os PDFs finais e, quando possível, seus arquivos-fonte editáveis.
8. Nunca adicione dados reais identificáveis de pacientes.

## 7. Modelo de descrição para Pull Request

```markdown
## Resumo
Descreva o que foi criado ou alterado e o motivo.

## Arquivos afetados
- `caminho/para/documento.pdf`
- `README.md` (se aplicável)

## Checklist
- [ ] Arquivos na pasta correta e com nomes consistentes.
- [ ] PDF revisado e legível.
- [ ] Conteúdo coerente com os documentos relacionados.
- [ ] README e links atualizados, se necessário.
- [ ] Nenhum dado pessoal real ou confidencial incluído.

## Revisor
@integrante
```
