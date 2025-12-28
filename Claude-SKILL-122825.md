 SKILLS.md

## Comprehensive AI Skills Documentation

This document outlines 10 specialized AI skills for document processing, analysis, and application development. Each skill provides detailed capabilities and mandatory triggers for activation.

---

## Skill 1: PDF to Markdown Transformer & Summarizer

**pdf-markdown-analyzer**

### Description
Advanced PDF document processing that converts any PDF file into clean, structured markdown format with comprehensive summarization capabilities.

### Capabilities
- **PDF Text Extraction**: Full text extraction from multi-page PDF documents with layout preservation
- **Markdown Conversion**: Intelligent conversion maintaining headers, lists, tables, and formatting
- **Image Handling**: Extract and reference embedded images
- **Table Recognition**: Convert PDF tables into markdown table format
- **Comprehensive Summary**: Generate detailed 4000-5000 word analytical summaries
- **Structure Analysis**: Identify and preserve document hierarchy
- **Metadata Extraction**: Capture author, title, creation date, and document properties

### Summary Features
- Executive summary (200-300 words)
- Detailed section-by-section analysis
- Key findings and insights
- Statistical data presentation
- References and citations
- Conclusion and recommendations

### Output Format
```markdown
# [Document Title]

## Metadata
- **Author**: [Name]
- **Date**: [Date]
- **Pages**: [Number]

## Executive Summary
[200-300 words overview]

## Comprehensive Analysis
[4000-5000 words detailed summary]

## Key Insights
- [Insight 1]
- [Insight 2]

## Conclusion
[Final analysis]
```

### MANDATORY TRIGGERS
PDF, .pdf, pdf file, convert pdf, pdf to markdown, extract pdf, pdf analysis, document conversion, pdf summary

### Supported Formats
- PDF 1.0 - 2.0
- Scanned PDFs (with OCR)
- Multi-column layouts
- Academic papers
- Reports and whitepapers

---

## Skill 2: Multi-Format Document Organizer & Keyword Highlighter

**doc-organizer-coral**

### Description
Transform text, DOCX, and markdown files into beautifully organized markdown with coral-colored keyword highlighting and comprehensive summarization.

### Capabilities
- **Format Support**: TXT, DOCX, MD, RTF
- **Intelligent Organization**: Auto-detect structure and reorganize content
- **Keyword Extraction**: AI-powered keyword identification
- **Coral Color Highlighting**: Apply `<span style="color: coral;">keyword</span>` to important terms
- **Semantic Analysis**: Group related content intelligently
- **Hierarchical Structuring**: Create logical header hierarchy
- **Cross-referencing**: Link related sections
- **Summary Generation**: 4000-5000 word comprehensive summary

### Keyword Highlighting Criteria
- Technical terms (15-20%)
- Key concepts (20-25%)
- Important names and entities (10-15%)
- Action items and conclusions (10-15%)
- Statistical data (5-10%)

### Output Format
```markdown
# <span style="color: coral;">Main Title</span>

## Table of Contents
[Auto-generated with coral keywords]

## Organized Content
Content with <span style="color: coral;">highlighted keywords</span>

## Comprehensive Summary (4000-5000 words)
[Detailed analysis with coral-highlighted key terms]

## Keyword Index
- <span style="color: coral;">Keyword 1</span>: Context
- <span style="color: coral;">Keyword 2</span>: Context
```

### MANDATORY TRIGGERS
text file, docx, word document, .md, markdown file, organize, structure, keywords, highlight, coral, document analysis, text processing

### Processing Pipeline
1. File parsing and format detection
2. Content extraction and cleaning
3. Structural analysis
4. Keyword identification (AI-powered)
5. Coral color application
6. Summary generation
7. Index creation

---

## Skill 3: Entity Extraction & Contextual Analysis Engine

**entity-context-analyzer**

### Description
Extract 20 key entities from any document with rich contextual information, comments, and relationships, accompanied by comprehensive summary documentation.

### Capabilities
- **Entity Recognition**: Identify 20 most significant entities
- **Entity Types**: People, organizations, locations, concepts, products, technologies, events, dates
- **Contextual Analysis**: Provide surrounding context for each entity
- **Relationship Mapping**: Show connections between entities
- **Sentiment Analysis**: Determine entity sentiment in document
- **Frequency Tracking**: Count entity mentions
- **Commentary**: AI-generated insights per entity
- **Comprehensive Summary**: 4000-5000 word analytical document

### Entity Structure
```markdown
## Entity [N]: [Entity Name]

**Type**: [Person/Organization/Location/Concept/etc.]
**Frequency**: [N mentions]
**Sentiment**: [Positive/Neutral/Negative]

### Context
[Paragraph explaining where and how entity appears]

### Key Relationships
- Related to: [Entity X]
- Interacts with: [Entity Y]
- Part of: [Entity Z]

### Comments
[AI-generated insights about significance]

### Quotes/References
> "[Direct quote mentioning entity]"
```

### Analysis Output
```markdown
# Entity Analysis Report

## Overview
Total Entities: 20
Document Length: [X words]
Analysis Date: [Date]

## Entity List
1. [Entity 1] - [Type]
2. [Entity 2] - [Type]
...

## Detailed Entity Analysis
[20 detailed entity sections]

## Entity Relationship Map
[Visual representation in markdown]

## Comprehensive Summary (4000-5000 words)
[Detailed analysis incorporating all entities]

## Statistical Analysis
[Tables with entity metrics]
```

### MANDATORY TRIGGERS
entities, extract entities, entity recognition, NER, named entities, context analysis, relationship mapping, entity extraction, semantic analysis

### Entity Selection Criteria
- Frequency of appearance (30%)
- Contextual importance (30%)
- Relationship centrality (20%)
- Semantic significance (20%)

---

## Skill 4: Multi-API Streamlit Application Generator

**streamlit-multiapi-builder**

### Description
Generate production-ready Streamlit applications with OPENAI, GEMINI, and ANTHROPIC API integrations, complete deployment configuration for Hugging Face Spaces.

### Capabilities
- **app.py Generation**: Complete Streamlit application code
- **agents.yaml Configuration**: Advanced agent definitions
- **Multi-API Support**: OpenAI, Gemini, Anthropic Claude
- **API Key Management**: Environment variables + user input
- **Security**: Masked API keys from environment
- **Error Handling**: Comprehensive exception management
- **Session State**: Persistent user data
- **File Upload**: Support multiple file formats
- **Response Streaming**: Real-time API responses

### Generated Files

#### app.py Structure
```python
import streamlit as st
import os
from openai import OpenAI
import google.generativeai as genai
import anthropic

# Configuration
st.set_page_config(page_title="AI Assistant", layout="wide")

# API Key Management
def get_api_keys():
    # Check environment first
    openai_key = os.getenv("OPENAI_API_KEY")
    gemini_key = os.getenv("GEMINI_API_KEY")
    anthropic_key = os.getenv("ANTHROPIC_API_KEY")
    
    # User input if not in environment (with masking)
    # Implementation details...
    
# Main application
# [Full implementation]
```

