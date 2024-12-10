---
title: Template Document Model
layout: default
---

<div class="mermaid">
erDiagram
    Template {
        datetime createdDate
        string customInstructions
        boolean deployed
        string description
        boolean hasUpdatedAdvancedTemplate
        boolean instructionsAreInLanguageOriginalTemplateRef
        string languageCode
        ref languageOriginalTemplateRef
        datetime lastUsed
        string name
        number order
        object properties
        boolean readyToDeploy
        array[ref] standardTags
        array templateSections
        string type
    }

    TemplateProperties {
        array[ref] applicableInterests
        array[ref] applicableSpecies
        boolean usesMedicalAbbreviations
    }

    TemplateSection {
        string body
        string instructions
        number order
        string title
    }

    StandardTag {
        ref tagReference
    }

    Interest {
        ref interestReference
    }

    Species {
        ref speciesReference
    }

    Template ||--|| TemplateProperties : "has"
    Template ||--o{ TemplateSection : "contains"
    Template ||--o{ StandardTag : "has"
    TemplateProperties ||--o{ Interest : "references"
    TemplateProperties ||--o{ Species : "references"

</div>

