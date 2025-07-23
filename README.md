# IISER Tech Connect ✨

## 🚀 Empowering IISER Bhopal's Tech Community

**IISER Tech Connect** is a dynamic web-based prototype designed to revolutionize the Google Developer Group (GDG) on Campus experience at IISER Bhopal. Our mission is to cultivate a vibrant, inclusive, and interconnected tech ecosystem, providing unparalleled opportunities for learning, mentorship, and real-world industry exposure.

## 💡 The Challenge We're Solving

Despite IISER Bhopal's research prowess and engineering talent, the GDG on Campus community faces critical hurdles:

* **Bridging the Interdisciplinary Divide:** A significant gap exists in integrating students from core sciences (Biology, Chemistry, Physics) into tech-driven initiatives, limiting the potential for groundbreaking interdisciplinary solutions.

* **Lack of Structured Growth & Mentorship:** Junior developers often struggle to find consistent guidance and clear learning pathways. Events tend to be isolated, hindering sustained skill development and practical project experience.

* **Limited Industry & Alumni Gateway:** Our community currently lacks robust connections with industry professionals and a strong alumni network in product-based tech roles, restricting vital access to real-world insights, networking, and career opportunities.

## 🎯 Our Innovative Solution

IISER Tech Connect offers a centralized, intelligent platform meticulously crafted to overcome these challenges:

* **Fostering Interdisciplinarity:** We're creating dedicated showcases for research-oriented tech projects and actively promoting cross-disciplinary collaboration, inviting diverse perspectives to solve complex problems.

* **Structured Mentorship & Learning:** Our platform formalizes mentorship programs, offering clear learning roadmaps and hands-on "pet project" opportunities under experienced guidance, ensuring continuous skill enhancement.

* **Boosting Engagement & Visibility:** Leveraging personalized event recommendations and a central hub for all GDG activities, we aim to dramatically improve event turnout and community participation.

* **Building Robust Industry Bridges:** An integrated gateway connects students with our growing alumni network and industry experts, facilitating invaluable insights, networking events, and career guidance.

## ✨ Prototype Key Features

This working prototype showcases the core functionalities that form the backbone of IISER Tech Connect:

1.  **User Authentication:** Seamless and secure registration and login using email and password.

2.  **Customizable User Profiles:** Students can build rich profiles, detailing their name, bio, interests (e.g., AI, Bioinformatics, Web Dev), contact information, and indicate their availability as a mentor.

3.  **Interdisciplinary Project Hub:** A collaborative space where users can post their projects, research ideas, or problem statements, and browse others' contributions to find collaborators or inspiration. Users can add, view, and manage their own projects.

4.  **Mentorship Hub:** A dedicated directory listing registered mentors with their profiles, tech lead roles, and interests, enabling students to easily identify and connect with suitable guides.