#### agents.yaml Structure
```yaml
agents:
  - name: document_analyzer
    model: gpt-4
    temperature: 0.7
    max_tokens: 4000
    system_prompt: |
      You are an expert document analyzer...
    
  - name: code_generator
    model: claude-3-opus
    temperature: 0.3
    max_tokens: 8000
    system_prompt: |
      You are a senior software engineer...
    
  - name: creative_writer
    model: gemini-pro
    temperature: 0.9
    max_tokens: 2000
    system_prompt: |
      You are a creative content writer...

configurations:
  openai:
    models: [gpt-4, gpt-4-turbo, gpt-3.5-turbo]
  gemini:
    models: [gemini-pro, gemini-pro-vision]
  anthropic:
    models: [claude-3-opus, claude-3-sonnet, claude-3-haiku]
```

### Deployment Files

#### requirements.txt
```
streamlit==1.32.0
openai==1.12.0
google-generativeai==0.3.2
anthropic==0.18.1
python-dotenv==1.0.0
pyyaml==6.0.1
```

#### README.md
```markdown
# AI Multi-API Assistant

Deployment instructions for Hugging Face Spaces...
```

### Features
- **API Selection**: Dropdown to choose API provider
- **Model Selection**: Dynamic model list per provider
- **Temperature Control**: Slider for response creativity
- **Token Limit**: Adjustable max tokens
- **System Prompt**: Customizable agent behavior
- **Chat History**: Session-based conversation memory
- **File Processing**: Upload and analyze documents
- **Export**: Download responses as markdown

### MANDATORY TRIGGERS
streamlit, app.py, agents.yaml, hugging face, space, deployment, openai api, gemini api, anthropic api, claude api, api integration, web app

### Security Features
- Environment variable priority
- Masked API key display
- No API key logging
- Secure session management
- HTTPS enforcement

---

## Skill 5: WOW UI Designer with Theme & Style Systems

**wow-ui-designer**

### Description
Transform existing applications into stunning interfaces with light/dark themes, multilingual support (English/Traditional Chinese), and 20 artist-inspired styles with jackpot selection feature.

### Capabilities
- **Theme System**: Light/Dark mode with smooth transitions
- **Bilingual Support**: English ⇄ Traditional Chinese (繁體中文)
- **20 Artist Styles**: Famous painter-inspired color schemes and layouts
- **Jackpot Feature**: Random style selector with animation
- **Feature Preservation**: All original functionality maintained
- **Responsive Design**: Mobile, tablet, desktop optimized
- **Accessibility**: WCAG 2.1 AA compliant
- **Animation System**: Smooth transitions and micro-interactions

### Artist Style Collection

1. **Vincent van Gogh** - Swirling blues and yellows, expressive brushstrokes
2. **Claude Monet** - Soft pastels, water lily motifs, impressionist blur
3. **Pablo Picasso** - Cubist geometry, bold primary colors, abstract forms
4. **Salvador Dalí** - Surreal gradients, melting effects, dreamlike atmosphere
5. **Frida Kahlo** - Vibrant Mexican colors, floral patterns, bold contrasts
6. **Wassily Kandinsky** - Abstract geometric shapes, spiritual colors
7. **Georgia O'Keeffe** - Organic curves, desert tones, flower close-ups
8. **Jackson Pollock** - Splattered patterns, chaotic energy, action painting
9. **Andy Warhol** - Pop art colors, repeated patterns, high contrast
10. **Henri Matisse** - Fauvist colors, paper cut-out shapes, bold simplicity
11. **Edvard Munch** - Emotional colors, wavy lines, expressionist mood
12. **Gustav Klimt** - Gold patterns, ornate decorations, art nouveau
13. **Yayoi Kusama** - Polka dots, infinite patterns, psychedelic colors
14. **Banksy** - Stencil effects, street art aesthetic, monochrome with red
15. **Hokusai** - Japanese waves, ukiyo-e style, indigo and white
16. **Rothko** - Color field blocks, meditative gradients, minimal
17. **Mondrian** - Primary colors, grid layouts, neo-plasticism
18. **Basquiat** - Neo-expressionist, crown motifs, street art energy
19. **Caravaggio** - Dramatic lighting, chiaroscuro, baroque elegance
20. **Renaissance** - Classical proportions, gold accents, symmetrical

### Code Structure

```python
import streamlit as st

# Theme Configuration
THEMES = {
    "light": {
        "primary": "#1f77b4",
        "background": "#ffffff",
        "text": "#333333",
        "secondary": "#f0f2f6"
    },
    "dark": {
        "primary": "#58d68d",
        "background": "#0e1117",
        "text": "#fafafa",
        "secondary": "#262730"
    }
}

# Language Support
TRANSLATIONS = {
    "en": {
        "title": "AI Assistant",
        "select_style": "Select Style",
        "jackpot": "🎰 Jackpot!",
        # ... more translations
    },
    "zh": {
        "title": "AI 助手",
        "select_style": "選擇風格",
        "jackpot": "🎰 老虎機！",
        # ... more translations
    }
}

# Artist Styles
ARTIST_STYLES = {
    "van_gogh": {
        "primary": "#4169E1",
        "secondary": "#FFD700",
        "accent": "#87CEEB",
        "font": "cursive",
        "pattern": "swirl"
    },
    # ... 19 more styles
}

# Jackpot Animation
def jackpot_spin():
    import random
    import time
    
    placeholder = st.empty()
    for i in range(20):
        style = random.choice(list(ARTIST_STYLES.keys()))
        placeholder.markdown(f"## 🎰 {style}")
        time.sleep(0.1)
    
    final_style = random.choice(list(ARTIST_STYLES.keys()))
    st.balloons()
    return final_style

# Apply Custom CSS
def apply_style(theme, language, artist_style):
    css = f"""
    <style>
        :root {{
            --primary-color: {THEMES[theme]['primary']};
            --background-color: {THEMES[theme]['background']};
            --text-color: {THEMES[theme]['text']};
            --artist-primary: {ARTIST_STYLES[artist_style]['primary']};
            --artist-secondary: {ARTIST_STYLES[artist_style]['secondary']};
        }}
        
        .main {{
            background-color: var(--background-color);
            color: var(--text-color);
            transition: all 0.3s ease;
        }}
        
        /* Artist-specific styles */
        .artist-border {{
            border: 3px solid var(--artist-primary);
            border-radius: 10px;
            padding: 20px;
            background: linear-gradient(
                135deg, 
                var(--artist-primary) 0%, 
                var(--artist-secondary) 100%
            );
        }}
        
        /* Animations */
        @keyframes fadeIn {{
            from {{ opacity: 0; transform: translateY(20px); }}
            to {{ opacity: 1; transform: translateY(0); }}
        }}
        
        .animated {{
            animation: fadeIn 0.5s ease-in;
        }}
    </style>
    """
    st.markdown(css, unsafe_allow_html=True)
```

### UI Components

