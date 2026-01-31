# Deploying Online Job Portal to Render

This guide explains how to deploy the application to [Render](https://render.com/).

## Prerequisites
- A GitHub repository with this code.
- A Render account.
- Your Firebase project configuration keys.

## Deployment Steps

1.  **Push to GitHub**: Ensure your latest changes are pushed to your GitHub repository.
2.  **Create New Static Site on Render**:
    - Go to your Render Dashboard.
    - Click **New +** and select **Static Site**.
    - Connect your GitHub repository.
3.  **Configure Service**:
    - **Name**: Choose a name (e.g., `online-job-portal`).
    - **Branch**: Select your main branch (e.g., `main` or `master`).
    - **Build Command**: `npm install && npm run build`
    - **Publish Directory**: `dist`
4.  **Environment Variables**:
    - Click on **Advanced** or find the **Environment** tab after creation.
    - Add the following variables (values found in your Firebase Project Settings):
      - `VITE_FIREBASE_API_KEY`
      - `VITE_FIREBASE_AUTH_DOMAIN`
      - `VITE_FIREBASE_PROJECT_ID`
      - `VITE_FIREBASE_STORAGE_BUCKET`
      - `VITE_FIREBASE_MESSAGING_SENDER_ID`
      - `VITE_FIREBASE_APP_ID`

    ### How to find these values:
    1.  Go to the [Firebase Console](https://console.firebase.google.com/).
    2.  Select your project.
    3.  Click the **Gear icon** (Settings) next to "Project Overview" in the sidebar and select **Project settings**.
    4.  Scroll down to the **Your apps** section.
    5.  Select your web app (indicated by `</>`). If you haven't created one, click **Add app** and select the web platform (`</>`).
    6.  Under **SDK setup and configuration**, select **Config**.
    7.  You will see a code snippet with `const firebaseConfig = { ... }`. Copy the values inside the quotes for each key.

5.  **Deploy**: Render will automatically start building. Once finished, your site will be live!

> [!NOTE]
> Since this is a client-side React app using Firebase, we deploy it as a **Static Site**. All the logic happens in the user's browser, communicating directly with Firebase.
