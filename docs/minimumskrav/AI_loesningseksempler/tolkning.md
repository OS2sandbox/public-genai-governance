# Tolkningssystem

___Pt. kun chatgpt udkast - ikke gennemarbejdet/verificeret___

Et konkret eksempel på hvordan logikken i en AI løsning kunne se ud. Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)

Et system der transkriberer og oversætter via 2-3 pipelines og påpeger uoverenstemmelser 

```mermaid
flowchart LR

    mic["Live audio stream"] --> core

    subgraph core["Core Application / Multi-Pipeline Logic"]

        direction TB

        start([Receive audio chunk])

        split["Duplicate audio stream"]

        subgraph P1["Pipeline 1"]
            asr1["ASR Model A"]
            trans1["Translate Model A"]
        end

        subgraph P2["Pipeline 2"]
            asr2["ASR Model B"]
            trans2["Translate Model B"]
        end

        subgraph P3["Pipeline 3"]
            asr3["ASR Model C"]
            trans3["Translate Model C"]
        end

        compare["Compare translations:
                 - Semantic similarity
                 - Terminology deviations
                 - Named entities"]

        flag{"Significant deviation?"}

        highlight["Highlight differences"]

        output([Output translation
                + confidence score])

        start --> split
        split --> asr1 --> trans1 --> compare
        split --> asr2 --> trans2 --> compare
        split --> asr3 --> trans3 --> compare
        compare --> flag
        flag -- Yes --> highlight --> output
        flag -- No --> output
    end
```