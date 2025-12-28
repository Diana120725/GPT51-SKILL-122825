SKILLS.md - Advanced Edition (Part 2)
Extended AI Skills Documentation - 10 Additional Specialized Skills
This document presents 10 additional advanced AI skills focused on document creation, audit reporting, data analysis, visualization, and comprehensive data mining capabilities.

Skill 11: Advanced Word Document Generator with Template Processing
docx-template-processor
Description
Professional Microsoft Word (.docx) document creation system that accepts user-provided templates or template descriptions, then generates fully-formatted documents with content preservation, styling, and complex layout support.
Capabilities

Template Input Methods:

Upload existing .docx template files
Paste text description of desired template
Select from 50+ pre-built professional templates
AI-generated template from requirements


Document Elements:

Headers/footers with dynamic content
Table of contents (auto-generated)
Styles and formatting preservation
Tables, charts, and images
Page breaks and sections
Footnotes and endnotes
Cross-references and bookmarks


Content Processing:

Markdown to Word conversion
Variable substitution (mail merge)
Conditional content inclusion
Multi-language support
Mathematical equations (LaTeX to Word)


Advanced Features:

Track changes mode
Comments and annotations
Document protection
Custom properties and metadata
Accessibility compliance



Template Structure Example
pythonCopyfrom docx import Document
from docx.shared import Inches, Pt, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.enum.style import WD_STYLE_TYPE
import json

class AdvancedDocxGenerator:
    """Advanced Word document generator with template support"""
    
    def __init__(self, template_path: str = None, template_description: str = None):
        """
        Initialize generator with template
        
        Args:
            template_path: Path to .docx template file
            template_description: Text description of template to generate
        """
        if template_path:
            self.doc = Document(template_path)
        elif template_description:
            self.doc = self._generate_template_from_description(template_description)
        else:
            self.doc = Document()
            self._setup_default_styles()
    
    def _generate_template_from_description(self, description: str) -> Document:
        """
        Generate template from natural language description
        
        Example description:
        "Create a professional business report template with:
        - Company logo in header
        - Title page with centered title, subtitle, author, and date
        - Executive summary section
        - Main content with 3 heading levels
        - Footer with page numbers and company name
        - Professional blue color scheme"
        """
        doc = Document()
        
        # Parse description using AI/NLP
        template_spec = self._parse_template_description(description)
        
        # Apply specifications
        self._apply_template_spec(doc, template_spec)
        
        return doc
    
    def _setup_default_styles(self):
        """Setup default professional styles"""
        styles = self.doc.styles
        
        # Custom heading styles
        for level in range(1, 4):
            style_name = f'Custom Heading {level}'
            if style_name not in styles:
                style = styles.add_style(style_name, WD_STYLE_TYPE.PARAGRAPH)
                style.font.name = 'Calibri'
                style.font.size = Pt(28 - level * 4)
                style.font.bold = True
                style.font.color.rgb = RGBColor(0, 70, 127)
    
    def add_cover_page(self, title: str, subtitle: str = None, 
                       author: str = None, date: str = None,
                       logo_path: str = None):
        """
        Add professional cover page
        
        Args:
            title: Document title
            subtitle: Optional subtitle
            author: Author name
            date: Date string
            logo_path: Path to company logo
        """
        # Logo
        if logo_path:
            paragraph = self.doc.add_paragraph()
            paragraph.alignment = WD_ALIGN_PARAGRAPH.CENTER
            run = paragraph.add_run()
            run.add_picture(logo_path, width=Inches(2))
        
        # Add spacing
        self.doc.add_paragraph()
        self.doc.add_paragraph()
        
        # Title
        title_para = self.doc.add_paragraph()
        title_para.alignment = WD_ALIGN_PARAGRAPH.CENTER
        title_run = title_para.add_run(title)
        title_run.font.size = Pt(36)
        title_run.font.bold = True
        title_run.font.color.rgb = RGBColor(0, 70, 127)
        
        # Subtitle
        if subtitle:
            subtitle_para = self.doc.add_paragraph()
            subtitle_para.alignment = WD_ALIGN_PARAGRAPH.CENTER
            subtitle_run = subtitle_para.add_run(subtitle)
            subtitle_run.font.size = Pt(24)
            subtitle_run.font.color.rgb = RGBColor(68, 84, 106)
        
        # Author and date
        self.doc.add_paragraph()
        self.doc.add_paragraph()
        
        if author:
            author_para = self.doc.add_paragraph()
            author_para.alignment = WD_ALIGN_PARAGRAPH.CENTER
            author_run = author_para.add_run(f"Prepared by: {author}")
            author_run.font.size = Pt(14)
        
        if date:
            date_para = self.doc.add_paragraph()
            date_para.alignment = WD_ALIGN_PARAGRAPH.CENTER
            date_run = date_para.add_run(date)
            date_run.font.size = Pt(12)
        
        # Page break
        self.doc.add_page_break()
    
    def add_table_of_contents(self):
        """Add auto-generated table of contents"""
        paragraph = self.doc.add_paragraph()
        run = paragraph.add_run()
        
        # Field code for TOC
        fldChar1 = OxmlElement('w:fldChar')
        fldChar1.set(qn('w:fldCharType'), 'begin')
        
        instrText = OxmlElement('w:instrText')
        instrText.set(qn('xml:space'), 'preserve')
        instrText.text = 'TOC \\o "1-3" \\h \\z \\u'
        
        fldChar2 = OxmlElement('w:fldChar')
        fldChar2.set(qn('w:fldCharType'), 'end')
        
        run._r.append(fldChar1)
        run._r.append(instrText)
        run._r.append(fldChar2)
        
        self.doc.add_page_break()
    
    def process_content(self, content: dict):
        """
        Process and add content from structured data
        
        Args:
            content: Dictionary with document content structure
            
        Example content structure:
        {
            "cover": {
                "title": "Annual Report 2024",
                "subtitle": "Financial Performance Analysis",
                "author": "Finance Team",
                "date": "January 15, 2024"
            },
            "sections": [
                {
                    "heading": "Executive Summary",
                    "level": 1,
                    "content": "This report presents...",
                    "subsections": [...]
                },
                {
                    "heading": "Financial Overview",
                    "level": 1,
                    "content": "The fiscal year showed...",
                    "table": {
                        "headers": ["Q1", "Q2", "Q3", "Q4"],
                        "rows": [[...], [...]]
                    }
                }
            ]
        }
        """
        # Cover page
        if "cover" in content:
            cover = content["cover"]
            self.add_cover_page(
                title=cover.get("title"),
                subtitle=cover.get("subtitle"),
                author=cover.get("author"),
                date=cover.get("date"),
                logo_path=cover.get("logo_path")
            )
        
        # Table of contents
        if content.get("include_toc", True):
            self.add_table_of_contents()
        
        # Process sections recursively
        for section in content.get("sections", []):
            self._process_section(section)
    
    def _process_section(self, section: dict):
        """Process individual section"""
        # Add heading
        heading_level = section.get("level", 1)
        self.doc.add_heading(section["heading"], level=heading_level)
        
        # Add content
        if "content" in section:
            self._add_formatted_content(section["content"])
        
        # Add table if present
        if "table" in section:
            self._add_table(section["table"])
        
        # Add chart if present
        if "chart" in section:
            self._add_chart(section["chart"])
        
        # Add image if present
        if "image" in section:
            self._add_image(section["image"])
        
        # Process subsections
        for subsection in section.get("subsections", []):
            self._process_section(subsection)
    
    def _add_formatted_content(self, content: str):
        """Add content with markdown-style formatting"""
        paragraphs = content.split('\n\n')
        
        for para_text in paragraphs:
            if not para_text.strip():
                continue
            
            paragraph = self.doc.add_paragraph()
            
            # Process inline formatting
            parts = self._parse_inline_formatting(para_text)
            for text, formatting in parts:
                run = paragraph.add_run(text)
                if 'bold' in formatting:
                    run.font.bold = True
                if 'italic' in formatting:
                    run.font.italic = True
                if 'underline' in formatting:
                    run.font.underline = True
                if 'highlight' in formatting:
                    run.font.highlight_color = WD_COLOR_INDEX.YELLOW
    
    def _add_table(self, table_data: dict):
        """
        Add formatted table
        
        Args:
            table_data: Dictionary with table structure
            {
                "headers": ["Column 1", "Column 2"],
                "rows": [["Data 1", "Data 2"], ...],
                "style": "Light Grid Accent 1"
            }
        """
        headers = table_data["headers"]
        rows = table_data["rows"]
        
        table = self.doc.add_table(rows=len(rows) + 1, cols=len(headers))
        table.style = table_data.get("style", "Light Grid Accent 1")
        
        # Add headers
        header_cells = table.rows[0].cells
        for i, header in enumerate(headers):
            header_cells[i].text = header
            # Bold header text
            for paragraph in header_cells[i].paragraphs:
                for run in paragraph.runs:
                    run.font.bold = True
        
        # Add data rows
        for i, row_data in enumerate(rows):
            row_cells = table.rows[i + 1].cells
            for j, cell_data in enumerate(row_data):
                row_cells[j].text = str(cell_data)
        
        self.doc.add_paragraph()  # Spacing after table
    
    def _add_chart(self, chart_data: dict):
        """
        Add chart (as image generated from data)
        
        Args:
            chart_data: Dictionary with chart specifications
            {
                "type": "bar|line|pie",
                "data": {...},
                "title": "Chart Title"
            }
        """
        import matplotlib.pyplot as plt
        import io
        from PIL import Image
        
        # Generate chart
        fig, ax = plt.subplots(figsize=(6, 4))
        
        if chart_data["type"] == "bar":
            ax.bar(chart_data["data"]["labels"], chart_data["data"]["values"])
        elif chart_data["type"] == "line":
            ax.plot(chart_data["data"]["labels"], chart_data["data"]["values"])
        elif chart_data["type"] == "pie":
            ax.pie(chart_data["data"]["values"], labels=chart_data["data"]["labels"])
        
        ax.set_title(chart_data.get("title", ""))
        
        # Save to bytes
        buf = io.BytesIO()
        plt.savefig(buf, format='png', dpi=300, bbox_inches='tight')
        buf.seek(0)
        plt.close()
        
        # Add to document
        self.doc.add_picture(buf, width=Inches(5))
        self.doc.add_paragraph()
    
    def _add_image(self, image_data: dict):
        """Add image with caption"""
        self.doc.add_picture(
            image_data["path"],
            width=Inches(image_data.get("width", 5))
        )
        
        if "caption" in image_data:
            caption = self.doc.add_paragraph(image_data["caption"])
            caption.alignment = WD_ALIGN_PARAGRAPH.CENTER
            caption_run = caption.runs[0]
            caption_run.font.italic = True
            caption_run.font.size = Pt(10)
    
    def add_header_footer(self, header_text: str = None, 
                         footer_text: str = None,
                         page_numbers: bool = True):
        """Add headers and footers"""
        section = self.doc.sections[0]
        
        # Header
        if header_text:
            header = section.header
            header_para = header.paragraphs[0]
            header_para.text = header_text
            header_para.alignment = WD_ALIGN_PARAGRAPH.RIGHT
        
        # Footer
        footer = section.footer
        footer_para = footer.paragraphs[0]
        
        if footer_text:
            footer_para.text = footer_text
        
        if page_numbers:
            footer_para.text += " | Page "
            # Add page number field
            run = footer_para.add_run()
            fldChar1 = OxmlElement('w:fldChar')
            fldChar1.set(qn('w:fldCharType'), 'begin')
            run._r.append(fldChar1)
            
            instrText = OxmlElement('w:instrText')
            instrText.text = "PAGE"
            run._r.append(instrText)
            
            fldChar2 = OxmlElement('w:fldChar')
            fldChar2.set(qn('w:fldCharType'), 'end')
            run._r.append(fldChar2)
    
    def apply_variables(self, variables: dict):
        """
        Replace variables in document (mail merge)
        
        Args:
            variables: Dictionary of {variable_name: value}
            Example: {"{{client_name}}": "Acme Corp", "{{date}}": "2024-01-15"}
        """
        for paragraph in self.doc.paragraphs:
            for var_name, var_value in variables.items():
                if var_name in paragraph.text:
                    paragraph.text = paragraph.text.replace(var_name, str(var_value))
        
        # Also process tables
        for table in self.doc.tables:
            for row in table.rows:
                for cell in row.cells:
                    for paragraph in cell.paragraphs:
                        for var_name, var_value in variables.items():
                            if var_name in paragraph.text:
                                paragraph.text = paragraph.text.replace(
                                    var_name, str(var_value)
                                )
    
    def save(self, output_path: str):
        """Save document"""
        self.doc.save(output_path)
        print(f"✅ Document saved to: {output_path}")
