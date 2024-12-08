# CoVet Documentation

Welcome to the CoVet documentation.

## Data Model Overview

<div class="mermaid">
erDiagram
    Case ||--o{ Content : has
    Case ||--o{ Activity : has
    Content ||--o{ ContentRequest : "referenced by"
    Content }|--|| User : "created by"
    Case }|--|| User : "owned by"
    Activity }|--|| User : "created by"
    ContentRequest }|--|| User : "requested by"
</div>

## Documentation Sections

- [Data Models](./data-models/overview.md)

