---
title: Firestore Cases Model
layout: default
---

# Firestore Cases Model

This document provides a comprehensive overview of the `cases` collection, its fields, subcollections, relationships, and internal objects.

---

## Overview of `cases`

The `cases` collection is the core of the system, representing individual medical cases. Each document in `cases` contains the following:

- **Metadata**: Information such as the case name, status, and creation details.
- **Relationships**: Links to users, teams, and other cases.
- **Embedded Objects**: Summarized data (e.g., `contentCounts`) and state flags (e.g., `contentSecondaryStatuses`).
- **Subcollections**: Associated data for activity, content, and content requests.

---

## Full Entity-Relationship Diagram

<div class="mermaid">
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
    ContentRequests }|--|| Content : "references single content"
</div>