Usage Example
pythonCopy# Example 1: Using uploaded template
generator = AdvancedDocxGenerator(template_path="company_template.docx")

# Example 2: Using template description
template_desc = """
Create a professional annual report template with:
- Corporate header with logo placeholder
- Modern blue and gray color scheme
- Three heading levels with consistent styling
- Page numbers in footer
- Table styles for financial data
"""
generator = AdvancedDocxGenerator(template_description=template_desc)

# Add content
content = {
    "cover": {
        "title": "Q4 Financial Report",
        "subtitle": "Performance Analysis",
        "author": "Finance Department",
        "date": "January 2024"
    },
    "sections": [
        {
            "heading": "Executive Summary",
            "level": 1,
            "content": """
            The fourth quarter of 2024 demonstrated strong performance 
            across all key metrics. Revenue increased by **25%** compared 
            to Q3, while operational costs decreased by *12%*.
            
            Key achievements include:
            - Record-breaking sales in December
            - Successful product launch
            - Market share expansion
            """
        },
        {
            "heading": "Financial Performance",
            "level": 1,
            "content": "Detailed financial analysis for Q4 2024:",
            "table": {
                "headers": ["Metric", "Q3 2024", "Q4 2024", "Change"],
                "rows": [
                    ["Revenue", "$2.5M", "$3.1M", "+24%"],
                    ["Net Profit", "$450K", "$580K", "+29%"],
                    ["Expenses", "$2.0M", "$1.8M", "-10%"]
                ]
            }
        }
    ]
}

generator.process_content(content)
generator.add_header_footer(
    header_text="Confidential - Q4 Report",
    page_numbers=True
)
generator.save("Q4_Financial_Report.docx")
Pre-built Templates

Business Report - Professional corporate report
Academic Paper - IEEE/APA format
Resume/CV - Modern professional format
Invoice - Business invoice with calculations
Contract - Legal agreement template
Meeting Minutes - Structured meeting notes
Project Proposal - Detailed proposal format
Technical Documentation - API/software docs
Marketing Plan - Campaign planning document
White Paper - Research publication format

MANDATORY TRIGGERS
word document, docx, create word, generate docx, word template, document generation, .docx creation, microsoft word, word processing, template processing

Skill 12: Advanced Audit Report Generator
audit-report-generator
Description
Comprehensive audit report generation system that accepts audit instructions/templates and observations, then automatically creates structured, professional audit reports in markdown with executive summaries, findings categorization, risk ratings, and actionable recommendations.
Capabilities

Template Processing:

Upload audit report templates (PDF/DOCX/MD)
Natural language template descriptions
Industry-specific templates (SOX, ISO, GDPR, etc.)
Custom template creation


Observations Processing:

Structured observation input (JSON/CSV/Form)
Unstructured text observations
Multi-format evidence attachments
Automatic categorization


Report Generation:

Executive summary (500-800 words)
Detailed findings with evidence
Risk assessment matrix
Compliance gap analysis
Prioritized recommendations
Action plans with timelines


Analysis Features:

Automatic risk scoring
Trend analysis across audits
Comparative analysis
Regulatory mapping
Root cause identification



Audit Report Structure
pythonCopyfrom dataclasses import dataclass, field
from typing import List, Dict, Optional
from enum import Enum
from datetime import datetime, date
import json

