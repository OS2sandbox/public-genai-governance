# Bilagskontrol

Et konkret eksempel på hvordan logikken i en AI løsning kunne se ud. Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)

```mermaid
flowchart LR

    item["New/Updated Procurement Item"] --> core

    subgraph core["Core Application / Consistency Logic"]

        direction TB

        start([Receive item data])

        extract["Extract:
                 - Item name
                 - Description
                 - Image
                 - Category"]

        imageCheck["Image classification"]

        semanticCheck["Semantic consistency:
                       name ↔ description"]

        webLookup["Optional:
                   Online product lookup
                   (if allowed)"]

        compareWeb["Compare with
                    external data"]

        score["Generate consistency score"]

        decision{"Below threshold?"}

        flag["Flag inconsistency
              for review"]

        approve["Mark consistent"]

        start --> extract --> imageCheck
        extract --> semanticCheck
        semanticCheck --> webLookup --> compareWeb --> score --> decision
        decision -- Yes --> flag
        decision -- No --> approve
    end

    flag --> procurement["Procurement system review queue"]
    approve --> procurement
```