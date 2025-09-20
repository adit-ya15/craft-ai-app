# CraftAI: AI-Powered Marketing Assistant for Artisans
CraftAI is a web-based platform designed to empower local and traditional artisans by providing them with a suite of generative AI tools to enhance their digital presence. It bridges the gap between traditional craftsmanship and the modern digital marketplace, offering an end-to-end solution from content creation to a live, community-driven marketplace.

### Live Demo: [https://craft-ai-app.netlify.app/]

## The Problem
Indian artisans, rich in cultural heritage and traditional skills, often face significant challenges in the digital world. A lack of digital marketing skills, limited resources, and the difficulty of writing compelling stories about their craft severely restrict their market reach and profitability.

## The Solution: An End-to-End Toolkit
CraftAI provides a complete, zero-installation toolkit that takes an artisan from Story to Sale. It allows them to:

1. **Create** compelling marketing content using AI.

2. **List** their products with beautiful, AI-generated descriptions.

3. **Showcase** their work on a live, real-time marketplace.

## Key Features
- ### Multi-Language AI Marketing Suite:

  - **Product Description Generator**: Creates rich, descriptive, and SEO-friendly listings from text or product photos.

  - **Social Media Post Creator**: Generates engaging posts with emojis and hashtags.

  - **Brand Story Writer**: Crafts authentic "About Us" narratives.

  - **Marketing Copy Generator**: Produces catchy promotional text for sales.

- ### Integrated E-commerce Platform:

  - **Personal Product Management**: A private dashboard for artisans to upload, manage, and             delete their own listings.

  - **Live Community Marketplace**: A real-time, shared marketplace where products from all artisans are instantly displayed for customers to discover.

- ### Zero-Installation & Fully Responsive:

  - Built as a single HTML file, the application runs in any modern browser on any device without any setup required for the end-user.

- ### Demo Mode for Presentations:

  - The marketplace is pre-populated with beautiful sample products for demonstration purposes, which are replaced by live data as soon as a real product is listed.

## Technology Stack
- **Frontend**: HTML5, Tailwind CSS, Vanilla JavaScript (ESM)

- **Backend (Serverless)**:

- **Database**: Google Firebase Firestore (for a real-time NoSQL database)

- **Authentication**: Google Firebase Authentication (for Anonymous sign-in)

- **Generative AI**: Google Gemini API

## Local Setup and Configuration Guide
To run this project on your local machine, follow these steps.

### 1. Download the Code

- Download the index.html file (renamed from artisan-ai-assistant.html).

### 2. Configure Firebase

- Create a new project in the Firebase Console.

- **Enable Authentication**: Go to the "Authentication" section, click the "Sign-in method" tab, and enable the Anonymous provider.

- **Create Firestore Database**: Go to the "Firestore Database" section, click "Create database", and start in test mode.

- **Update Security Rules**: Go to the "Rules" tab in Firestore and replace the existing rules with the following:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /artifacts/{appId}/public/data/{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```
- **Get Config Keys**: In your Firebase project settings, find your web app's configuration object.

### 3. Add Keys to index.html

- Open the index.html file.

- **Add Firebase Config**: Right before the closing </head> tag, add the following script and fill it with your Firebase config keys:
```
<script>
    const firebaseConfig = {
        apiKey: "YOUR_API_KEY",
        authDomain: "YOUR_AUTH_DOMAIN",
        projectId: "YOUR_PROJECT_ID",
        storageBucket: "YOUR_STORAGE_BUCKET",
        messagingSenderId: "YOUR_SENDER_ID",
        appId: "YOUR_APP_ID"
    };
    window.__firebase_config = JSON.stringify(firebaseConfig);
    window.__app_id = firebaseConfig.projectId;
    window.__initial_auth_token = ""; // Leave empty
</script>
```

-  **Add Gemini API Key**: In the main script at the bottom of the file, find the following line and add your Google AI API key:
```
const API_KEY = "YOUR_GEMINI_API_KEY";
```

### 4. Run the Application

- Save the index.html file and open it in any modern web browser. The application is now fully functional.