```python
# Sidebar Configuration
with st.sidebar:
    st.image("logo.png", width=200)
    
    # Language Selector
    language = st.selectbox(
        "🌐 Language / 語言",
        ["English", "繁體中文"],
        index=0
    )
    lang_code = "en" if language == "English" else "zh"
    
    # Theme Toggle
    theme = st.radio(
        TRANSLATIONS[lang_code]["theme"],
        ["☀️ Light", "🌙 Dark"],
        horizontal=True
    )
    theme_code = "light" if "Light" in theme else "dark"
    
    # Artist Style Selector
    st.markdown("---")
    st.subheader(TRANSLATIONS[lang_code]["select_style"])
    
    col1, col2 = st.columns([3, 1])
    with col1:
        artist_style = st.selectbox(
            "🎨",
            list(ARTIST_STYLES.keys()),
            format_func=lambda x: x.replace("_", " ").title()
        )
    with col2:
        if st.button("🎰"):
            artist_style = jackpot_spin()
            st.rerun()
    
    # Style Preview
    with st.expander("🖼️ Preview"):
        st.color_picker(
            "Primary",
            ARTIST_STYLES[artist_style]['primary']
        )
        st.color_picker(
            "Secondary",
            ARTIST_STYLES[artist_style]['secondary']
        )

# Apply styles
apply_style(theme_code, lang_code, artist_style)
```

### MANDATORY TRIGGERS
UI design, redesign, wow ui, themes, light mode, dark mode, multilingual, chinese, 繁體中文, artist styles, painter styles, jackpot, style selector, beautiful ui, modern design

### Enhancement Features
- **Smooth Transitions**: 0.3s ease for all color changes
- **Hover Effects**: Interactive buttons and cards
- **Loading Animations**: Spinners matching artist style
- **Toast Notifications**: Themed success/error messages
- **Glassmorphism**: Frosted glass effects for modals
- **Neumorphism**: Soft shadows for cards

---

## Skill 6: Technical Specification Document Generator

**tech-spec-generator**

### Description
Create comprehensive technical specification documents including SRS, architecture diagrams, environment setup, deployment instructions, and advanced prompts. Output: 6000-7000 words in markdown.

### Document Sections

#### 1. Executive Summary (500 words)
- Project overview
- Objectives and goals
- Stakeholders
- Success metrics
- Timeline summary

#### 2. Software Requirements Specification (SRS) (1200 words)

**Functional Requirements**
```markdown
### FR-001: User Authentication
**Priority**: High
**Description**: System shall provide secure user authentication
**Acceptance Criteria**:
- Users can register with email/password
- Password must meet complexity requirements
- JWT token issued upon successful login
- Session expires after 24 hours
**Dependencies**: None
```

**Non-Functional Requirements**
- Performance: Response time < 200ms
- Scalability: Support 10,000 concurrent users
- Security: OWASP Top 10 compliance
- Availability: 99.9% uptime
- Usability: WCAG 2.1 AA accessibility

#### 3. System Architecture (1500 words)

**Architecture Diagram**
```markdown
┌─────────────────┐
│   Client Layer   │
│  (React/Vue)    │
└────────┬────────┘
         │
┌────────▼────────┐
│   API Gateway   │
│   (Kong/Nginx)  │
└────────┬────────┘
         │
┌────────▼────────────────────┐
│   Application Layer         │
│  ┌──────┐  ┌──────┐        │
│  │ API  │  │ Auth │        │
│  │Service│  │Service│       │
│  └──────┘  └──────┘        │
└────────┬────────────────────┘
         │
┌────────▼────────────────────┐
│   Data Layer                │
│  ┌──────┐  ┌──────┐        │
│  │  DB  │  │Cache │        │
│  │Postgres│  │Redis│        │
│  └──────┘  └──────┘        │
└─────────────────────────────┘
```

**Components**
- Frontend: React 18, TypeScript, Tailwind CSS
- Backend: FastAPI, Python 3.11, async/await
- Database: PostgreSQL 15, TimescaleDB
- Cache: Redis 7, Redis Sentinel
- Message Queue: RabbitMQ, Celery
- Storage: AWS S3, CloudFront CDN
- Monitoring: Prometheus, Grafana, Sentry

#### 4. Environment Settings (800 words)

**Development Environment**
```bash
# .env.development
APP_ENV=development
DEBUG=true
LOG_LEVEL=debug

# Database
DATABASE_URL=postgresql://user:pass@localhost:5432/db
DATABASE_POOL_SIZE=5

# Redis
REDIS_URL=redis://localhost:6379/0

# APIs
OPENAI_API_KEY=sk-...
GEMINI_API_KEY=AI...
ANTHROPIC_API_KEY=sk-ant-...

# Security
SECRET_KEY=dev-secret-key-change-in-prod
JWT_ALGORITHM=HS256
JWT_EXPIRATION=86400

# CORS
CORS_ORIGINS=["http://localhost:3000"]
```

**Production Environment**
```bash
# .env.production
APP_ENV=production
DEBUG=false
LOG_LEVEL=info

# Database (managed)
DATABASE_URL=${RDS_CONNECTION_STRING}
DATABASE_POOL_SIZE=20
DATABASE_SSL=true

# Redis (managed)
REDIS_URL=${ELASTICACHE_CONNECTION_STRING}
REDIS_SENTINEL=true

# APIs (from secrets manager)
OPENAI_API_KEY=${SECRET_OPENAI_KEY}
GEMINI_API_KEY=${SECRET_GEMINI_KEY}
ANTHROPIC_API_KEY=${SECRET_ANTHROPIC_KEY}

# Security
SECRET_KEY=${SECRET_JWT_KEY}
JWT_ALGORITHM=RS256
JWT_EXPIRATION=3600

# CORS
CORS_ORIGINS=["https://app.example.com"]

# Monitoring
SENTRY_DSN=${SECRET_SENTRY_DSN}
DATADOG_API_KEY=${SECRET_DATADOG_KEY}
```

#### 5. Deployment Instructions (1000 words)

**Docker Deployment**
```dockerfile
# Dockerfile
FROM python:3.11-slim

WORKDIR /app

# Install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application
COPY . .

# Create non-root user
RUN useradd -m appuser && chown -R appuser:appuser /app
USER appuser

# Expose port
EXPOSE 8000

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=40s \
  CMD curl -f http://localhost:8000/health || exit 1

# Run application
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

**Docker Compose**
```yaml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "8000:8000"
    environment:
      - DATABASE_URL=postgresql://postgres:password@db:5432/appdb
      - REDIS_URL=redis://redis:6379
    depends_on:
      - db
      - redis
    restart: unless-stopped
    
  db:
    image: postgres:15-alpine
    volumes:
      - postgres_data:/var/lib/postgresql/data
    environment:
      POSTGRES_PASSWORD: password
      POSTGRES_DB: appdb
    
  redis:
    image: redis:7-alpine
    volumes:
      - redis_data:/data

volumes:
  postgres_data:
  redis_data:
```

**Kubernetes Deployment**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: app-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: app
        image: myapp:latest
        ports:
        - containerPort: 8000
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: app-secrets
              key: database-url
        resources:
          requests:
            memory: "256Mi"
            cpu: "250m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 8000
          initialDelaySeconds: 30
          periodSeconds: 10
```