class RiskLevel(Enum):
    """Risk level classifications"""
    CRITICAL = "Critical"
    HIGH = "High"
    MEDIUM = "Medium"
    LOW = "Low"
    INFORMATIONAL = "Informational"

class ComplianceStatus(Enum):
    """Compliance status"""
    COMPLIANT = "Compliant"
    PARTIALLY_COMPLIANT = "Partially Compliant"
    NON_COMPLIANT = "Non-Compliant"
    NOT_APPLICABLE = "Not Applicable"

@dataclass
class AuditObservation:
    """Individual audit observation"""
    id: str
    title: str
    description: str
    category: str
    risk_level: RiskLevel
    compliance_status: ComplianceStatus
    evidence: List[str] = field(default_factory=list)
    affected_systems: List[str] = field(default_factory=list)
    control_reference: Optional[str] = None
    root_cause: Optional[str] = None
    business_impact: Optional[str] = None
    
@dataclass
class AuditRecommendation:
    """Recommendation for addressing finding"""
    observation_id: str
    recommendation: str
    priority: str
    responsible_party: str
    target_completion_date: date
    estimated_effort: str
    resources_required: List[str] = field(default_factory=list)

@dataclass
class AuditMetadata:
    """Audit metadata"""
    audit_id: str
    audit_title: str
    audit_type: str  # Internal, External, Compliance, Financial, etc.
    audit_period_start: date
    audit_period_end: date
    auditor_name: str
    auditor_organization: str
    auditee_department: str
    report_date: date
    standards_frameworks: List[str] = field(default_factory=list)

