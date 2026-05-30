# API Security Risk Analysis – JSONPlaceholder API

## Project Overview

This project focuses on conducting a security assessment of the JSONPlaceholder REST API to identify common API security risks, authentication weaknesses, authorization issues, excessive data exposure, and information disclosure vulnerabilities.

The assessment was performed using read-only testing techniques and follows industry-standard API security review practices based on the OWASP API Security Top 10 framework.

This project demonstrates how security professionals evaluate APIs and document security findings along with practical remediation recommendations.

---

## Objectives

- Analyze publicly available API endpoints.
- Assess authentication mechanisms.
- Review authorization controls.
- Identify excessive data exposure risks.
- Inspect HTTP response headers.
- Evaluate security controls.
- Perform risk classification and reporting.
- Recommend remediation strategies.

---

## Introduction

Application Programming Interfaces (APIs) are essential components of modern web applications, mobile applications, cloud platforms, and SaaS environments.

Since APIs often process sensitive information and business-critical functionality, security assessments are necessary to identify vulnerabilities that could expose user data or application resources.

This project evaluates the JSONPlaceholder API from a security perspective and demonstrates common API security weaknesses found in real-world environments.

---

## Target API

**JSONPlaceholder**

Available Resources:

```http
/users
/posts
/comments
/albums
/photos
/todos
```

JSONPlaceholder is a public REST API designed for educational and testing purposes.

---

## Tools Used

| Tool | Purpose |
|--------|----------|
| Postman | API endpoint testing |
| Google Chrome | Endpoint inspection |
| Browser Developer Tools | Header analysis |
| Documentation Review | API behavior analysis |
| OWASP API Security Top 10 | Security assessment framework |

---

## Assessment Scope

The assessment included:

- Documentation review
- Endpoint enumeration
- Authentication assessment
- Authorization assessment
- Response header analysis
- Data exposure review
- Risk identification
- Security reporting

### Assessment Type

- Read-Only Security Review
- Non-Intrusive Testing
- No Exploitation Performed

---

## Methodology

1. Review API documentation.
2. Enumerate available endpoints.
3. Test endpoint accessibility.
4. Evaluate authentication requirements.
5. Analyze authorization controls.
6. Inspect API response headers.
7. Identify security risks.
8. Document findings and recommendations.

---

# Key Findings

## 1. Unauthenticated Endpoint Access

### Risk Level
Medium

### Observation

API endpoints returned valid responses without requiring authentication credentials.

### Business Impact

Unauthorized users may access information that should normally be protected.

### Recommendation

Implement:

- OAuth 2.0
- JWT Authentication
- API Key Authentication

---

## 2. Weak Authentication Controls

### Risk Level
Medium

### Observation

Requests were successfully processed despite no authentication being configured.

### Business Impact

Lack of identity verification increases the risk of unauthorized access.

### Recommendation

- Enforce authentication before request processing.
- Implement secure token validation.
- Use access control policies.

---

## 3. Excessive Data Exposure

### Risk Level
Medium

### Observation

User responses exposed:

- Names
- Email addresses
- Phone numbers
- Websites
- Company details
- Address information
- Geo-location information

### Business Impact

Exposed information may aid attackers during reconnaissance activities.

### Recommendation

Apply data minimization principles and return only required fields.

---

## 4. Broken Object Level Authorization (BOLA)

### Risk Level
High

### Observation

Different user records could be accessed by modifying identifiers:

```http
/users/1
/users/2
/users/3
```

### Business Impact

In production environments, attackers could access data belonging to other users.

### Recommendation

- Validate ownership of requested resources.
- Implement object-level authorization checks.
- Enforce role-based access control (RBAC).

---

## 5. Technology Information Disclosure

### Risk Level
Low

### Observation

Response headers disclosed technologies such as:

- Express
- Cloudflare

### Business Impact

Technology disclosure assists attackers during reconnaissance and vulnerability identification.

### Recommendation

Remove unnecessary server and framework disclosure headers.

---

# Security Controls Observed

The assessment identified several positive security controls:

### Security Headers

```http
X-Content-Type-Options: nosniff
```

### Rate Limiting Controls

```http
X-RateLimit-Limit
X-RateLimit-Remaining
```

### Additional Protection

- Safe error handling behavior
- Response validation mechanisms
- Controlled endpoint responses

---

# Risk Assessment Summary

| Finding | Severity |
|----------|----------|
| Unauthenticated Endpoint Access | Medium |
| Weak Authentication | Medium |
| Excessive Data Exposure | Medium |
| Broken Object Level Authorization (BOLA) | High |
| Technology Information Disclosure | Low |

---

# Recommendations

## Authentication

- Implement OAuth 2.0
- Use JWT tokens
- Enforce API key validation

## Authorization

- Implement Object Level Authorization
- Apply Role-Based Access Control (RBAC)
- Validate user ownership

## Data Protection

- Return only necessary information
- Mask sensitive fields
- Apply least privilege principles

## Security Headers

- Continue using security headers
- Strengthen response security policies
- Maintain secure HTTP configurations

## Information Disclosure

- Hide server version information
- Remove framework disclosure headers
- Minimize technology exposure

## API Hardening

- Continue rate limiting
- Monitor suspicious requests
- Perform regular API security reviews

---

# Mapping to OWASP API Security Top 10

| Finding | OWASP API Risk |
|----------|----------------|
| Broken Object Level Authorization | API1:2023 |
| Weak Authentication | API2:2023 |
| Excessive Data Exposure | API3:2023 |
| Unauthenticated Access | API2:2023 |
| Information Disclosure | Security Misconfiguration |

---

# Learning Outcomes

Through this project, I gained practical experience in:

- API Security Testing
- Postman API Assessment
- Authentication Analysis
- Authorization Review
- Security Header Inspection
- Risk Assessment
- OWASP API Security Top 10
- Vulnerability Reporting
- API Hardening Recommendations

---

# References

- OWASP API Security Top 10
- JSONPlaceholder Documentation
- Postman Documentation
- Future Interns Cyber Security Internship Guidelines

---

# Conclusion

This API Security Risk Analysis demonstrates how security professionals evaluate APIs for authentication weaknesses, authorization flaws, excessive data exposure, and information disclosure risks.

Although JSONPlaceholder is intentionally public and designed for educational purposes, the findings reflect common vulnerabilities frequently encountered in real-world SaaS and web application APIs. Implementing the recommended security controls would significantly improve API security posture and reduce potential attack surfaces.

---

## Author

**THIRUKUMARAN S**  
Cyber Security Intern  
B.E. Computer Science and Engineering (Cyber Security)  
Future Interns Cyber Security Internship
