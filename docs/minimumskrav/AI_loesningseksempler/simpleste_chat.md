# Simple sprogmodel chat

Et konkret eksempel på hvordan logikken i en AI løsning kunne se ud. Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)

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

        storage@{ shape: win-pane, label: "Conversation history" }
        
        ctx["Load conversation history
             from temporary storage"]
             
        prompt@{ shape: doc, label: "System prompt: 
                                     Du er en hjælpsom..." }     

        compose["Compose prompt:
                - System prompt
                - Conversation history
                - New user message"]

        callModel["Call LLM"]

        store["Store:
               - User message
               - Model response"]

        respond([Return response])

        inVizAnchor ~~~ start 
        inVizAnchor ~~~ storage 
        inVizAnchor ~~~ prompt
        
        storage <--> ctx --> compose
        start ---> compose --> callModel --> store --> respond
        prompt ---> compose
        store --> storage
    end

    respond -->|Response| chat
```