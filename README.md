# Daniel Garcia Araque

**Senior Software Engineer | Software Architect**

Bogota, Colombia

[GitHub](https://github.com/DanielAraqueStudios) | [Email](mailto:est.daniel.garciaa@unimilitar.edu.co)

---

## Professional Summary

Software Engineer with 5+ years of experience designing and building **production-grade B2B platforms** with emphasis on **scalable architecture**, **data integrity**, and **system reliability**. Proven track record delivering **8+ production insurance tech systems**, multi-site IoT infrastructure, and cloud-native solutions using AWS. Demonstrated success as a **technical consultant** with 20+ client projects across industries (insurance, healthcare, retail, hospitality). Strong advocate for **documentation-driven development**, modular design patterns, and long-term maintainability. Demonstrated ability to lead technical decision-making, define standards, and collaborate with business stakeholders to translate requirements into robust, sustainable systems. English: Conversational (B2), actively improving.

---

## Core Competencies

### Architecture & Design
- Modular and domain-driven architecture
- Multi-tier system design (Edge + Cloud + Database)
- Scalability planning for national/international deployment
- Technical documentation and ADRs (Architecture Decision Records)
- API-first design principles

### Backend & APIs
- Python (FastAPI, Pandas, Pydantic, SQLAlchemy)
- REST API design and implementation
- Real-time communication (WebSocket, MQTT)
- Data transformation and ETL pipelines
- TypeScript / Node.js
- Third-party API integration (DIAN, WhatsApp)

### Desktop Applications
- PyQt6 GUI development (Dark Mode, tabbed interfaces)
- PDF generation engines (ReportLab)
- Standalone executable distribution (PyInstaller)
- Cross-platform packaging and deployment

### Data & Infrastructure
- PostgreSQL (partitioning, triggers, materialized views)
- DynamoDB for time-series telemetry
- Excel automation with openpyxl (deterministic outputs)
- Data validation and schema enforcement
- Multi-source data integration

### DevOps & CI/CD
- Docker and Docker Compose orchestration
- AWS CloudFormation (Infrastructure as Code)
- GitHub Actions workflows
- LocalStack for local AWS development
- Automated testing pipelines

### Security & Quality
- X.509 certificate management (mTLS)
- TLS 1.3 encryption
- VPN IPsec site-to-site configuration
- Input validation and sanitization
- Type hints and static analysis (mypy)

### Collaboration & Leadership
- Technical standards definition
- Sprint-based delivery with metrics tracking
- Cross-functional stakeholder collaboration
- Code review and quality assurance
- Mentoring and knowledge transfer

---

## Selected Projects

### Conciliator Softseguros Celer
**Insurance Data Reconciliation Platform** | Production System

**Context:** Built a production-grade backend to automate insurance portfolio reconciliation between two data sources (Softseguros and Celer), processing thousands of records with 100% data integrity.

**Role:** Technical Lead / System Owner

**Architecture:** Modular Python backend with domain-driven design, featuring a transformation engine, validation layer, and Excel output generator with deterministic formatting.

**Key Technical Decisions:**
- Implemented 3-tier matching logic (full match, partial match, special cases) with 9-digit receipt tolerance for handling data inconsistencies
- Designed streaming architecture for large file processing (50,000+ rows) using bulk operations instead of cell-by-cell processing
- Established Softseguros priority over Celer for duplicate resolution with automatic conflict detection
- Created comprehensive column mapping system (49 input columns to 23 standardized output columns)

**Impact:**
- Achieved 100% row preservation and data integrity across all transformations
- Reduced manual reconciliation time from days to seconds
- Delivered production metrics: 4.90% match rate detection, 736 unique records processed, 6 duplicates automatically resolved
- Sprint-based delivery with 90%+ test coverage

**Technologies:** Python, FastAPI, Pandas, Pydantic, openpyxl, PostgreSQL, pytest, mypy

---

### Insurance Document Automation System
**Collection Letter Generator** | Production System | SEGUROS UNIÓN

**Context:** Designed and built a production-grade document automation platform for insurance collection letters, deployed as a standalone desktop application for end-users with zero technical dependencies.

**Role:** System Architect / Full-Stack Developer

**Architecture:** Modular Python application with separation of concerns: GUI layer (PyQt6), business logic layer (Pydantic models), document generation layer (ReportLab PDF engine), and persistence layer (JSON-based CRUD).

```
┌──────────────────────┐
│   GUI (PyQt6)        │  ← Dark Mode, 3 tabs, CRUD inline
└──────────┬───────────┘
           │
┌──────────▼───────────┐
│  Pydantic Models     │  ← Asegurado, Poliza, Documento, MontosCobro
└──────────┬───────────┘
           │
┌──────────▼───────────┐
│  PDF Generators      │  ← ReportLab, BaseGenerator, Components
└──────────┬───────────┘
           │
┌──────────▼───────────┐
│  Utils / Managers    │  ← PayeeManager CRUD, Logger, Config
└──────────────────────┘
```

**Key Technical Decisions:**
- Implemented DIAN NIT verification algorithm (Colombian tax authority) for client validation
- Designed flexible validation system to accommodate real-world data inconsistencies while maintaining integrity
- Built PayeeManager with CRUD operations and usage tracking for 24+ Colombian insurance companies (Suramericana, Bolívar, Mapfre, Liberty, Allianz, etc.)
- Created portable executable distribution (45.48 MB standalone .exe) using PyInstaller for non-technical users
- Implemented comprehensive test suite (14 unit tests for PayeeManager alone)

**Impact:**
- Reduced document generation time from manual process (hours) to automated workflow (<2 seconds per letter)
- Achieved zero-dependency deployment: end-users only need the executable, no Python installation required
- Established maintainable architecture: generators/, models/, utils/, validators/, templates/, tests/
- Full audit trail with structured logging and document traceability

**Technologies:** Python 3.13, PyQt6, Pydantic 2.0, ReportLab, PyInstaller, JSON persistence, pytest

---

### Insurance Production Dashboard
**Business Intelligence Platform** | SEGUROS UNIÓN

**Context:** Built a dashboard application for processing and filtering insurance production reports from Excel (.xlsb) files with interactive visualization and export capabilities.

**Role:** Developer

**Architecture:** Python backend/frontend separation with dashboard utilities for data transformation and filtered CSV exports.

**Key Technical Decisions:**
- Designed Excel binary file parser for .xlsb format
- Implemented multi-criteria filtering with CSV output for downstream processing
- Created reusable dashboard utilities module

**Technologies:** Python, Pandas, Excel automation (.xlsb), CSV, Dashboard visualization

---

### IoT Agriculture Platform
**Multi-Site Smart Farming Infrastructure** | Enterprise-Scale Design

**Context:** Designed comprehensive IoT infrastructure for an agricultural company with 8 distributed sites across Boyaca and Cundinamarca regions, integrating 8,176 sensors, 2,024 RFID readers, and 2,024 IP cameras.

**Role:** System Architect / Full-Stack Developer

**Architecture:** Three-tier architecture with Edge Computing layer (gateways for local processing), Cloud layer (AWS IoT Core + Lambda + RDS), and Frontend layer (React dashboard with real-time WebSocket updates).

**Key Technical Decisions:**
- Designed IP addressing plan (10.0.0.0/16) with /19 subnets per site, supporting 65,536 total addresses with room for growth
- Implemented 48 VLANs for network segmentation by function (sensors, RFID, cameras, edge servers, management, users)
- Chose MQTT over TLS (port 8883) for sensor telemetry with Eclipse Mosquitto broker
- Selected LoRaWAN (915MHz) for remote field sensors with 15km range, WiFi for facilities
- Designed PostgreSQL schema with temporal partitioning for sensor_readings table (monthly partitions)

**Impact:**
- Enabled real-time monitoring of 8,176 sensors with <100ms latency
- Achieved 98.5% uptime across 8 sites with edge computing for offline resilience
- Automated irrigation control based on sensor thresholds with full traceability

**Technologies:** Python (FastAPI), TypeScript (React), PostgreSQL, AWS IoT Core, CloudFormation, Docker, MQTT, LoRaWAN, VPN IPsec

---

### AWS IoT Core Healthcare Monitoring
**Vital Signs Monitoring System** | Real-Time Streaming

**Context:** Implemented end-to-end IoT system for healthcare device monitoring (BedSide Monitor) with real-time anomaly detection and cloud persistence.

**Role:** Developer / Architect

**Architecture:** Event-driven pipeline: MQTT Publisher -> AWS IoT Core -> Kinesis Data Streams -> Lambda Consumers -> DynamoDB, with LocalStack for local development.

**Key Technical Decisions:**
- Implemented X.509 certificate authentication for device identity (mTLS)
- Designed Kinesis stream with multiple consumers (anomaly detector + DynamoDB writer)
- Used LocalStack 4.0+ for cost-free local development and testing

**Impact:**
- Processed 5,247 messages with 100% success rate (0% packet loss)
- Achieved 115ms average end-to-end latency (62-197ms range)
- Detected 541 anomalies (10.3%) with real-time alerting

**Technologies:** Python, AWS IoT Core, Amazon Kinesis, DynamoDB, Docker, LocalStack, X.509 Certificates

---

### Data Migration Platform
**Softseguros Migration System** | B2B Insurance Tool

**Context:** Developed comprehensive data migration toolkit for insurance client data, integrating DIAN (Colombian Tax Authority) API for NIT validation and automated data enrichment.

**Role:** Technical Lead / Developer

**Architecture:** Modular Python application with backend API, interactive CLI tools, and GUI for client data migration.

**Key Technical Decisions:**
- Implemented DIAN verification digit algorithm for NIT validation
- Created interactive calculators for batch NIT processing
- Designed template filling system for Softseguros platform import

**Impact:**
- Automated client data validation reducing manual verification errors
- Enabled batch processing of thousands of records with built-in error correction
- Established GitHub Copilot instructions for team productivity

**Technologies:** Python 97%, FastAPI, Excel automation, DIAN API integration

---

### PID Control System with Database Integration
**Industrial Temperature Control** | Embedded + Full-Stack

**Context:** Built complete PID temperature control system using ESP32-S3 microcontroller with PostgreSQL database integration for laboratory communications practice.

**Role:** Full-Stack Developer

**Architecture:** Embedded firmware (C++) + Node.js backend + PostgreSQL database with WebSocket real-time streaming.

**Key Technical Decisions:**
- Implemented configurable PID parameters (Kp, Ki, Kd) with real-time tuning via REST API
- Designed 5-minute rolling window for historical data access (laboratory requirement)
- Used WebSocket for real-time sensor data streaming at 1 Hz

**Impact:**
- Achieved ±1°C steady-state accuracy with <30 second response time
- Delivered 100ms communication latency over WiFi
- Created exportable CSV functionality for data analysis

**Technologies:** C++ (Arduino), Node.js, PostgreSQL, WebSocket, REST API, ESP32-S3

---

### Intelligent Energy Industry System
**Industrial Automation Prototype** | IoT & Energy Monitoring

**Context:** Developed ESP32-based intelligent automation system combining environmental monitoring, climate control, door automation, and real-time energy consumption tracking.

**Role:** Embedded Systems Developer

**Architecture:** Non-blocking concurrent task management with state machine implementation for multiple actuators.

**Key Technical Decisions:**
- Implemented exponential moving average (alpha=0.15) for sensor noise reduction
- Designed voltage divider circuit for solar panel monitoring up to 9.2V
- Created Watt-hour energy consumption calculation for each actuator

**Impact:**
- Demonstrated real-time energy monitoring with per-device tracking
- Automated climate control based on temperature thresholds
- Documented complete hardware specifications and safety considerations

**Technologies:** C++, ESP32, DHT11, HC-SR04, MAX6675 Thermocouple, PWM, DAC

---

### Technical Consulting Portfolio
**20+ Client Projects** | Full-Stack Development & Automation

**Context:** Delivered custom software solutions for diverse businesses across Colombia, demonstrating adaptability, client communication skills, and end-to-end project delivery.

**Representative Projects:**

| Client | Industry | Solution | Technology |
|--------|----------|----------|------------|
| SEGUROS UNIÓN | Insurance | Collection letter generator, production dashboard | Python, PyQt6, ReportLab |
| Acrildental | Healthcare | WhatsApp quotation bot | JavaScript, WhatsApp API |
| Mantra Coworking | Real Estate | Business website (3 versions) | JavaScript, React |
| Carnicería Casa Rioja | Retail | Quotation system | JavaScript |
| Arte Acero | Manufacturing | Business platform | JavaScript |
| Bioteck | Healthcare | Web application | JavaScript |
| LFC Arquitectura | Architecture | Portfolio site | JavaScript |
| CH Beauty Salon | Beauty | Booking platform (2 versions) | JavaScript, HTML |
| Dulces El Trapiche | Food | Business website | JavaScript |
| La Katrina Gastrobar | Hospitality | Restaurant platform | JavaScript |
| El Escondrijo | Entertainment | Venue website | JavaScript |
| OK Producciones | Events | Production company site | JavaScript |

**Impact:**
- Established repeatable delivery process: requirements gathering → design → development → deployment
- Built long-term client relationships with return engagements (Mantra Coworking: 3 versions)
- Demonstrated domain versatility across 8+ industries

---

## Documentation & Process Culture

- **README-Driven Development:** Every project includes comprehensive README with architecture diagrams, installation guides, and troubleshooting sections
- **Technical Documentation:** Column mapping guides, API endpoint documentation, and hardware specifications
- **Sprint Tracking:** Visible sprint achievements with completion metrics and test coverage reports
- **Code Standards:** Established coding standards with type hints, mypy compliance, and automated formatting (Black, Ruff)
- **Structured Logging:** Correlation IDs and contextual logging for production observability
- **Decision Records:** Key architectural decisions documented with rationale

---

## Education

**Mechatronics Engineering**  
Universidad Militar Nueva Granada  
Expected Graduation: 2026

---

## Languages

- **Spanish:** Native
- **English:** Conversational (B2), actively improving

---

## Technical Metrics

| Metric | Value |
|--------|-------|
| GitHub Contributions (Last Year) | 782+ |
| Public Repositories | 111 |
| Primary Languages | Python, TypeScript, JavaScript, C++ |
| Production Systems Delivered | 8+ |
| Client Projects Completed | 20+ |
| Test Coverage (Key Projects) | 90%+ |
| Desktop Apps Deployed | 2 (standalone .exe) |

---

## Keywords

Python, FastAPI, Pandas, PostgreSQL, AWS IoT Core, CloudFormation, Docker, REST API, MQTT, TypeScript, React, Node.js, Pydantic, SQLAlchemy, openpyxl, DynamoDB, Kinesis, X.509, TLS, VPN, LoRaWAN, ESP32, C++, CI/CD, GitHub Actions, LocalStack, Terraform, Infrastructure as Code, B2B Platforms, Insurance Tech, IoT, Edge Computing, Data Pipelines, ETL, System Architecture, Technical Leadership, PyQt6, ReportLab, PDF Generation, Desktop Applications, PyInstaller, DIAN API, Colombian Tax Integration, Technical Consulting, WhatsApp API, Client Delivery

---

*Last Updated: February 2026*