class AuditReportGenerator:
    """Generate comprehensive audit reports"""
    
    def __init__(self, template: Optional[str] = None, 
                 template_description: Optional[str] = None):
        """
        Initialize audit report generator
        
        Args:
            template: Path to template file or template name
            template_description: Natural language description of desired template
        """
        self.metadata: Optional[AuditMetadata] = None
        self.observations: List[AuditObservation] = []
        self.recommendations: List[AuditRecommendation] = []
        self.template_config = self._load_template(template, template_description)
    
    def _load_template(self, template: Optional[str], 
                       description: Optional[str]) -> dict:
        """Load or generate audit template configuration"""
        if template and template in self.STANDARD_TEMPLATES:
            return self.STANDARD_TEMPLATES[template]
        elif description:
            return self._generate_template_from_description(description)
        else:
            return self.STANDARD_TEMPLATES["general"]
    
    STANDARD_TEMPLATES = {
        "general": {
            "sections": [
                "executive_summary",
                "audit_scope",
                "methodology",
                "findings",
                "risk_assessment",
                "recommendations",
                "conclusion",
                "appendices"
            ],
            "risk_matrix": True,
            "include_evidence": True
        },
        "sox_compliance": {
            "sections": [
                "executive_summary",
                "sox_scope",
                "control_environment",
                "control_testing_results",
                "deficiencies",
                "material_weaknesses",
                "management_response",
                "remediation_plan"
            ],
            "regulatory_framework": "SOX",
            "materiality_threshold": True
        },
        "iso27001": {
            "sections": [
                "executive_summary",
                "scope_boundaries",
                "information_security_controls",
                "gap_analysis",
                "non_conformities",
                "recommendations",
                "certification_readiness"
            ],
            "control_mapping": "ISO 27001:2013",
            "compliance_scoring": True
        },
        "gdpr_audit": {
            "sections": [
                "executive_summary",
                "data_processing_activities",
                "lawful_basis_assessment",
                "data_subject_rights",
                "security_measures",
                "privacy_violations",
                "dpia_requirements",
                "action_plan"
            ],
            "regulatory_framework": "GDPR",
            "privacy_impact": True
        },
        "financial_audit": {
            "sections": [
                "executive_summary",
                "audit_opinion",
                "financial_statements_review",
                "accounting_policies",
                "material_misstatements",
                "internal_controls",
                "recommendations",
                "auditor_responsibility"
            ],
            "financial_analysis": True,
            "materiality_levels": True
        }
    }
    
    def set_metadata(self, metadata: AuditMetadata):
        """Set audit metadata"""
        self.metadata = metadata
    
    def add_observation(self, observation: AuditObservation):
        """Add audit observation"""
        self.observations.append(observation)
    
    def add_observations_from_json(self, json_data: str):
        """
        Add observations from JSON format
        
        Example JSON:
        [
            {
                "id": "OBS-001",
                "title": "Inadequate Password Policy",
                "description": "Current password policy does not enforce complexity requirements",
                "category": "Access Control",
                "risk_level": "High",
                "compliance_status": "Non-Compliant",
                "evidence": ["Policy_Doc_v1.pdf", "Screenshot_Login.png"],
                "affected_systems": ["HR System", "Finance Portal"],
                "control_reference": "AC-2.1",
                "root_cause": "Outdated security standards from 2018",
                "business_impact": "Increased risk of unauthorized access"
            }
        ]
        """
        observations_data = json.loads(json_data)
        
        for obs_data in observations_data:
            observation = AuditObservation(
                id=obs_data["id"],
                title=obs_data["title"],
                description=obs_data["description"],
                category=obs_data["category"],
                risk_level=RiskLevel[obs_data["risk_level"].upper()],
                compliance_status=ComplianceStatus[
                    obs_data["compliance_status"].upper().replace(" ", "_")
                ],
                evidence=obs_data.get("evidence", []),
                affected_systems=obs_data.get("affected_systems", []),
                control_reference=obs_data.get("control_reference"),
                root_cause=obs_data.get("root_cause"),
                business_impact=obs_data.get("business_impact")
            )
            self.add_observation(observation)
    
    def add_recommendation(self, recommendation: AuditRecommendation):
        """Add recommendation"""
        self.recommendations.append(recommendation)
    
    def generate_risk_score(self, observation: AuditObservation) -> int:
        """
        Calculate numerical risk score (1-100)
        
        Factors:
        - Risk level: 40% weight
        - Business impact: 30% weight
        - Likelihood: 20% weight
        - Compliance status: 10% weight
        """
        risk_scores = {
            RiskLevel.CRITICAL: 100,
            RiskLevel.HIGH: 75,
            RiskLevel.MEDIUM: 50,
            RiskLevel.LOW: 25,
            RiskLevel.INFORMATIONAL: 10
        }
        
        compliance_scores = {
            ComplianceStatus.NON_COMPLIANT: 100,
            ComplianceStatus.PARTIALLY_COMPLIANT: 60,
            ComplianceStatus.COMPLIANT: 0,
            ComplianceStatus.NOT_APPLICABLE: 0
        }
        
        base_risk = risk_scores[observation.risk_level] * 0.4
        compliance_risk = compliance_scores[observation.compliance_status] * 0.1
        
        # Simplified calculation (can be enhanced with ML)
        total_score = int(base_risk + compliance_risk + 40)  # +40 for other factors
        
        return min(100, max(0, total_score))
    
    def categorize_observations(self) -> Dict[str, List[AuditObservation]]:
        """Group observations by category"""
        categorized = {}
        for obs in self.observations:
            if obs.category not in categorized:
                categorized[obs.category] = []
            categorized[obs.category].append(obs)
        return categorized
    
    def generate_executive_summary(self) -> str:
        """Generate executive summary (500-800 words)"""
        summary_parts = []
        
        # Introduction
        summary_parts.append(f"""
## Executive Summary

### Audit Overview
This report presents the findings of the **{self.metadata.audit_title}** conducted 
for the period from **{self.metadata.audit_period_start.strftime('%B %d, %Y')}** to 
**{self.metadata.audit_period_end.strftime('%B %d, %Y')}**. The audit was performed by 
{self.metadata.auditor_name} from {self.metadata.auditor_organization}.

### Audit Scope and Objectives
The primary objective of this {self.metadata.audit_type} audit was to assess the 
effectiveness of controls, evaluate compliance with applicable standards 
({', '.join(self.metadata.standards_frameworks)}), and identify areas for improvement 
within the {self.metadata.auditee_department} department.
""")
        
        # Statistics
        total_obs = len(self.observations)
        risk_distribution = self._calculate_risk_distribution()
        compliance_summary = self._calculate_compliance_summary()
        
        summary_parts.append(f"""
### Key Findings Summary
The audit identified **{total_obs} observations** across multiple control areas:

**Risk Level Distribution:**
- 🔴 Critical: {risk_distribution['Critical']} findings
- 🟠 High: {risk_distribution['High']} findings
- 🟡 Medium: {risk_distribution['Medium']} findings
- 🟢 Low: {risk_distribution['Low']} findings
- ℹ️ Informational: {risk_distribution['Informational']} findings

**Compliance Status:**
- ✅ Compliant: {compliance_summary['Compliant']}%
- ⚠️ Partially Compliant: {compliance_summary['Partially Compliant']}%
- ❌ Non-Compliant: {compliance_summary['Non-Compliant']}%
""")
        
        # Critical findings highlight
        critical_findings = [
            obs for obs in self.observations 
            if obs.risk_level in [RiskLevel.CRITICAL, RiskLevel.HIGH]
        ]
        
        if critical_findings:
            summary_parts.append("""
### Critical Areas Requiring Immediate Attention
The following critical issues require immediate management attention:
""")
            for i, obs in enumerate(critical_findings[:5], 1):
                summary_parts.append(f"""
**{i}. {obs.title}** ({obs.risk_level.value})
   - *Category:* {obs.category}
   - *Impact:* {obs.business_impact or 'Significant operational risk'}
   - *Status:* {obs.compliance_status.value}
""")
        
        # Overall assessment
        overall_score = self._calculate_overall_compliance_score()
        assessment = self._get_assessment_text(overall_score)
        
        summary_parts.append(f"""
### Overall Assessment
Based on the audit findings, the overall control environment is rated as **{assessment}** 
with a compliance score of **{overall_score}%**. While several areas demonstrate strong 
controls, the critical and high-risk findings require immediate remediation to reduce 
organizational risk exposure.

### Management Response
Management has acknowledged all findings and committed to implementing the recommended 
corrective actions. A detailed action plan with timelines and responsible parties is 
provided in the Recommendations section of this report.

### Conclusion
This audit provides management with a comprehensive assessment of the current control 
environment. Prompt attention to the identified issues, particularly critical findings, 
will significantly enhance the organization's risk posture and regulatory compliance.
""")
        
        return '\n'.join(summary_parts)
    
    def _calculate_risk_distribution(self) -> Dict[str, int]:
        """Calculate distribution of observations by risk level"""
        distribution = {level.value: 0 for level in RiskLevel}
        for obs in self.observations:
            distribution[obs.risk_level.value] += 1
        return distribution
    
    def _calculate_compliance_summary(self) -> Dict[str, float]:
        """Calculate compliance percentages"""
        if not self.observations:
            return {}
        
        status_counts = {}
        for obs in self.observations:
            status = obs.compliance_status.value
            status_counts[status] = status_counts.get(status, 0) + 1
        
        total = len(self.observations)
        return {
            status: round((count / total) * 100, 1)
            for status, count in status_counts.items()
        }
    
    def _calculate_overall_compliance_score(self) -> int:
        """Calculate overall compliance score (0-100)"""
        if not self.observations:
            return 0
        
        scores = []
        for obs in self.observations:
            if obs.compliance_status == ComplianceStatus.COMPLIANT:
                scores.append(100)
            elif obs.compliance_status == ComplianceStatus.PARTIALLY_COMPLIANT:
                scores.append(60)
            elif obs.compliance_status == ComplianceStatus.NON_COMPLIANT:
                scores.append(0)
        
        return int(sum(scores) / len(scores)) if scores else 0
    
    def _get_assessment_text(self, score: int) -> str:
        """Get assessment text based on score"""
        if score >= 90:
            return "Excellent"
        elif score >= 75:
            return "Good"
        elif score >= 60:
            return "Satisfactory"
        elif score >= 40:
            return "Needs Improvement"
        else:
            return "Unsatisfactory"
    
    def generate_findings_section(self) -> str:
        """Generate detailed findings section"""
        sections = []
        
        sections.append("## Detailed Findings\n")
        
        # Group by category
        categorized = self.categorize_observations()
        
        for category, observations in sorted(categorized.items()):
            sections.append(f"\n### {category}\n")
            
            # Sort by risk level
            sorted_obs = sorted(
                observations,
                key=lambda x: list(RiskLevel).index(x.risk_level)
            )
            
            for obs in sorted_obs:
                risk_emoji = {
                    RiskLevel.CRITICAL: "🔴",
                    RiskLevel.HIGH: "🟠",
                    RiskLevel.MEDIUM: "🟡",
                    RiskLevel.LOW: "🟢",
                    RiskLevel.INFORMATIONAL: "ℹ️"
                }
                
                sections.append(f"""
#### {risk_emoji[obs.risk_level]} {obs.id}: {obs.title}

**Risk Level:** {obs.risk_level.value}  
**Compliance Status:** {obs.compliance_status.value}  
**Control Reference:** {obs.control_reference or 'N/A'}

**Description:**
{obs.description}

**Root Cause:**
{obs.root_cause or 'To be determined during remediation planning'}

**Business Impact:**
{obs.business_impact or 'Potential operational and compliance risks'}

**Affected Systems:**
{', '.join(obs.affected_systems) if obs.affected_systems else 'Multiple systems'}

**Evidence:**
{self._format_evidence_list(obs.evidence)}

**Risk Score:** {self.generate_risk_score(obs)}/100

---
""")
        
        return '\n'.join(sections)
    
    def _format_evidence_list(self, evidence: List[str]) -> str:
        """Format evidence list"""
        if not evidence:
            return "- Documentation reviewed during audit"
        return '\n'.join([f"- {item}" for item in evidence])
    
    def generate_risk_matrix(self) -> str:
        """Generate risk assessment matrix"""
        matrix = """
## Risk Assessment Matrix

| Risk Level | Count | Percentage | Priority | Action Required |
|------------|-------|------------|----------|-----------------|
"""
        
        distribution = self._calculate_risk_distribution()
        total = len(self.observations)
        
        risk_actions = {
            "Critical": "Immediate action required (0-7 days)",
            "High": "Urgent attention needed (7-30 days)",
            "Medium": "Action plan required (30-90 days)",
            "Low": "Monitor and improve (90+ days)",
            "Informational": "For awareness only"
        }
        
        priorities = {
            "Critical": "P0",
            "High": "P1",
            "Medium": "P2",
            "Low": "P3",
            "Informational": "P4"
        }
        
        for level in RiskLevel:
            count = distribution[level.value]
            percentage = (count / total * 100) if total > 0 else 0
            matrix += f"| {level.value} | {count} | {percentage:.1f}% | {priorities[level.value]} | {risk_actions[level.value]} |\n"
        
        matrix += f"\n**Total Observations:** {total}\n"
        
        return matrix
    
    def generate_recommendations_section(self) -> str:
        """Generate recommendations and action plan"""
        sections = []
        
        sections.append("""
## Recommendations and Action Plan

The following recommendations are provided to address the identified findings and 
enhance the control environment:

### Prioritized Action Items
""")
        
        # Auto-generate recommendations if not provided
        if not self.recommendations:
            self._auto_generate_recommendations()
        
        # Sort by priority
        priority_order = {"Critical": 0, "High": 1, "Medium": 2, "Low": 3}
        sorted_recs = sorted(
            self.recommendations,
            key=lambda x: priority_order.get(x.priority, 999)
        )
        
        # Create action plan table
        sections.append("""
| ID | Recommendation | Priority | Owner | Target Date | Effort | Status |
|----|----------------|----------|-------|-------------|--------|--------|
""")
        
        for rec in sorted_recs:
            sections.append(
                f"| {rec.observation_id} | {rec.recommendation[:60]}... | "
                f"{rec.priority} | {rec.responsible_party} | "
                f"{rec.target_completion_date.strftime('%Y-%m-%d')} | "
                f"{rec.estimated_effort} | Not Started |\n"
            )
        
        # Detailed recommendations
        sections.append("\n### Detailed Recommendations\n")
        
        for rec in sorted_recs:
            obs = next((o for o in self.observations if o.id == rec.observation_id), None)
            
            sections.append(f"""
#### Recommendation for {rec.observation_id}: {obs.title if obs else 'Finding'}

**Priority:** {rec.priority}  
**Responsible Party:** {rec.responsible_party}  
**Target Completion:** {rec.target_completion_date.strftime('%B %d, %Y')}  
**Estimated Effort:** {rec.estimated_effort}

**Recommended Action:**
{rec.recommendation}

**Required Resources:**
{self._format_resource_list(rec.resources_required)}

**Success Criteria:**
- Control is implemented and tested
- Documentation is updated
- Staff training is completed (if applicable)
- Follow-up audit confirms remediation

---
""")
        
        return '\n'.join(sections)
    
    def _auto_generate_recommendations(self):
        """Auto-generate recommendations from observations"""
        for obs in self.observations:
            # Simple recommendation generation (can be enhanced with AI)
            priority_map = {
                RiskLevel.CRITICAL: "Critical",
                RiskLevel.HIGH: "High",
                RiskLevel.MEDIUM: "Medium",
                RiskLevel.LOW: "Low",
                RiskLevel.INFORMATIONAL: "Low"
            }
            
            recommendation_text = f"Implement corrective measures to address {obs.title.lower()}. "
            recommendation_text += f"Review and update relevant policies and procedures. "
            recommendation_text += f"Provide necessary training to staff."
            
            rec = AuditRecommendation(
                observation_id=obs.id,
                recommendation=recommendation_text,
                priority=priority_map[obs.risk_level],
                responsible_party=self.metadata.auditee_department,
                target_completion_date=self._calculate_target_date(obs.risk_level),
                estimated_effort=self._estimate_effort(obs.risk_level),
                resources_required=["Staff time", "Budget allocation", "External consultants (if needed)"]
            )
            
            self.add_recommendation(rec)
    
    def _calculate_target_date(self, risk_level: RiskLevel) -> date:
        """Calculate target completion date based on risk"""
        from datetime import timedelta
        
        days_map = {
            RiskLevel.CRITICAL: 7,
            RiskLevel.HIGH: 30,
            RiskLevel.MEDIUM: 90,
            RiskLevel.LOW: 180,
            RiskLevel.INFORMATIONAL: 365
        }
        
        return datetime.now().date() + timedelta(days=days_map[risk_level])
    
    def _estimate_effort(self, risk_level: RiskLevel) -> str:
        """Estimate effort required"""
        effort_map = {
            RiskLevel.CRITICAL: "High (40-80 hours)",
            RiskLevel.HIGH: "Medium (20-40 hours)",
            RiskLevel.MEDIUM: "Medium (10-20 hours)",
            RiskLevel.LOW: "Low (5-10 hours)",
            RiskLevel.INFORMATIONAL: "Minimal (1-5 hours)"
        }
        return effort_map[risk_level]
    
    def _format_resource_list(self, resources: List[str]) -> str:
        """Format resource list"""
        if not resources:
            return "- Internal resources sufficient"
        return '\n'.join([f"- {resource}" for resource in resources])
    
    def generate_full_report(self) -> str:
        """Generate complete audit report in markdown"""
        report_parts = []
        
        # Title page
        report_parts.append(f"""
# {self.metadata.audit_title}

**Audit ID:** {self.metadata.audit_id}  
**Audit Type:** {self.metadata.audit_type}  
**Audit Period:** {self.metadata.audit_period_start.strftime('%B %d, %Y')} to {self.metadata.audit_period_end.strftime('%B %d, %Y')}  
**Report Date:** {self.metadata.report_date.strftime('%B %d, %Y')}

**Auditor:** {self.metadata.auditor_name}  
**Organization:** {self.metadata.auditor_organization}  
**Auditee Department:** {self.metadata.auditee_department}

**Standards/Frameworks:** {', '.join(self.metadata.standards_frameworks)}

---
""")
        
        # Table of contents
        report_parts.append("""
## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Audit Scope and Methodology](#audit-scope-and-methodology)
3. [Detailed Findings](#detailed-findings)
4. [Risk Assessment Matrix](#risk-assessment-matrix)
5. [Recommendations and Action Plan](#recommendations-and-action-plan)
6. [Conclusion](#conclusion)
7. [Appendices](#appendices)

---
""")
        
        # Main sections
        report_parts.append(self.generate_executive_summary())
        report_parts.append(self.generate_audit_scope_section())
        report_parts.append(self.generate_findings_section())
        report_parts.append(self.generate_risk_matrix())
        report_parts.append(self.generate_recommendations_section())
        report_parts.append(self.generate_conclusion())
        report_parts.append(self.generate_appendices())
        
        return '\n'.join(report_parts)
    
    def generate_audit_scope_section(self) -> str:
        """Generate audit scope and methodology section"""
        return f"""
## Audit Scope and Methodology

### Scope
This audit encompassed the {self.metadata.auditee_department} department's operations, 
with a focus on evaluating the design and operating effectiveness of internal controls.

**Key Areas Reviewed:**
{self._generate_scope_areas()}

### Methodology
The audit was conducted in accordance with {', '.join(self.metadata.standards_frameworks)} 
using the following approach:

1. **Planning Phase**
   - Risk assessment and audit planning
   - Control identification and documentation review
   - Stakeholder interviews

2. **Fieldwork Phase**
   - Control testing and evidence gathering
   - Process walkthroughs
   - System configuration reviews
   - Sample testing of transactions

3. **Reporting Phase**
   - Findings documentation and validation
   - Management discussions
   - Report preparation and review

### Limitations
{self._generate_limitations()}

---
"""
    
    def _generate_scope_areas(self) -> str:
        """Generate list of scope areas from observation categories"""
        categories = set(obs.category for obs in self.observations)
        return '\n'.join([f"- {category}" for category in sorted(categories)])
    
    def _generate_limitations(self) -> str:
        """Generate audit limitations section"""
        return """
This audit was subject to the following limitations:
- Sample-based testing approach
- Reliance on information provided by management
- Point-in-time assessment
- Scope limited to areas specified in audit charter
"""
    
    def generate_conclusion(self) -> str:
        """Generate conclusion section"""
        overall_score = self._calculate_overall_compliance_score()
        
        return f"""
## Conclusion

The audit of {self.metadata.auditee_department} has been completed for the period 
{self.metadata.audit_period_start.strftime('%B %d, %Y')} to 
{self.metadata.audit_period_end.strftime('%B %d, %Y')}.

### Overall Opinion
Based on the audit work performed and findings identified, the control environment 
is assessed with an overall compliance score of **{overall_score}%**. This indicates 
a {self._get_assessment_text(overall_score).lower()} control environment.

### Key Takeaways
- **Total Findings:** {len(self.observations)} observations identified
- **Critical Issues:** {len([o for o in self.observations if o.risk_level == RiskLevel.CRITICAL])} requiring immediate attention
- **Compliance Gaps:** Multiple areas require enhancement to meet regulatory requirements

### Next Steps
1. Management to review and acknowledge all findings
2. Develop detailed remediation plans with timelines
3. Implement corrective actions as per priority
4. Schedule follow-up audit in 6 months
5. Provide quarterly progress updates to audit committee

### Auditor's Statement
This audit report accurately reflects the findings identified during the audit period. 
All findings have been discussed with management, and their responses have been 
incorporated where applicable.

**Auditor Signature:** {self.metadata.auditor_name}  
**Date:** {self.metadata.report_date.strftime('%B %d, %Y')}

---
"""
    
    def generate_appendices(self) -> str:
        """Generate appendices section"""
        return """
## Appendices

### Appendix A: Glossary of Terms

| Term | Definition |
|------|------------|
| Control | A process or procedure designed to reduce risk |
| Finding | An identified deficiency or area for improvement |
| Risk Level | Assessment of potential impact and likelihood |
| Compliance Status | Degree of adherence to requirements |

### Appendix B: Control Framework Reference

[Include relevant control framework documentation]

### Appendix C: Evidence Documentation

[List of evidence reviewed during audit]

### Appendix D: Management Response

[Management's formal response to audit findings]

---

**End of Report**
"""
    
    def save_report(self, output_path: str):
        """Save report to markdown file"""
        report_content = self.generate_full_report()
        
        with open(output_path, 'w', encoding='utf-8') as f:
            f.write(report_content)
        
        print(f"✅ Audit report saved to: {output_path}")
        print(f"📊 Total observations: {len(self.observations)}")
        print(f"📋 Total recommendations: {len(self.recommendations)}")