**CI/CD Pipeline (GitHub Actions)**
```yaml
name: Deploy to Production

on:
  push:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run tests
        run: |
          pip install -r requirements.txt
          pytest
  
  build:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build Docker image
        run: docker build -t myapp:${{ github.sha }} .
      - name: Push to registry
        run: docker push myapp:${{ github.sha }}
  
  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to Kubernetes
        run: |
          kubectl set image deployment/app-deployment \
            app=myapp:${{ github.sha }}
```

#### 6. Advanced Prompts (1000 words)

**Prompt Engineering Framework**

```markdown
### Structure
1. **Role Definition**: Define AI persona
2. **Context**: Provide background information
3. **Task**: Clear, specific instructions
4. **Format**: Expected output structure
5. **Constraints**: Limitations and requirements
6. **Examples**: Few-shot learning samples

### Template
You are a [ROLE] with expertise in [DOMAIN].

Context:
[BACKGROUND INFORMATION]

Task:
[SPECIFIC INSTRUCTIONS]

Output Format:
[STRUCTURE REQUIREMENTS]

Constraints:
- [CONSTRAINT 1]
- [CONSTRAINT 2]

Example:
Input: [EXAMPLE INPUT]
Output: [EXAMPLE OUTPUT]
```

**Advanced Prompt Examples**

**1. Code Review Prompt**
```
You are a senior software engineer conducting a thorough code review.

Context:
- Language: Python 3.11
- Framework: FastAPI
- Focus: Security, performance, maintainability

Task:
Review the following code and provide:
1. Security vulnerabilities (OWASP Top 10)
2. Performance bottlenecks
3. Code smells and anti-patterns
4. Suggestions for improvement
5. Refactored code examples

Output Format:
## Security Issues
[List with severity: Critical/High/Medium/Low]

## Performance Analysis
[Bottlenecks with metrics]

## Code Quality
[Issues with line numbers]

## Recommendations
[Prioritized improvements]

## Refactored Code
```python
[Improved version]
```

Constraints:
- Use type hints
- Follow PEP 8
- Include docstrings
- Add unit tests
```

**2. Document Analysis Prompt**
```
You are an expert business analyst with 15 years of experience in document analysis and strategic planning.

Context:
Document Type: [Annual Report/Technical Specification/Business Plan]
Industry: [Finance/Technology/Healthcare]
Length: [Number of pages]

Task:
Perform comprehensive analysis including:
1. Executive summary (300 words)
2. Key findings and insights
3. SWOT analysis
4. Financial metrics analysis
5. Risk assessment
6. Strategic recommendations
7. Competitive analysis
8. Market trends identification

Output Format:
# Document Analysis Report

## Executive Summary
[Concise overview]

## Detailed Analysis
### Section 1: [Name]
[Analysis]

### Section 2: [Name]
[Analysis]

## SWOT Analysis
| Strengths | Weaknesses |
|-----------|------------|
| ...       | ...        |

| Opportunities | Threats |
|---------------|---------|
| ...           | ...     |

## Financial Metrics
| Metric | Value | YoY Change |
|--------|-------|------------|
| ...    | ...   | ...        |

## Recommendations
1. [Priority 1 - High Impact]
2. [Priority 2 - Medium Impact]

Constraints:
- Cite page numbers for all claims
- Provide quantitative data where available
- Identify data gaps and limitations
- Consider industry standards
```

**3. Creative Content Generation**
```
You are a world-class content creator specializing in [Marketing/Technical Writing/Creative Fiction].

Context:
Target Audience: [Demographics, interests, pain points]
Brand Voice: [Professional/Casual/Technical/Playful]
Goal: [Inform/Persuade/Entertain/Educate]
Medium: [Blog post/Social media/Email/Video script]

Task:
Create engaging content that:
1. Captures attention in first 3 seconds
2. Addresses audience pain points
3. Provides actionable value
4. Includes clear call-to-action
5. Optimized for SEO (if applicable)

Output Format:
# [Compelling Headline]

## Hook
[Opening paragraph - 50 words]

## Main Content
[Body with subheadings - 500-800 words]

## Key Takeaways
- [Takeaway 1]
- [Takeaway 2]
- [Takeaway 3]

## Call to Action
[Clear next step]

## SEO Metadata
Title: [60 characters]
Description: [160 characters]
Keywords: [10 relevant keywords]

Constraints:
- Readability: Grade 8-10 level
- Tone: [Specified tone]
- Length: [Word count]
- Include: [Statistics/Examples/Case studies]
```

#### 7. API Documentation (800 words)

**REST API Endpoints**

```markdown
### Authentication

#### POST /api/v1/auth/register
Register a new user account.

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "SecurePass123!",
  "full_name": "John Doe"
}
```

**Response (201 Created):**
```json
{
  "user_id": "uuid-here",
  "email": "user@example.com",
  "full_name": "John Doe",
  "created_at": "2024-01-15T10:30:00Z"
}
```

**Error Responses:**
- 400: Invalid input
- 409: Email already registered
- 422: Validation error

---

#### POST /api/v1/auth/login
Authenticate user and receive JWT token.

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "SecurePass123!"
}
```

**Response (200 OK):**
```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIs...",
  "token_type": "bearer",
  "expires_in": 3600
}
```

### Document Processing

#### POST /api/v1/documents/analyze
Upload and analyze document.

**Headers:**
```
Authorization: Bearer {access_token}
Content-Type: multipart/form-data
```

**Request:**
```
file: [binary]
options: {
  "summary_length": 5000,
  "extract_entities": true,
  "language": "en"
}
```

**Response (200 OK):**
```json
{
  "document_id": "doc-uuid",
  "status": "completed",
  "summary": "Comprehensive summary...",
  "entities": [...],
  "metadata": {...}
}
```
```

#### 8. Testing Strategy (700 words)

**Test Pyramid**
- Unit Tests: 70%
- Integration Tests: 20%
- E2E Tests: 10%

**Coverage Requirements**
- Overall: >80%
- Critical paths: >95%
- New code: 100%

### MANDATORY TRIGGERS
technical specification, SRS, software requirements, system architecture, deployment, environment setup, technical documentation, specifications document, tech specs, architecture document

---

## Skill 7: Multi-Table Summary Generator

**data-summary-tables**

### Description
Create comprehensive summaries with 10 detailed tables in markdown format, totaling 6000-7000 words, based on any provided file or dataset.

### Capabilities
- **10 Table Creation**: Automatically generate 10 relevant tables
- **Data Analysis**: Extract key metrics and statistics
- **Comparative Analysis**: Side-by-side comparisons
- **Trend Identification**: Temporal data analysis
- **Category Breakdown**: Hierarchical data organization
- **Statistical Tables**: Mean, median, standard deviation, correlations
- **Summary Tables**: Executive summaries in tabular format
- **Cross-Reference Tables**: Relationship mapping
- **Comprehensive Narrative**: 6000-7000 words accompanying tables

