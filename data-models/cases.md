---
title: Firestore Cases Model
layout: default
---

# Firestore Cases Model

This document provides a detailed overview of the `cases` collection, its fields, subcollections, and related entities.

---

## Full Entity-Relationship Diagram

<div class="mermaid">
erDiagram
    Cases {
        string id
        string appVersion
        boolean archived
        boolean changedName
        datetime createdDate
        datetime lastModified
        string name
        string suggestedCaseName
        boolean deleted
        boolean generatedAnyContent
        boolean hasMedicalInformation
        boolean hiddenToDelete
        int status
        int timerValue
        ref createdBy
        string createdByName
        ref ownedBy
        string ownedByName
        ref nextCase
        ref previousCase
        array visibleToTeamRefs
    }

    CollaborativeData {
        array activeRecorders
        boolean hasActiveRecorder
    }

    ContentCounts {
        int emails
        int images
        int pdfs
        int recordings
        int records
        int summaries
    }

    ContentSecondaryStatuses {
        boolean allInputsProcessed
    }

    VisibleToTeamData {
        string teamName
        ref teamRef
    }

    Activity {
        string id
        string activityType
        ref contentRef
        string contentType
        string createdByName
        datetime createdDate
        array message
        boolean processByBackend
        string status
        ref userRef
    }

    ActivityMessage {
        string languageCode
        string string
    }

    Content {
        string id
        string appVersion
        datetime caseCreatedDate
        string caseName
        boolean changedName
        object contentData
        ref contentRequest
        ref createdBy
        string createdByName
        datetime createdDate
        int executionTime
        boolean hasCompleted
        boolean hasMedicalInformation
        array inputContentReferences
        boolean isMultiPet
        string languageCode
        datetime lastProcessingTime
        string name
        ref ownedBy
        string ownedByName
        boolean showInExportCenter
        int status
        string type
        boolean usedAllContentsInCase
        array visibleToTeamRefs
    }

    ContentData {
        string body
        string bodyOriginal
        array bodySections
        array bodySectionsOriginal
        string originalGeneratedBody
        ref templateUsed
        object recording
    }

    BodySection {
        string body
        string deltaBody
        int order
        string title
    }

    Recording {
        string detectedLanguage
        string downloadURL
        float duration
        string formattedTranscript
        string platform
        string selectedLanguage
        string storageReference
        string transcript
    }

    ContentRequests {
        string appVersion
        datetime createdDate
        array inputContentReferences
        boolean isMultiPet
        string languageCode
        ref singleContent
        string status
        array templates
        string type
        boolean usedAllContentsInCase
        ref userRef
    }

    Teams {
        string id
        string name
    }

    Cases ||--|| CollaborativeData : "has"
    Cases ||--|| ContentCounts : "has"
    Cases ||--|| ContentSecondaryStatuses : "has"
    Cases ||--o{ VisibleToTeamData : "has"
    Cases ||--o{ Activity : "contains"
    Cases ||--o{ Content : "contains"
    Cases ||--o{ ContentRequests : "has"
    Cases }o--o{ Teams : "visible to"
    
    Activity ||--o{ ActivityMessage : "contains"
    Activity }|--|| Content : "references"
    
    Content ||--|| ContentData : "has"
    ContentData ||--o{ BodySection : "contains"
    ContentData ||--o{ Recording : "may have"
    
    Content }|--|| ContentRequests : "requested by"
    ContentRequests }|--|| Teams : "visible to"

</div>