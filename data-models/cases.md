---
title: Firestore Cases Model
layout: default
---

# Firestore Cases Model

This document provides a detailed overview of the `cases` collection, its fields, subcollections, and related entities.

---

<div class="mermaid">
## Full Entity-Relationship Diagram
erDiagram
    %% Main Case Collection
    Cases {
        string id
        string name
        string status
        boolean archived
        object contentCounts
        object contentSecondaryStatuses
        datetime createdDate
        ref createdBy
        ref ownedBy
        ref nextCase
        ref previousCase
        array visibleToTeamRefs
    }

    %% Subcollection: Activity
    Activity {
        string id
        string activityType
        ref contentRef
        string contentType
        ref userRef
        datetime createdDate
        array message
        boolean processByBackend
        string status
    }

    %% Subcollection: Content
    Content {
        string id
        string caseName
        object contentData
        ref createdBy
        datetime createdDate
        boolean hasMedicalInformation
        string name
        string type
        array visibleToTeamRefs
    }

    %% Embedded Object: Content Data
    ContentData {
        string body
        string bodyOriginal
        array bodySections
        object deltaBody
        object bodySectionsOriginal
    }

    %% Subcollection: Content Requests
    ContentRequests {
        string id
        string type
        ref singleContent
        array templates
        string status
        boolean usedAllContentsInCase
        datetime createdDate
        ref userRef
    }

    %% Embedded Object: Content Counts
    ContentCounts {
        int emails
        int images
        int pdfs
        int recordings
        int records
        int summaries
    }

    %% Embedded Object: Content Secondary Statuses
    ContentSecondaryStatuses {
        boolean allInputsProcessed
    }

    %% Teams Collection
    Teams {
        string id
        string name
    }

    %% Relationships
    Cases ||--o{ ContentCounts : "tracks counts"
    Cases ||--o{ ContentSecondaryStatuses : "tracks statuses"
    Cases ||--o{ Activity : "owns"
    Cases ||--o{ Content : "owns"
    Cases ||--o{ ContentRequests : "owns"
    Cases ||--o{ Teams : "visible to teams"
    Activity }|--|| Content : "references content"
    Content }|--o{ ContentData : "contains detailed data"
    ContentRequests }|--|| Content : "references single content"
</div>