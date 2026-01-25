RIMT Smart Attendance - UPGRADE

# Overview

RIMT Smart Attendance is a Firebase-powered, attendance system designed to eliminate proxy attendance in classrooms. It uses real-time location verification, teacher-controlled session codes, and device fingerprinting to ensure that only students physically present near the teacher can mark attendance.

This project is built entirely with HTML, CSS, JavaScript, and Firebase (Auth + Firestore).

# Problem Statement

Classroom attendance is still inefficient in many institutions:
* Teachers waste valuable lecture time calling roll numbers
* Manual registers make analysis, tracking, and reporting painful
* Maintaining daily, monthly, and subject-wise data is tedious
* Students face delays and confusion during attendance marking

This system is not built only to stop proxy attendance.
Its primary goal is to save classroom time, automate record-keeping, and give teachers instant, structured data, while also reducing proxy attendance as a side benefit.

# Key Features
1.Teacher Panel
Firebase email/password authentication
Generate **unique 6-digit session codes**
Automatic teacher location capture
Live attendance dashboard (real-time)
View all historical attendance records
Filter by date, subject, roll number
Export attendance data to CSV

2. Student Panel
Location permission enforcement
Proximity check with teacher (Haversine formula)
Session-code-based attendance marking
Duplicate prevention using device fingerprinting
Instant feedback on attendance status

3. Live View Panel
Public live attendance view
Real-time Firestore updates
Device, time, and distance visibility

---Core Logic 

1. **Teacher logs in** using Firebase Authentication
2. Teacher generates a session → system stores:

   * Subject
   * Teacher latitude & longitude
   * Session code
3. Student enters session code 
4. System:
   * Fetches teacher location
   * Calculates distance using Haversine formula
   * Allows attendance only if ≤100 meters
     
5. Attendance is stored in Firestore with:
   * Location
   * Distance
   * Device ID
   * Timestamp

--- Location & Proximity Enforcement

* Uses `navigator.geolocation`
* High accuracy mode enabled
* Distance calculated in real-time
* Attendance rejected if:
  * Location permission denied
  * Student is outside allowed radius

Max Distance: 100 meters

## Security Measures

✔ Firebase Authentication for teachers
✔ Firestore rules (required in production)
✔ Device-based duplicate prevention
✔ Session-based attendance isolation
✔ No hardcoded credentials



## 🛠 Tech Stack

| Layer    | Technology              |
| -------- | ----------------------- |
| Frontend | HTML5, CSS3, JavaScript |
| Backend  | Firebase Firestore      |
| Auth     | Firebase Authentication |
| Realtime | Firestore Snapshots     |
| Location | Browser Geolocation API |

#  Project Structure

```
/
├── index.html        # Complete UI + Logic
├── README.md         # Project documentation
└── Firebase Console  # Auth + Firestore
```

# Firebase Setup

* Create Firebase project
* Enable Authentication (Email/Password)
* Enable Firestore Database
* Replace Firebase config in code

# Firestore Collections

**sessions**

```
{ code, subject, teacherLat, teacherLng, createdAt }
```

**attendance**

```
{ name, roll, subject, code, device, lat, lng, timestamp }
```

# Export & Reporting

* CSV export supported
* Compatible with Excel & Google Sheets
* Includes:

  * Student details
  * Session codes
  * Location distance
  * Timestamp


## 🔮 Future Improvements

* Face recognition (camera-based verification)
* QR-based dynamic tokens
* Admin dashboard
* Mobile app version
* Stronger device fingerprinting
* Anti-GPS-spoof detection

---

## 🧪 Testing Checklist

* ✅ Teacher login/logout
* ✅ Session creation
* ✅ Student proximity validation
* ✅ Duplicate prevention
* ✅ Live updates
* ✅ CSV export

---
GITHUB - WEB APP : https://preeti-kaur245.github.io/RIMT-Smart-Attendance-upgrade/
NETIFY - WEB APP : https://rimt-smart-attendance-dc3d26.netlify.app/
FIREBASE - HOSTING : coming soon 
APP MODEL - coming soon

## 👨‍💻 Author

Developed by: Manpreet kaur -  CodeVerse
Institution: RIMT University
Purpose: Academic + Practical Solution
#RIMT #SmartAttendance #EdTech #StartupIndia
© 2025 RIMT Smart Attendance. Made for RIMT, by RIMTians.

This project is intended for **educational and institutional use**.

