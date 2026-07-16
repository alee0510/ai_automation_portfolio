# Dynamic RAG Pipeline & Vector Database Synchronization

*(Insert architecture or workflow screenshot here)*

## Overview

Designed and implemented a production-ready Retrieval-Augmented Generation (RAG) pipeline that automatically synchronizes documents between cloud storage and a PostgreSQL vector database. The system keeps AI knowledge up to date by handling document creation, updates, and deletion without manual intervention.

---

## Business Problem

Most RAG implementations assume documents are static. When source files are updated or removed, the vector database becomes outdated, resulting in stale responses and AI hallucinations.

The client required a reliable solution that could:

* Keep the knowledge base synchronized automatically
* Support multiple document repositories
* Enforce department-level access permissions
* Scale without manual database maintenance

---

## Solution

Built an event-driven document management pipeline in **n8n** using **PostgreSQL (PGVector)** and **Google Gemini Embeddings**.

The workflow automatically:

* Monitors Google Drive for document changes
* Extracts and classifies document content
* Generates semantic embeddings
* Stores document metadata and vectors in PostgreSQL
* Detects file updates and performs transactional re-indexing
* Removes obsolete vectors when documents are deleted
* Maintains access control through document metadata

---

## Key Technologies

* n8n
* PostgreSQL
* PGVector
* Google Gemini Embeddings
* Google Drive API
* Event-Driven Automation
* Relational Database Design

---

## Business Impact

* Eliminated stale vector data by synchronizing document changes in near real time
* Improved AI response accuracy by ensuring retrieval always uses the latest documents
* Reduced operational maintenance through fully automated indexing
* Enabled department-based document permissions for secure enterprise knowledge retrieval
* Built a scalable architecture capable of supporting multiple document repositories

---

## Architecture Highlights

* Event-driven synchronization between Google Drive and PostgreSQL
* Transactional upsert strategy for reliable vector updates
* Normalized relational schema for documents, embeddings, and storage sources
* Automatic document classification and embedding generation
* Modular design supporting multiple cloud storage providers

---

### Links

GitHub _(if available)_

