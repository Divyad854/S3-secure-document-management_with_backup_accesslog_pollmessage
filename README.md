# Document Management System with backups and messages using AWS S3

## Overview
This project demonstrates an enterprise-grade, serverless document management system built using Amazon S3.  
The solution focuses on security, durability, auditability, and event-driven design.

---

## AWS Services Used
- Amazon S3 (Static Website Hosting, Versioning, Encryption)
- S3 Cross-Region Replication
- S3 Server Access Logging
- Amazon SQS (Event Notifications)
- IAM Roles and Bucket Policies

---

## Features
- Static website hosted on Amazon S3
- Secure private document storage bucket
- Server-side encryption enabled
- Object versioning for data protection
- Cross-region replication for disaster recovery
- Server access logging for auditing
- Event-driven notifications using Amazon SQS
- IAM role-based access control (no hardcoded credentials)

---

## Architecture
User → S3 Static Website  
Uploads → S3 Primary Document Bucket  
Events → Amazon SQS Queue  
Logs → S3 Logging Bucket  
Backup → S3 Replica Bucket (Cross-Region)

---

## Implementation Steps (High-Level)

1. Created an S3 bucket to host a static website and enabled public read access only for website files.
2. Created a private S3 bucket for document storage with:
   - Versioning enabled
   - Server-side encryption enabled
3. Configured server access logging to deliver logs to a dedicated logging bucket.
4. Set up cross-region replication to a backup S3 bucket for disaster recovery.
5. Created an Amazon SQS standard queue to receive S3 event notifications.
6. Configured S3 event notifications to send object upload events to the SQS queue.
7. Implemented IAM roles and bucket policies to enforce least-privilege access.
8. Verified all components using AWS Management Console (no CLI).

---

## How to Verify the Project (Demo Validation)

Since this is an infrastructure-based project, functionality is verified through AWS console operations:

- **Static Website**:  
  Accessed via S3 static website endpoint.

- **Document Upload & Versioning**:  
  Uploaded files to the primary bucket and verified multiple object versions.

- **Replication**:  
  Confirmed objects automatically appeared in the replica bucket.

- **Event Notifications**:  
  Uploaded objects triggered messages visible in the SQS queue.

- **Access Logging**:  
  Verified access log files in the logging bucket after a short delay.

---

## Notes
- This project does not run as a traditional application.
- It demonstrates AWS cloud architecture and service configuration.
- All resources were created under AWS Free Tier with minimal usage.

---
