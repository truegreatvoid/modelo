## Comandos

##### *Exibe o status atual do repositório, mostrando as mudanças que foram feitas, arquivos que foram adicionados ao stage, e o estado das branches.*
```bash 
git status
```

##### *Lista todas as branches locais no repositório. A branch atual é indicada com um asterisco (**).*
```bash 
git branch
```

##### *Cria uma nova branch com o nome especificado.*
```bash 
git branch <nome-da-branch>
```

##### *Muda para a branch especificada. Este comando atualiza o diretório de trabalho com os arquivos da branch escolhida.*
```bash 
git checkout <nome-da-branch>
```

##### *Cria uma nova branch e muda automaticamente para ela.*
```bash 
git checkout -b <nome-da-branch>
```

##### *Mescla as mudanças da branch especificada na branch atual.*
```bash 
git merge <nome-da-branch>
```

##### *Deleta a branch especificada. O Git não permitirá deletar a branch atual.*
```bash 
git branch -d <nome-da-branch>
```

##### *Força a deleção da branch, mesmo que tenha mudanças não mescladas.*
```bash 
git branch -D <nome-da-branch>
```

##### *Envia a branch especificada para o repositório remoto.*
```bash 
git push origin <nome-da-branch>
```

##### *Atualiza a branch atual com as últimas mudanças do repositório remoto.*
```bash 
git pull origin <nome-da-branch>
```

*Envia a branch especificada para o repositório remoto e define a branch remota como "upstream" para a branch local. Isso significa que, a partir desse momento, o Git saberá para qual branch remota enviar as futuras alterações (usando `git push`) e de qual branch remota buscar atualizações (usando `git pull`) sem precisar especificar o nome da branch remota novamente.*
```bash 
git push --set-upstream origin <nome-da-branch>
```

##### *Exibe o histórico de commits da branch atual em uma linha por commit, mostrando o hash do commit e a mensagem associada. Este formato compacto é útil para obter uma visão geral rápida do histórico de commits.*
```bash 
git log --oneline
```

## Criando uma Branch

**Passo 1**
##### *Exibe o status atual do repositório, verificar se não contém algum erro.*
```bash 
git status
```

**Passo 2**
##### *Lista todas as branches locais no repositório.*
```bash 
git branch
```

**Passo 3**
##### *Cria uma nova branch com o nome especificado.*
```bash 
git branch guero
```

**Passo 4**
##### *Muda para a branch especificada.*
```bash 
git checkout guero
```

**Passo 5**
##### *Subir a branch em questão para o repositório remoto (GitHub).*
```bash
git push --set-upstream origin guero
```
*Nota: Este comando não apenas envia a branch `guero` para o repositório remoto, mas também configura essa branch remota como a "upstream" para a branch local. Isso significa que, a partir de agora, você poderá usar `git push` e `git pull` sem precisar especificar o repositório e a branch, facilitando o gerenciamento de versões. Se você não utilizar o `--set-upstream`, a branch que acabou de criar ficará apenas local e não será sincronizada automaticamente com o repositório remoto.*

#### *Branch criada.*

## Fundindo uma Branch

**Passo 1**
##### *Exibe o status atual do repositório para verificar se não há erros e em qual branch você está no momento.*
```bash 
git status
```

**Passo 2**
##### *Certifique-se de que você está na branch na qual deseja aplicar o merge. Por exemplo, se você deseja mesclar as alterações da branch `tiago` na branch `main`, primeiro verifique se está na branch `main`.*
```bash 
git merge tiago
```
*Nota: Este comando mesclará as alterações da branch `tiago` na branch atual (`main` neste exemplo). É crucial garantir que você esteja na branch correta antes de executar o merge para evitar conflitos ou mesclagens indesejadas.*

#### *Branch mesclada.*

#### Tipos de Merge

#### **Fast-forward**
*O merge "Fast-forward" ocorre quando a branch de destino (por exemplo, `main`) não teve nenhum commit adicional desde que a branch a ser mesclada (por exemplo, `tiago`) foi criada. Nesse caso, o Git simplesmente move o ponteiro da branch de destino para o commit final da branch a ser mesclada. Não há necessidade de criar um commit de merge, pois a história linear do repositório não é interrompida.*

*Nota: Se a branch main não tiver novos commits em relação à branch tiago, o Git aplicará um `Fast-forward`, simplesmente avançando o ponteiro da branch main ara o commit mais recente da branch tiago.*

#### **Recursive**
*O merge "Recursive" é o método padrão usado pelo Git quando há divergências na história entre as duas branches. Se ambos os ramos tiverem novos commits, o Git criará um commit de merge que une as duas histórias. O método "recursive" tenta automaticamente resolver conflitos de merge ao combinar as mudanças, mas, em alguns casos, o Git pode precisar de intervenção manual para resolver conflitos.*

*Nota: Se a branch `main` tiver novos commits que não estão na branch `tiago`, o Git usará o método "recursive" para criar um commit de merge que une as duas histórias, mantendo a integridade da linha do tempo. Porém, se ocorrerem conflitos durante o merge, o Git deixará o processo "em aberto" e você precisará resolver manualmente esses conflitos nos arquivos afetados. Após resolver os conflitos, finalize o merge com `git add .` seguido de `git commit`. Finalmente, use `git push` para enviar as alterações mescladas ao repositório remoto.*

**Resumo do Processo:**
1. **Resolver Conflitos:** *Editar os arquivos conflitantes.*
2. **Adicionar Arquivos:** *Usar `git add .` para marcar os conflitos como resolvidos.*
3. **Commitar o Merge:** *Concluir o merge com `git commit`.*
4. **Enviar as Alterações:** *Usar `git push` para enviar as mudanças para o repositório remoto.*

*Esse passo final é crucial para garantir que as mudanças sejam compartilhadas com o restante da equipe ou estejam disponíveis no repositório remoto.*

---

**Dúvidas:**

**Por que usar apenas `git commit` e não `git commit "Atualização Exemplo 1"`?**  
*Porque o Git já entende que você tem um processo em aberto que se originou do merge. Dessa forma, o comando padrão para finalizar o merge é apenas `git commit`, sem a necessidade de adicionar uma mensagem personalizada, já que o Git gera uma mensagem padrão para merges.*

#### **Ort**
*O merge "Ort" é um método mais recente introduzido no Git, que melhora a performance e a eficiência do processo de merge. O objetivo do "Ort" é acelerar o processo de resolução de conflitos e melhorar a clareza do código durante o merge. Embora o "Ort" compartilhe semelhanças com o método "Recursive", ele foi projetado para lidar melhor com cenários complexos e grandes repositórios.*

*Nota: O "Ort" é recomendado quando se trabalha com repositórios grandes ou com históricos de merge complexos, pois ele oferece melhor performance e um processo de resolução de conflitos mais eficaz. Se você estiver em um ambiente que frequentemente encontra conflitos de merge, considerar o uso do "Ort" pode economizar tempo e reduzir a complexidade do merge.*

**Benefícios do Merge Ort:**
1. **Melhor Performance:** *O "Ort" é otimizado para lidar com grandes conjuntos de dados e históricos complexos.*
2. **Resolução de Conflitos Mais Eficiente:** *Oferece melhorias na forma como os conflitos são detectados e resolvidos.*
3. **Maior Clareza no Código:** *Facilita a manutenção da clareza do código durante o merge, especialmente em projetos com muitos colaboradores.*

**Como Ativar o Ort:**
- *Para utilizar o método "Ort", é necessário ter uma versão recente do Git e configurá-lo com o seguinte comando:*
```bash
git config --global merge.ort true
```