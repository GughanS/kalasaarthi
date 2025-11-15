# KalaSaarthi: The AI-Powered Artisan Marketplace

KalaSaarthi is an AI-powered web application designed to help traditional artisans sell their products online, with features for multi-language AI content generation and complete e-commerce functionality.

## The Problem

Traditional Indian artisans, while masters of their craft, are often locked out of the digital economy. They face significant barriers like a lack of digital marketing skills, difficulty in writing compelling product listings (especially in English), and the complexity of managing an online store. This "digital divide" limits their livelihood and risks their cultural heritage being lost.

## Our Solution

KalaSaarthi (meaning "Art's Charioteer") is a single-page web application that acts as an AI partner for these artisans. It simplifies the process of selling online into three simple steps: upload a photo, write a story (in their native language), and let the AI handle the rest.

The app generate professional, market-ready product titles, descriptions, and tags in the language of their choice (English, Hindi, or Tamil), completely removing the marketing and language barrier.

## Key Features

Dual User Roles: Separate, secure dashboards for "Buyers" and "Sellers".

AI Content Generation: Integrated Google Gemini API (gemini-2.5-flash-preview-09-2025) to generate product listings from a simple story.

Multilingual Support: Full UI translation and AI generation in English, हिन्दी (Hindi), and தமிழ் (Tamil).

Complete E-commerce Flow: Full marketplace, product filtering (by category, price, etc.), shopping cart, and order history.

Seller Dashboard: Easy-to-use-portal for artisans to manage products (Create, Read, Delete) and view sales analytics.

Modern Uploads: Supports drag-and-drop, file upload, and direct-from-camera photo capture.

Real-time Database: Built on Firebase Firestore for instant inventory updates (e.g., "Available" / "Sold").

Accessibility: Features like voice search, keyboard navigation, and a responsive light/dark theme.

## Tech Stack

Frontend: HTML5, Tailwind CSS, Vanilla JavaScript (ES6 Modules)

Backend: Firebase (Firestore Database, Firebase Authentication)

Generative AI: Google Gemini API

Libraries: Chart.js (for seller analytics)

## How to Run Locally

This project is a single, self-contained HTML file. You can run it directly in your browser after setting up the necessary backend services.

* Firebase Setup

  Go to the Firebase Console and create a new project.

  Enable Authentication:

  Go to Authentication -> Sign-in method.

  Enable Email/Password.

  Enable Anonymous. (This is crucial for the app to work locally without a custom token).

  Enable Firestore:

  Go to Firestore Database and create a database.

  Start in Test Mode. The app's database paths (artifacts/...) are designed for a specific environment. For local testing, you will need to either:

  Option A (Recommended): Update your Firestore Security Rules to allow reads/writes for authenticated users.

  Option B (Quickest): Manually edit the Firestore paths in KalaSaarthi_Marketplace.html to remove the /artifacts/appId/ prefixes (e.g., change                      doc(db,"artifacts", appId, "users", ...) to doc(db, "users", ...)).

  Get Config:

  In your project settings, find your Web App configuration object.

* Google Gemini API Setup

  Go to Google AI Studio and create a new API key.

  Make sure the key is enabled for the "Gemini API".

* Configure the App

  Open KalaSaarthi_Marketplace.html.

  Find the <script type="module"> section (around line 1224).

  Locate the fallback firebaseConfig object and paste your Firebase config there.

  Locate the GEMINI_API_KEY constant and paste your Gemini API key as a string.
  ```
  // ...
  // UPDATED: Replaced fallback config with your specific project details
  const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {
      apiKey: "PASTE_YOUR_FIREBASE_API_KEY_HERE",
      authDomain: "YOUR-PROJECT-ID.firebaseapp.com",
      projectId: "YOUR-PROJECT-ID",
      storageBucket: "YOUR-PROJECT-ID.appspot.com",
      messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID",
      measurementId: "YOUR_MEASUREMENT_ID"
  };
  // ...

  // --- Gemini API Configuration ---
  const GEMINI_API_KEY = "PASTE_YOUR_GEMINI_API_KEY_HERE"; 
  const GEMINI_API_URL = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${GEMINI_API_KEY}`;
  // ...
  ```


* Run

  Simply open the KalaSaarthi_Marketplace.html file in any modern web browser. The app will sign you in anonymously (since initialAuthToken will be null) and you    can start using it.

## License

This project is open-source. Feel free to use, modify, and distribute it.
