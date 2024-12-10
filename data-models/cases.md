---
title: Case Document Model
layout: default
---

<div class="mermaid">
erDiagram
    Cases {
        string id
        string appVersion
        boolean archived
        boolean changedName
        object collaborativeData
        object contentCounts
        object contentSecondaryStatuses
        ref createdBy
        string createdByName
        datetime createdDate
        boolean deleted
        boolean generatedAnyContent
        boolean hasMedicalInformation
        boolean hiddenToDelete
        datetime lastModified
        string name
        ref nextCase
        ref ownedBy
        string ownedByName
        ref previousCase
        int status
        string suggestedCaseName
        int timerValue
        array visibleToTeamDataType
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

    Activity {
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
        string appVersion
        datetime caseCreatedDate
        string caseName
        object contentData
        ref contentRequest
        ref createdBy
        string createdByName
        datetime createdDate
        int executionTime
        int exportStatus
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
        boolean clearPdfStorageReference
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

    Cases ||--|| CollaborativeData : "has"
    Cases ||--|| ContentCounts : "has"
    Cases ||--|| ContentSecondaryStatuses : "has"
    Cases ||--o{ Activity : "contains"
    Cases ||--o{ Content : "contains"
    Cases ||--o{ ContentRequests : "contains"
    
    Activity ||--o{ ActivityMessage : "contains"
    Activity }|--|| Content : "references"
    
    Content ||--|| ContentData : "has"
    ContentData ||--o{ BodySection : "contains"
    ContentData ||--o{ Recording : "may have"
    
    Content }|--|| ContentRequests : "requested by"
</div>