# Søgemoter til byrådsreferater

Et konkret eksempel på hvordan logikken i en AI løsning kunne se ud. Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)


```mermaid
flowchart LR

    user["User (Search field)"] -->|Search query| core

    subgraph core["Core Application / Business Logic"]

        direction TB

        start([Receive search query])

        auth{"User has read access
              to minutes?"}

        deny["Return access denied"]

        embed["Create embedding
               of query"]

        search["Vector DB similarity search"]

        filter["Filter by:
                - Access rights
                - Date
                - Board type"]

        rank["Rank by:
              - Similarity score
              - Recency
              - Metadata weight"]

        format["Format as:
                - Title
                - Snippet
                - Link"]

        return([Return result list])

        start --> auth
        auth -- No --> deny
        auth -- Yes --> embed --> search --> filter --> rank --> format --> return
    end

    return --> results["Search Results Page"]

    %% Re-indexing flow
    subgraph reindex["Indexing Pipeline"]

        minutes["New/Updated Minutes"]
        checkAccess["Check indexing rights"]
        chunk["Chunk document"]
        embed2["Generate embeddings"]
        store["Store in vector DB
               with metadata"]

        minutes --> checkAccess --> chunk --> embed2 --> store
    end
```