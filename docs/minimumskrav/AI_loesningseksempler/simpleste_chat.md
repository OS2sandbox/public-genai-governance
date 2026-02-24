# Simple sprogmodel chat

Det simplest mulige konkrete eksempel på hvordan logikken i en AI løsning kunne se ud. 
Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)

Her er der hverken rettigheder eller forbindelse til ekstern forretningsdata
og heller ikke nogle test cases eller performance mål (da vi allerede ved at 
en sådan løsning ikke kan bruges til andet end et eksempel)

```mermaid
flowchart TD
    classDef inViz fill:None,stroke-width:0px;

    subgraph UI["UI"]
        chat["Chat Interface"]
    end

    chat -->|User message| start

    subgraph core["Kerneapplikation/ Forretningslogik"]
        direction TB
        
        inVizAnchor:::inViz@{shape: junction}
        start([Receive message])
        prompt@{ shape: doc, label: "System prompt: 
                                     Du er en hjælpsom..." }
        ctx["Load conversation history
            from temporary storage"]
                                     
        inVizAnchor ~~~ ctx
        inVizAnchor ~~~ start
        inVizAnchor ~~~ prompt
    
        storage@{ shape: win-pane, label: "Conversation history" }
             
        compose["Compose prompt:
                - System prompt
                - Conversation history
                - New user message"]

        callModel["Call LLM"]

        store["Store:
               - User message
               - Model response"]

        respond([Return response])

        ctx <--> storage 
        ctx --> compose --> callModel --> store --> storage
        start --> compose 
        prompt --> compose
        store --> respond
    end

    respond -->|Response| chat
```

**Take-away**: Selv i det simpleste tilfælde er en AI model kun en del af en AI løsning.

##TODO: Maybe implement the above in two pseudo code files (`frontend.code` and `backend.code`)... 