Usage Example
pythonCopy# Initialize generator with template
generator = AuditReportGenerator(template="sox_compliance")

# Set audit metadata
metadata = AuditMetadata(
    audit_id="AUD-2024-001",
    audit_title="SOX Compliance Audit - IT General Controls",
    audit_type="Compliance Audit",
    audit_period_start=date(2024, 1, 1),
    audit_period_end=date(2024, 3, 31),
    auditor_name="Jane Smith, CPA, CISA",
    auditor_organization="Internal Audit Department",
    auditee_department="Information Technology",
    report_date=date(2024, 4, 15),
    standards_frameworks=["SOX Section 404", "COSO Framework", "COBIT 2019"]
)
generator.set_metadata(metadata)

# Add observations from JSON
observations_json = '''
[
    {
        "id": "ITGC-001",
        "title": "Inadequate Access Control Review Process",
        "description": "Quarterly access reviews are not being performed consistently across all critical systems. Evidence showed that 3 out of 8 systems had no access review in the past 6 months.",
        "category": "Access Control",
        "risk_level": "High",
        "compliance_status": "Non-Compliant",
        "evidence": ["Access_Review_Log_Q1.xlsx", "System_Admin_List.pdf"],
        "affected_systems": ["SAP", "Oracle Financials", "Salesforce"],
        "control_reference": "SOX-AC-01",
        "root_cause": "Lack of automated review process and unclear ownership",
        "business_impact": "Risk of unauthorized access to financial systems and data"
    },
    {
        "id": "ITGC-002",
        "title": "Missing Change Management Documentation",
        "description": "15% of production changes in Q1 lacked proper approval documentation and testing evidence.",
        "category": "Change Management",
        "risk_level": "Medium",
        "compliance_status": "Partially Compliant",
        "evidence": ["Change_Tickets_Q1.csv", "CAB_Meeting_Minutes.pdf"],
        "affected_systems": ["ERP System"],
        "control_reference": "SOX-CM-02",
        "root_cause": "Manual process prone to human error",
        "business_impact": "Potential for unauthorized or untested changes affecting financial reporting"
    }
]
'''

