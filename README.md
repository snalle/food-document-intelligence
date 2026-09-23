# Food Document Intelligence

A reproducible benchmark for evaluating PDF parsing strategies on publicly available food-industry technical documentation.
## Overview

Food manufacturers and ingredient suppliers frequently distribute technical information across PDF documents such as product specifications, technical data sheets, allergen declarations, Halal and Kosher certificates, and food-safety documentation.

These documents vary considerably in structure. Important information may appear in paragraphs, tables, headers, certificates, or semi-structured layouts, making reliable extraction and retrieval challenging.

This project investigates whether structure-aware document parsing provides measurable benefits over lightweight PDF text extraction.

## Research Questions

**RQ1**: Does structure-aware PDF parsing materially improve retrieval quality relative to lightweight text extraction?

**RQ2**: For which document characteristics — such as tables, complex layouts, or scanned documents — does structure-aware parsing provide the largest improvement?

**RQ3**: How do parsing approaches differ in processing time, cost, and reliability, and how do these trade-offs relate to retrieval quality?

## Planned Approaches

The benchmark will investigate tools representing different approaches to document processing.

### Local / Open-source

- PyMuPDF — lightweight PDF text and layout extraction (https://github.com/pymupdf/pymupdf)
- PyMuPDF4LLM - Markdown-oriented PDF extraction for LLM and retrieval workflows (https://github.com/pymupdf/pymupdf4llm)
- Docling — structure-aware document parsing (https://github.com/docling-project/docling)
- Marker — PDF-to-structured-text conversion (https://github.com/datalab-to/marker)
- Unstructured — document partitioning and preprocessing (https://github.com/Unstructured-IO/unstructured)

Not every tool provides the same functionality. Part of the project is to investigate the trade-offs between lightweight extraction, specialized extraction, and full document-understanding pipelines.

### Managed / API-based

Potential later comparisons include:

- LlamaParse
- Azure AI Document Intelligence
- Amazon Textract
- FireCrawl


Managed services will be added after the local/open-source benchmark and evaluation pipeline have been established.

All downstream retrieval settings will be kept as consistent as possible so that the effect of the parsing strategy can be evaluated independently.
## Dataset

The benchmark uses publicly available technical documents from food-industry manufacturers and ingredient suppliers.

Target document types include:

- Product specifications
- Technical Data Sheets (TDS)
- Allergen declarations
- Halal certificates
- Kosher certificates
- Food-safety and quality certificates
- Regulatory statements

The corpus will contain documents from multiple suppliers to provide variation in layouts and document templates.

Third-party PDFs are not necessarily distributed directly with this repository. Source URLs and document metadata are recorded to support reproducibility while respecting document ownership and redistribution restrictions.

## Process

```
                    SAME PDFs
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
 PyMuPDF4LLM        Docling         Marker       ...
        │              │              │
        ▼              ▼              ▼
     Markdown       Markdown       Markdown
        │              │              │
        └──────────────┼──────────────┘
                       │
              SAME chunking strategy
                       │
              SAME embedding model
                       │
               SAME vector store
                       │
                 SAME queries
                       │
                       ▼
              RETRIEVAL QUALITY
```


## Evaluation

**To be decided**

## Project Structure
```
document-intelligence-benchmark/
├── README.md
```

The repository structure will evolve as the benchmark is implemented.

## Data and Privacy

This project uses publicly available documents only.

No confidential, proprietary, or internal company documents are used in the benchmark.

## License

The source code in this repository is licensed separately from the third-party documents used for evaluation. Copyright and licensing of source documents remain with their respective owners.