### Table Types

#### Table 1: Executive Summary
| Metric | Value | Description |
|--------|-------|-------------|
| Total Records | 10,245 | Complete dataset size |
| Date Range | 2020-2024 | Time period covered |
| Categories | 15 | Number of classifications |
| Key Finding 1 | 45% increase | Primary insight |
| Key Finding 2 | $2.5M | Financial impact |

#### Table 2: Descriptive Statistics
| Variable | Count | Mean | Median | Std Dev | Min | Max |
|----------|-------|------|--------|---------|-----|-----|
| Revenue | 1000 | $125K | $98K | $45K | $10K | $500K |
| Users | 1000 | 1,250 | 980 | 450 | 100 | 5,000 |
| Engagement | 1000 | 67% | 72% | 15% | 20% | 98% |

#### Table 3: Category Breakdown
| Category | Count | Percentage | Revenue | Avg. Value |
|----------|-------|------------|---------|------------|
| Enterprise | 150 | 15% | $5.2M | $34,667 |
| Mid-Market | 450 | 45% | $8.1M | $18,000 |
| Small Business | 400 | 40% | $2.8M | $7,000 |
| **Total** | **1000** | **100%** | **$16.1M** | **$16,100** |

#### Table 4: Time Series Analysis
| Period | Metric A | Growth % | Metric B | Growth % | Events |
|--------|----------|----------|----------|----------|--------|
| Q1 2023 | 1,200 | - | $450K | - | Product Launch |
| Q2 2023 | 1,450 | +20.8% | $523K | +16.2% | Marketing Campaign |
| Q3 2023 | 1,680 | +15.9% | $612K | +17.0% | Partnership |
| Q4 2023 | 2,100 | +25.0% | $785K | +28.3% | Holiday Season |

#### Table 5: Comparative Analysis
| Feature | Option A | Option B | Option C | Winner |
|---------|----------|----------|----------|--------|
| Cost | $50/mo | $75/mo | $100/mo | A |
| Performance | Good | Excellent | Good | B |
| Support | 24/5 | 24/7 | Business hours | B |
| Scalability | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | B |
| **Score** | 7/10 | 9/10 | 6/10 | **B** |

#### Table 6: Correlation Matrix
| Variable | Revenue | Users | Engagement | Retention | Satisfaction |
|----------|---------|-------|------------|-----------|--------------|
| Revenue | 1.00 | 0.82 | 0.67 | 0.75 | 0.58 |
| Users | 0.82 | 1.00 | 0.73 | 0.68 | 0.61 |
| Engagement | 0.67 | 0.73 | 1.00 | 0.85 | 0.79 |
| Retention | 0.75 | 0.68 | 0.85 | 1.00 | 0.81 |
| Satisfaction | 0.58 | 0.61 | 0.79 | 0.81 | 1.00 |

#### Table 7: Risk Assessment
| Risk Category | Probability | Impact | Score | Mitigation | Owner |
|---------------|-------------|--------|-------|------------|-------|
| Data Breach | Low (20%) | Critical | 8 | Encryption, audits | Security Team |
| Market Competition | High (70%) | High | 7 | Differentiation | Product Team |
| Regulatory Change | Medium (40%) | High | 6 | Legal monitoring | Compliance |
| Technical Debt | High (65%) | Medium | 5 | Refactoring | Engineering |

#### Table 8: Geographic Distribution
| Region | Customers | Revenue | Avg. Order | Growth YoY | Market Share |
|--------|-----------|---------|------------|------------|--------------|
| North America | 450 | $7.2M | $16,000 | +25% | 38% |
| Europe | 320 | $5.1M | $15,938 | +18% | 27% |
| Asia Pacific | 180 | $2.9M | $16,111 | +45% | 15% |
| Latin America | 50 | $0.9M | $18,000 | +60% | 5% |

#### Table 9: Feature Usage
| Feature | Active Users | Usage % | Satisfaction | Priority |
|---------|--------------|---------|--------------|----------|
| Dashboard | 8,500 | 85% | 4.5/5 | High |
| Reports | 7,200 | 72% | 4.2/5 | High |
| Analytics | 6,100 | 61% | 4.7/5 | Medium |
| Integrations | 4,800 | 48% | 4.0/5 | Medium |
| API Access | 2,300 | 23% | 4.8/5 | Low |

#### Table 10: Action Items & Recommendations
| Priority | Action | Owner | Timeline | Est. Impact | Resources |
|----------|--------|-------|----------|-------------|-----------|
| 🔴 Critical | Fix security vulnerability | Security | 1 week | $500K saved | 3 engineers |
| 🔴 Critical | Launch feature X | Product | 2 weeks | +15% revenue | 5 people |
| 🟡 High | Optimize database | Engineering | 1 month | -30% costs | 2 engineers |
| 🟡 High | Marketing campaign | Marketing | 6 weeks | +2000 users | $50K budget |
| 🟢 Medium | Documentation update | Tech Writing | 2 months | Better support | 1 writer |

### Output Structure
```markdown
# Comprehensive Analysis Report

## Executive Summary (500 words)
[Overview of findings]

## Table 1: [Title]
[Table with detailed caption explaining insights]

### Analysis (600 words)
[Detailed narrative explaining table data, trends, implications]

## Table 2: [Title]
[Table with detailed caption]

### Analysis (600 words)
[Detailed narrative]

[... 8 more tables with analysis ...]

## Consolidated Insights (1000 words)
[Cross-table analysis and overall conclusions]

## Recommendations (500 words)
[Action items based on all tables]

## Appendix
### Methodology
[How data was analyzed]

### Data Sources
[References]

### Limitations
[Known constraints]
```

### MANDATORY TRIGGERS
tables, summary tables, data tables, comprehensive summary, statistical analysis, data summary, tabular format, multi-table report, table generation

---

## Skill 8: Interactive Jupyter Notebook Generator

**jupyter-notebook-creator**

### Description
Generate fully functional Jupyter notebooks with executable code, visualizations, markdown explanations, and interactive widgets for data analysis, machine learning, and educational purposes.

### Capabilities
- **Complete Notebooks**: Ready-to-run .ipynb files
- **Code Cells**: Python, R, Julia support
- **Markdown Cells**: Rich documentation with LaTeX
- **Visualizations**: Matplotlib, Seaborn, Plotly, Altair
- **Interactive Widgets**: ipywidgets for dynamic interaction
- **Data Analysis**: Pandas, NumPy, SciPy workflows
- **Machine Learning**: Scikit-learn, TensorFlow, PyTorch examples
- **Best Practices**: PEP 8, documentation, error handling

### Notebook Structure

