---
title: Firestore Cases Model
layout: default
---

# Firestore Cases Model

This diagram provides an overview of the `cases` collection and its relationships to subcollections (`activity`, `content`, `contentRequests`).

<div class="mermaid">
erDiagram
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

    Cases ||--o{ Activity : "has activity"
    Cases ||--o{ Content : "contains"
    Cases ||--o{ ContentRequests : "requests"
    Activity }|--|| Content : "references"
    ContentRequests }|--|| Content : "references single content"
</div>