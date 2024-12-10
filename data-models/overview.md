---
title: Data Models
layout: default
---

# Data Models Overview

Our application is built around three core models that work together to provide a comprehensive veterinary documentation system.

<div class="model-grid">
    <div class="model-card">
        <h2>📁 Case</h2>
        <p>The primary container for all content and clinical activity. Cases organize patient records, communications, and medical documentation.</p>
        <a href="cases" class="model-link">View Case Model →</a>
    </div>

    <div class="model-card">
        <h2>👤 User</h2>
        <p>Represents veterinary professionals and staff members. Contains authentication, preferences, and practice-specific settings.</p>
        <a href="user" class="model-link">View User Model →</a>
    </div>

    <div class="model-card">
        <h2>📝 Template</h2>
        <p>Defines structured formats for clinical documentation. Supports multiple languages and specialties.</p>
        <a href="template" class="model-link">View Template Model →</a>
    </div>
</div>

<style>
.model-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin: 2rem 0;
}

.model-card {
    background: var(--mermaid-alt-bg);
    border: 1px solid var(--mermaid-border);
    border-radius: 8px;
    padding: 1.5rem;
    transition: transform 0.2s, box-shadow 0.2s;
}

.model-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

.model-card h2 {
    margin-top: 0;
    color: var(--primary-color);
    font-size: 1.5rem;
}

.model-card p {
    margin: 1rem 0;
    line-height: 1.6;
}

.model-link {
    display: inline-block;
    color: var(--primary-color);
    text-decoration: none;
    font-weight: 600;
    margin-top: 1rem;
}

.model-link:hover {
    text-decoration: underline;
}
</style>