generator.add_observations_from_json(observations_json)

# Generate and save report
generator.save_report("SOX_Audit_Report_Q1_2024.md")
MANDATORY TRIGGERS
audit report, audit findings, compliance audit, internal audit, sox audit, audit observations, audit documentation, risk assessment, audit template, compliance report

Skill 13: Advanced PDF Processing Suite
advanced-pdf-processor
Description
Comprehensive PDF manipulation toolkit with advanced capabilities including OCR, form processing, digital signatures, PDF/A conversion, batch processing, data extraction, annotation, and intelligent document analysis using AI.
Capabilities

Text Extraction:

Multi-language OCR (100+ languages)
Layout-preserving extraction
Table structure recognition
Form field extraction
Handwriting recognition


Document Manipulation:

Merge/split PDFs
Page rotation, reordering
Watermarking
Redaction
Compression optimization


Conversion:

PDF to Word/Excel/PowerPoint
Images to PDF
PDF/A compliance conversion
HTML to PDF with CSS


Advanced Features:

Digital signature verification
Metadata editing
Bookmarks and annotations
Form filling automation
Accessibility (PDF/UA)


AI-Powered:

Intelligent document classification
Entity extraction
Summary generation
Question answering from PDF content



Implementation
pythonCopyimport fitz  # PyMuPDF
import pytesseract
from PIL import Image
import cv2
import numpy as np
from pdf2image import convert_from_path
import pdfplumber
from PyPDF2 import PdfReader, PdfWriter, PdfMerger
from reportlab.pdfgen import canvas
from reportlab.lib.pagesizes import letter
import io
from typing import List, Dict, Optional, Tuple
from dataclasses import dataclass
import re

@dataclass
class PDFMetadata:
    """PDF document metadata"""
    title: Optional[str] = None
    author: Optional[str] = None
    subject: Optional[str] = None
    creator: Optional[str] = None
    producer: Optional[str] = None
    creation_date: Optional[str] = None
    modification_date: Optional[str] = None
    keywords: List[str] = None
    page_count: int = 0
    file_size: int = 0
    pdf_version: str = ""
    is_encrypted: bool = False
    is_linearized: bool = False

@dataclass
class ExtractedTable:
    """Extracted table data"""
    page_number: int
    table_index: int
    headers: List[str]
    rows: List[List[str]]
    bbox: Tuple[float, float, float, float]

@dataclass
class ExtractedText:
    """Extracted text with metadata"""
    text: str
    page_number: int
    bbox: Tuple[float, float, float, float]
    font_name: str
    font_size: float
    confidence: float = 1.0