5.  **Dynamic Events & Workshops:** Displays a curated list of upcoming GDG events and workshops. Includes a **"Get Personalized Recommendations"** feature (simulated using Google AI's Gemini API capabilities) that suggests events based on a user's declared interests.

## 🛠️ Technologies Powering IISER Tech Connect

This solution is proudly built leveraging Google's powerful and scalable ecosystem:

* **Firebase:**
    * **Firebase Authentication:** For robust and secure user identity management.
    * **Cloud Firestore:** A flexible, scalable NoSQL cloud database for real-time data storage and synchronization.

* **IDX (Integrated Development Experience):** The cutting-edge development environment used to build this prototype efficiently.

* **Google AI (Gemini API):** (Currently simulated) Planned for advanced features like intelligent content generation and highly personalized event recommendations.

* **React:** A declarative and efficient JavaScript library for building dynamic and responsive user interfaces.

* **Tailwind CSS:** A utility-first CSS framework that enables rapid and consistent styling for a modern, mobile-first design.

## 🚀 Getting Started

This project is delivered as a single HTML file, making deployment incredibly straightforward!

### Prerequisites

Before you begin, ensure you have:

* A **Google Account**

* A **GitHub Account** (if you plan to deploy using GitHub Pages)

### 1. Firebase Project Setup (Crucial!)

For the authentication and data storage features to work, you **must** configure your own Firebase project:

* **Create a Firebase Project:**
    1.  Navigate to the [Firebase Console](https://console.firebase.google.com/).
    2.  Click **"Add project"** and follow the on-screen instructions to create a new project.

* **Add a Web App to Your Project:**
    1.  From your new Firebase project's overview, click the **web icon (`</>`)** to register a new web application.
    2.  Follow the registration steps. Firebase will provide you with a `firebaseConfig` JavaScript object. **Copy this entire object carefully.**

* **Enable Email/Password Authentication:**
    1.  In the Firebase Console, go to **"Authentication"** (under the "Build" section).
    2.  Click the **"Sign-in method"** tab.
    3.  Locate **"Email/Password"** and **enable it** by toggling the switch. Click **"Save"**.

* **Set Up Firestore Security Rules:**
    1.  In the Firebase Console, go to **"Firestore Database"** (under "Build").
    2.  Click on the **"Rules"** tab.
    3.  **Replace the existing rules** in the editor with the following to ensure proper data access:

        ```firestore
        rules_version = '2';
        service cloud.firestore {
          match /databases/{database}/documents {
            // Allow authenticated users to read/write public project data
            match /artifacts/{appId}/public/data/projects/{projectId} {
              allow read, write: if request.auth != null;
            }

            // Allow authenticated users to read/write their own private profile data
            match /artifacts/{appId}/users/{userId}/profile/data {
              allow read, write: if request.auth != null && request.auth.uid == userId;
            }

            // Allow authenticated users to list user IDs (e.g., to find mentors)
            match /artifacts/{appId}/users/{userId} {
              allow read: if request.auth != null;
            }
          }
        }
        ```
    4.  Click **"Publish"** to apply the rules.

### 2. Update `index.html` with Your Firebase Configuration

* Open the `index.html` file (from the prototype code) in your preferred text editor.

* Locate the `<script type="module">` block, specifically the `firebaseConfig` variable (around line 50).

* **Replace the placeholder object** with the actual `firebaseConfig` object you copied from your Firebase Console.

    ```javascript
    const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {
        // PASTE YOUR ACTUAL FIREBASE CONFIG HERE, e.g.:
        apiKey: "AIzaSyC-YOUR_API_KEY",
        authDomain: "your-project-id.firebaseapp.com",
        projectId: "your-project-id",
        storageBucket: "your-project-id.appspot.com",
        messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
        appId: "YOUR_APP_ID"
    };
    ```
    *Ensure you uncomment the lines and replace `YOUR_...` with your specific values.*

### 3. Running the Prototype Locally (Optional)

For a quick local test (recommended for Firebase functionality):

* Navigate to the directory containing `index.html` in your terminal.

* Run a simple Python HTTP server:
    ```bash
    python -m http.server
    ```

* Open your web browser and go to `http://localhost:8000`.

### 4. Deploying to GitHub Pages

Share your prototype with the world!

1.  **Create a New GitHub Repository:** If you haven't already, create a new **public** repository on GitHub (e.g., `iiser-tech-connect`).

2.  **Upload `index.html`:** Add (or commit) your modified `index.html` file directly to the **root** of your repository.

3.  **Enable GitHub Pages:**
    * Go to your repository's **"Settings"** tab.
    * In the left sidebar, click **"Pages"**.
    * Under "Build and deployment", select **"Deploy from a branch"** for the source.
    * For "Branch", choose your primary branch (usually `main`) and select `/ (root)` for the folder.
    * Click **"Save"**.

4.  **Access Your Live Site:** GitHub Pages will now build and deploy your site. This usually takes a few minutes. Once complete, you'll find the live URL under the "Pages" section (e.g., `https://your-username.github.io/your-repo-name/`).

## 💻 How to Use the App

1.  **Register/Login:** Create a new account using your email and a password (minimum 6 characters) or log in if you already have an account.

2.  **Profile:** Navigate to the "Profile" tab to update your personal details, write a bio, list your technical interests (comma-separated), provide contact information, and indicate if you'd like to serve as a mentor.

3.  **Projects:** Visit the "Projects" section to add your own interdisciplinary projects or browse projects submitted by other community members. You can also delete your own entries.

4.  **Mentors:** Explore the "Mentors" tab to see a list of available mentors, view their expertise, and find their contact details to initiate a connection.

5.  **Events:** Check the "Events" page for upcoming workshops and sessions. Click "Get Personalized Recommendations" to see events tailored to your interests (as defined in your profile).

---

We encourage you to explore, contribute, and help expand this prototype into a full-fledged platform for the IISER Bhopal GDG on Campus community!
