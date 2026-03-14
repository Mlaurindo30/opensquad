# Research Squad

Um squad para pesquisa e análise de informações da web.

## Uso

```bash
npx opensquad run squads/research
```

## Descrição

Este squad é usado quando AKIRA precisa de:
- Pesquisa multi-fonte na web
- Análise de informações complexas
- Síntese de dados de múltiplas fontes
- Relatórios de pesquisa estruturados

## Fluxo

```
1. researcher  → Coleta informações da web
2. analyst     → Analisa e sintetiza dados
3. writer      → Produz relatório final
```

## Skills Utilizadas

- apify - Web scraping e automação
- image-fetcher - Captura de screenshots e imagens

## Agentes

### researcher
- **Role:** Pesquisador web
- **Model:** glm-5:cloud (via AKIRA)
- **Tools:** apify, image-fetcher
- **Output:** Dados brutos coletados

### analyst
- **Role:** Analista de dados
- **Model:** glm-5:cloud (via AKIRA)
- **Tools:** Nenhuma (análise pura)
- **Output:** Análise estruturada

### writer
- **Role:** Escritor técnico
- **Model:** glm-5:cloud (via AKIRA)
- **Tools:** Nenhuma (escrita pura)
- **Output:** Relatório final em markdown

## Checkpoints

- **Após analyst:** "A análise está correta? Prosseguir para escrita?"
- **Após writer:** "O relatório está completo? Publicar?"

## Integração com AKIRA

Quando AKIRA identifica uma tarefa de pesquisa complexa:

1. AKIRA chama a skill `opensquad`
2. Skill delega para este squad
3. Squad executa em sequência
4. Resultado retorna para AKIRA
5. AKIRA entrega ao usuário

## Exemplo

**Input:** "Pesquise sobre as melhores práticas de arquitetura de microserviços"

**Output:** Relatório completo com:
- Definições e conceitos
- Padrões arquiteturais
- Casos de uso
- Referências
- Recomendações