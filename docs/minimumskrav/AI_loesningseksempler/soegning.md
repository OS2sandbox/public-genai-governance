# Søgemoter til byrådsreferater

Et konkret eksempel på hvordan logikken i en AI løsning kunne se ud. Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)

Eksemplet her er forsimplet i forhold til hvad man i praksis ville være nødt 
til at sætte op. Særligt to ting er meget simplificeret:
- Ingestion flowet, dvs optaget af information i den søgebare database. 
  For at få lidt mere blik for kompleksiteten henvises til [digestion løsningen]
  altså dokument forståelses(/fordøjelses)motoren, som udgør processen indtil 
  information indsættes i vektordatabasen.
- Fremsøgningen, hvor den nuværende state-of-art tilsiger en mere agentisk tilgang, 
  hvor en seperat sprogmodel vurdere hvad en god søgestreng ville være og evt. kan 
  prøve at modificerer denne, hvis den ikke vurdere at de umiddelbare resultater
  svarer på brugeren forespørgsel.

```mermaid
flowchart TD
    classDef optional stroke-width:2px,stroke-dasharray: 5 5
    %% ,color:#fff
    
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
            prompt2:::optional@{ shape: doc, label: "Evt. embedding prompt: Passage: " }
            embed2@{ shape: lean-l, label: "Generate embeddings
                    (Call embedding model)" }
            store["Update vector DB collection with new/update minutes
                   (and relevant metadata)"]
    
            prompt2 --> embed2
            minutes --> chunk --> embed2 --> store
        end
        
        store --> vdb
        
        subgraph retrive["Retrival pipeline"]
            
            start([Receive search query])
            
            prompt:::optional@{ shape: doc, label: "Evt. embedding prompt: Query: " }
            embed@{ shape: lean-l, label: "Create embedding of query
                   (Call embedding model)" }
    
            search["Vector DB similarity search"]
    
            format["Format as:
                    - Title
                    - Snippet
                    - Link"]
    
            return([Return result list])
    
            user -->|Search query| start --> embed --> search --> format --> return
            prompt --> embed
        end
        
        search <--> vdb
        
    end
    system -->|Læseadgang| minutes
    
    return --> results

    
```