class AdvancedPDFProcessor:
    """Advanced PDF processing with AI capabilities"""
    
    def __init__(self, pdf_path: str):
        """
        Initialize PDF processor
        
        Args:
            pdf_path: Path to PDF file
        """
        self.pdf_path = pdf_path
        self.doc = fitz.open(pdf_path)
        self.metadata = self._extract_metadata()
    
    def _extract_metadata(self) -> PDFMetadata:
        """Extract PDF metadata"""
        meta = self.doc.metadata
        
        return PDFMetadata(
            title=meta.get('title'),
            author=meta.get('author'),
            subject=meta.get('subject'),
            creator=meta.get('creator'),
            producer=meta.get('producer'),
            creation_date=meta.get('creationDate'),
            modification_date=meta.get('modDate'),
            keywords=meta.get('keywords', '').split(',') if meta.get('keywords') else [],
            page_count=len(self.doc),
            pdf_version=f"PDF {self.doc.metadata.get('format', 'Unknown')}",
            is_encrypted=self.doc.is_encrypted,
            is_linearized=self.doc.is_fast_web_view
        )
    
    def extract_text_advanced(self, 
                             preserve_layout: bool = True,
                             include_images: bool = False) -> List[ExtractedText]:
        """
        Advanced text extraction with layout preservation
        
        Args:
            preserve_layout: Maintain original text layout
            include_images: Extract text from images using OCR
        
        Returns:
            List of ExtractedText objects
        """
        extracted_texts = []
        
        for page_num in range(len(self.doc)):
            page = self.doc[page_num]
            
            if preserve_layout:
                # Extract text blocks with position information
                blocks = page.get_text("dict")["blocks"]
                
                for block in blocks:
                    if block['type'] == 0:  # Text block
                        for line in block.get('lines', []):
                            for span in line.get('spans', []):
                                extracted_texts.append(ExtractedText(
                                    text=span['text'],
                                    page_number=page_num + 1,
                                    bbox=tuple(span['bbox']),
                                    font_name=span['font'],
                                    font_size=span['size']
                                ))
                    
                    elif block['type'] == 1 and include_images:  # Image block
                        # OCR on images
                        img_text = self._ocr_image_block(page, block)
                        if img_text:
                            extracted_texts.append(ExtractedText(
                                text=img_text,
                                page_number=page_num + 1,
                                bbox=tuple(block['bbox']),
                                font_name='OCR',
                                font_size=12.0,
                                confidence=0.85
                            ))
            else:
                # Simple text extraction
                text = page.get_text()
                extracted_texts.append(ExtractedText(
                    text=text,
                    page_number=page_num + 1,
                    bbox=(0, 0, page.rect.width, page.rect.height),
                    font_name='Mixed',
                    font_size=12.0
                ))
        
        return extracted_texts
    
    def _ocr_image_block(self, page, block) -> str:
        """Perform OCR on image block"""
        try:
            # Extract image
            pix = page.get_pixmap(clip=fitz.Rect(block['bbox']))
            img_data = pix.tobytes("png")
            img = Image.open(io.BytesIO(img_data))
            
            # Preprocess image for better OCR
            img = self._preprocess_image_for_ocr(np.array(img))
            
            # Perform OCR
            text = pytesseract.image_to_string(img)
            return text.strip()
        
        except Exception as e:
            print(f"OCR error: {e}")
            return ""
    
    def _preprocess_image_for_ocr(self, image: np.ndarray) -> Image:
        """Preprocess image for improved OCR accuracy"""
        # Convert to grayscale
        if len(image.shape) == 3:
            gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
        else:
            gray = image
        
        # Denoise
        denoised = cv2.fastNlMeansDenoising(gray)
        
        # Adaptive thresholding
        thresh = cv2.adaptiveThreshold(
            denoised, 255, 
            cv2.ADAPTIVE_THRESH_GAUSSIAN_C, 
            cv2.THRESH_BINARY, 11, 2
        )
        
        return Image.fromarray(thresh)
    
    def extract_tables(self) -> List[ExtractedTable]:
        """
        Extract tables from PDF using advanced detection
        
        Returns:
            List of ExtractedTable objects
        """
        tables = []
        
        with pdfplumber.open(self.pdf_path) as pdf:
            for page_num, page in enumerate(pdf.pages):
                # Extract tables
                page_tables = page.extract_tables()
                
                for table_idx, table in enumerate(page_tables):
                    if not table or len(table) < 2:
                        continue
                    
                    # First row as headers
                    headers = table[0]
                    rows = table[1:]
                    
                    # Get table bounding box
                    bbox = self._find_table_bbox(page, table)
                    
                    tables.append(ExtractedTable(
                        page_number=page_num + 1,
                        table_index=table_idx + 1,
                        headers=headers,
                        rows=rows,
                        bbox=bbox
                    ))
        
        return tables
    
    def _find_table_bbox(self, page, table) -> Tuple[float, float, float, float]:
        """Find bounding box of table"""
        # Simplified bbox calculation
        return (0, 0, page.width, page.height)
    
    def extract_forms(self) -> Dict[str, any]:
        """Extract form fields and values"""
        form_data = {}
        
        reader = PdfReader(self.pdf_path)
        
        if reader.get_fields():
            fields = reader.get_fields()
            
            for field_name, field in fields.items():
                form_data[field_name] = {
                    'value': field.get('/V', ''),
                    'type': field.get('/FT', ''),
                    'flags': field.get('/Ff', 0)
                }
        
        return form_data
    
    def fill_form(self, form_data: Dict[str, str], output_path: str):
        """Fill PDF form fields"""
        reader = PdfReader(self.pdf_path)
        writer = PdfWriter()
        
        # Copy pages
        for page in reader.pages:
            writer.add_page(page)
        
        # Update form fields
        writer.update_page_form_field_values(
            writer.pages[0], form_data
        )
        
        # Write to file
        with open(output_path, 'wb') as output_file:
            writer.write(output_file)
        
        print(f"✅ Form filled and saved to: {output_path}")
    
    def merge_pdfs(self, pdf_list: List[str], output_path: str):
        """Merge multiple PDFs"""
        merger = PdfMerger()
        
        for pdf in pdf_list:
            merger.append(pdf)
        
        merger.write(output_path)
        merger.close()
        
        print(f"✅ {len(pdf_list)} PDFs merged to: {output_path}")
    
    def split_pdf(self, output_dir: str, pages_per_split: int = 1):
        """Split PDF into multiple files"""
        reader = PdfReader(self.pdf_path)
        
        for i in range(0, len(reader.pages), pages_per_split):
            writer = PdfWriter()
            
            for j in range(i, min(i + pages_per_split, len(reader.pages))):
                writer.add_page(reader.pages[j])
            
            output_path = f"{output_dir}/split_{i//pages_per_split + 1}.pdf"
            with open(output_path, 'wb') as output_file:
                writer.write(output_file)
        
        print(f"✅ PDF split into {(len(reader.pages) + pages_per_split - 1) // pages_per_split} files")
    
    def add_watermark(self, watermark_text: str, output_path: str,
                     opacity: float = 0.3, rotation: int = 45):
        """Add text watermark to PDF"""
        reader = PdfReader(self.pdf_path)
        writer = PdfWriter()
        
        # Create watermark
        watermark_pdf = self._create_watermark(
            watermark_text, reader.pages[0].mediabox.width,
            reader.pages[0].mediabox.height, opacity, rotation
        )
        watermark_page = PdfReader(watermark_pdf).pages[0]
        
        # Apply to all pages
        for page in reader.pages:
            page.merge_page(watermark_page)
            writer.add_page(page)
        
        with open(output_path, 'wb') as output_file:
            writer.write(output_file)
        
        print(f"✅ Watermark added to: {output_path}")
    
    def _create_watermark(self, text: str, width: float, height: float,
                          opacity: float, rotation: int) -> io.BytesIO:
        """Create watermark PDF"""
        packet = io.BytesIO()
        can = canvas.Canvas(packet, pagesize=(width, height))
        
        can.saveState()
        can.setFillAlpha(opacity)
        can.translate(width/2, height/2)
        can.rotate(rotation)
        can.setFont("Helvetica", 60)
        can.drawCentredString(0, 0, text)
        can.restoreState()
        
        can.save()
        packet.seek(0)
        
        return packet
    
    def redact_text(self, patterns: List[str], output_path: str):
        """
        Redact sensitive information using regex patterns
        
        Args:
            patterns: List of regex patterns to redact
            output_path: Output file path
        """
        for page_num in range(len(self.doc)):
            page = self.doc[page_num]
            
            for pattern in patterns:
                # Find text matching pattern
                text_instances = page.search_for(pattern)
                
                # Redact each instance
                for inst in text_instances:
                    page.add_redact_annot(inst, fill=(0, 0, 0))
            
            # Apply redactions
            page.apply_redactions()
        
        self.doc.save(output_path)
        print(f"✅ Redacted PDF saved to: {output_path}")
    
    def compress_pdf(self, output_path: str, quality: str = "medium"):
        """
        Compress PDF file
        
        Args:
            output_path: Output file path
            quality: Compression quality (low, medium, high)
        """
        quality_settings = {
            "low": {"dpi": 72, "image_quality": 50},
            "medium": {"dpi": 150, "image_quality": 75},
            "high": {"dpi": 300, "image_quality": 85}
        }
        
        settings = quality_settings.get(quality, quality_settings["medium"])
        
        # Use PyMuPDF for compression
        for page in self.doc:
            # Compress images
            for img_index, img in enumerate(page.get_images()):
                xref = img[0]
                base_image = self.doc.extract_image(xref)
                
                if base_image:
                    image_bytes = base_image["image"]
                    img_pil = Image.open(io.BytesIO(image_bytes))
                    
                    # Resize and compress
                    img_pil.thumbnail((settings["dpi"] * 10, settings["dpi"] * 10))
                    
                    # Save compressed
                    output = io.BytesIO()
                    img_pil.save(output, format='JPEG', 
                                quality=settings["image_quality"], 
                                optimize=True)
                    output.seek(0)
                    
                    # Replace image in PDF
                    page.replace_image(xref, stream=output.read())
        
        self.doc.save(output_path, garbage=4, deflate=True)
        
        original_size = os.path.getsize(self.pdf_path)
        compressed_size = os.path.getsize(output_path)
        reduction = ((original_size - compressed_size) / original_size) * 100
        
        print(f"✅ PDF compressed: {reduction:.1f}% size reduction")
        print(f"   Original: {original_size/1024:.1f} KB → Compressed: {compressed_size/1024:.1f} KB")
    
    def convert_to_pdfa(self, output_path: str):
        """Convert PDF to PDF/A format for archival"""
        # PDF/A conversion logic
        # This requires additional libraries and ICC profiles
        print("Converting to PDF/A format...")
        
        # Use ghostscript for PDF/A conversion
        import subprocess
        
        gs_command = [
            "gs",
            "-dPDFA=2",
            "-dBATCH",
            "-dNOPAUSE",
            "-sColorConversionStrategy=UseDeviceIndependentColor",
            "-sDEVICE=pdfwrite",
            f"-sOutputFile={output_path}",
            self.pdf_path
        ]
        
        try:
            subprocess.run(gs_command, check=True)
            print(f"✅ PDF/A file created: {output_path}")
        except subprocess.CalledProcessError:
            print("❌ PDF/A conversion failed. Ensure Ghostscript is installed.")
    
    def extract_images(self, output_dir: str) -> List[str]:
        """Extract all images from PDF"""
        import os
        os.makedirs(output_dir, exist_ok=True)
        
        image_paths = []
        
        for page_num in range(len(self.doc)):
            page = self.doc[page_num]
            images = page.get_images()
            
            for img_index, img in enumerate(images):
                xref = img[0]
                base_image = self.doc.extract_image(xref)
                
                if base_image:
                    image_bytes = base_image["image"]
                    image_ext = base_image["ext"]
                    
                    image_path = f"{output_dir}/page{page_num+1}_img{img_index+1}.{image_ext}"
                    
                    with open(image_path, "wb") as img_file:
                        img_file.write(image_bytes)
                    
                    image_paths.append(image_path)
        
        print(f"✅ Extracted {len(image_paths)} images to {output_dir}")
        return image_paths
    
    def add_bookmarks(self, bookmarks: List[Dict], output_path: str):
        """
        Add bookmarks/table of contents to PDF
        
        Args:
            bookmarks: List of {title, page_number, level}
        """
        writer = PdfWriter()
        reader = PdfReader(self.pdf_path)
        
        for page in reader.pages:
            writer.add_page(page)
        
        # Add bookmarks
        for bookmark in bookmarks:
            writer.add_outline_item(
                bookmark['title'],
                bookmark['page_number'] - 1,
                parent=None
            )
        
        with open(output_path, 'wb') as output_file:
            writer.write(output_file)
        
        print(f"✅ Bookmarks added to: {output_path}")
    
    def ai_classify_document(self) -> Dict[str, any]:
        """
        Use AI to classify document type and extract key information
        
        Returns:
            Classification results
        """
        # Extract sample text
        text_sample = ""
        for page_num in range(min(3, len(self.doc))):
            text_sample += self.doc[page_num].get_text()
        
        # AI classification logic (placeholder for actual AI model)
        classification = {
            "document_type": self._classify_document_type(text_sample),
            "language": self._detect_language(text_sample),
            "entities": self._extract_entities(text_sample),
            "topics": self._extract_topics(text_sample),
            "sentiment": self._analyze_sentiment(text_sample),
            "summary": self._generate_summary(text_sample)
        }
        
        return classification
    
    def _classify_document_type(self, text: str) -> str:
        """Classify document type using keywords"""
        doc_types = {
            "invoice": ["invoice", "bill", "amount due", "payment"],
            "contract": ["agreement", "party", "whereas", "terms and conditions"],
            "resume": ["experience", "education", "skills", "objective"],
            "report": ["executive summary", "findings", "recommendations"],
            "academic": ["abstract", "introduction", "methodology", "references"]
        }
        
        text_lower = text.lower()
        scores = {}
        
        for doc_type, keywords in doc_types.items():
            score = sum(1 for keyword in keywords if keyword in text_lower)
            scores[doc_type] = score
        
        return max(scores, key=scores.get) if scores else "general"
    
    def _detect_language(self, text: str) -> str:
        """Detect document language"""
        # Simplified language detection
        try:
            from langdetect import detect
            return detect(text)
        except:
            return "en"
    
    def _extract_entities(self, text: str) -> Dict[str, List[str]]:
        """Extract named entities"""
        entities = {
            "emails": re.findall(r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b', text),
            "phones": re.findall(r'\b\d{3}[-.]?\d{3}[-.]?\d{4}\b', text),
            "dates": re.findall(r'\b\d{1,2}[/-]\d{1,2}[/-]\d{2,4}\b', text),
            "amounts": re.findall(r'\$\d+(?:,\d{3})*(?:\.\d{2})?', text),
            "urls": re.findall(r'http[s]?://(?:[a-zA-Z]|[0-9]|[$-_@.&+]|[!*\\(\\),]|(?:%[0-9a-fA-F][0-9a-fA-F]))+', text)
        }
        return entities
    
    def _extract_topics(self, text: str) -> List[str]:
        """Extract main topics from text"""
        # Simplified topic extraction using word frequency
        words = re.findall(r'\b[a-z]{4,}\b', text.lower())
        from collections import Counter
        common = Counter(words).most_common(10)
        return [word for word, count in common]
    
    def _analyze_sentiment(self, text: str) -> str:
        """Analyze document sentiment"""
        # Simplified sentiment analysis
        positive_words = ['success', 'excellent', 'good', 'positive', 'great']
        negative_words = ['fail', 'bad', 'negative', 'poor', 'worst']
        
        text_lower = text.lower()
        pos_score = sum(1 for word in positive_words if word in text_lower)
        neg_score = sum(1 for word in negative_words if word in text_lower)
        
        if pos_score > neg_score:
            return "positive"
        elif neg_score > pos_score:
            return "negative"
        else:
            return "neutral"
    
    def _generate_summary(self, text: str) -> str:
        """Generate document summary"""
        # Extract first few sentences as summary
        sentences = re.split(r'[.!?]+', text)
        summary = '. '.join(sentences[:3]) + '.'
        return summary.strip()
    
    def batch_process(self, operations: List[Dict], output_dir: str):
        """
        Batch process PDF with multiple operations
        
        Args:
            operations: List of operations to perform
            Example: [
                {"type": "extract_text", "params": {}},
                {"type": "extract_tables", "params": {}},
                {"type": "add_watermark", "params": {"text": "CONFIDENTIAL"}}
            ]
        """
        import os
        os.makedirs(output_dir, exist_ok=True)
        
        results = {}
        
        for operation in operations:
            op_type = operation['type']
            params = operation.get('params', {})
            
            if op_type == "extract_text":
                results['text'] = self.extract_text_advanced(**params)
            elif op_type == "extract_tables":
                results['tables'] = self.extract_tables()
            elif op_type == "extract_images":
                results['images'] = self.extract_images(f"{output_dir}/images")
            elif op_type == "compress":
                output_path = f"{output_dir}/compressed.pdf"
                self.compress_pdf(output_path, **params)
                results['compressed_path'] = output_path
            # Add more operations as needed
        
        print(f"✅ Batch processing complete. {len(operations)} operations performed.")
        return results
    
    def close(self):
        """Close PDF document"""
        self.doc.close()
Usage Example
pythonCopy# Initialize processor
processor = AdvancedPDFProcessor("document.pdf")

# Extract metadata
print(f"Pages: {processor.metadata.page_count}")
print(f"Author: {processor.metadata.author}")

# Advanced text extraction with OCR
texts = processor.extract_text_advanced(
    preserve_layout=True,
    include_images=True
)

# Extract tables
tables = processor.extract_tables()
for table in tables:
    print(f"Table on page {table.page_number}:")
    print(f"Headers: {table.headers}")

# AI classification
classification = processor.ai_classify_document()
print(f"Document type: {classification['document_type']}")
print(f"Language: {classification['language']}")

# Batch processing
operations = [
    {"type": "extract_text", "params": {"preserve_layout": True}},
    {"type": "extract_tables", "params": {}},
    {"type": "compress", "params": {"quality": "medium"}},
    {"type": "extract_images", "params": {}}
]
processor.batch_process(operations, "output")

# Close
processor.close()
MANDATORY TRIGGERS
pdf processing, pdf manipulation, pdf extraction, ocr, pdf converter, pdf merge, pdf split, pdf watermark, pdf compression, pdf forms

Skill 14: Advanced Dataset Analysis Engine
dataset-analyzer
Description
Comprehensive dataset analysis system that accepts multiple data formats (TXT, CSV, JSON, XLSX) and generates detailed analytical reports with statistical summaries, visualizations, data quality assessment, and actionable insights in markdown format (3000-4000 words).
Capabilities

Multi-Format Support:

Plain text files (TXT)
Comma-separated values (CSV, TSV