```json
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Advanced Data Analysis Project\n",
    "**Author**: AI Assistant\n",
    "**Date**: 2024-01-15\n",
    "**Purpose**: Comprehensive analysis of dataset X\n",
    "\n",
    "## Table of Contents\n",
    "1. [Environment Setup](#setup)\n",
    "2. [Data Loading](#loading)\n",
    "3. [Exploratory Analysis](#eda)\n",
    "4. [Feature Engineering](#features)\n",
    "5. [Modeling](#modeling)\n",
    "6. [Results](#results)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Environment Setup\n",
    "import pandas as pd\n",
    "import numpy as np\n",
    "import matplotlib.pyplot as plt\n",
    "import seaborn as sns\n",
    "from sklearn.model_selection import train_test_split\n",
    "from sklearn.preprocessing import StandardScaler\n",
    "\n",
    "# Configuration\n",
    "plt.style.use('seaborn-v0_8')\n",
    "sns.set_palette('husl')\n",
    "%matplotlib inline\n",
    "\n",
    "# Suppress warnings\n",
    "import warnings\n",
    "warnings.filterwarnings('ignore')\n",
    "\n",
    "print('✅ Environment ready')"
   ]
  }
 ]
}
```

### Key Features

#### Interactive Widgets
```python
import ipywidgets as widgets
from IPython.display import display

# Slider for parameter tuning
learning_rate = widgets.FloatSlider(
    value=0.01,
    min=0.001,
    max=0.1,
    step=0.001,
    description='Learning Rate:',
    continuous_update=False
)

# Dropdown for model selection
model_selector = widgets.Dropdown(
    options=['Linear Regression', 'Random Forest', 'XGBoost'],
    description='Model:',
)

# Button to run analysis
run_button = widgets.Button(
    description='Run Analysis',
    button_style='success',
    icon='play'
)

def on_run_clicked(b):
    # Analysis code here
    print(f'Running {model_selector.value} with LR={learning_rate.value}')

run_button.on_click(on_run_clicked)

display(model_selector, learning_rate, run_button)
```

#### Advanced Visualizations
```python
import plotly.express as px
import plotly.graph_objects as go

# Interactive scatter plot
fig = px.scatter(
    df, 
    x='feature_1', 
    y='feature_2',
    color='category',
    size='value',
    hover_data=['name', 'date'],
    title='Interactive Feature Analysis'
)
fig.show()

# 3D surface plot
fig = go.Figure(data=[go.Surface(z=Z, x=X, y=Y)])
fig.update_layout(
    title='3D Model Visualization',
    scene=dict(
        xaxis_title='X Axis',
        yaxis_title='Y Axis',
        zaxis_title='Z Axis'
    )
)
fig.show()
```

### Template Categories

1. **Data Analysis Template**: EDA, statistics, visualization
2. **Machine Learning Template**: Full ML pipeline with model comparison
3. **Time Series Template**: Forecasting with ARIMA, Prophet
4. **Deep Learning Template**: Neural network training with TensorFlow
5. **Statistical Analysis Template**: Hypothesis testing, distributions
6. **Web Scraping Template**: BeautifulSoup, Selenium workflows
7. **API Integration Template**: REST API interaction examples
8. **Educational Template**: Step-by-step learning materials

### MANDATORY TRIGGERS
jupyter, notebook, ipynb, interactive notebook, python notebook, data analysis notebook, ml notebook, code notebook, executable code

---

## Skill 9: API Integration Testing Suite Generator

**api-test-suite-generator**

### Description
Generate comprehensive API testing suites with unit tests, integration tests, load tests, and security tests using pytest, unittest, and specialized testing frameworks.

### Capabilities
- **Test Structure**: Pytest-based test organization
- **API Testing**: REST, GraphQL, WebSocket tests
- **Mock Data**: Fixtures and factories
- **Authentication Tests**: JWT, OAuth, API keys
- **Load Testing**: Locust and Artillery configurations
- **Security Testing**: OWASP API Security Top 10
- **CI/CD Integration**: GitHub Actions, GitLab CI
- **Coverage Reports**: HTML and XML coverage reports
- **Documentation**: Test case documentation

### Test Suite Structure

```python
# tests/conftest.py
import pytest
from fastapi.testclient import TestClient
from sqlalchemy import create_engine
from sqlalchemy.orm import sessionmaker
from app.main import app
from app.database import Base, get_db

# Test database
SQLALCHEMY_TEST_DATABASE_URL = "sqlite:///./test.db"
engine = create_engine(SQLALCHEMY_TEST_DATABASE_URL)
TestingSessionLocal = sessionmaker(bind=engine)

@pytest.fixture(scope="function")
def db_session():
    """Create test database session"""
    Base.metadata.create_all(bind=engine)
    db = TestingSessionLocal()
    try:
        yield db
    finally:
        db.close()
        Base.metadata.drop_all(bind=engine)

@pytest.fixture(scope="function")
def client(db_session):
    """Create test client"""
    def override_get_db():
        try:
            yield db_session
        finally:
            db_session.close()
    
    app.dependency_overrides[get_db] = override_get_db
    return TestClient(app)

@pytest.fixture
def auth_headers(client):
    """Get authentication headers"""
    response = client.post("/api/v1/auth/login", json={
        "email": "test@example.com",
        "password": "testpass123"
    })
    token = response.json()["access_token"]
    return {"Authorization": f"Bearer {token}"}

@pytest.fixture
def sample_user_data():
    """Sample user data for testing"""
    return {
        "email": "newuser@example.com",
        "password": "SecurePass123!",
        "full_name": "Test User"
    }
```

### Unit Tests
```python
# tests/test_auth.py
import pytest
from app.auth import hash_password, verify_password, create_jwt_token

class TestPasswordHashing:
    """Test password hashing functionality"""
    
    def test_hash_password(self):
        """Test password hashing"""
        password = "SecurePassword123!"
        hashed = hash_password(password)
        
        assert hashed != password
        assert len(hashed) > 50
        assert hashed.startswith("$2b$")
    
    def test_verify_correct_password(self):
        """Test password verification with correct password"""
        password = "SecurePassword123!"
        hashed = hash_password(password)
        
        assert verify_password(password, hashed) is True
    
    def test_verify_incorrect_password(self):
        """Test password verification with incorrect password"""
        password = "SecurePassword123!"
        hashed = hash_password(password)
        
        assert verify_password("WrongPassword", hashed) is False

class TestJWTToken:
    """Test JWT token functionality"""
    
    def test_create_token(self):
        """Test JWT token creation"""
        user_id = "user-123"
        token = create_jwt_token(user_id)
        
        assert isinstance(token, str)
        assert len(token) > 100
        assert token.count('.') == 2  # JWT has 3 parts
    
    def test_token_expiration(self):
        """Test token expiration"""
        user_id = "user-123"
        token = create_jwt_token(user_id, expires_in=1)
        
        import time
        time.sleep(2)
        
        from app.auth import decode_jwt_token
        with pytest.raises(Exception):
            decode_jwt_token(token)
```

