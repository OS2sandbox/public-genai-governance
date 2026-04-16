### Code Review Process (Basis)

```mermaid
graph TD
    A["<b>1. Feature Complete</b><br/>Developer finishes task locally"] --> B["<b>2. Pull Request (PR)</b><br/>Description of 'what' and 'why'"]
    B --> C{"<b>3. Peer Review</b><br/>Colleague reviews code"}
    
    C -->|Changes requested| D["<b>4. Dialog & Revision</b><br/>Feedback loop and code updates"]
    D --> C
    
    C -->|Approved| E["<b>5. Merge</b><br/>Code merged into main project"]

    style A fill:#f9f,stroke:#333,stroke-width:2px
    style E fill:#bbf,stroke:#333,stroke-width:2px
    style C fill:#fff4dd,stroke:#d4a017,stroke-width:2px
