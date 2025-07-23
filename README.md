# IISER Tech Connect

## 🚀 Project Overview

**IISER Tech Connect** is a web-based prototype addressing key challenges within the GDG on Campus community at IISER Bhopal. It aims to build a more inclusive, structured, and connected tech ecosystem, enhancing learning, mentorship, and industry exposure for students.

## 💡 Problem Statement

The GDG on Campus at IISER Bhopal faces a multi-faceted disconnect:

* **Limited Interdisciplinary Engagement:** Poor involvement of core science students in tech activities.

* **Insufficient Mentorship & Learning Pathways:** Juniors lack structured guidance and project-based learning.

* **Weak Industry & Alumni Connections:** Limited access to real-world insights and career opportunities.

## 🎯 Solution Approach

IISER Tech Connect provides a centralized platform to:

* **Foster Interdisciplinarity:** Dedicated spaces for research-oriented tech projects and cross-disciplinary collaboration.

* **Structure Mentorship:** Formalized programs with clear learning paths and hands-on experience.

* **Boost Engagement:** Personalized event recommendations and a central hub for GDG activities.

* **Build Industry Bridges:** A gateway for alumni and industry professionals to connect with students.

## ✨ Key Features (Prototype)

The prototype demonstrates:

1.  **User Authentication:** Secure registration and login.

2.  **User Profiles:** Customizable profiles with interests and mentor status.

3.  **Interdisciplinary Project Hub:** Add, view, and delete projects.

4.  **Mentorship Hub:** Browse and connect with registered mentors.

5.  **Events & Workshops:** Lists events with simulated personalized recommendations.

## 🛠️ Technologies Used

Built with Google's scalable technologies:

* **Firebase:** Authentication, Cloud Firestore.

* **IDX (Integrated Development Experience)**

* **Google AI (Gemini API):** (Simulated) For recommendations.

* **React:** Frontend UI.

* **Tailwind CSS:** Styling.

## 🚀 Setup & Running the Project

This is a single HTML file project, easy to deploy.

### Prerequisites

* Google Account

* GitHub Account (for GitHub Pages)

### 1. Firebase Project Setup

* **Create Project & Web App:** Go to [Firebase Console](https://console.firebase.google.com/), create a project, and add a web app to get your `firebaseConfig`.

* **Enable Email/Password Auth:** In Firebase Console > Authentication > Sign-in method, enable "Email/Password".

* **Set Firestore Security Rules:** In Firebase Console > Firestore Database > Rules, replace existing rules with the provided security rules (allowing authenticated read/write for public projects and user-specific profiles). **Remember to publish the rules.**

### 2. Update `index.html` with Firebase Config

* Open `index.html`.

* Locate the `firebaseConfig` object within `<script type="module">`.

* **Replace the placeholder** with your actual `firebaseConfig` copied from Firebase Console.

### 3. Running Locally (Optional)

* Use `python -m http.server` and open `http://localhost:8000`.

### 4. Deploying to GitHub Pages

1.  Create a new GitHub Repository.

2.  Upload `index.html` to the repository root.

3.  Go to **Repository Settings > Pages**, select `main` branch and `/ (root)` folder, then click **Save**.

4.  Access your site via the provided GitHub Pages link.

## 💻 Usage

1.  **Register/Login:** Create an account or sign in.

2.  **Profile:** Update your details and interests.

3.  **Projects:** Add your projects or browse others.

4.  **Mentors:** Find and connect with mentors.

5.  **Events:** Check upcoming events and get recommendations.

Feel free to explore, contribute, and expand upon this prototype!
