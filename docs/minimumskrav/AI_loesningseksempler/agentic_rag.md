# Agentisk RAG over vejledning til lønsystem

Et konkret eksempel på hvordan logikken i en AI løsning kunne se ud. Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)

```mermaid
flowchart LR

    user["User Question"] --> core

    subgraph core["Core Application / Agent Logic"]

        direction TB

        start([Receive question])

        plan["Agent plans:
              - Need policy?
              - Need calculation rule?
              - Need employee data?"]

        retrieveDocs["Retrieve relevant
                      policy documents"]

        retrieveData["Call salary system API
                      (if authorized)"]

        toolCheck{"Tool call needed?"}

        calc["Execute calculation tool"]

        synth["Synthesize answer
               using LLM"]

        verify["Self-check:
                - Grounded?
                - Missing sources?"]

        answer([Return answer
                + references])

        start --> plan --> retrieveDocs --> toolCheck
        toolCheck -- Yes --> calc --> synth
        toolCheck -- No --> synth
        plan --> retrieveData
        synth --> verify --> answer
    end
```