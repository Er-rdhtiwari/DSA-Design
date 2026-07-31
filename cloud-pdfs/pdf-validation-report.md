# PDF Validation Report

## Summary

- Source folder: `/Users/radheshyam/Desktop/BSS/DSA-Design/cloud`
- PDF output folder: `/Users/radheshyam/Desktop/BSS/DSA-Design/cloud/cloud-pdfs`
- Source pattern: `Day*.md`
- Expected Markdown file count: 14
- Discovered Markdown file count: 14
- Difference from expected count: +0
- PDFs generated: 14
- PDFs successfully validated: 14
- Source files unchanged: Yes
- One-to-one filename mapping: Yes
- Unresolved rendering issues: None

Validation included independent PDF reopening, non-empty checks, A4 portrait/landscape dimensions, 18 mm content-bound checks, page-number-only margin checks, required font-size checks, heading-order checks, visible character preservation, duplicate alphabetic-content checks, table/code structure checks, active-link target checks, Mermaid node/label/edge equivalence checks, and PNG render inspection of every page.

## Per-file results and checksum record

| Source Markdown filename | SHA-256 before | SHA-256 after | Generated PDF filename | PDF page count | Generation status | Validation status | Formatting issue detected | Formatting adjustment applied | Source content unchanged |
| --- | --- | --- | --- | ---: | --- | --- | --- | --- | --- |
| Day-12-ML-Fundamentals-Interview-Prep.md | 2b2fe442c209d82ae308bd2d2a400a80fd91bd24a505a52fab07efbf0d4a4efb | 2b2fe442c209d82ae308bd2d2a400a80fd91bd24a505a52fab07efbf0d4a4efb | Day-12-ML-Fundamentals-Interview-Prep.pdf | 21 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 272 characters); post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; source unchanged. | Yes |
| Day-13-Neural-Networks-and-Transformers.md | a285b2e9dc4a69e7961c3a716b3d0e45d43282e20e18089a7dc63e9efb3ca484 | a285b2e9dc4a69e7961c3a716b3d0e45d43282e20e18089a7dc63e9efb3ca484 | Day-13-Neural-Networks-and-Transformers.pdf | 23 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 280 characters); post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; source unchanged. | Yes |
| Day-14-LLM-Fundamentals-Interview-Prep.md | 8234183f8b4dc0f729f5f271b0595832c17da8df9dfa80f8702bbc92a5972fe6 | 8234183f8b4dc0f729f5f271b0595832c17da8df9dfa80f8702bbc92a5972fe6 | Day-14-LLM-Fundamentals-Interview-Prep.pdf | 21 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 586 characters); double-digit ordered-list markers near the left margin; post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; increased list indentation to keep markers inside 18 mm; source unchanged. | Yes |
| Day-15-Multimodal-Models-and-Diffusion.md | 739317a114dc2f76f1fe2fe622e784f34e2d4b524cd8083b8085766da8b2c43c | 739317a114dc2f76f1fe2fe622e784f34e2d4b524cd8083b8085766da8b2c43c | Day-15-Multimodal-Models-and-Diffusion.pdf | 30 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 355 characters); post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; source unchanged. | Yes |
| Day-16-Training-vs-Fine-Tuning-vs-PEFT.md | 464fc64d7eb51108fb941bb00192a77ead722bcaf25fe4fc02262bec82f9c7cf | 464fc64d7eb51108fb941bb00192a77ead722bcaf25fe4fc02262bec82f9c7cf | Day-16-Training-vs-Fine-Tuning-vs-PEFT.pdf | 28 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 697 characters); double-digit ordered-list markers near the left margin; post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; increased list indentation to keep markers inside 18 mm; source unchanged. | Yes |
| Day-17-LLM-Inference-Deployment.md | 8fc8fe5e8d3725a8393764b18fc10db338410d495b3d1b5d35a44a7fdac6fec9 | 8fc8fe5e8d3725a8393764b18fc10db338410d495b3d1b5d35a44a7fdac6fec9 | Day-17-LLM-Inference-Deployment.pdf | 26 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 654 characters); double-digit ordered-list markers near the left margin; post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; increased list indentation to keep markers inside 18 mm; source unchanged. | Yes |
| Day-18-Part-1-Docker-Compose-for-GenAI.md | 876c2b70dfec43c163fb4323f8d25bc61f57b75b0f7966ebc49ba320f37de7c0 | 876c2b70dfec43c163fb4323f8d25bc61f57b75b0f7966ebc49ba320f37de7c0 | Day-18-Part-1-Docker-Compose-for-GenAI.pdf | 55 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 316 characters); inline code inside a heading; post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; made inline heading code inherit the heading size and bold weight; source unchanged. | Yes |
| Day-18-Part-2-Terraform-IaC-Fundamentals-for-AWS.md | fbf1e2b87332b9f36198ebe86461235e3d8d03e4ea2b10a43ba0891652a38aaf | fbf1e2b87332b9f36198ebe86461235e3d8d03e4ea2b10a43ba0891652a38aaf | Day-18-Part-2-Terraform-IaC-Fundamentals-for-AWS.pdf | 33 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 411 characters); double-digit ordered-list markers near the left margin; inline code inside a heading; post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; increased list indentation to keep markers inside 18 mm; made inline heading code inherit the heading size and bold weight; source unchanged. | Yes |
| Day-19-AWS-GenAI-Infrastructure-with-Terraform.md | bfa7f35c55c80838eb5b2d78adf2707235152ac627e5512a51e44f66b754f057 | bfa7f35c55c80838eb5b2d78adf2707235152ac627e5512a51e44f66b754f057 | Day-19-AWS-GenAI-Infrastructure-with-Terraform.pdf | 30 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 600 characters); inline code inside a heading; post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; made inline heading code inherit the heading size and bold weight; source unchanged. | Yes |
| Day-20-Kubernetes-and-Helm-for-GenAI-Apps.md | 2ebc92e026532fb50085f8f54fadf3460bc49eed2451e707ec7e13e514d6a443 | 2ebc92e026532fb50085f8f54fadf3460bc49eed2451e707ec7e13e514d6a443 | Day-20-Kubernetes-and-Helm-for-GenAI-Apps.pdf | 30 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 720 characters); double-digit ordered-list markers near the left margin; inline code inside a heading; post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; increased list indentation to keep markers inside 18 mm; made inline heading code inherit the heading size and bold weight; source unchanged. | Yes |
| Day-21-Jenkins-CI-CD-for-GenAI.md | f4109294838465ae75dcfc6146f2c8584edc0e3aa41a207af4bf869caa48ea25 | f4109294838465ae75dcfc6146f2c8584edc0e3aa41a207af4bf869caa48ea25 | Day-21-Jenkins-CI-CD-for-GenAI.pdf | 27 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 822 characters); post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; source unchanged. | Yes |
| Day-22-Argo-CD-GitOps-for-GenAI.md | 7a2c1199ddc0b825685b89d3b939f725791b6acff84d1587d372191eeadfa083 | 7a2c1199ddc0b825685b89d3b939f725791b6acff84d1587d372191eeadfa083 | Day-22-Argo-CD-GitOps-for-GenAI.pdf | 55 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 359 characters); double-digit ordered-list markers near the left margin; inline code inside a heading; post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; increased list indentation to keep markers inside 18 mm; made inline heading code inherit the heading size and bold weight; source unchanged. | Yes |
| Day-23-MLflow-MLOps-and-LLMOps.md | c20d9cf1475dd919195bfed7610bc647a0fc29510afae4155f3e6bfdbd41102a | c20d9cf1475dd919195bfed7610bc647a0fc29510afae4155f3e6bfdbd41102a | Day-23-MLflow-MLOps-and-LLMOps.pdf | 46 | Success | Pass | Detected overflow risk from long code/table content (longest source line: 489 characters); double-digit ordered-list markers near the left margin; inline code inside a heading; post-render: none. | Applied source-preserving line wrapping for code/identifiers and table cells; increased list indentation to keep markers inside 18 mm; made inline heading code inherit the heading size and bold weight; source unchanged. | Yes |
| Day-24-Environments-and-Final-End-to-End-Integration.md | ff7c3772764a3a583dda8c7d90bb036e55b9d78661da4c2c5d8b56a3683bd7ea | ff7c3772764a3a583dda8c7d90bb036e55b9d78661da4c2c5d8b56a3683bd7ea | Day-24-Environments-and-Final-End-to-End-Integration.pdf | 53 | Success | Pass | Detected Mermaid blocks rendered as code instead of diagrams; two left-to-right flows were too wide for a readable print page; explicit ordered-list starts could reset visually; post-render: none. | Rendered all three Mermaid blocks as source-equivalent vector diagrams; used three dedicated A4 landscape pages; reflowed the two wide flows without changing nodes, labels, branches or edges; preserved explicit list numbering; source unchanged. | Yes |

