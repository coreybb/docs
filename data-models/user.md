---
title: Cases Document Model
layout: default
---

<div class="mermaid">
classDiagram
    class User {
        +String uid
        +String customerID
        +String display_name
        +String email
        +String firstName
        +String lastName
        +DateTime created_time
        +Boolean enableSnippets
        +Boolean firstAccountLoginCompleted
        +Boolean isTrial
        +String photo_url
        +Number recordCount
        +String subscriptionType
        +DateTime subscriptionExpirationDate
        +Boolean welcomeEmailSent
    }

    class Abbreviations {
        +Array abbreviations[*]
        +Array categories[*]
        +Boolean enabled
    }

    class AbbreviationEntry {
        +String abbreviation
        +String category
        +Boolean clientFacing
        +String languageCode
        +String longForm
    }

    class Category {
        +String id
        +String languageCode
        +String name
    }

    class LanguagePreferences {
        +String appLanguage
        +Array regionPreferences
    }

    class OnboardingPreferences {
        +Object profileDefaultNormals
        +Number profileDetailLevelPreference
        +Array profileInterest
        +String profileName
        +String profileRole
        +Array profileSpecies
        +Object profileUnits
    }

    class PDFPreferences {
        +String email
        +Boolean showCustomHeader
        +Boolean showEmail
        +Boolean showHospitalName
        +Boolean showLogo
        +Boolean showName
        +Boolean showNumberPages
        +Boolean showPhone
    }

    class RecordingSettings {
        +Number maxRecordingTimeLimit
        +Boolean soundOnStartAndStopEnabled
    }

    class TeamData {
        +Array allUsersInTeamsUserIsIn
        +Array canManageTeams
        +Array canSupportTeamRefs
        +Array canSupportTeams
        +Array isMemberOfTeams
        +Array openInvites
        +Array ownsTeams
    }

    class PersonalTag {
        +DateTime createdDate
        +Boolean isStandard
        +Array name
        +Reference standardRef
        +Array templates
    }

    class PersonalTemplate {
        +Boolean boldAbnormals
        +DateTime createdDate
        +String description
        +Boolean hasUpdatedAdvancedTemplate
        +Boolean isFavorite
        +Boolean isStandard
        +Boolean isVisible
        +String languageCode
        +String name
        +Number order
        +Object properties
        +Reference standardRef
        +String subtype
        +Array tags
        +String type
    }

    class TemplateProperties {
        +Array applicableInterests
        +Array applicableSpecies
        +Boolean usesMedicalAbbreviations
    }

    User *-- Abbreviations
    User *-- LanguagePreferences
    User *-- OnboardingPreferences
    User *-- PDFPreferences
    User *-- RecordingSettings
    User *-- TeamData
    User "1" *-- "many" PersonalTag
    User "1" *-- "many" PersonalTemplate
    PersonalTemplate *-- TemplateProperties
    Abbreviations *-- "many" AbbreviationEntry
    Abbreviations *-- "many" Category

</div>