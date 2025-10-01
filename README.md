# 🚀 Go Wallet Demo

<p align="center">
  <img src="https://img.shields.io/badge/Flutter-3.0+-02569B?style=for-the-badge&logo=flutter&logoColor=white" alt="Flutter">
  <img src="https://img.shields.io/badge/Dart-3.0+-0175C2?style=for-the-badge&logo=dart&logoColor=white" alt="Dart">
  <img src="https://img.shields.io/badge/Architecture-Clean%20%2B%20MVVM-green?style=for-the-badge" alt="Architecture">
  <img src="https://img.shields.io/badge/State-Cubit-orange?style=for-the-badge" alt="State Management">
</p>

<p align="center">
  <strong>A production-ready Flutter fintech demo featuring enterprise-grade security, biometric authentication, and seamless money transfers</strong>
</p>

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Key Highlights](#-key-highlights)
- [Features](#-features)
- [Security Implementation](#-security-implementation)
- [Screenshots](#-screenshots)
- [Architecture](#-architecture)
- [Tech Stack](#️-tech-stack)
- [Download](#-download)
- [CI/CD Pipeline](#-cicd-pipeline)
- [Getting Started](#-getting-started)
- [Contact](#-contact)

---

## 🎯 Overview

**Go Wallet** is a comprehensive Flutter-based fintech demonstration that showcases modern mobile wallet capabilities with a strong emphasis on security and user experience. Built with clean architecture principles, this app demonstrates best practices in mobile financial application development, including biometric authentication, secure PIN management, real-time expense tracking, and instant money transfers.

---

## ✨ Key Highlights

- 🔐 **Enterprise-Grade Security** – Custom keyboard, screenshot prevention, root/jailbreak detection
- 🚀 **CI/CD Ready** – Automated deployment with Fastlane to App Distribution
- 🏗️ **Clean Architecture** – MVVM pattern with Cubit state management
- 📊 **Visual Analytics** – Interactive charts for expense tracking
- ⚡ **Instant Transfers** – QR code, username, or contact-based transfers
- 🔑 **Multi-Factor Auth** – Biometric + PIN + OTP verification

---

## 🎨 Features

### 🌟 Splash & Onboarding
- Native Flutter splash screen with brand identity
- **3-slide onboarding experience:**
  - **Slide 1:** Send money instantly using username, phone number, or QR code—no account number required
  - **Slide 2:** Track expenses with visual statistics (daily, weekly, monthly)
  - **Slide 3:** Fast, secure, and reliable transfers completed within seconds

### 🔐 Authentication & Registration
- **Multi-modal login:**
  - Username & password
  - Biometric authentication (fingerprint/Face ID)
- **Secure registration flow:**
  - Personal details collection (name, username, phone, password)
  - Terms & conditions acceptance
  - Email OTP verification
  - Custom PIN setup with secure keyboard
  - Success confirmation screens

### 🏠 Landing & Home Screen
- **Bottom navigation:** Home, Expenses, Profile
- **Personalized dashboard:**
  - Dynamic welcome message
  - Wallet balance with hide/unhide toggle
- **Quick Actions:**
  - Share username via deep link
  - Display personal QR code
  - Instant transfer initiation
- **Fast Transfer:**
  - Scrollable recent recipients
  - One-tap pre-filled transfer
- **Transaction History:**
  - Real-time status tracking (Pending, Failed, Success)

### 💸 Money Transfers
- **Multiple transfer methods:**
  - Username lookup
  - QR code scanning
  - Phone contact selection
- **Smart amount entry:**
  - Custom amount input
  - Preset value suggestions
- **Transaction details:**
  - Optional description field
  - PIN confirmation with secure keyboard

### 📊 Expense Management
- **Visual analytics:**
  - Interactive charts (today, last week, last month, current month)
  - Expense breakdown by category
- **Transaction management:**
  - Detailed transaction history
  - Filter and search capabilities
- **Add expenses:**
  - Quick-add via bottom sheet
  - Amount suggestions
  - Category selection or creation

### 👤 Profile & Settings
- Account settings management
- Saved payment cards
- Personal information editing
- In-app rating system
- Secure logout functionality

---

## 🔒 Security Implementation

Go Wallet implements **multi-layered security** to protect user data and prevent unauthorized access:

### 1. Custom Secure Keyboard
- Prevents keylogging and screen recording detection
- Used for PIN entry and sensitive data input

### 2. Screenshot Prevention
- Blocks screenshots and screen recording
- Protects sensitive financial information

### 3. Device Integrity Checks
```dart
Future<bool> securityGate() async {
  final isNotTrust = await JailbreakRootDetection.instance.isNotTrust;
  final isJailBroken = await JailbreakRootDetection.instance.isJailBroken;
  final isRealDevice = await JailbreakRootDetection.instance.isRealDevice;
  final issues = await JailbreakRootDetection.instance.checkForIssues;

  final isDebugged = issues.contains(JailbreakIssue.debugged);

  // 🚨 Device is compromised if: rooted/jailbroken, emulator, untrusted, or debugged (release only)
  final compromised = 
      isJailBroken || 
      !isRealDevice || 
      isNotTrust || 
      (kReleaseMode && isDebugged);

  return compromised;
}
```

**Security checks include:**
- ✅ Root/Jailbreak detection
- ✅ Emulator detection
- ✅ Developer mode detection (release builds)
- ✅ Device trust validation

### 4. Secure Authentication Flow
- Biometric verification (fingerprint/Face ID)
- Email OTP confirmation
- Custom PIN with secure input
- Session management

---

## 📸 Screenshots

### Authentication Flow
<table>
  <tr>
    <td align="center" width="25%">
      <img src="https://github.com/user-attachments/assets/fc7512ab-983c-4719-a3ec-5385d8b3faa7" width="200px" alt="Login with Biometric"/>
      <br />
      <sub><b>🔐 Login Screen</b></sub>
      <br />
      <sub>Username/Password & Biometric Auth</sub>
    </td>
    <td align="center" width="25%">
      <img src="https://github.com/user-attachments/assets/107520bc-e85f-4c95-b7ba-912a1e6e2f85" width="200px" alt="User Registration"/>
      <br />
      <sub><b>📝 Registration</b></sub>
      <br />
      <sub>Create Account with Personal Details</sub>
    </td>
    <td align="center" width="25%">
      <img src="https://github.com/user-attachments/assets/65fb827c-b3aa-4a01-ae0d-91f09d1fa5ba" width="200px" alt="Email OTP Verification"/>
      <br />
      <sub><b>✉️ OTP Verification</b></sub>
      <br />
      <sub>Email Confirmation Code Entry</sub>
    </td>
    <td align="center" width="25%">
      <img src="https://github.com/user-attachments/assets/0b0d7f33-1edc-4af7-af50-bfc9105528fa" width="200px" alt="Custom Secure PIN Keyboard"/>
      <br />
      <sub><b>🔢 Secure PIN Setup</b></sub>
      <br />
      <sub>Custom Keyboard for PIN Security</sub>
    </td>
  </tr>
</table>

### Main Features
<table>
  <tr>
    <td align="center" width="25%">
      <img src="https://github.com/user-attachments/assets/7556e773-9c0e-49d0-8305-89b7cd4f5758" width="200px" alt="Wallet Home Dashboard"/>
      <br />
      <sub><b>🏠 Home Dashboard</b></sub>
      <br />
      <sub>Balance, Quick Actions & Transactions</sub>
    </td>
    <td align="center" width="25%">
      <img src="https://github.com/user-attachments/assets/17b78bd5-f0ad-47a9-b340-65630bf1b67d" width="200px" alt="Personal QR Code"/>
      <br />
      <sub><b>📱 QR Code</b></sub>
      <br />
      <sub>Share Username via QR</sub>
    </td>
    <td align="center" width="25%">
      <img src="https://github.com/user-attachments/assets/54fc9628-ac7b-47c4-a826-622ae9601710" width="200px" alt="Send Money Transfer"/>
      <br />
      <sub><b>💸 Money Transfer</b></sub>
      <br />
      <sub>Send via Username, QR or Contacts</sub>
    </td>
    <td align="center" width="25%">
      <img src="https://github.com/user-attachments/assets/04c66cba-faec-4b29-8453-d3ed760f4a13" width="200px" alt="Expense Analytics Charts"/>
      <br />
      <sub><b>📊 Expense Analytics</b></sub>
      <br />
      <sub>Visual Charts & Statistics</sub>
    </td>
  </tr>
</table>

### Expense & Profile Management
<table>
  <tr>
    <td align="center" width="33%">
      <img src="https://github.com/user-attachments/assets/a93cca38-7b37-4b9e-b651-1e457da53017" width="200px" alt="Transaction History"/>
      <br />
      <sub><b>📋 Transaction History</b></sub>
      <br />
      <sub>Detailed Expense Breakdown</sub>
    </td>
    <td align="center" width="33%">
      <img src="https://github.com/user-attachments/assets/a8ffe40c-6458-4646-beba-aa536e4b6f44" width="200px" alt="Add New Expense"/>
      <br />
      <sub><b>➕ Add Expense</b></sub>
      <br />
      <sub>Quick Add with Category Selection</sub>
    </td>
    <td align="center" width="33%">
      <img src="https://github.com/user-attachments/assets/05c6e129-9c2a-4e9e-a999-66fddaed5aa8" width="200px" alt="User Profile Settings"/>
      <br />
      <sub><b>👤 Profile & Settings</b></sub>
      <br />
      <sub>Account Management & App Settings</sub>
    </td>
  </tr>
</table>

---

## 🏗️ Architecture

Go Wallet is built using **Clean Architecture** principles combined with **MVVM (Model-View-ViewModel)** pattern:

```
lib/
├── core/                 # Core utilities and constants
├── data/                 # Data layer (repositories, data sources)
├── domain/               # Business logic (entities, use cases)
├── presentation/         # UI layer (screens, widgets, cubits)
└── main.dart            # App entry point
```

**Benefits:**
- ✅ Separation of concerns
- ✅ Testability and maintainability
- ✅ Scalability for future features
- ✅ Independent layer development

---

## 🛠️ Tech Stack

| Category | Technology |
|----------|-----------|
| **Framework** | Flutter 3.0+ |
| **Language** | Dart 3.0+ |
| **Backend** | Firebase (Authentication, Firestore, Storage) |
| **Architecture** | Clean Architecture + MVVM |
| **State Management** | Cubit (flutter_bloc) |
| **Security** | local_auth, jailbreak_root_detection |
| **UI Components** | Custom widgets, Material Design 3 |
| **Charts** | fl_chart |
| **QR Code** | qr_flutter, mobile_scanner |
| **CI/CD** | Fastlane + Firebase App Distribution |

---

## 📥 Download

### APK Release
Download and test the latest version: **v1.0.0+7**

**[📲 Download Go Wallet APK v1.0.0+7](releases/app-release.apk)** (Updated: October 01, 2025)

*Compatible with Android 5.0 (API 21) and above*

---

## 🔄 CI/CD Pipeline

Go Wallet uses **Fastlane** for automated build and distribution:

### Features:
- ✅ Automated build process
- ✅ Code signing management
- ✅ Firebase App Distribution integration
- ✅ Version management
- ✅ Changelog generation

### Pipeline Workflow:
```
Code Push → GitHub Actions → Fastlane Build → Firebase Distribution → Testers Notified
```


## 📝 License

This project is a demonstration/portfolio piece. Feel free to use it for learning purposes.

---

## 📞 Contact

**Developer:** Haitham Magdy Adel

- 📧 Email: [hmagdyadel1@gmail.com](mailto:hmagdyadel1@gmail.com)
- 📱 Phone: +201125516481
- 💼 LinkedIn: [linkedin.com/in/HaithamMagdy](https://www.linkedin.com/in/HaithamMagdy)
- 🐙 GitHub: [github.com/hmagdyadel](https://github.com/hmagdyadel)

---

## 👥 Credits

**UI/UX Design:** Moller Magdy  
**Flutter Development:** Haitham Magdy Adel  
**Backend (Firebase):** Haitham Magdy Adel

---

## 🙏 Acknowledgments

- Flutter team for the amazing framework
- Firebase for backend infrastructure
- Open-source community for excellent packages

---

<p align="center">
  Made with ❤️ by Haitham Magdy Adel
</p>

<p align="center">
  ⭐ Star this repo if you find it helpful!
</p>
