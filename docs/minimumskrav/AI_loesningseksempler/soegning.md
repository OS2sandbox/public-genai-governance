# Søgemoter til byrådsreferater

Et konkret eksempel på hvordan logikken i en AI løsning kunne se ud. Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)


```mermaid
flowchart TD
    
    subgraph UI["UI - Webpage/Application"]
        user@{ shape: in-out, label: "Input/Search field"} 
        
        results@{ shape: in-out, label: "Output list element"}
    end

    system@{ shape: cloud, label: "Referat opbevaringssystem"}

    subgraph core["`Core Application / Business Logic`"]
        direction TB
        
        vdb@{ shape: db, label: "vectorDB\n kollektion"}
        %% Re-indexing flow
        subgraph ingest["Ingestion Pipeline"]
    
            minutes(["New/Updated Minutes"])
            chunk["Chunk document"]
            embed2["Generate embeddings
                    (Call embedding model)"]
            store["Update vector DB collection with new/update minutes
                   (and relevant metadata)"]
    
            minutes --> chunk --> embed2 --> store
        end
        
        store --> vdb
        
        subgraph retrive["Retrival pipeline"]
            
            start([Receive search query])
    
            embed["Create embedding of query
                   (Call embedding model)"]
    
            search["Vector DB similarity search"]
    
            format["Format as:
                    - Title
                    - Snippet
                    - Link"]
    
            return([Return result list])
    
            user-->|Search query| start --> embed --> search --> format --> return
            
        end
        
        search <--> vdb
        
    end
    system -->|Læserettigheder| minutes
    
    return --> results

    
```