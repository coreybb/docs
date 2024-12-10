---
title: Welcome
layout: default
---

# Covet Docs

Welcome to CoVet's documentation hub!

--- 

### **Core Architecture**

#### Frontend developed using Flutter Flow

- No-code builder with custom code support
- Visual drag-and-drop interface with action flows for logic
- Custom widgets and functions capabilities
- Direct Firebase integration

#### Backend powered by Firebase infrastructure

- Multiple Firebase projects for different environments
- Firebase Admin SDK for cloud functions
- Direct frontend-to-Firebase communication (no API layer)

### **System Components**

#### **Frontend Layer**

- Main application interface (Flutter Flow)
- Chrome extension for data export
- Administrative dashboard
- Cloud functions for business logic
- Staging/development preview environments

#### **Backend Infrastructure**

- Firebase services integration
- Firestore database (NoSQL)
- Authentication system
- Cloud Functions
- Hosting services
- Crashlytics
- Extensions (Mailchimp, Algolia)

#### **Source Control & Deployment**

- GitHub repositories structure:
    - `covet` (main frontend)
    - `covet-extension` (Chrome extension)
    - `covet-admin` (admin dashboard)
    - `covet-backend` (cloud functions)
    - `covet-dev-end` (local development environment)
- Limited branch management in Flutter Flow
- Main development branch
- Production copy branch for hotfixes
- Automated deployment pipelines
- Branch-based deployment
- Environment-specific configurations

### **Environment Structure**

- **Development**: `dev.covet`
    - Connected to development Firebase instance
- **Staging**: `staging.covet`
    - Connected to production Firebase for beta testing
- **Production**: `app.covet`
    - Production Firebase instance

### **Technical Implementation**

#### **Database Design**

- NoSQL structure with strategic data duplication and [document polymorphism](https://www.mongodb.com/developer/products/mongodb/polymorphic-pattern/)
- Sub-collections for related data (cases, contents, etc.)
- Optimized read/write operations for cost efficiency
- Flexible schema with defined collection structures

#### **Security**

- Firebase Rules-based security
- **Admin SDK** bypass for cloud functions
- Authentication integration


#### **Integration Points**

- Search functionality via **Algolia**
- Payment processing through **Stripe**
- Email services via **Mailchimp**
- Authentication through **Firebase (Identity Platform)**

#### **Development Tools**

- **[Firefoo](https://www.firefoo.app)** for Firestore database management
- **Google Cloud Console** for monitoring
- **[Flutter Flow](https://www.flutterflow.io/)** for frontend development
- **Firebase Console** for service management


### Sections

- [Data Models](./data-models/overview.md)

