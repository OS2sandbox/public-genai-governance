# Dokument forståelse/digestion

___Pt. kun chatgpt udkast - ikke gennemarbejdet/verificeret___

Et konkret eksempel på hvordan logikken i en AI løsning kunne se ud. Diagrammet skal ses som en eksemplificering af det
[generelle overblik af komponenter i en AI løsning](../baggrund_objekt_for_os2AI.md#ai-løsning)

```mermaid
flowchart LR

    source["Incoming Documents
            (email / API / upload)"] --> core

    subgraph core["Core Application / Business Logic"]

        direction TB

        start([Receive document])

        classify["Classify document type
                  (vision + text model)"]

        route{"Document type?"}

        invoice["Invoice pipeline"]
        contract["Contract pipeline"]
        unknown["Unknown → manual review"]

        extractInvoice["Extract:
                        - Amount
                        - Vendor
                        - Date"]

        extractContract["Extract:
                         - Parties
                         - Duration
                         - Clauses"]

        validate["Validate fields
                  against rules"]

        store["Store structured data"]

        start --> classify --> route
        route -- Invoice --> invoice --> extractInvoice --> validate --> store
        route -- Contract --> contract --> extractContract --> validate --> store
        route -- Unknown --> unknown
    end

    store --> downstream["ERP / Archive System"]
```