# AI-Powered-Career-Coach-Assistant
Automating Skill-Gap Analysis, Training Recommendations and Coaching Workflow Using Amazon Q Business

##Project Overview

Career4All, a career-development platform, was facing challenges scaling its coaching operations as learner volume increased. Coaches manually reviewed CVs, compared them with job descriptions, performed skill-gap analysis, searched through course catalogs, and generated personalized learning schedules. This workflow was time-consuming, inconsistent, and not scalable.

This project delivers an AI-powered Career Coach Assistant Application built with Amazon Q Business, Amazon Q Apps, and Amazon S3. The solution automates major coaching responsibilities while maintaining human oversight through coach-driven refinements.

The result is a scalable, secure, enterprise-ready application that improves efficiency, ensures consistency, and enhances the learner experience.

##🎯 Core Objectives

- Automate CV review and skill-gap analysis

- Automatically recommend relevant training programs

- Generate personalized learning schedules

- Allow coaches to refine AI suggestions

- Integrate both PDF and S3-based course catalogs

- Restrict access to specialized courses using ACL

- Implement keyword/content filtering for ethical outputs

- Enable scalable and continuous catalog updates


##🔧 Technologies Used
|Technology	                     |Purpose                                           |
|--------------------------------|--------------------------------------------------|
|Amazon Q Business	               |AI reasoning, document indexing, recommendations|
|Amazon Q Apps	                   |No-code UI for the assistant|
|Amazon S3	                       |Storage for course catalogs & ACL files|
|IAM Identity Center	             |User authentication & coach roles|
|ACL JSON Configuration	           |Role-based content access|
|PDF Document Indexing	           |Searchable course catalogs|
|S3 Sync Scheduling	               |Automatic catalog updates|


##🧠 System Architecture <br>

  Learner CV + Job Description <br>
            ↓ <br>
      Amazon Q App <br>
            ↓ <br>
      Amazon Q Business <br>
    (Retrieval + Reasoning) <br>
            ↓ <br>
   Indexed PDF / S3 Course Catalogs <br>
            ↓ <br>
Skill Gap Analysis → Training Recommendations → Learning Schedule <br>
            ↓ <br>
      Coach Refinement Input <br>
            ↓ <br>
      Final Recommended Plan

##🚀 Implementation Breakdown <br>
Section 1 — Basic Application Setup <br>
✔ Step 1.1 — Created the base Q App

A new Amazon Q App titled Career Coach Assistant was created.

✔ Step 1.2 — Added input cards

Student CV Input

Job Description Input

These allow text or file content depending on lab constraints.

✔ Step 1.3 — Added Skill Gap Analysis Output

The AI compares CV with job description to extract:

- Required skills

- Current skills

- Missing skills

✔ Step 1.4 — Added Training Recommendation Output

The app retrieves matching courses from indexed documents.

✔ Step 1.5 — Verified functionality

Initial functionality confirmed with sample CVs and JDs.

Section 2 — Customizing the Application

✔ Step 2.1 — Added Learning Schedule Output

AI generates a 4-week personalized learning roadmap.

✔ Step 2.2 — Added Coach Recommendation Input

Coaches can adjust recommendations using natural language input.

Section 3 — Enhancing with PDF Catalog Indexing

Coaches requested that training suggestions come from an official PDF catalog.

✓ Uploaded PDF catalog into Q Business

The PDF was indexed and made searchable.

✓ Verified retrieval accuracy

Queries correctly returned relevant course listings.

Section 4 — Adding S3 as a Dynamic Data Source

Manual uploads were not scalable.

To fix this:

- A new S3 bucket was created

- All course PDFs were uploaded

- Q Business was connected to the bucket

- Automatic weekly sync was enabled

Now coaches just upload new catalogs to S3 → and Q Business updates automatically.

Section 5 — Securing the System

5.1 Role-Based Access Control (ACL)

Some courses (e.g., Medical) must only be accessed by qualified coaches.

A custom ACL JSON file was created:

[
  {
    "keyPrefix": "s3://career4all-cv-uploads/Data/Medicine/", <br>
    "aclEntries": [ <br>
      { <br>
        "Name": "career.coach.two",  <br>
        "Type": "USER",  <br>
        "Access": "ALLOW" <br>
      }  <br>
    ]  <br>
  }, <br>
  {  <br>
    "keyPrefix": "s3://career4all-cv-uploads/Data/Medicine/", <br>
    "aclEntries": [<br>
      { <br>
        "Name": "career.coach.one", <br>
        "Type": "USER", <br>
        "Access": "DENY" <br>
      } <br>
    ] <br>
  }, <br>
  {  <br>
    "keyPrefix": "s3://career4all-cv-uploads/Data/Security/",  <br>
    "aclEntries": [  <br>
      {  <br>
        "Name": "CareerCoaches",  <br>
        "Type": "GROUP", <br>
        "Access": "ALLOW"  <br>
      }  <br>
    ]  <br>
  }  <br>
]  <br>

This file was uploaded to S3 and linked in Q Business.

5.2 Keyword Blocking

Restricted terms included:

Gambling

Casino

Attack

Self-harm

These were blocked to ensure ethical and safe recommendations.

##🧪 Testing & Validation

Testing included:

- Multiple CV formats

- Various job descriptions

- Course catalog retrieval

- ACL visibility testing with different coach roles

- Keyword moderation validation

- Document ingestion sync accuracy

The system worked smoothly across all scenarios.

##⭐ Key Outcomes

- Reduced manual effort by ~80%

- Consistent training recommendations

- Dynamic catalog updates via S3

- Secure role-based access

- Scalable AI-driven coaching workflow

- Fully cloud-native & serverless

- Perfect for real-world enterprise scenarios

##📈 Future Enhancements

- Integrate Amazon Bedrock for multimodal CV parsing (PDF/Images)

- Store user sessions and history in DynamoDB

- Add Power BI dashboard for learner progress

- Expand catalog metadata for improved RAG performance

- Add recommendation confidence scoring

🏆 Conclusion

The AI-Powered Career Coach Assistant demonstrates how AWS-native generative AI tools can transform traditional workflows.
Using Amazon Q Business, S3, and IAM governance, this project provides a scalable, secure, and intelligent coaching system that enhances efficiency while keeping human coaches in control.

This project showcases real-world cloud engineering skills in:

- AI automation

- Retrieval-augmented generation (RAG)

- Secure data governance

- No-code application development

- AWS enterprise architecture