## Structure checks

| Source Markdown filename | Headings | Tables | Code blocks / diagrams | Active link targets | Result |
| --- | ---: | ---: | ---: | ---: | --- |
| Day-12-ML-Fundamentals-Interview-Prep.md | 94 | 4 | 57 | 0 | Pass |
| Day-13-Neural-Networks-and-Transformers.md | 96 | 1 | 58 | 0 | Pass |
| Day-14-LLM-Fundamentals-Interview-Prep.md | 91 | 7 | 45 | 13 | Pass |
| Day-15-Multimodal-Models-and-Diffusion.md | 135 | 3 | 54 | 0 | Pass |
| Day-16-Training-vs-Fine-Tuning-vs-PEFT.md | 126 | 6 | 29 | 0 | Pass |
| Day-17-LLM-Inference-Deployment.md | 110 | 2 | 52 | 11 | Pass |
| Day-18-Part-1-Docker-Compose-for-GenAI.md | 172 | 2 | 180 | 30 | Pass |
| Day-18-Part-2-Terraform-IaC-Fundamentals-for-AWS.md | 113 | 1 | 83 | 20 | Pass |
| Day-19-AWS-GenAI-Infrastructure-with-Terraform.md | 98 | 1 | 50 | 16 | Pass |
| Day-20-Kubernetes-and-Helm-for-GenAI-Apps.md | 99 | 0 | 94 | 8 | Pass |
| Day-21-Jenkins-CI-CD-for-GenAI.md | 62 | 2 | 48 | 11 | Pass |
| Day-22-Argo-CD-GitOps-for-GenAI.md | 164 | 5 | 98 | 27 | Pass |
| Day-23-MLflow-MLOps-and-LLMOps.md | 105 | 10 | 64 | 31 | Pass |
| Day-24-Environments-and-Final-End-to-End-Integration.md | 151 | 12 | 27 | 12 | Pass |

## Unresolved issues

None.
