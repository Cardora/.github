# **Cardora**
*Bridging Event Organizers & Attendees*

### **Team Mission**
We serve as the seamless connection between event organizers and attendees, creating efficient and engaging event experiences.

---

## **Repository Structure**

```bash
├── /agenda                # Solution documentation & planning
├── /architecture          # System architecture & design decisions  
├── /basic-app             # Prototype (Verification & Issuer functionality)
```

### **Key Directories**
- **`agenda/`** - Detailed project documentation, requirements, and roadmaps
- **`architecture/`** - Technical diagrams, system flows, and infrastructure
- **`basic-app/`** - Minimal viable prototype for core functionality validation

# Agenda 

# Cardora: Digital Card Management Platform

![cardora.png](/cardora.png)




## Problem Analysis

### Stakeholder Pain Points & Solutions

| Stakeholder | Problem | Pain Points | "What If" Solution | Benefits |
|-------------|---------|-------------|---------------------|----------|
| **Business Owner** | Need to arrange event quickly | - Long card production time<br>- Shipping delays<br>- Manual distribution | Digital cards issued instantly | - No physical production<br>- No shipping wait<br>- Real-time issuance |
| **Business Owner** | Card ordering process | - Bulk ordering required<br>- Minimum order quantities<br>- Upfront costs | On-demand digital issuance | - Pay per card<br>- No minimums<br>- No inventory |
| **Business Owner** | Time constraints | - Lead time for physical cards<br>- Last-minute attendees | Instant digital delivery | - Same-day event setup<br>- Add attendees anytime |
| **User** | Physical card dependency | - Forgetting cards<br>- Loss/theft<br>- Damage | Mobile wallet integration | - Always available on phone<br>- Backup in cloud |
| **User** | Multiple cards | - Wallet clutter<br>- Organization difficulty | Unified digital card app | - All cards in one place<br>- Easy switching |
| **User** | Replacement delays | - Waiting for new cards<br>- Verification hassles | Instant digital reissuance | - Self-service replacement<br>- Immediate access |
| **User** | Pre-event checklist | - Manual card verification<br>- Anxiety about forgetting | Push notification reminders | - Automated check<br>- Last-minute alerts |

### Problem Statement

Traditional physical card systems create logistical bottlenecks for event organizers and friction for users who struggle with card management, leading to:
- Slow onboarding for last-minute participants
- High costs and waste from unused physical cards
- Poor user experience from lost/forgotten cards
- Operational inefficiencies in card distribution

---

## Security & Privacy Framework

### Trust Issues Resolution

**Business Owner:** "What if my employee data gets leaked? I'm concerned about privacy."

**Cardora:** "We completely understand your concern. With Cardora, we offer **two security modes** to match your privacy requirements – and in both cases, we never store raw personal information."

---

**Business Owner:** "What are these two modes?"

**Cardora:** "We have:

**Mode 1: Hash-Based Cards** (Standard)
- Your employee data stays in *your* HR system
- We generate a cryptographic hash (digital fingerprint) of employee ID/email
- Original data is discarded immediately
- Verification happens by comparing hashes – no personal data stored

**Mode 2: Self-Sovereign Cards** (Premium)
- Each employee gets their own cryptographic key pair
- Cards are digitally signed by the employee's private key
- We only store the public signature – no personal data at all
- Employee controls their own card completely"

---

**Business Owner:** "Which mode should I choose?"

**Cardora:** "Most organizations start with **Hash-Based Cards** because:
- Simple setup for bulk employee onboarding
- You control the card issuance process
- Lower cost per card

**Self-Sovereign Cards** are better if you have:
- Employees who handle highly sensitive data
- Remote workers who need maximum privacy control
- Compliance requirements for zero data storage

You can even mix both modes within your organization – executives might use Self-Sovereign while general employees use Hash-Based."

---

**Business Owner:** "How does verification work with two different systems?"

