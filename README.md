# PDF Parsing Experimentation

This repository showcases an iterative experimentation phase for extracting text, tables, and images from PDFs using multiple libraries. This phase is focused on understanding the efficiency, performance, and limitations of various tools before designing a comprehensive pipeline.

---

## Overview

### Current Features:
- **Text Extraction**: Using `PyMuPDF` and `LangChain` (PyPDFLoader).
- **Table Extraction**: Comparison between `pdfplumber` and `Camelot`.
- **Image Extraction**: Using `PyMuPDF` with optional OCR via Tesseract.
- **Performance Metrics**: Execution time, memory usage, and extraction accuracy for each method.

---

## Setup

### Prerequisites:
- Python 3.7 or higher
- Install dependencies:
  ```bash
  pip install -r requirements.txt
  ```

---

## Usage

### Extract Text, Tables, and Images

1. Update the `pdf_path` with your PDF file.
2. Modify `EXPERIMENT_NAME` and extraction methods as needed.
3. Run the pipeline:
   ```bash
   python pdf_parser.py
   ```

---

## Results and Observations

### **1. Text Extraction**
| Library                 | Execution Time (Avg) | Memory Usage (Avg) | Items Extracted | Pages Processed | Success Rate |
| ----------------------- | -------------------- | ------------------ | --------------- | --------------- | ------------ |
| PyMuPDF                 | 0.75 seconds         | 0.0 MB             | 53              | 53              | 100%         |
| LangChain (PyPDFLoader) | 0.81 seconds         | 0.0 MB             | 53              | 53              | 100%         |

### **2. Table Extraction**
| Library    | Execution Time (Avg) | Memory Usage (Avg) | Items Extracted | Pages Processed | Success Rate |
| ---------- | -------------------- | ------------------ | --------------- | --------------- | ------------ |
| Camelot    | 23.24 seconds        | 134.83 MB          | 64              | 49              | 100%         |
| pdfplumber | 8.69 seconds         | 127.05 MB          | 22              | 11              | 100%         |

### **3. Image Extraction**
| Library | Execution Time (Avg) | Memory Usage (Avg) | Items Extracted | Pages Processed | Success Rate |
| ------- | -------------------- | ------------------ | --------------- | --------------- | ------------ |
| PyMuPDF | 14.26 seconds        | 0.0 MB             | 27              | 22              | 100%         |

---

## Performance Summary

| Aspect       | PyMuPDF (Text/Image) | LangChain (PyPDFLoader) | pdfplumber (Tables) | Camelot (Tables) |
| ------------ | -------------------- | ----------------------- | ------------------- | ---------------- |
| **Speed**    | Very Fast            | Fast                    | Moderate            | Moderate         |
| **Memory**   | High                 | Low                     | Moderate            | Moderate         |
| **Accuracy** | High                 | Moderate                | Moderate            | High             |

---

## Experimental Results (First 53 Pages)

| Metric              | Text Extraction (PyMuPDF) | Table Extraction (Camelot) | Image Extraction (PyMuPDF) |
| ------------------- | ------------------------- | -------------------------- | -------------------------- |
| **Execution Time**  | 0.75 seconds              | 23.24 seconds              | 14.26 seconds              |
| **Memory Usage**    | 0.0 MB                    | 134.83 MB                  | 0.0 MB                     |
| **Items Extracted** | 53                        | 64                         | 27                         |
| **Success Rate**    | 100%                      | 100%                       | 100%                       |

---

## Conclusive Thoughts
1. **Current Insights**:
   - `PyMuPDF` is efficient for text and image extraction but uses more memory than `LangChain` (PyPDFLoader).
   - `pdfplumber` outperforms `Camelot` in flexibility but lacks detailed metadata.
   - Image extraction is faster without OCR, but OCR enhances usability for text-based images.

2. **Future Steps**:
   - Integrate and test `PaddleOCR` and `PP-Structure` for comprehensive text, table, and image extraction.
   - Explore other libraries:
     - **Unstructured**: Advanced layout and semantic understanding.
     - **PDFMiner**: Reliable for text extraction and metadata.
     - **Pdftables**: Specialized for converting tables to structured formats.
     - **LLMWhisperer**: Leverage LLMs for better contextual understanding.

---

## Contribute

This project is an ongoing exploration. Feel free to suggest improvements or new libraries/tools for evaluation.

---

## License

This repository is licensed under the MIT License.