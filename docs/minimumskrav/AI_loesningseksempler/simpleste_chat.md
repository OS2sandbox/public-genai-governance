# Simple sprogmodel chat

Et konkret eksempel på hvordan logikken i en AI løsning kunne se ud. Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)

```mermaid
flowchart LR

    subgraph UI["Chat UI"]
        user["User"]
        chat["Chat Interface"]
        user --> chat
    end

    chat -->|User message| core

    subgraph core["Core Application / Business Logic"]

        direction TB

        start([Receive message])

        ctx["Load conversation history
             from temporary storage"]

        compose["Compose prompt:
                - System prompt
                - Conversation history
                - New user message"]

        callModel["Call LLM"]

        validate{"Output valid?
                  (length / safety /
                   format checks)"}

        retry["Re-prompt or adjust
               parameters"]

        store["Store:
               - User message
               - Model response"]

        respond([Return response])

        start --> ctx --> compose --> callModel --> validate
        validate -- No --> retry --> callModel
        validate -- Yes --> store --> respond
    end

    core -->|Response| chat
```