**Cardora:** "That's the beauty – **verifiers don't need to know which mode was used**. Our scanner automatically detects the card type and applies the correct verification method. It's completely seamless."

---

### Advanced Cryptographic Security

**Business Owner:** "But what if someone reverse-engineers the hashes?"

**Cardora:** "With our advanced cryptographic approach, we go beyond basic hashing:

1. **Asymmetric Key Protection**
    - Each card is signed using ECDSA (Elliptic Curve Digital Signature Algorithm)
    - Your organization holds the private key - we never store it

2. **Dual-Layer Security**
   ```python
   # Card signing process
   signature = ecdsa_sign(
       message=card_details, 
       private_key=org_private_key
   )
   # Generates unique cryptographic signature
   ```
    - The signed card contains:  
      • Public metadata (visible)  
      • Digital signature (verifiable)  
      • No stored personal data

3. **Zero-Data Verification**
    - Verifiers only need your organization's public key
    - No central database of personal information exists to compromise"

---
# Video Demo

## Project Overview

Watch the complete demonstration of Cardora in action.

<div align="center">
  <video width="640" height="480" controls poster="./assets/video-thumbnail.jpg">
    <source src="./cardora.mp4" type="video/mp4">
    <source src="./cardora.webm" type="video/webm">
    <source src="./cardora.ogg" type="video/ogg">
    Your browser does not support the video tag.
    <p>
      <a href="./cardora.mp4">Download the demo video</a> to watch it locally.
    </p>
  </video>
</div>


## Key Features

- **Privacy-First**: Two security modes with zero personal data storage
-  **Instant Issuance**: Digital cards created and delivered immediately
-  **Mobile Integration**: Native wallet support across platforms
-  **Seamless Verification**: Automatic detection of card types
-  **Pay-Per-Use**: No minimum orders or upfront inventory costs
-  **Cross-Platform**: Works across different mobile wallets and devices

## Technology Stack

- **Cryptography**: ECDSA (Elliptic Curve Digital Signature Algorithm)
- **Hashing**: Advanced cryptographic hashing with salt protection
- **Mobile Integration**: Cardora App support 
- **Verification**: QR code 

----

# Application in Stories

### **User Stories (Mobile App - Card Holder)**

1. **Registration & Login**
   - As a user, I can register with my email, password, and public key (as my address).
   - I can log in securely to access my digital cards.

2. **Card Management**
   - **Event Cards**: Automatically appear on my screen when issued.
   - **Employee Cards**: Must request from registered organizations.
   - I can view cards in **Hash** or **Cryptographic** mode.

3. **Security & Settings**
   - I can export my private key.
   - I can log out to keep my cards secure.
   - *(Future)* Suspend cards if my phone is stolen.

4. **Dual Mode Access**
   - I can switch between **Normal User** and **Verifier** roles.

---

### **User Stories (Admin Portal - Organization Owner)**

1. **Registration & Dashboard**
   - I can register as a **Customer** or **Organization**.
   - After login, I see a dashboard with:
      - Organizations I manage
      - Billing history
      - Settings

2. **Card Issuance & Management**
   - Under each organization, I see **Events/Entities** and issued cards.
   - I can **import data** to generate digital cards.
   - I can customize card fields (tags) before creation.

3. **Preview & Approval**
   - After setting fields, I see a **card sample**.
   - I can **edit** (adjust UI/attributes) or **approve**.
   - On approval, I see **cost estimation** and pay via **USDC (Crypto) or Fiat (Asian Payment/Dinger)**.

4. **Post-Payment**
   - After payment, backend processes cards.
   - I receive an **email notification with invoice** upon completion.

---

### **MVP Scope**
-  **Mobile User**: Registration, login, card viewing, basic security.
-  **Admin**: Organization management, card creation, payment.
-  *Later*: Card suspension (lost phone), advanced verifier features.


# UI Imagination 

This is the simple customer of our application would love to see his dashboard and issue cards
- [Customer Admin](https://brand-card-flow.lovable.app)


