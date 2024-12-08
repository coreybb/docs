---
title: Welcome
layout: default
---

# Covet Documentation

Welcome to CoVet's documentation hub! 

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

## Sections

- [Data Models](./data-models/overview.md)