### Integration Tests
```python
# tests/test_api_integration.py
import pytest

class TestUserRegistration:
    """Test user registration flow"""
    
    def test_register_new_user(self, client, sample_user_data):
        """Test successful user registration"""
        response = client.post(
            "/api/v1/auth/register",
            json=sample_user_data
        )
        
        assert response.status_code == 201
        data = response.json()
        assert data["email"] == sample_user_data["email"]
        assert "user_id" in data
        assert "password" not in data
    
    def test_register_duplicate_email(self, client, sample_user_data):
        """Test registration with existing email"""
        # First registration
        client.post("/api/v1/auth/register", json=sample_user_data)
        
        # Second registration with same email
        response = client.post(
            "/api/v1/auth/register",
            json=sample_user_data
        )
        
        assert response.status_code == 409
        assert "already registered" in response.json()["detail"].lower()
    
    def test_register_invalid_email(self, client, sample_user_data):
        """Test registration with invalid email"""
        sample_user_data["email"] = "invalid-email"
        response = client.post(
            "/api/v1/auth/register",
            json=sample_user_data
        )
        
        assert response.status_code == 422

class TestDocumentProcessing:
    """Test document processing endpoints"""
    
    def test_upload_document(self, client, auth_headers, tmp_path):
        """Test document upload"""
        # Create test file
        test_file = tmp_path / "test.txt"
        test_file.write_text("Test document content")
        
        with open(test_file, "rb") as f:
            response = client.post(
                "/api/v1/documents/upload",
                files={"file": ("test.txt", f, "text/plain")},
                headers=auth_headers
            )
        
        assert response.status_code == 200
        data = response.json()
        assert "document_id" in data
        assert data["status"] == "uploaded"
    
    def test_analyze_document(self, client, auth_headers):
        """Test document analysis"""
        # Upload document first
        document_id = "doc-123"
        
        response = client.post(
            f"/api/v1/documents/{document_id}/analyze",
            json={"summary_length": 5000},
            headers=auth_headers
        )
        
        assert response.status_code == 200
        data = response.json()
        assert "summary" in data
        assert len(data["summary"]) > 0
```

### Load Tests
```python
# tests/locustfile.py
from locust import HttpUser, task, between

class APIUser(HttpUser):
    """Simulate API user behavior"""
    wait_time = between(1, 3)
    
    def on_start(self):
        """Login before starting tasks"""
        response = self.client.post("/api/v1/auth/login", json={
            "email": "test@example.com",
            "password": "testpass123"
        })
        self.token = response.json()["access_token"]
        self.headers = {"Authorization": f"Bearer {self.token}"}
    
    @task(3)
    def get_documents(self):
        """Get user documents"""
        self.client.get(
            "/api/v1/documents",
            headers=self.headers
        )
    
    @task(1)
    def upload_document(self):
        """Upload new document"""
        files = {"file": ("test.txt", b"Test content", "text/plain")}
        self.client.post(
            "/api/v1/documents/upload",
            files=files,
            headers=self.headers
        )
    
    @task(2)
    def analyze_document(self):
        """Analyze document"""
        self.client.post(
            "/api/v1/documents/doc-123/analyze",
            json={"summary_length": 1000},
            headers=self.headers
        )
```

### Security Tests
```python
# tests/test_security.py
import pytest

class TestAuthenticationSecurity:
    """Test authentication security"""
    
    def test_access_without_token(self, client):
        """Test accessing protected endpoint without token"""
        response = client.get("/api/v1/documents")
        assert response.status_code == 401
    
    def test_access_with_invalid_token(self, client):
        """Test accessing with invalid token"""
        headers = {"Authorization": "Bearer invalid-token"}
        response = client.get("/api/v1/documents", headers=headers)
        assert response.status_code == 401
    
    def test_sql_injection_attempt(self, client):
        """Test SQL injection protection"""
        response = client.post("/api/v1/auth/login", json={
            "email": "test@example.com' OR '1'='1",
            "password": "password"
        })
        assert response.status_code in [401, 422]
    
    def test_xss_attempt(self, client, auth_headers):
        """Test XSS protection"""
        response = client.post(
            "/api/v1/documents/upload",
            files={"file": ("test.txt", b"<script>alert('xss')</script>")},
            headers=auth_headers
        )
        
        # Content should be sanitized
        doc_id = response.json()["document_id"]
        get_response = client.get(
            f"/api/v1/documents/{doc_id}",
            headers=auth_headers
        )
        assert "<script>" not in get_response.text
```

### MANDATORY TRIGGERS
api testing, test suite, pytest, unit tests, integration tests, load testing, security testing, api tests, test automation, testing framework

---

## Skill 10: Knowledge Graph & Ontology Builder

**knowledge-graph-builder**

### Description
Create comprehensive knowledge graphs and ontologies from unstructured data, visualizing relationships between entities, concepts, and providing semantic network analysis with export to multiple formats.

### Capabilities
- **Entity Extraction**: NLP-based entity recognition
- **Relationship Mapping**: Identify connections between entities
- **Ontology Creation**: Hierarchical concept organization
- **Graph Visualization**: Interactive network diagrams
- **Semantic Analysis**: Concept similarity and clustering
- **Export Formats**: JSON, RDF, OWL, GraphML, Cypher
- **Query Interface**: SPARQL and Cypher query support
- **Integration**: Neo4j, RDF stores, graph databases

### Knowledge Graph Structure

