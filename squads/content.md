# Content Squad

Um squad para criação de conteúdo com múltiplos formatos.

## Uso

```bash
npx opensquad run squads/content
```

## Descrição

Este squad é usado quando AKIRA precisa criar:
- Artigos e posts para blog
- Conteúdo para redes sociais
- Imagens e gráficos
- Publicações multi-plataforma

## Fluxo

```
1. researcher  → Pesquisa o tema
2. writer      → Cria o conteúdo textual
3. designer    → Cria assets visuais (Canva/image-creator)
4. publisher   → Publica nas plataformas (instagram-publisher/blotato)
```

## Skills Utilizadas

- apify - Pesquisa web
- canva - Design automatizado
- image-creator - HTML/CSS para imagens
- image-fetcher - Captura de imagens
- instagram-publisher - Publicação no Instagram
- blotato - Publicação multi-plataforma

## Agentes

### researcher
- **Role:** Pesquisador de conteúdo
- **Model:** glm-5:cloud (via AKIRA)
- **Tools:** apify, image-fetcher
- **Output:** Brief de conteúdo

### writer
- **Role:** Redator de conteúdo
- **Model:** glm-5:cloud (via AKIRA)
- **Tools:** Nenhuma
- **Output:** Texto final em markdown

### designer
- **Role:** Designer gráfico
- **Model:** glm-5:cloud (via AKIRA)
- **Tools:** canva, image-creator
- **Output:** Imagens e assets visuais

### publisher
- **Role:** Publicador de conteúdo
- **Model:** glm-5:cloud (via AKIRA)
- **Tools:** instagram-publisher, blotato
- **Output:** Publicações nas plataformas

## Checkpoints

- **Após researcher:** "O brief está completo? Prosseguir?"
- **Após writer:** "O texto está aprovado? Criar visuals?"
- **Após designer:** "As imagens estão boas? Publicar?"

## Integração com AKIRA

### Delegação

Quando AKIRA recebe uma tarefa como:
> "Crie um post sobre microserviços e publique no Instagram"

AKIRA:
1. Identifica que precisa de múltiplas skills
2. Chama a skill `opensquad`
3. Delega para o squad `content`
4. Aguarda resultado
5. Entrega ao usuário

### Skill opensquad

```markdown
Use este skill quando AKIRA precisa delegar tarefas complexas:

| Tarefa | Delegate to OpenSquad? |
|--------|------------------------|
| Pesquisa multi-fonte | ✅ Research Squad |
| Criação de conteúdo | ✅ Content Squad |
| Publicação em redes sociais | ✅ Content Squad |
| Análise de dados | ✅ Research Squad |
| Mudança simples de código | ❌ Handle directly |
```

## Exemplo

**Input:** "Crie um carousel para Instagram sobre as novidades do OpenClaw v2026.3.12"

**Output:**
1. Brief de conteúdo com pontos-chave
2. Texto do carousel (5-10 slides)
3. Imagens criadas no Canva
4. Publicação no Instagram via instagram-publisher