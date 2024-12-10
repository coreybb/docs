---
title: User Document Model
layout: default
---

<div class="mermaid">
erDiagram
    User {
        string uid
        string customerID
        string display_name
        string email
        string firstName
        string lastName
        datetime created_time
        boolean enableSnippets
        boolean firstAccountLoginCompleted
        boolean isTrial
        string photo_url
        number recordCount
        string subscriptionType
        datetime subscriptionExpirationDate
        boolean welcomeEmailSent
    }

    Abbreviations {
        array abbreviations
        array categories
        boolean enabled
    }

    AbbreviationEntry {
        string abbreviation
        string category
        boolean clientFacing
        string languageCode
        string longForm
    }

    Category {
        string id
        string languageCode
        string name
    }

    LanguagePreferences {
        string appLanguage
        array regionPreferences
    }

    OnboardingPreferences {
        object profileDefaultNormals
        number profileDetailLevelPreference
        array profileInterest
        string profileName
        string profileRole
        array profileSpecies
        object profileUnits
    }

    PDFPreferences {
        string email
        boolean showCustomHeader
        boolean showEmail
        boolean showHospitalName
        boolean showLogo
        boolean showName
        boolean showNumberPages
        boolean showPhone
    }

    RecordingSettings {
        number maxRecordingTimeLimit
        boolean soundOnStartAndStopEnabled
    }

    TeamData {
        array allUsersInTeamsUserIsIn
        array canManageTeams
        array canSupportTeamRefs
        array canSupportTeams
        array isMemberOfTeams
        array openInvites
        array ownsTeams
    }

    PersonalTag {
        datetime createdDate
        boolean isStandard
        array name
        ref standardRef
        array templates
    }

    PersonalTemplate {
        boolean boldAbnormals
        datetime createdDate
        string description
        boolean hasUpdatedAdvancedTemplate
        boolean isFavorite
        boolean isStandard
        boolean isVisible
        string languageCode
        string name
        number order
        object properties
        ref standardRef
        string subtype
        array tags
        string type
    }

    TemplateProperties {
        array applicableInterests
        array applicableSpecies
        boolean usesMedicalAbbreviations
    }

    User ||--|| Abbreviations : "has"
    User ||--|| LanguagePreferences : "has"
    User ||--|| OnboardingPreferences : "has"
    User ||--|| PDFPreferences : "has"
    User ||--|| RecordingSettings : "has"
    User ||--|| TeamData : "has"
    User ||--o{ PersonalTag : "contains"
    User ||--o{ PersonalTemplate : "contains"
    PersonalTemplate ||--|| TemplateProperties : "has"
    Abbreviations ||--o{ AbbreviationEntry : "contains"
    Abbreviations ||--o{ Category : "contains"

</div>