```python
# knowledge_graph.py
from dataclasses import dataclass
from typing import List, Dict, Set
import networkx as nx
import matplotlib.pyplot as plt
from pyvis.network import Network

@dataclass
class Entity:
    """Knowledge graph entity"""
    id: str
    label: str
    type: str
    properties: Dict[str, any]
    aliases: List[str] = None
    
@dataclass
class Relationship:
    """Relationship between entities"""
    source: str
    target: str
    type: str
    properties: Dict[str, any]
    confidence: float

class KnowledgeGraph:
    """Knowledge graph builder and analyzer"""
    
    def __init__(self):
        self.graph = nx.DiGraph()
        self.entities: Dict[str, Entity] = {}
        self.relationships: List[Relationship] = []
    
    def add_entity(self, entity: Entity):
        """Add entity to knowledge graph"""
        self.entities[entity.id] = entity
        self.graph.add_node(
            entity.id,
            label=entity.label,
            type=entity.type,
            **entity.properties
        )
    
    def add_relationship(self, relationship: Relationship):
        """Add relationship to knowledge graph"""
        self.relationships.append(relationship)
        self.graph.add_edge(
            relationship.source,
            relationship.target,
            type=relationship.type,
            confidence=relationship.confidence,
            **relationship.properties
        )
    
    def find_paths(self, source: str, target: str) -> List[List[str]]:
        """Find all paths between two entities"""
        try:
            paths = list(nx.all_simple_paths(
                self.graph, source, target, cutoff=5
            ))
            return paths
        except nx.NetworkXNoPath:
            return []
    
    def get_neighbors(self, entity_id: str, depth: int = 1) -> Set[str]:
        """Get neighboring entities up to specified depth"""
        neighbors = set()
        current_level = {entity_id}
        
        for _ in range(depth):
            next_level = set()
            for node in current_level:
                next_level.update(self.graph.neighbors(node))
            neighbors.update(next_level)
            current_level = next_level
        
        return neighbors
    
    def calculate_centrality(self) -> Dict[str, float]:
        """Calculate PageRank centrality"""
        return nx.pagerank(self.graph)
    
    def detect_communities(self) -> List[Set[str]]:
        """Detect communities using Louvain algorithm"""
        undirected = self.graph.to_undirected()
        import community as community_louvain
        partition = community_louvain.best_partition(undirected)
        
        communities = {}
        for node, comm_id in partition.items():
            if comm_id not in communities:
                communities[comm_id] = set()
            communities[comm_id].add(node)
        
        return list(communities.values())
    
    def visualize(self, output_file: str = "knowledge_graph.html"):
        """Create interactive visualization"""
        net = Network(
            height="800px",
            width="100%",
            directed=True,
            notebook=False
        )
        
        # Add nodes
        for entity_id, entity in self.entities.items():
            net.add_node(
                entity_id,
                label=entity.label,
                title=f"{entity.type}: {entity.label}",
                color=self._get_color_by_type(entity.type)
            )
        
        # Add edges
        for rel in self.relationships:
            net.add_edge(
                rel.source,
                rel.target,
                title=rel.type,
                value=rel.confidence
            )
        
        net.save_graph(output_file)
        print(f"✅ Visualization saved to {output_file}")
    
    def export_to_cypher(self) -> str:
        """Export to Neo4j Cypher format"""
        cypher_queries = []
        
        # Create entities
        for entity in self.entities.values():
            props = ", ".join([
                f"{k}: '{v}'" for k, v in entity.properties.items()
            ])
            query = f"CREATE (:{entity.type} {{id: '{entity.id}', label: '{entity.label}', {props}}})"
            cypher_queries.append(query)
        
        # Create relationships
        for rel in self.relationships:
            query = f"""
            MATCH (a {{id: '{rel.source}'}}), (b {{id: '{rel.target}'}})
            CREATE (a)-[:{rel.type} {{confidence: {rel.confidence}}}]->(b)
            """
            cypher_queries.append(query)
        
        return "\n".join(cypher_queries)
    
    def export_to_rdf(self) -> str:
        """Export to RDF/Turtle format"""
        from rdflib import Graph, Namespace, Literal, URIRef
        from rdflib.namespace import RDF, RDFS
        
        g = Graph()
        ns = Namespace("http://example.org/kg/")
        
        # Add entities
        for entity in self.entities.values():
            entity_uri = URIRef(ns[entity.id])
            g.add((entity_uri, RDF.type, URIRef(ns[entity.type])))
            g.add((entity_uri, RDFS.label, Literal(entity.label)))
            
            for key, value in entity.properties.items():
                g.add((entity_uri, URIRef(ns[key]), Literal(value)))
        
        # Add relationships
        for rel in self.relationships:
            g.add((
                URIRef(ns[rel.source]),
                URIRef(ns[rel.type]),
                URIRef(ns[rel.target])
            ))
        
        return g.serialize(format='turtle')
    
    @staticmethod
    def _get_color_by_type(entity_type: str) -> str:
        """Get color based on entity type"""
        colors = {
            "Person": "#FF6B6B",
            "Organization": "#4ECDC4",
            "Location": "#45B7D1",
            "Concept": "#FFA07A",
            "Event": "#98D8C8",
            "Product": "#F7DC6F"
        }
        return colors.get(entity_type, "#95A5A6")
```

### Example Usage

```python
# Build knowledge graph from document
from knowledge_graph import KnowledgeGraph, Entity, Relationship

kg = KnowledgeGraph()

# Add entities
kg.add_entity(Entity(
    id="person_1",
    label="Albert Einstein",
    type="Person",
    properties={
        "birth_year": 1879,
        "nationality": "German",
        "field": "Physics"
    },
    aliases=["Einstein"]
))

kg.add_entity(Entity(
    id="concept_1",
    label="Theory of Relativity",
    type="Concept",
    properties={
        "year_published": 1905,
        "field": "Physics"
    }
))

kg.add_entity(Entity(
    id="org_1",
    label="Princeton University",
    type="Organization",
    properties={
        "founded": 1746,
        "type": "University"
    }
))

# Add relationships
kg.add_relationship(Relationship(
    source="person_1",
    target="concept_1",
    type="DEVELOPED",
    properties={"year": 1905},
    confidence=0.95
))

kg.add_relationship(Relationship(
    source="person_1",
    target="org_1",
    type="WORKED_AT",
    properties={"start_year": 1933, "end_year": 1955},
    confidence=0.98
))

# Analyze
centrality = kg.calculate_centrality()
communities = kg.detect_communities()

# Visualize
kg.visualize("einstein_knowledge_graph.html")

# Export
cypher_script = kg.export_to_cypher()
rdf_data = kg.export_to_rdf()

print("Knowledge Graph Analysis Complete!")
print(f"Entities: {len(kg.entities)}")
print(f"Relationships: {len(kg.relationships)}")
print(f"Communities: {len(communities)}")
```

### Output Formats

#### JSON Export
```json
{
  "entities": [
    {
      "id": "person_1",
      "label": "Albert Einstein",
      "type": "Person",
      "properties": {
        "birth_year": 1879,
        "nationality": "German",
        "field": "Physics"
      },
      "centrality": 0.45
    }
  ],
  "relationships": [
    {
      "source": "person_1",
      "target": "concept_1",
      "type": "DEVELOPED",
      "confidence": 0.95
    }
  ],
  "statistics": {
    "total_entities": 50,
    "total_relationships": 120,
    "avg_degree": 4.8,
    "density": 0.12
  }
}
```

### MANDATORY TRIGGERS
knowledge graph, ontology, semantic network, entity relationships, graph database, network analysis, knowledge base, graph visualization, semantic web, RDF, Neo4j

---

## Summary Table

| Skill # | Name | Primary Function | Output Format | Word Count | Triggers |
|---------|------|------------------|---------------|------------|----------|
| 1 | PDF to Markdown | Convert PDF to MD with summary | Markdown | 4000-5000 | pdf, pdf file, convert pdf |
| 2 | Document Organizer | Organize docs with coral keywords | Markdown | 4000-5000 | docx, organize, keywords |
| 3 | Entity Analyzer | Extract 20 entities with context | Markdown | 4000-5000 | entities, NER, extraction |
| 4 | Streamlit Builder | Multi-API app generation | Python/YAML | N/A | streamlit, api, deployment |
| 5 | UI Designer | Transform UI with themes/styles | Python/CSS | N/A | ui design, themes, styles |
| 6 | Tech Spec Generator | Comprehensive specifications | Markdown | 6000-7000 | tech specs, SRS, architecture |
| 7 | Table Summary | 10-table comprehensive summary | Markdown | 6000-7000 | tables, data summary |
| 8 | Jupyter Generator | Interactive notebook creation | .ipynb | N/A | jupyter, notebook, ipynb |
| 9 | Test Suite Generator | API testing automation | Python | N/A | api testing, pytest, tests |
| 10 | Knowledge Graph | Build semantic networks | Multiple | N/A | knowledge graph, ontology |

---

**Document Version**: 1.0  
**Last Updated**: 2024-01-15  
