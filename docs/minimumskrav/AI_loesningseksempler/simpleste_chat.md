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
        
        subgraph inputSrcs[" "]

            inVizAnchor:::inViz@{shape: junction}

            storage@{ shape: win-pane, label: "Conversation history" }
            start([Receive message])
            prompt@{ shape: doc, label: "System prompt: 
                                         Du er en hjælpsom..." }
                                         
            inVizAnchor ~~~ storage 
            inVizAnchor ~~~ start
            inVizAnchor ~~~ prompt
        

        end
        
        ctx["Load conversation history
             from temporary storage"]
             
        compose["Compose prompt:
                - System prompt
                - Conversation history
                - New user message"]

        callModel["Call LLM"]

        store["Store:
               - User message
               - Model response"]

        respond([Return response])

        storage <--> ctx --> compose --> callModel --> store --> storage
        start ---> compose 
        prompt ---> compose
        store --> respond
    end

    respond -->|Response| chat
```