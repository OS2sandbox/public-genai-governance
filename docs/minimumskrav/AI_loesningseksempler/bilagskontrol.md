# Bilagskontrol

Et konkret eksempel på hvordan logikken i en AI løsning kunne se ud. Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)

```mermaid
flowchart LR

    upload["Receipt image upload"] --> core

    subgraph core["Core Application / Expense Logic"]

        direction TB

        start([Receive image])

        ocr["OCR + Vision extraction:
             - Vendor
             - Date
             - Total
             - VAT"]

        classify["Classify expense type"]

        matchPolicy["Check company policy:
                     - Allowed vendor?
                     - Amount limit?
                     - VAT rules?"]

        fraudCheck["Fraud signals:
                    - Duplicate receipt?
                    - Edited image?
                    - Suspicious timing?"]

        decision{"Approved?"}

        approve["Mark approved"]

        reject["Flag for manual review"]

        start --> ocr --> classify --> matchPolicy --> fraudCheck --> decision
        decision -- Yes --> approve
        decision -- No --> reject
    end

    approve --> accounting["Accounting System"]
    reject --> reviewer["Human reviewer queue"]
```