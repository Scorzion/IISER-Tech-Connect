# IISER Tech Connect ✨

## 🚀 Empowering the Tech Pulse of IISER Bhopal

**IISER Tech Connect** is a web-based prototype I built to reimagine the Google Developer Group (GDG) on Campus experience at IISER Bhopal. The aim is to foster a vibrant, inclusive, and tightly-knit tech ecosystem that offers real opportunities for learning, mentorship, and industry exposure.

## 💡 The Problem We're Tackling

Despite the technical potential and research strength at IISER Bhopal, our GDG community has been facing a few pressing challenges:

* **Interdisciplinary Disconnect:** There’s a notable gap when it comes to integrating students from Physics, Chemistry, and Biology into tech-driven efforts—limiting the scope of innovative, cross-domain solutions.

* **Unstructured Growth & Mentorship:** Many juniors struggle with direction—there’s no consistent mentoring or long-term project engagement. Events often happen in isolation without continuity or real-world context.

* **Weak Industry & Alumni Pipeline:** There's limited access to alumni in product-based tech roles and a thin connection with industry professionals—both critical for guidance, networking, and internships.

## 🎯 My Purpose-Built Solution

**IISER Tech Connect** is my answer to these gaps—a centralized, purpose-driven platform to bring coherence, mentorship, and opportunity to our growing tech community.

* **Interdisciplinary Collaboration:** Users can post or join research-oriented tech projects, encouraging scientists and engineers to collaborate and think beyond their silos.

* **Structured Mentorship Programs:** A built-in mentorship hub and guided learning paths give juniors the support they need to grow through pet projects and personalized development tracks.

* **Increased Engagement & Visibility:** A central dashboard for all GDG activities—including personalized event recommendations—boosts community interaction and ownership.

* **Strong Industry + Alumni Gateway:** By integrating mentor profiles and professional connections, the platform opens new doors to insights, networking sessions, and career guidance from those already in the field.

## ✨ Key Features of the Prototype

This is a working prototype and includes the following core features:

1.  **User Authentication** – Secure sign-up/login via email and password.
2.  **Customizable User Profiles** – Users can update bios, list tech interests (e.g., AI, Bioinformatics), share contact details, and optionally declare availability as mentors.
3.  **Project Collaboration Hub** – A space to post, browse, and collaborate on interdisciplinary projects.
4.  **Mentorship Directory** – A searchable list of registered mentors with their skills and interests.
5.  **Events & Workshops Page** – A dynamic event board with a **"Get Personalized Recommendations"** feature (powered by simulated Gemini API) based on user interests.

## 🛠️ Tech Stack & Tools

I chose tools that scale well and align with Google’s ecosystem:

* **Firebase:**
    * **Authentication:** Secure user login.
    * **Cloud Firestore:** Real-time, NoSQL database for storing user and project data.

* **Google IDX:** For modern, cloud-native development.

* **React:** My go-to library for building a dynamic, component-based UI.

* **Tailwind CSS:** For sleek, responsive, utility-first styling.

* **Gemini API (Simulated):** Intended for future use in personalized suggestions and content generation.

## 🚀 Getting Started

This project runs entirely from a single HTML file—simple to deploy, fast to iterate!

### Prerequisites

You'll need:

* A **Google Account**
* A **GitHub Account** (if deploying via GitHub Pages)

---

### 1. Firebase Setup

To enable authentication and database features, follow these steps:

#### Create a Firebase Project

1. Visit the [Firebase Console](https://console.firebase.google.com/)
2. Click **"Add project"**, and follow the steps to create a new one.

#### Add a Web App

1. Inside your Firebase project, click the web icon (`</>`) to register a new web app.
2. Firebase will give you a `firebaseConfig` object—copy this safely.

#### Enable Email/Password Authentication

1. In the Firebase Console, go to **Authentication > Sign-in method**
2. Enable **Email/Password**, then click **Save**

#### Set Up Firestore Security Rules

1. Go to **Firestore Database > Rules**
2. Replace the default rules with the following:

```firestore
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /artifacts/{appId}/public/data/projects/{projectId} {
      allow read, write: if request.auth != null;
    }

    match /artifacts/{appId}/users/{userId}/profile/data {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }

    match /artifacts/{appId}/users/{userId} {
      allow read: if request.auth != null;
    }
  }
}
```

3. Click **Publish**

---

### 2. Insert Your Firebase Config in `index.html`

Open your `index.html` file in your preferred editor.

Find the `firebaseConfig` object (inside a `<script type="module">` block) around line 50.

Replace the placeholder with your actual config:

```javascript
const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {
    apiKey: "AIzaSyC-YOUR_API_KEY",
    authDomain: "your-project-id.firebaseapp.com",
    projectId: "your-project-id",
    storageBucket: "your-project-id.appspot.com",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

> 🔥 Make sure to uncomment and replace the values properly.

---

### 3. Test Locally (Optional but Recommended)

To preview Firebase features locally:

1. In your terminal, `cd` into the folder containing `index.html`
2. Run a Python server:

```bash
python -m http.server
```

3. Open [http://localhost:8000](http://localhost:8000) in your browser.

---

### 4. Deploy via GitHub Pages

#### Steps:

1. Create a **new public repo** on GitHub (e.g., `iiser-tech-connect`)
2. Upload your modified `index.html` to the root
3. Go to **Settings > Pages**
4. Under "Source", choose `main` branch and root folder `/`
5. Save, and wait for GitHub Pages to publish the site

> You'll find the live URL under **Pages** (e.g., `https://your-username.github.io/iiser-tech-connect/`)

---

## 💻 Using the App

Here's a quick walkthrough:

1. **Register or Login** – Sign up using your email and password  
2. **Profile Tab** – Add your name, bio, interests (comma-separated), contact info, and mentor status  
3. **Projects Section** – Post your research or tech ideas, or explore others’ projects  
4. **Mentors Page** – Browse mentor profiles based on tech interests and connect directly  
5. **Events Page** – View upcoming GDG events, and use “Get Personalized Recommendations” for smart suggestions

---

## 🌱 Final Words

This is just the beginning. IISER Tech Connect is a passion project aimed at making our tech community stronger, smarter, and more collaborative. If you’re at IISER Bhopal and passionate about tech, research, or mentorship, I invite you to explore and contribute.

Let’s build something great—together.
